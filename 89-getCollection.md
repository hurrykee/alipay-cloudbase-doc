# getCollection

返回文档查询集合信息，若不存在该集合，则返回 null。getCollection 方法类型定义：
```
function getCollection(collectionName: string): Promise<CollectionDescription | null>;
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

当查询操作失败时，将抛出 FunctionError 异常。
| 字段 | 类型 | 说明 |
| --- | --- | --- |
| error.code | string | 固定为 DATABASE_OPERATION_ERR。 |
| error.message | string | 格式为 requestId {requestId}, {errMsg}。 |
| error.requestID | string | 请求 traceId，用于日志查询。 |
| error.errCode | number | 错误码。 |


## 示例

getCollection 方法示例代码。
```TypeScript
const cloud = require("@alipay/faas-server-sdk");

exports.main = async (event, context) => {
const db = cloud.database();
return await db.getCollection('example');
};
```
​
