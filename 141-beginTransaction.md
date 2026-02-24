# beginTransaction

返回文档开启事务，并返回 MysqlTransaction client。
```
<?php
public function beginTransaction(): MysqlTransaction
```


## 请求参数

无。

### 返回参数

MysqlTransaction client.

## 示例


```PHP
<?php

use Cloud\Cloud;
function beginTransaction($event, $context)
{
$logger = $context->getLogger();
$cloud = new Cloud();
$transaction = $cloud->mysql()->beginTransaction();
$result = null;
$table = "your_table";
$rows = array(
"user_name" => "your_name",
"description" => "mysql transaction description"
);
try {
$result = $transaction->insert($table, $rows);
$logger->info("insert", "insert response:%s", json_encode($result));
$transaction->commit();
} catch (Exception $e) {
$logger->error("insert", "transaction insert response:%s", $e->getMessage());
$transaction->rollback();
}
return $result;
}
```
​
