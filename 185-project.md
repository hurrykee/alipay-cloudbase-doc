# project

返回文档聚合流水线的输出时，指定字段隐藏或显示。
```
<?php
public function project(array $project): Aggregate
```


## 请求参数


| 字段名 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| project | array | 是 | 无 | 字段隐藏或显示信息。 |


## 返回参数

Aggregate 聚合流水线构建 client。

## 示例


```PHP
<?php

use Cloud\Cloud;

function project($event, $context)
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
->project(["some-field-name" => 1, "some-another-field-name" => 1])
->end();
$logger->info("project", "project response:%s", json_encode($result));
return $result;
}
```
​
