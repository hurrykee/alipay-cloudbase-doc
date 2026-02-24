# group

返回文档聚合流水线的分组阶段，通过参数 _id 指定分组字段，返回结果一条记录为一个分组。支持端：云函数 、小程序端。group 方法类型定义：
```
function group(group: object): Aggregate;
```


## 请求参数 object

group 参数结构为：
```
{
_id: <expression>,
<key1>: <operator1>,
<key2>: <operator2>,
...
}
```
分组统计规则，其中 _id 为必填项，用于指定分组字段，该字段的相同取值归为一组，再通过其他 key 进行计数、平均值计算等等统计操作。

## 返回参数

Aggregate 聚合流水线构建对象。

## 云函数示例

### 按单个值分组


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
_id: '$class', // 以 class 维度分组
count: $.count(), // 计数
total: $.sum('$score'), // 累加分数总和
min: $.min('$score'), // 统计分数最小值
max: $.max('$score'), // 统计分数最大值
avg: $.avg('$score'), // 计算平均分
})
.end();
```


### 按多个值分组

_id 也支持传入多个值，即多个值均相等的归类为一个组。
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
// 统计每个班级每个年龄段的人数
.group({
_id: {
className: '$class',
age: '$age',
},
count: $.count(),
})
.end();
```


## 小程序端示例

### 按单个值分组



### 按多个值分组

_id 也支持传入多个值，即多个值均相等的归类为一个组。  ​
