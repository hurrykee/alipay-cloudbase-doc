# skip

返回文档进行查询操作时，指定跳过的数量，返回指定位置后的文档。支持端：云函数 、小程序端。skip 方法类型定义：
```
function skip(skip: number): Query;
```


## 请求参数

skip 跳过的文档数量。

## 返回参数

Query 查询构造对象。

## 云函数示例


```JavaScript
const cloud = require("@alipay/faas-server-sdk");

exports.main = async (event, context) => {
const db = cloud.database();
return await db.collection('example')
.where({
class: 'class-one',
})
.skip(10) // 从第 11 个开始返回
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
.skip(10) // 从第 11 个开始返回
.get();
```
​
