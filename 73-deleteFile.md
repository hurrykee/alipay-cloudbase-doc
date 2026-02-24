# deleteFile

返回文档删除云存储空间中的文件。
```
function deleteFile(fileList: string[]): Promise<DeleteFileResult>;
```


## 请求参数

fileList: string[] 云存储文件 ID 列表。

## 返回参数

DeleteFileResult.
| 字段名 | 类型 | 说明 |
| --- | --- | --- |
| fileList | FileInfo[] | 文件列表。 |
FileInfo.
| 字段名 | 类型 | 说明 |
| --- | --- | --- |
| fileID | string | 云存储文件 ID。 |
| status | number | 删除操作状态码0为成功，-1为失败。 |
| errMsg | string | 成功为 ok，失败为删除失败原因。 |


## 异常

当 fileList 或 fileID 校验失败时，将抛出 INVALID_PARAM 异常。
| 字段 | 类型 | 说明 |
| --- | --- | --- |
| error.code | string | 固定为 INVALID_PARAM。 |
| error.message | string | 格式为 Invalid param "{key}", {reason}。 |
当服务端返回失败时，将抛出 FunctionError 异常。
| 字段 | 类型 | 说明 |
| --- | --- | --- |
| error.code | string | 固定为 CALL_STORAGE_ERR。 |
| error.message | string | 格式为 requestId {requestId}, {errMsg}。 |
| error.requestID | string | 请求 traceId，用于日志查询。 |
| error.errCode | number | 错误码。 |


## 示例

deleteFile 示例。
```TypeScript
const cloud = require("@alipay/faas-server-sdk");

exports.main = async (event, context) => {
const res = await cloud.deleteFile({
fileList: ['cloud://example/simple.text', 'cloud://example/simple.png'],
});
return res.fileList;
};
```
​
