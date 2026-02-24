# update

返回文档接口功能：更新一条或多条文档数据。支持端：云函数 、小程序端。update 方法类型定义：
```
function update(data: UpdateData): Promise<UpdateResult>;
```


## 请求参数

UpdateData.
| 字段名 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| data | object | 是 | 无 | 文档数据。 |


## 返回值

UpdateResult.
| 字段名 | 类型 | 说明 |
| --- | --- | --- |
| count | number | 更新文档数。 |


## 函数示例

### 更新一条文档数据


```JavaScript
const cloud = require("@alipay/faas-server-sdk");
exports.main = async (event, context) => {
const db = cloud.database();
const filter = {
class: 'class-one',
};
const updateData = {
lastScore: "10"
};
const res = await db.collection('student')
.where(filter)
.update({
data: updateData
});
return res;
};
```


### 更新全部文档数据


```JavaScript
const ctx = my.cloud.createCloudContext({
env: 'env-database', // 云环境 id
});
// 云环境初始化
await ctx.init();
// 获取 Database 实例
const db = ctx.database();
await db
.collection('example')
.doc('some-doc-id')
.update({
data: {
description: 'to be updated',
done: true,
},
});
```


### 根据条件更新多条文档数据



## 小程序示例

​
