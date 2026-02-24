# downloadFile

返回文档云存储空间下载文件。
```
<?php
public function downloadFile(DownloadFileParam $param): DownloadFileResult
```


## 请求参数

### DownloadFileParam


| 字段名 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| fileID | string | 是 | 无 | 云存储文件 ID。 |


## 返回参数

### DownloadFileResult


| 字段名 | 类型 | 说明 |
| --- | --- | --- |
| fileContent | Buffer | 文件内容。 |
| statusCode | int | 上传资源请求返回的 HTTP 状态码。 |


## 示例


```PHP
<?php

use Cloud\Cloud;
use Cloud\OSS\DownloadFileParam;
use Cloud\OSS\DownloadFileResult;
function downloadFile($event, $context): DownloadFileResult
{
$logger = $context->getLogger();
$cloud = new Cloud();
$fileId = "some-file-id";
$entity = new DownloadFileParam($fileId);
$result = $cloud->downloadFile($entity);
$logger->info("downloadFile", "downloadFile response:%s",json_encode($result));
return $result;
}
```
​
