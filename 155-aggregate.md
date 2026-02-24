# aggregate

返回文档新建聚合操作，通过组合流水线组合完成聚合操作后，需要通过 end 方法发起实际的聚合操作请求。
```
<?php
public function aggregate(): Aggregate
```


## 请求参数

无。

## 返回参数

Aggregate 聚合流水线构建 client。

## 示例


```PHP
<?php

use Cloud\Cloud;
function aggregate($event, $context): array
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
$logger->info("aggregate", "aggregate response:%s", json_encode($result));
return $result;
}
```
​
