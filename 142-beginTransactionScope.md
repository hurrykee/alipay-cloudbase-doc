# beginTransactionScope

返回文档新建事务运行作用域。
```
<?php
public function beginTransactionScope(callable $callable)
```


## 请求参数


| 字段名 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| scope | callable | 是 | 无 | 回调函数。 |


## 返回参数

事物操作结果。

## 示例


```PHP
<?php

use Cloud\Cloud;
use Cloud\Mysql\MysqlTransaction;
function beginTransactionScope($event, $context): int
{
$logger = $context->getLogger();
$cloud = new Cloud();
$mysql = $cloud->mysql();
$inserted = 0;
$table = "your_table";
try {
$callable = function (MysqlTransaction $transaction) use ($table, $logger) {
$rows = array(
"user_name" => "your_name",
"description" => "begin transaction scope description"
);
$inserted = $transaction->insert($table, $rows);
$logger->info("transaction", "transaction inserted response:%s", json_encode($inserted));
};
$mysql->beginTransactionScope($callable);
} catch (Throwable $throwable) {
$logger->info("beginTransactionScope", "beginTransactionScope response:%s", $throwable->getMessage());
}
return $inserted;
}
```
​
