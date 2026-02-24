# doc

返回文档获取集合中指定的文档对象，需通过 _id 参数指定文档的 id。doc 方法定义：
```
function doc(_id: string): Document;
```


## 请求参数

_id: string 文档 id。

## 返回参数

Document 文档对象。

## 云函数示例


```JavaScript
const cloud = require("@alipay/faas-server-sdk");

exports.main = async (event, context) => {

const db = cloud.database()

return await db.collection('example').doc("some-id")
};
```
​
