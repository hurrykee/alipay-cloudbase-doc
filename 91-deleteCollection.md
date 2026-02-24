# deleteCollection

返回文档删除集合。deleteCollection 方法类型定义：
```
function deleteCollection(collectionName: string): Promise<DeleteResult>;
```


## 请求参数

collectionName: string 集合名。

## 返回参数

DeleteResult.
| 字段名 | 类型 | 说明 |
| --- | --- | --- |
| count | number | 删除数量。 |


## 异常

当删除操作失败时，将抛出 FunctionError 异常。
| 字段 | 类型 | 说明 |
| --- | --- | --- |
| error.code | string | 固定为 DATABASE_OPERATION_ERR。 |
| error.message | string | 格式为 requestId {requestId}, {errMsg}。 |
| error.requestID | string | 请求 traceId，用于日志查询。 |
| error.errCode | number | 错误码。 |


## 示例

deleteCollection 方法示例代码：
```JavaScript
const cloud = require("@alipay/faas-server-sdk");

exports.main = async (event, context) => {
const db = cloud.database();
return await db.deleteCollection('example');
};
```
​
