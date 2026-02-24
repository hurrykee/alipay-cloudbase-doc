# runTransaction

返回文档新建事务并在事务中执行回调函数。runTransaction 方法类型定义：
```
function runTransaction<T = any>(scope: (transaction: Transaction) => Promise<T>): Promise<T>
```


## 请求参数

scope: (transaction: Transaction) => Promise<T> 回调函数，回调函数的入参为新创建的事务。

## 返回参数

Promise<T>.该函数返回值为回调函数的返回值。

## 回调函数说明

用户实现事务处理回调函数，该函数接收一个参数 transaction，可对事务进行操作。 transaction 对象提供了 commit， rollback 以及 collection 方法。 ●collection 方法用于在当前事务下获取集合对象并行相应操作。●rollback 方法用于在需要终止事务并进行回滚时调用。在回调函数抛出异常时，若事务未被提交/回滚，则 runTransaction 会自动调用该方法。●commit 方法用于结束事务并进行提交时调用。通常不需要手动执行，runTransaction 执行结束后会自动调用该方法。在回调函数执行结束后，runTransaction 会认为当前事务已经执行完成，会自动提交事务，并返回事务处理回调函数的返回值。因此，若在回调函数中有其他异步操作（例如，setTimeout、未被 await 的异步函数）可能导致异步执行异常。在回调函数中，可手动调用 rollback 并传入 reason，在回调函数执行结束后，将抛出 reason。若回调函数抛出异常，且未手动调用 collection 或 rollback，此时 runTransaction 将自动调用 rollback ,再将异常抛出。

## 注意事项

1在事务处理回调函数中，需要通过 transaction 对象获取 collection 对象，直接通过 cloud.database().collection() 获取的 collection 对象无法读取事务中的数据。2在事务回调函数中，嵌套再次调用 runTransaction 将创建新的事务，即嵌套的 runTransaction 和外层的 runTransaction 属于两个事务。

## 示例

购物时，创建订单并扣款的事务例子。
```JavaScript
const cloud = require("@alipay/faas-server-sdk");

exports.main = async (event, context) => {
const db = cloud.database();
try {
const res = await db.runTransaction(async transaction => {
const orderCollection = transaction.collection('order');
const accountCollection = transaction.collection('account');
const account = await accountCollection.doc('account-123').get();
if (account.amount < 10) {
// 抛出异常，终止事务执行并回滚
throw new Error('账户余额不足');
}
const order = await orderCollection.add({
data: {
orderName: 'order-123',
status: 'CREATED',
},
});
const amountLeft = account.amount - 10;
await accountCollection.doc('account-123').update({
data: {
amount: amountLeft,
}
});
return {
orderId: order._id,
amountLeft,
};
});
console.log('事务执行成功，下单成功', res);
return {
success: true,
orderId: res.orderId,
amountLeft: res.amountLeft,
};
```
​
