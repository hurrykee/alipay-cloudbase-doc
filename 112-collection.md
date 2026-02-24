# collection

返回文档获取当前事务下的集合对象并行相应操作。collection 函数的定义：
```
function collection(collectionName: string): Collection;
```


## 请求参数

collectionName: string 集合名。

## 返回参数

Collection 集合对象。

## 示例


```JavaScript
const cloud = require("@alipay/faas-server-sdk");

exports.main = async (event, context) => {
const db = cloud.database();
const res = await db.runTransaction(async transaction => {
await transaction.collection('order').add({
data: {
orderName: 'order-123',
status: 'CREATED',
},
});
});
return {
success: true,
data: res,
}
};
```
​
