# downloadFile

返回文档●从云存储空间下载文件。●downloadFile 方法定义。
```
function downloadFile(param: DownloadFileParam): Promise<DownloadFileResult>;
```


## 请求参数

DownloadFileParam.
| 字段名 | 类型 | 是否必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| fileID | string | 是 | 无 | 云存储文件 ID。 |


## 返回参数

DownloadFileResult.
| 字段名 | 类型 | 说明 |
| --- | --- | --- |
| fileContent | Buffer | 文件内容。 |
| statusCode | number | 上传资源请求返回的 HTTP 状态码。 |


## 异常

当 fileID 校验失败时，将抛出 INVALID_PARAM 异常。
| 字段 | 类型 | 说明 |
| --- | --- | --- |
| error.code | string | 固定为 INVALID_PARAM。 |
| error.message | string | 格式为 Invalid param "fileID", {reason}。 |
当服务端返回失败时，将抛出 CALL_STORAGE_ERR 异常。
| 字段 | 类型 | 说明 |
| --- | --- | --- |
| error.code | string | 固定为 CALL_STORAGE_ERR。 |
| error.message | string | 格式为 requestId {requestId}, {errMsg}。 |
| error.requestID | string | 请求 traceId，用于日志查询。 |
| error.errCode | number | 错误码。 |


## 示例

downloadFile 示例：
```JavaScript
const fs = require('fs');
const path = require('path');
const cloud = require("@alipay/faas-server-sdk");

exports.main = async (event, context) => {
const res await cloud.downloadFile({
fileID: 'cloud://example/simple.text',
});
return res.fileContent.toString('utf-8');
};
```
​
