# query

返回文档执行 sql 语句。
```
<?php
public function query(string $sql, array $values = null)
```


## 请求参数


| 字段名 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| sql | string | 是 | 无 | sql 语句模版。 |
| values | array | 否 | 无 | 渲染到 sql 语句中的参数。 |


## 返回参数

sql 语句执行结果。

## 示例


```PHP
<?php

use Cloud\Cloud;
function query($event, $context)
{
$logger = $context->getLogger();
$cloud = new Cloud();
$mysql = $cloud->mysql();
$sql = "CREATE TABLE IF NOT EXISTS `your_table` (`id` int(11) NOT NULL AUTO_INCREMENT, `user_name` varchar(255) DEFAULT NULL, `description` varchar(255) DEFAULT NULL, `password` varchar(250) DEFAULT NULL, PRIMARY KEY (`id`)) ENGINE=InnoDB;";
$result = $mysql->query($sql);
$logger->info("query", "query response:%s", json_encode($result));
return $result;
}
```
​
