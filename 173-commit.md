# commit

返回文档结束事务并进行提交。
```
<?php
public function commit(): GetObjectAclResponse
```


## 请求参数

无。

## 返回参数

### GetObjectAclResponse


| 字段名 | 类型 | 说明 |
| --- | --- | --- |
| message | string | 请求返回message。 |
| trace_id | string | - |
| success | string | 请求结果。 |
| data | array \| string | 请求返回数据。 |
| code | string | 请求结果code。 |


## 示例


```PHP
<?php

use Cloud\Cloud;
use Cloud\Mongodb\AddDocumentParam;
use Cloud\Mongodb\AddOneDocumentParam;
function commit($event, $context)
{
$logger = $context->getLogger();
$cloud = new Cloud();
$database = $cloud->database();
$transaction = $database->startTransaction();
$data = array(
"keyOneValue" => "valueOne",
"keyTwoValue" => "valueTwo"
);
$param = new AddOneDocumentParam(
$data);
$entity = new AddDocumentParam($param);
$result = null;
try {
$result = $transaction->collection("collectionName")
->add($entity);
$transaction->commit();
} catch (Exception $exception) {
$transaction->rollback($exception->getMessage());
}
$logger->info("commit", "commit response:%s", json_encode($result));
return $result;
}
```
​
