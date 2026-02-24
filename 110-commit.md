# commit

返回文档结束事务并进行提交。commit 方法类型定义：
```TypeScript
function commit(): Promise<void>
```


## 示例


```JavaScript
const cloud = require("@alipay/faas-server-sdk");

exports.main = async (event, context) => {
const db = cloud.database();
try {
const transaction = await db.startTransaction();
const order = await transaction.collection('order').add({
data: {
orderName: 'order-123',
status: 'CREATED',
},
});
await transaction.commit();
return {
success: true,
order,
};
} catch(e) {
return {
success: false,
message: e.message,
};
}
};
```
​
