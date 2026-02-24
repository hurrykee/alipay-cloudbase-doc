# unwind

返回文档从输入文档解构数组字段以输出每个元素的文档。
```
<?php
public function unwind($unwind): Aggregate
```


## 请求参数


| 字段名 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| unwind | string \| UnwindParam | 是 | 无 | 排序字段信息。 |


## 返回参数

Aggregate 聚合流水线构建 client。

## 示例


```PHP
<?php

use Cloud\Cloud;
use Cloud\Mongodb\UnwindParam;

function unwind($event, $context)
{
$logger = $context->getLogger();
$cloud = new Cloud();
$database = $cloud->database();
$command = $database->command;
$array = array(
"_id" => $command->eq("some-one-id")
);

$result = $database
->collection("collectionName")
->aggregate()
->match($array)
->unwind(new UnwindParam("$" . "some-field-name"))
->end();
$logger->info("unwind", "unwind response:%s", json_encode($result));
return $result;
}
```
​
