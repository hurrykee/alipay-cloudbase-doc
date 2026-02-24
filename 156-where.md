# where

返回文档指定查询条件，需要配合 get、count 等方法进行带条件的查询操作。
```
<?php
public function where(array $match): Query
```


## 请求参数


| 字段名 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| match | array | 是 | 无 | 查询条件。 |


## 返回参数

Query 查询构造 client。

## 示例


```PHP
<?php

use Cloud\Cloud;
function where($event, $context): array
{
$logger = $context->getLogger();
$cloud = new Cloud();
$database = $cloud->database();
$match = array(
"_id" => "some-doc-id"
);
$result = $database
->collection("collectionName")
->where($match)
->get();
$logger->info("where", "where response:%s", json_encode($result));
return $result;
}
```
​
