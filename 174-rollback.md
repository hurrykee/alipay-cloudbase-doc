# rollback

返回文档终止事务并进行回滚。
```
<?php
public function rollback(string $reason): GetObjectAclResponse
```


## 请求参数


| 字段名 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| reason | string | 是 | 无 | 事务回滚原因。 |


## 返回参数

### GetObjectAclResponse


| 字段名 | 类型 | 备注 |
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
function rollback($event, $context)
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
throw new Exception("add document failed");
} catch (Exception $exception) {
$transaction->rollback($exception->getMessage());
}
$logger->info("rollback", "rollback response:%s", json_encode($result));
return $result;
}
```
​
