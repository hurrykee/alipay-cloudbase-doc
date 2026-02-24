# where

返回文档指定查询条件，需要配合 get，count 等方法进行带条件的查询操作。支持端：云函数。where 方法类型定义：
```
function where(match: object | QueryCommand | QueryChain): Query;
```


## 请求参数

match 查询条件。

## 返回参数

Query 查询构造对象。

## 云函数示例


```TypeScript
const cloud = require("@alipay/faas-server-sdk");

exports.main = async (event, context) => {
const db = cloud.database();
return await db.collection('example').where({
class: 'class-one',
score: db.command.gt(90),
}).get();
};
```
​
