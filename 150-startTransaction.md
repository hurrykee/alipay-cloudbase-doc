# startTransaction

返回文档创建并开始新事务。
```
<?php
public function startTransaction(): Transaction
```


## 请求参数

无。

## 返回参数

transaction 事务对象，提供了 commit， rollback 以及 collection 方法用于进行事务操作。●collection 方法用于在当前事务下获取集合对象并行相应操作。●rollback 方法用于在需要终止事务并进行回滚时调用。●commit 方法用于结束事务并进行提交时调用。

## 示例


```PHP
<?php
use Cloud\Cloud;
use Cloud\Mongodb\AddDocumentParam;
use Cloud\Mongodb\AddOneDocumentParam;
function startTransaction()
{
$cloud = new Cloud();
$database = $cloud->database();
$transaction = $database->startTransaction();
$data = array(
'keyOneValue' => 'valueOne',
'keyTwoValue' => 'valueTwo'
);
$param = new AddOneDocumentParam(
$data);
$entity = new AddDocumentParam($param);
$result = null;
try {
$result = $transaction->collection('collectionName')
->add($entity);
$transaction->commit();
return $result;
} catch (Exception $exception) {
$transaction->rollback($exception->getMessage());
}
return $result;
}
```
​
