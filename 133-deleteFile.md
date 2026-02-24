# deleteFile

返回文档删除云存储空间中的文件。
```
<?php
public function deleteFile(array $fileList): DeleteFileResult
```


## 请求参数


| 字段名 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| fileList | array | 是 | 无 | 云存储文件 ID 列表。 |


## 返回参数

### DeleteFileResult


| 字段名 | 类型 | 说明 |
| --- | --- | --- |
| fileList | FileInfo[] | 文件列表。 |


### FileInfo


| 字段名 | 类型 | 说明 |
| --- | --- | --- |
| fileID | string | 云存储文件 ID。 |
| status | int | 删除操作状态码0为成功，-1为失败。 |
| message | string | 成功为 ok，失败为删除失败原因。 |


## 示例


```PHP
<?php

use Cloud\Cloud;
use Cloud\OSS\DeleteFileResult;
function deleteFile($event, $context): DeleteFileResult
{
$logger = $context->getLogger();
$cloud = new Cloud();
$fileId = "some-file-id";
$array = array(
$fileId
);
$result = $cloud->deleteFile($array);
$logger->info("deleteFile", "deleteFile response:%s", json_encode($result));
return $result;
}
```
​
