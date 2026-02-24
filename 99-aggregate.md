# aggregate

返回文档新建聚合操作，通过组合流水线组合完成聚合操作后，需要通过 end 方法发起实际的聚合操作请求。支持端：云函数 、小程序端 。

## 请求参数

无。

## 返回参数

Aggregate 聚合流水线构建对象。

## 功能说明

目前还没有全量支持 mongo 官方提供的所有操作，后续云开发会根据用户的需求以及开发计划尽量全部支持，目前 aggregate 支持下列 4 种操作：●match：通过字段过滤出符合条件的 document。●group：通过字段对 document 进行分组，以计算总和、最大值、最小值、平均值等参数。●sample：随机采样 N 条 document。●lookup：连表查询，与同一数据库下的一个指定 collection 进行左外连接。

## 云函数示例

### match + group


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
})
.group({
_id: '$class',
count: db.command.aggregate.count(),
avgScore: db.command.aggregate.avg('$score'),
})
.end();
```


### match + sample


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


## 小程序端示例

### match + group



### match + sample

​
