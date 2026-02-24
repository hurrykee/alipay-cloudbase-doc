# listCollection

返回文档查询集合列表。listCollection 方法类型定义：
```
function listCollection(limit?: number, skip?: number): Promise<Array<CollectionDescription>>;
```


## 请求参数


| 字段名 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| limit | number | 否 | 10 | 查询数量。 |
| skip | number | 否 | 0 | 跳过 skip 数量的集合，常用于分页。 |


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


```TypeScript
const cloud = require("@alipay/faas-server-sdk");

exports.main = async (event, context) => {
const db = cloud.database();
// 查询第 6 到 第10 个集合的信息
return await db.listCollection(5, 1);
};
```
​
