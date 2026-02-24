# sample

返回文档聚合流水线的抽样阶段，从文档列表中随机选取指定数量的文档。
```
<?php
public function sample(SampleAggregateParam $sample = null): Aggregate
```


## 请求参数

### SampleAggregateParam


| 字段名 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| size | int | 是 | 无 | 数量。 |


## 返回参数

Aggregate 聚合流水线构建 client。

## 示例


```PHP
<?php
use Cloud\Cloud;
use Cloud\Mongodb\SampleAggregateParam;
function sample($event, $context): array
{
$logger = $context->getLogger();
$cloud = new Cloud();
$database = $cloud->database();
$sample = new SampleAggregateParam(2);
$result = $database
->collection("collectionName")
->aggregate()
->sample($sample)
->end();
$logger->info("sample", "sample response:%s", json_encode($result));
return $result;
}
```
​
