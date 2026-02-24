# get

返回文档获取文档列表，可在构建查询条件后获取以得到筛选后的文档列表。支持端：云函数 、小程序端。get 方法类型定义：
```
function get<T=any>(): Promise<Array<T>>;
```


## 请求参数

无。

## 返回参数

文档列表。

## 云函数示例

### 获取满足条件的文档列表


```JavaScript
const ctx = my.cloud.createCloudContext({
env: 'env-database', // 云环境 id
});
// 云环境初始化
await ctx.init();
// 获取 Database 实例
const db = ctx.database();
await db.collection('example').where({
_openid: cloud.getAlipayContext().OPENID,
done: false,
}).get();
```


### 分页获取数据


```JavaScript
const ctx = my.cloud.createCloudContext({
env: 'env-database', // 云环境 id
});
// 云环境初始化
await ctx.init();
// 获取 Database 实例
const db = ctx.database();
await db.collection('example')
.where({
_openid: cloud.getAlipayContext().OPENID,
})
.skip(10) // 从第 11 条开始返回
.limit(20) // 只返回 20 条
.get();
```


## 小程序示例

### 获取满足条件的文档列表



### 分页获取数据

​
