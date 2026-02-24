# createCollection

返回文档新建集合，若已存在同名集合，则会抛出异常。createCollection 方法类型定义：
```
function createCollection(collectionName: string): Promise<CollectionDescription>;
```


## 请求参数

collectionName: string 集合名。

## 返回参数

CollectionDescription.
| 字段名 | 类型 | 说明 |
| --- | --- | --- |
| coll_id | number | 集合 id。 |
| coll_name | string | 集合名。 |
| db_id | number | 数据库 id。 |
| create_time | number | 集合创建时间戳。 |


## 异常

当新建操作失败时，将抛出 FunctionError 异常。
| 字段 | 类型 | 说明 |
| --- | --- | --- |
| error.code | string | 固定为 DATABASE_OPERATION_ERR |
| error.message | string | 格式为 requestId {requestId}, {errMsg} |
| error.requestID | string | 请求 traceId，用于日志查询 |
| error.errCode | number | 错误码 |


## 示例

createCollection 方法示例代码：
```TypeScript
const cloud = require("@alipay/faas-server-sdk");

exports.main = async (event, context) => {
const db = cloud.database();
return await db.createCollection('example');
};
```
​
