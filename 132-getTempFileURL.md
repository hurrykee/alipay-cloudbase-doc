# getTempFileURL

返回文档通过云文件 ID 获取文件链接，通过此方法一次最多可获取50个文件链接。
```
<?php
public function getTempFileURL(array $fileList): GetTempFileURLResult
```


## 请求参数


| 字段名 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| fileList | array | 是 | 无 | 云存储文件 ID 列表。 |


## 返回参数

### GetTempFileURLResult


| 字段名 | 类型 | 说明 |
| --- | --- | --- |
| fileList | TempFileInfo[] | 文件列表。 |


### TempFileInfo


| 字段名 | 类型 | 说明 |
| --- | --- | --- |
| fileID | string | 云存储文件 ID。 |
| tempFileURL | string | 文件链接。 |
| status | int | 操作状态码，0为成功，-1为失败。 |
| message | string | 成功为 ok，失败为失败原因。 |


## 示例


```PHP
<?php

use Cloud\Cloud;
use Cloud\OSS\GetTempFileURLResult;
function getTempFileURL($event, $context): GetTempFileURLResult
{
$logger = $context->getLogger();
$cloud = new Cloud();
$fileId = "some-file-id";
$array = array(
$fileId
);
$result = $cloud->getTempFileURL($array);
$logger->info("getTempFileURL", "getTempFileURL response:%s",json_encode($result));
return $result;
}
```
​
