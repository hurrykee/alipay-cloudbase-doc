# addFields

返回文档聚合流水线的输出时，添加输出字段。
```
<?php
public function addFields(array $fields): Aggregate
```


## 请求参数


| 字段名 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| fields | array | 是 | 无 | 添加字段信息。 |


## 返回参数

Aggregate 聚合流水线构建 client。

## 示例


```PHP
<?php

use Cloud\Cloud;
use Ramsey\Uuid\Uuid;

function addFields($event, $context)
{
$logger = $context->getLogger();
$cloud = new Cloud();
$database = $cloud->database();
$aggregateArray = array(
"fieldName" => Uuid::uuid4()->toString()
);
$result = $database
->collection("collectionName")
->aggregate()
->addFields($aggregateArray)
->end();
$logger->info("addFields", "addFields response:%s", json_encode($result));
return $result;
}
```
​
