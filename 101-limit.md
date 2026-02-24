# limit

返回文档限制查询结果数量上限，需要配合 get 等方法完成真实操作请求。支持端：云函数 、小程序端。limit 方法类型定义：
```
function limit(limit: number): Query;
```


## 请求参数

limit 最大返回数量。

## 返回参数

Query 查询构造对象。

## 云函数示例


```TypeScript
const cloud = require("@alipay/faas-server-sdk");

exports.main = async (event, context) => {
const db = cloud.database();
return await db.collection('example')
.where({
class: 'class-one',
})
.limit(5) // 最多返回 5 个
.get();
};
```


## 小程序端示例


```TypeScript
const ctx = my.cloud.createCloudContext({
env: 'env-database', // 云环境 id
});
// 云环境初始化
await ctx.init();
// 获取 Database 实例
const db = ctx.database();
await db.collection('example')
.where({
class: 'class-one',
})
.limit(5) // 最多返回 5 个
.get();
```
​
