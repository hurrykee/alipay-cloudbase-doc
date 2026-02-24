# update

返回文档更新数据。
```
<?php
function update(string $table, array $row, UpdateOption $option = null): UpdateResult
```


## 请求参数


| 字段名 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| table | string | 是 | 无 | 更新操作表名。 |
| row | array | 是 | 无 | 更新数据。 |
| options | UpdateOption | 否 | 无 | 更新设置。 |


### UpdateOption


| 字段名 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| where | array | 否 | 无 | 更新条件。 |
| columns | array | 否 | 无 | 指定更新列名。 |


## 返回

UpdateResult.
| 字段名 | 类型 | 说明 |
| --- | --- | --- |
| count | int | 更新数据行数。 |


## 示例


```PHP
<?php

use Cloud\Cloud;
use Cloud\Mysql\UpdateOption;
use Cloud\Mysql\UpdateResult;

function update($event, $context): UpdateResult
{
$logger = $context->getLogger();
$cloud = new Cloud();
$mysql = $cloud->mysql();
$table = "your_table";
$where = array(
"user_name" => "your_name"
);
$row = array(
"description" => "updated mysql demo description"
);
$updateOption = new UpdateOption($where);
$result = $mysql->update($table, $row, $updateOption);
$logger->info("update", "update response:%s", json_encode($result));
return $result;
}
```
​
