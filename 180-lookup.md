# lookup

返回文档聚合流水线的连表查询聚合阶段，与同一数据库下的一个指定 collection 进行左外连接。对该 collection 中的每一个 doc，增加一个数组字段，该数组包含满足连接匹配条件的 doc 列表。lookup 有两种使用方式。
```
<?php
public function lookup($sample): Aggregate
```


## 请求参数


| 字段名 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| sample | EqualityMatchLookupParam \| JoinLookupParam | 是 | 无 | - |


### EqualityMatchLookupParam


| 字段名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| from | string | 是 | 要连接的 collection 名。 |
| localField | string | 是 | 当前 collection 进行相等匹配的字段。 |
| foreignField | string | 是 | 被连接 collection 进行相等匹配的字段。 |
| as | string | 是 | 连接结果数组字段名。 |


### JoinLookupParam


| 字段名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| from | string | 是 | 要连接的 collection 名。 |
| let | string | 否 | 指定在 pipeline 中可以使用的变量。 |
| pipeline | string | 是 | 被连接 collection 中执行的流水线操作。 |
| as | string | 是 | 连接结果数组字段名。 |


## 返回参数

Aggregate 聚合流水线构建 client。

## 示例


```PHP
<?php

use Cloud\Cloud;
function lookup($event, $context): array
{
$logger = $context->getLogger();
$cloud = new Cloud();
$database = $cloud->database();
$param = new EqualityMatchLookupParam(
"fromCollectionName",
"_id",
"_id",
"newList"
);
$result = $database
->collection("collectionName")
->aggregate()
->lookup($param)
->end();
$logger->info("lookup", "lookup response:%s", json_encode($result));
return $result;
}
```
​
