# limit

返回文档限制查询结果数量上限，需要配合 get 等方法完成真实操作请求。
```
<?php
public function limit(int $limit): Query
```


## 请求参数


| 字段名 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| limit | int | 是 | 无 | 最大返回数量。 |


## 返回参数

Query 查询构造 client。

## 示例


```PHP
<?php

use Cloud\Cloud;
function limit($event, $context): array
{
$logger = $context->getLogger();
$cloud = new Cloud();
$database = $cloud->database();
$result = $database
->collection("collectionName")
->limit(3)
->get();
$logger->info("limit", "limit response:%s", json_encode($result));
return $result;
}
```
​
