# collection

返回文档获取当前事务下的集合对象并行相应操作。
```
<?php
public function collection(string $collectionName): Collection
```


## 请求参数


| 字段名 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| collectionName | string | 是 | 无 | 集合名。 |


## 返回参数

集合对象。

## 示例


```PHP
<?php

use Cloud\Cloud;
use Cloud\Mongodb\Transaction;
function collection($event, $context)
{
$logger = $context->getLogger();
$cloud = new Cloud();
$database = $cloud->database();
$callback = function (Transaction $transaction) use ($logger) {
$collection = $transaction->collection("collectionName");
$result = $collection->get();
$logger->info("get", "get response:%s", json_encode($result));
return $result;
};
$result = $database->runTransaction($callback);
$logger->info("collection", "collection response:%s", json_encode($result));
return $result;
}
```
​
