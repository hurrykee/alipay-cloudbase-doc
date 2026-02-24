# remove

返回文档删除一条文档数据。支持端：云函数 、小程序端。remove 方法类型定义：
```
function remove(): Promise<DeleteResult>;
```


## 请求参数

无。

## 返回参数

DeleteResult.
| 字段名 | 类型 | 说明 |
| --- | --- | --- |
| count | number | 删除文档数。 |


## 云函数示例


```TypeScript
const cloud = require("@alipay/faas-server-sdk");

exports.main = async (event, context) => {
const db = cloud.database();
return await db
.collection('example')
.doc('some-doc-id')
.remove();
};
```


## 小程序示例


```TypeScript
const ctx = my.cloud.createCloudContext({
env: 'env-database', // 云环境 id
});
// 云环境初始化
await ctx.init();
// 获取 Database 实例
const db = ctx.database();
await db
.collection('example')
.doc('some-doc-id')
.remove();
```
​
