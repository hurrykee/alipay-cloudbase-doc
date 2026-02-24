# listCollection

返回文档查询集合列表。
```
<?php
public function listCollection(int $limit = 10, int $skip = 0): array
```


## 请求参数


| 字段名 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| limit | int | 否 | 10 | 查询数量。 |
| skip | int | 否 | 0 | 跳过 skip 数量的集合，常用于分页。 |


## 返回参数

集合。

## 示例


```PHP
<?php

use Cloud\Cloud;
function listCollection($event, $context): array
{
$logger = $context->getLogger();
$cloud = new Cloud();
$database = $cloud->database();
$result = $database->listCollection();
$logger->info("listCollection", "listCollection response:%s", json_encode($result));
return $result;
}
```
​
