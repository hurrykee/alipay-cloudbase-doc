# count

返回文档统计行数。
```
<?php
public function count(string $table, array $where): int
```


## 请求参数


| 字段名 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| table | string | 是 | 无 | 操作表名。 |
| where | array | 否 | 无 | 过滤条件。 |


## 返回参数

符合条件的行数。

## 示例


```PHP
<?php

use Cloud\Cloud;
function mysqlCount($event, $context): int
{
$logger = $context->getLogger();
$cloud = new Cloud();
$mysql = $cloud->mysql();
$table = "your_table";
$where = array(
"user_name" => "your_name"
);
$result = $mysql->count($table, $where);
$logger->info("count", "count response:%s", json_encode($result));
return $result;
}
```
​
