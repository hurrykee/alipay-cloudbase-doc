# skip

返回文档进行查询操作时，指定跳过的数量，返回指定位置后的文档。
```
<?php
public function skip(int $skip): Query
```


## 请求参数


| 字段名 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| skip | int | 是 | 无 | 跳过的文档数量。 |


## 返回参数

Query 查询构造 client。

## 示例


```PHP
<?php
use Cloud\Cloud;
function skip($event, $context): array
{
$logger = $context->getLogger();
$cloud = new Cloud();
$database = $cloud->database();
$result = $database
->collection("collectionName")
->skip(1)
->get();
$logger->info("skip", "skip response:%s", json_encode($result));
return $result;
}
```
​
