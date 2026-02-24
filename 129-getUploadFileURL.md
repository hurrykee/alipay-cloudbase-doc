# getUploadFileURL

返回文档获取文件上传链接。
```
<?php
public function getUploadFileURL($cloudPath): GetUploadFileURLResult
```


## 请求参数


| 字段名 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| cloudPath | string \| GetUploadFileURLParam | 是 | 无 | 云存储路径。 |


### GetUploadFileURLParam


| 字段名 | 类型 | 说明 |
| --- | --- | --- |
| cloudPath | string | 云存储路径。 |


## 返回参数

### GetUploadFileURLResult


| 字段名 | 类型 | 说明 |
| --- | --- | --- |
| fileID | string | 文件 ID。 |
| uploadUrl | string | 文件上传 url。 |
| requestId | string | - |


## 示例


```PHP
<?php

use Cloud\Cloud;
use Cloud\Http\HttpException;
use Cloud\Utils\StringUtil;

function getUploadFileURL($event, $context): array
{
$logger = $context->getLogger();
$cloud = new Cloud();
$fileName = "test_fileName_" . bin2hex(random_bytes(8));
$cloudPath = "test/$fileName.txt";

// 读取当前文件内容
$file = fopen("php://temp", "w+");
if ($file) {
fwrite($file, "Hello, World!");
rewind($file);
}
$result = $cloud->getUploadFileURL($cloudPath);
$url = $result->uploadUrl;

$curl = curl_init();
curl_setopt($curl, CURLOPT_URL, $url);
curl_setopt($curl, CURLOPT_PUT, 1);
curl_setopt($curl, CURLOPT_INFILE, $file);
curl_setopt($curl, CURLOPT_FOLLOWLOCATION, true);
curl_exec($curl);
$httpStatus = curl_getinfo($curl, CURLINFO_HTTP_CODE);
if ($httpStatus !== 200) {
$message = sprintf("upload file failed reason:%s, upload url:%s", curl_error($curl), $url);
$logger->info("main", $message);
throw HttpException::STORAGE_ERR($httpStatus, $message, StringUtil::EMPTY);
}
curl_close($curl);
return array(
```
​
