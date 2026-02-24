# runTransaction

返回文档新建事务并在事务中执行回调函数。
```
<?php
public function runTransaction(callable $scope)
```


## 请求参数


| 字段名 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| scope | callable | 是 | 无 | 回调函数，回调函数的入参为新创建的事务。 |


## 返回参数

该函数返回值为回调函数的返回值。

## 示例


```PHP
<?php
use Cloud\Cloud;
use Cloud\Mongodb\Transaction;
use Cloud\Utils\StringUtil;
use Cloud\Mongodb\AddDocumentParam;
use Cloud\Mongodb\AddOneDocumentParam;
function runTransaction($event, $context)
{
$logger = $context->getLogger();
$cloud = new Cloud();
$database = $cloud->database();
$callback = function (Transaction $transaction)use ($logger) {
$id = StringUtil::EMPTY;
$data = array(
"keyOneValue" => "valueOne",
"keyTwoValue" => "valueTwo"
);
$param = new AddOneDocumentParam(
$data,
$id);
$entity = new AddDocumentParam($param);
$result = $transaction
->collection("collectionName")
->add($entity);
$logger->info("add", "add response:%s", json_encode($result));
return $result;
};
$result = $database->runTransaction($callback);
$logger->info("runTransaction", "runTransaction response:%s", json_encode($result));
return $result;
}
```
​
