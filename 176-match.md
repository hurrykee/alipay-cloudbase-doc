# match

返回文档聚合流水线的条件过滤阶段，根据条件过滤文档后把符合条件的文档传递给下一流水线阶段。
```
<?php
public function match($match): Aggregate
```


## 请求参数


| 字段名 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| match | array \| QueryChain | 是 | 无 | 查询条件。 |


## 返回参数

Aggregate 聚合流水线构建 client。

## 示例


```PHP
<?php

use Cloud\Cloud;
function match($event, $context): array
{
$logger = $context->getLogger();
$cloud = new Cloud();
$database = $cloud->database();
$aggregateMatch = array(
"_id" => "some-doc-id"
);
$result = $database
->collection("collectionName")
->aggregate()
->match($aggregateMatch)
->end();
$logger->info("match", "match response:%s", json_encode($result));
return $result;
}
```
​
