# sample

返回文档聚合流水线的抽样阶段，从文档列表中随机选取指定数量的文档。支持端：云函数 、小程序端。sample 方法类型定义：
```
function sample(sample: SampleAggregateParam): Aggregate;
```


## 请求参数


| 字段名 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| size | number | 是 | - | 样本数。 |


## 返回参数

Aggregate 聚合流水线构建对象。

## 云函数示例


```TypeScript
const cloud = require("@alipay/faas-server-sdk");

exports.main = async (event, context) => {
const db = cloud.database();
// 随机获取一个班级 one 中分数大于 90 分的文档
return await db.collection('example')
.aggregate()
.match({
class: 'class-one',
score: db.command.gt(90),
})
.sample({
size: 1,
})
.end();
};
```


## 云端研发示例


```TypeScript
const ctx = my.cloud.createCloudContext({
env: 'env-database', // 云环境 id
});
// 云环境初始化
await ctx.init();
// 获取 Database 实例
const db = ctx.database();
await db.collection('example')
.aggregate()
.match({
class: 'class-one',
score: db.command.gt(90),
})
.sample({
size: 1,
})
.end();
```
​
