# uploadFile

返回文档上传本地文件到云存储空间。
```
function uploadFile(param: UploadFileParam): Promise<UploadFileResult>;
```


## 请求参数

UploadFileParam.
| 字段名 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| cloudPath | string | 是 | 无 | 云存储路径。 |
| fileContent | Buffer \| Readable | 是 | 无 | 上传文件内容。 |


## 返回参数

UploadFileResult.
| 字段名 | 类型 | 说明 |
| --- | --- | --- |
| fileID | string | 文件 ID。 |
| statusCode | number | 上传文件请求返回的 HTTP 状态码。 |


## 异常

当服务端返回失败时，将抛出 FunctionError 异常。
| 字段 | 类型 | 说明 |
| --- | --- | --- |
| error.code | string | 固定为 CALL_STORAGE_ERR。 |
| error.message | string | 格式为 requestId {requestId}, {errMsg}。 |
| error.requestID | string | 请求 traceId 用于日志查询。 |
| error.errCode | number | 错误码。 |


## 示例


```JavaScript
const fs = require('fs');
const path = require('path');
const cloud = require("@alipay/faas-server-sdk");

exports.main = async (event, context) => {
const fileContent = fs.createReadStream(path.join(__dirname, 'simple.png'));
return await cloud.uploadFile({
cloudPath: 'example/simple.png',
fileContent,
});
};
```
​
