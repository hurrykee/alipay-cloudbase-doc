# MySQL 概览

返回文档获取 MySQL client。
```
<?php
public function mysql(): MysqlClient
```


## 入参

无。

## 返回

MysqlClient.
| API | 类别 | 备注 |
| --- | --- | --- |
| mysql->query() | 方法 | 执行 sql 语句。 |
| mysql->insert() | 插入数据。 |  |
| mysql->update() | 更新数据。 |  |
| mysql->select() | 查询数据。 |  |
| mysql->delete() | 删除数据。 |  |
| mysql->count() | 统计行数。 |  |
| mysql->beginTransaction() | 开启事物。 |  |
| mysql->beginTransactionScope() | 新建事务运行作用域。 |  |


## 代码示例


```PHP
<?php
use Cloud\Cloud;

$cloud = new Cloud();
$mysql = $cloud->mysql();
```
​
