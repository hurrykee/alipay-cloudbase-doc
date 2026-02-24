# count

返回文档统计文档数量，可在构建查询条件后获取以得到满足条件的文档数量。支持端：云函数 、小程序端 。count 方法类型定义：
```
function count(): Promise<CountDocumentResult>;
```


## 请求参数

无。

## 返回参数

CountDocumentResult.
| 字段名 | 类型 | 说明 |
| --- | --- | --- |
| total | number | 返回数量。 |


## 云函数示例


```TypeScript
const cloud = require("@alipay/faas-server-sdk");

exports.main = async (event, context) => {
const db = cloud.database();
return await db.collection('example').where({
done: false,
}).count();
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
await db.collection('example').where({
done: false,
}).count();
};
```
​
