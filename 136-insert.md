# insert

返回文档插入数据。
```
<?php
public function insert(string $table, array $rows, InsertOption $option = null)
```


## 请求参数


| 字段名 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| table | string | 是 | 无 | 插入数据的表名。 |
| rows | array | 是 | 无 | 需要插入的一条或多条数据。 |
| options | InsertOption | 否 | 无 | 插入设置。 |


### InsertOption


| 字段名 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| columns | array | 否 | 无 | 指定要插入的列名。 |


## 返回参数

插入的数量。

## 示例


```PHP
<?php

use Cloud\Cloud;
function insert($event, $context)
{
$logger = $context->getLogger();
$cloud = new Cloud();
$mysql = $cloud->mysql();
$table = "your_table";
$rows = array(
"user_name" => "your_name",
"description" => "mysql demo description"
);
$result = $mysql->insert($table, $rows);
$logger->info("insert", "insert response:%s", json_encode($result));
return $result;
}
```
​
