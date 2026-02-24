# group

返回文档聚合流水线的分组阶段，通过参数 _id 指定分组字段，返回结果一条记录为一个分组。
```
<?php
public function group($group): Aggregate
```


## 请求参数


| 字段名 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| group | array \| QueryChain | 是 | 无 | 分组统计规则，其中 _id 为必填项，用于指定分组字段，该字段的相同取值归为一组，再通过其他 key 进行计数、平均值计算等等统计操作。 |
group 参数结构为：
```
{
_id => <expression>,
<key1> => <operator1>,
<key2> => <operator2>,
...
}
```


## 返回参数

Aggregate 聚合流水线构建 client。

## 示例


```PHP
<?php
use Cloud\Cloud;
function group($event, $context): array
{
$logger = $context->getLogger();
$cloud = new Cloud();
$database = $cloud->database();
$command = $database->command;
$aggregateCommand = $command->aggregate;
$aggregateArray = array(
"_id" => "$" . "class",
"max" => $aggregateCommand->max("$" . "some-field-name")
);
$result = $database
->collection("collectionName")
->aggregate()
->group($aggregateArray)
->end();
$logger->info("group", "group response:%s", json_encode($result));
return $result;
}
```
​
