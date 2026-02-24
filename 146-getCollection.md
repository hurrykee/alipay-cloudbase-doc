# getCollection

返回文档查询集合信息。
```
<?php

public function getCollection(string $collectionName): CollectionDescription
```


## 请求参数


| 字段名 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| collectionName | string | 是 | 无 | 集合名。 |


## 返回参数

### CollectionDescription


| 字段名 | 类型 | 说明 |
| --- | --- | --- |
| coll_id | int | 集合 id。 |
| coll_name | string | 集合名。 |
| db_id | int | 数据库 id。 |
| create_time | int | 集合创建时间戳。 |


## 示例


```PHP
<?php

use Cloud\Cloud;
use Cloud\Mongodb\CollectionDescription;
function getCollection($event, $context): CollectionDescription
{
$logger = $context->getLogger();
$cloud = new Cloud();
$database = $cloud->database();
$result = $database->getCollection("collectionName");
$logger->info("getCollection", "getCollection response:%s", json_encode($result));
return $result;
}
```
​
