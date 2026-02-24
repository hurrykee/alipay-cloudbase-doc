# limit

返回文档聚合流水线的输出时，限制输出的文档数量。
```
<?php
public function limit(int $limit): Aggregate
```


## 请求参数


| 字段名 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| limit | int | 是 | 无 | 最多输出数据数量。 |


## 返回参数

Aggregate 聚合流水线构建 client。

## 示例


```PHP
<?php

use Cloud\Cloud;

function limit($event, $context)
{
$logger = $context->getLogger();
$cloud = new Cloud();
$database = $cloud->database();
$command = $database->command;
$array = array(
"some-field-name" => $command->gt("some-one-number")
);

$result = $database
->collection("collectionName")
->aggregate()
->match($array)
->limit(2)
->end();
$logger->info("limit", "limit response:%s", json_encode($result));
return $result;
}
```
​
