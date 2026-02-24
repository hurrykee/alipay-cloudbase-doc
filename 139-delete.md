# delete

返回文档删除数据。
```
<?php
public function delete(string $table, array $where): DeleteResult
```


## 请求参数


| 字段名 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| table | string | 是 | 无 | 删除操作表名。 |
| where | array | 否 | 无 | 删除条件。 |


## 返回参数

### DeleteResult


| 字段名 | 类型 | 说明 |
| --- | --- | --- |
| count | int | 删除数据行数。 |


## 示例


```PHP
<?php
use Cloud\Cloud;
use Cloud\Mysql\DeleteResult;
function delete($event, $context): DeleteResult
{
$logger = $context->getLogger();
$cloud = new Cloud();
$mysql = $cloud->mysql();
$table = "your_table";
$where = array(
"user_name" => "your_name"
);
$result = $mysql->delete($table, $where);
$logger->info("delete", "delete response:%s", json_encode($result));
return $result;
}
```
​
