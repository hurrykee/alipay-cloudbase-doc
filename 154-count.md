# count

返回文档统计文档数量，可在构建查询条件后获取以得到满足条件的文档数量。
```
<?php
public function count(): CountDocumentResult
```


## 请求参数

无。

## 返回参数

### CountDocumentResult


| 字段名 | 类型 | 说明 |
| --- | --- | --- |
| total | int | 返回数量。 |


## 示例


```PHP
<?php

use Cloud\Cloud;
use Cloud\Mongodb\CountDocumentResult;
function documentCount($event, $context): CountDocumentResult
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
->count();
$logger->info("count", "count response:%s", json_encode($result));
return $result;
}
```
​
