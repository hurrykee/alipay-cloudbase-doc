# projection

返回文档指定返回结果中文档的字段。支持端：云函数 、小程序端。projection 方法类型定义：
```
function projection(projection: object): Query;
```


## 请求参数

projection 字段是否返回的配置，对象 key 为字段名，value 为 true 或1表示需要返回，value 为 false 或-1表示不需要返回。

## 返回参数

Query 查询构造对象。

## 云函数示例

返回 name, description，不返回 secret。
```JavaScript
const cloud = require("@alipay/faas-server-sdk");

exports.main = async (event, context) => {
const db = cloud.database();
return await db.collection('example').projection({
name: true,
description: 1,
secret: false,
}).get();
};
```


## 小程序端示例


```JavaScript
const ctx = my.cloud.createCloudContext({
env: 'env-database', // 云环境 id
});
// 云环境初始化
await ctx.init();
// 获取 Database 实例
const db = ctx.database();
await db.collection('example').projection({
name: true,
description: 1,
secret: false,
}).get();
```
​
