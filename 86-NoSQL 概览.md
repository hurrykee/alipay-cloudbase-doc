# NoSQL 概览

返回文档获取 mongoDB 数据库对象。cloud.database 方法类型定义：
```
function database(param?: GetDatabaseParam): Database;
```


## 参数 GetDatabaseParam


| 字段名 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| throwOnNotFound | boolean | 否 | true | doc(id).get() 为空时，是否抛出异常。 |
| ignoreCollectionExists | boolean | 否 | false | createCollection 时，若 collection 已存在，是否直接返回已存在的 collection。若为 false，则抛出异常。 |
| timeout | number \| [ number, number ] | 否 | 5000 | ●请求超时时间（单位：毫秒），默认为5秒。●类型为 number 时，表示建立连接和响应超时时间为相同值； 类型为 [number, number] 时，表示分别设置两阶段的超时时间。●超时时间最大为5分钟，若超过该值，将被修改为5分钟。●若此处未设置 timeout，将取 cloud.init 设置的 timeout。 |


## 返回值 Database


| 字段 | 类别 | 说明 |
| --- | --- | --- |
| Database.command | 属性 | 数据库操作符。 |
| Database.collection | 方法 | 获取集合对象。 |
| Database.createCollection | 新建集合。 |  |
| Database.getCollection | 查询集合信息。 |  |
| Database.listCollection | 查询集合列表。 |  |
| Database.deleteCollection | 删除集合。 |  |
| Database.runTransaction | 新建事务并在事务中执行回调函数。 |  |
| Database.startTransaction | 新建事务。 |  |


## 示例


```TypeScript
const cloud = require("@alipay/faas-server-sdk");
// 获取 cloud 环境中的 mongoDB 数据库对象
const db = cloud.database();
});
```
​
