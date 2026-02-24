# match

返回文档聚合流水线的条件过滤阶段，根据条件过滤文档后把符合条件的文档传递给下一流水线阶段。支持端：云函数 、小程序端。
```
function match(match: object | QueryCommand | QueryChain): Aggregate;
```


## 请求参数

match 查询条件。

## 返回参数

Aggregate 聚合流水线构建对象。

## 云函数示例

### 只过滤


```JavaScript
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
.end();
```


### 过滤后统计


```JavaScript
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
score: db.command.gt(90),
})
.group({
_id: '$class',
count: $.count(),
})
.end();
```


## 小程序端示例

### 只过滤



### 过滤后统计

​
