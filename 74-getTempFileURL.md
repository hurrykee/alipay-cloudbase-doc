# getTempFileURL

返回文档通过云文件 ID 获取文件链接，所获取的公有文件链接不会过期，私有文件链接为10分钟有效期。通过此方法一次最多可获取5个文件链接。DeleteFile 方法定义：
```
function getTempFileURL(fileList: string[]): Promise<GetTempFileURLResult>;
```


## 参数

fileList: string[] 云存储文件 ID 列表。

## 返回值

GetTempFileURLResult.
| 字段名 | 类型 | 说明 |
| --- | --- | --- |
| fileList | TempFileInfo[] | 文件列表。 |
TempFileInfo.
| 字段名 | 类型 | 说明 |
| --- | --- | --- |
| fileID | string | 云存储文件 ID。 |
| tempFileURL | string | 文件链接。 |
| status | number | 删除操作状态码，0为成功，-1为失败。 |
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

getTempFileURL 示例：
```TypeScript
const cloud = require("@alipay/faas-server-sdk");

exports.main = async (event, context) => {
const res = await cloud.getTempFileURL({
fileList: ['cloud://example/simple.text', 'cloud://example/simple.png'],
});
return res.fileList;
};
```
​
