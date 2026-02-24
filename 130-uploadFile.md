# uploadFile

返回文档上传本地文件到云存储空间。
```
<?php
public function uploadFile(UploadFileParam $param): UploadFileResult
```


## 请求参数

### UploadFileParam


| 字段名 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| cloudPath | string | 是 | 无 | 云存储路径。 |
| fileContent | Buffer \| Readable | 是 | 无 | 上传文件内容。 |


## 返回参数

### UploadFileResult


| 字段名 | 类型 | 说明 |
| --- | --- | --- |
| fileID | string | 文件 ID。 |
| statusCode | int | 上传文件请求返回的 HTTP 状态码。 |


## 示例


```PHP
<?php

use Cloud\Cloud;
use Cloud\OSS\UploadFileParam;
use Cloud\OSS\UploadFileResult;
function uploadFile($event, $context): UploadFileResult
{
$logger = $context->getLogger();
$fileId = "index.txt";
$cloud = new Cloud();
$file = fopen("php://temp", "w+");
if ($file) {
fwrite($file, "Hello, World!");
rewind($file);
$logger->info("uploadFile", "File stream created successfully.");
}
$entity = new UploadFileParam($fileId, $file);
$result = $cloud->uploadFile($entity);
fclose($file);
$logger->info("uploadFile", "uploadFile response:%s",json_encode($result));
return $result;
}
```
​
