# select

返回文档查询数据。
```
<?php
public function select(string $table, SelectOption $option = null): array
```


## 请求参数


| 字段名 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| table | string | 是 | 无 | 查询操作表名。 |
| options | SelectOption | 否 | 无 | 查询设置。 |


### SelectOption


```
<?php
public function __construct(array $columns = [], array $where = [], array $orders = [], int $limit = 100, int $skip = 0)
```

| 字段名 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| columns | array | 否 | 无 | 指定查询列名。 |
| where | array | 否 | 无 | 查询条件。 |
| orders | array | 否 | 无 | 排序规则，类型为 string 时，以 orders 字段升序排序。 |
| limit | int | 否 | 无 | 最大返回数量 |
| skip | int | 否 | 无 | 跳过 skip 数量 |


## 返回参数

查询结果列表。
```PHP
<?php

$result = array(
array(
"user_name" => "test_user_222c8db9670983c1",
"description" => "mysql demo user"
),
array(
"user_name" => "test_user_12a9288b0f679a35",
"description" => "mysql demo user"
)
);
```


## 示例


```PHP
<?php

use Cloud\Cloud;
use Cloud\Mysql\SelectOption;
function select($event, $context): array
{
$logger = $context->getLogger();
$cloud = new Cloud();
$mysql = $cloud->mysql();
$table = "your_table";
$columns = array(
"user_name",
"description"
);
$orders = array(
"user_name" => "desc"
);
$where = array(
"user_name" => "your_name"
);
$limit = 1;
$skip = 1;
$selectOption = new SelectOption(
$columns,
$where,
$orders,
$limit,
$skip
);
$result = $mysql->select($table, $selectOption);
$logger->info("select", "select response:%s", json_encode($result));
return $result;
}
```
​
