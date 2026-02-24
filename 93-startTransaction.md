# startTransaction

返回文档创建并开始新事务。startTransaction 方法类型定义：
```
function startTransaction(): Promise<Transaction>
```


## 返回参数

Promise<Transaction>.transaction 事务对象，提供了 commit， rollback 以及 collection 方法用于进行事务操作。●collection 方法用于在当前事务下获取集合对象并行相应操作。●rollback 方法用于在需要终止事务并进行回滚时调用。●commit 方法用于结束事务并进行提交时调用。

## 示例

购物时，创建订单并扣款的事务示例：
```JavaScript
const cloud = require("@alipay/faas-server-sdk");

exports.main = async (event, context) => {
const db = cloud.database();
try {
const transaction = await db.startTransaction();
const orderCollection = transaction.collection('order');
const accountCollection = transaction.collection('account');
const account = await accountCollection.doc('account-123').get();
if (account.amount < 10) {
console.log('事务执行失败，下单失败');
await transaction.rollback();
return {
success: false,
message: '账户余额不足',
};
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
await transaction.commit();
console.log('事务执行成功，下单成功');
return {
success: true,
orderId: order._id,
amountLeft,
};
```
​
