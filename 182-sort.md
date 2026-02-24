# sort

返回文档聚合流水线的输出时，按照指定字段排序。
```
<?php
public function sort(array $sort): Aggregate
```


## 请求参数


| 字段名 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| sort | array | 是 | 无 | 排序字段信息。 |


## 返回参数

Aggregate 聚合流水线构建 client。

## 示例


```PHP
<?php

use Cloud\Cloud;

function sortExample($event, $context)
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
->sort(["some-field-name" => "desc"])
->end();
$logger->info("sort", "sort response:%s", json_encode($result));
return $result;
}
```
​
