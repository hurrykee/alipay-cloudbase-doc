# remove

返回文档删除集合中全部信息。
```
<?php
public function remove(): DeleteResult
```


## 请求参数

无。

## 返回参数

### DeleteResult


| 字段名 | 类型 | 说明 |
| --- | --- | --- |
| count | int | 删除文档数。 |


## 示例


```PHP
<?php

use Cloud\Cloud;
use Cloud\Mongodb\DeleteResult;
function remove($event, $context): DeleteResult
{
$logger = $context->getLogger();
$cloud = new Cloud();
$database = $cloud->database();
$result = $database
->collection("collectionName")
->remove();
$logger->info("remove", "remove response:%s", json_encode($result));
return $result;
}
```
​
