# rollback

返回文档终止事务并进行回滚。rollback 方法类型定义：
```
function rollback(reason: any): Promise<void>
```


## 请求参数

reason: any 事务回滚原因，在 runTransaction 回调函数中使用时，将由 runTransaction 函数运行结束后抛出该值。

## 示例


```JavaScript
const cloud = require("@alipay/faas-server-sdk");

exports.main = async (event, context) => {
const db = cloud.database();
try {
await db.runTransaction(async transaction => {
await transaction.collection('order').add({
data: {
orderName: 'order-123',
status: 'CREATED',
},
});
await transaction.rollback(new Error('下单失败，余额不足'));
});
} catch(e) {
return {
success: false,
message: e.message, // '下单失败，余额不足'
};
}
};
```
​
