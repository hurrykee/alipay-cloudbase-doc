# add

返回文档新增文档，需通过 _id 参数指定文档的 id。add 方法类型定义：
```
function doc(param: AddDocumentParam): Promise<AddDocumentResult>;
```


## 请求参数

AddDocumentParam.●可设置 data._id 以指定新建文档的 id，不传则由服务端生成。●若未设置 data._openid，则默认会设置为当前上下文中用户的 openid。
| 字段名 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| data | object | 是 | 无 | 新增文档数据。 |


## 返回参数

AddDocumentResult.
| 字段名 | 类型 | 说明 |
| --- | --- | --- |
| _id | string | 新增文档的 id。 |


## 示例


```JavaScript
const cloud = require("@alipay/faas-server-sdk");

exports.main = async (event, context) => {
const db = cloud.database();
return await db.collection('example').add({
data: {
// _id: 'some-id', // 可自定义 id 或由服务端自动生成
// _openid: 'some-open-id', // 可设置 openid 或默认设置为当前上下文中的用户的 openid
done: false,
text: 'example',
},
});
};
```
​
