# deleteCollection

返回文档删除集合。
```
<?php
public function deleteCollection(string $collectionName): DeleteResult
```


## 请求参数


| 字段名 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| collectionName | string | 是 | 无 | 集合名。 |


## 返回参数

### DeleteResult


| 字段名 | 类型 | 说明 |
| --- | --- | --- |
| count | int | 删除数量。 |


## 示例


```PHP
<?php

use Cloud\Cloud;
use Cloud\Mongodb\DeleteResult;
function deleteCollection($event, $context): DeleteResult
{
$logger = $context->getLogger();
$cloud = new Cloud();
$database = $cloud->database();
$result = $database->deleteCollection("collectionName");
$logger->info("deleteCollection", "deleteCollection response:%s", json_encode($result));
return $result;
}
```
​
