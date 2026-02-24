# orderBy

返回文档指定查询的排序规则。
```
<?php
public function orderBy(string $field, string $sort): Query
```


## 请求参数


| 字段名 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| field | string | 是 | 无 | 排序字段名。 |
| sort | string | 是 | 无 | 排序规则：Sort::ASC 升序；Sort::DESC 降序。 |


## 返回参数

Query 查询构造 client。

## 示例


```PHP
<?php
use Cloud\Cloud;
function orderBy($event, $context): array
{
$logger = $context->getLogger();
$cloud = new Cloud();
$database = $cloud->database();
$result = $database
->collection("collectionName")
->orderBy(
"keyValue",
"desc"
)
->get();
$logger->info("orderBy", "orderBy response:%s", json_encode($result));
return $result;
}
```
​
