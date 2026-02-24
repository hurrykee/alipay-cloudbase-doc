# orderBy

返回文档指定查询的排序规则。支持端：云函数 、小程序端。orderBy 方法类型定义：
```
function orderBy(field: string, sort: Sort): Query;
```


## 请求参数


| 字段名 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| field | string | 是 | 无 | 排序字段名。 |
| sort | Sort | 是 | 无 | 排序规则：●Sort.ASC 升序。●Sort.DESC 降序。 |


## 返回参数

Query 查询构造对象。

## 云函数示例

### 按一个字段排序


```JavaScript
const ctx = my.cloud.createCloudContext({
env: 'env-database', // 云环境 id
});
// 云环境初始化
await ctx.init();
// 获取 Database 实例
const db = ctx.database();
await db.collection('example')
// 按照高度升序排序
.orderBy('height', "asc")
.get();
```


### 按多个字段排序


```JavaScript
const ctx = my.cloud.createCloudContext({
env: 'env-database', // 云环境 id
});
// 云环境初始化
await ctx.init();
// 获取 Database 实例
const db = ctx.database();
await db.collection('example')
// 先按照高度升序排序，再按照重量降序排序
.orderBy('height', "asc")
.orderBy('weight', "desc")
.get();
```


## 小程序端示例

### 按一个字段排序



### 按多个字段排序

​
