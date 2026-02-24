# skip

返回文档聚合流水线的输出时，跳过前 n 个文档。
```
<?php
public function skip(int $skip): Aggregate
```


## 请求参数


| 字段名 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| skip | int | 是 | 无 | 跳过前 skip 条数据。 |


## 返回参数

Aggregate 聚合流水线构建 client。

## 示例


```PHP
<?php

use Cloud\Cloud;

function skip($event, $context)
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
->skip(2)
->end();
$logger->info("skip", "skip response:%s", json_encode($result));
return $result;
}
```
​
