# collection

返回文档获取集合对象，需要通过 collectionName 参数指定集合名。collection 方法类型定义：
```
function collection(collectionName: string): Collection;
```


## 请求参数

collectionName: string 集合名。

## 返回参数

Collection 集合对象。

## 示例


```TypeScript
const cloud = require("@alipay/faas-server-sdk");

exports.main = async (event, context) => {
const db = cloud.database()
return await db.collection('example').get()
};
```
​
