# update

返回文档更新集合中全部信息。
```
<?php
public function update(UpdateData $data): UpdateResult
```


## 请求参数

### UpdateData


| 字段名 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| data | array | 是 | 无 | 文档数据。 |


## 返回参数

### UpdateResult


| 字段名 | 类型 | 说明 |
| --- | --- | --- |
| count | int | 更新文档数。 |


## 示例


```PHP
<?php

use Cloud\Cloud;
use Cloud\Mongodb\UpdateData;
use Cloud\Mongodb\UpdateResult;
function update($event, $context): UpdateResult
{
$logger = $context->getLogger();
$cloud = new Cloud();
$database = $cloud->database();
$data = new UpdateData(
array(
"keyValue" => "updateValue"
)
);
$result = $database
->collection("collectionName")
->update($data);
$logger->info("update", "update response:%s", json_encode($result));
return $result;
}
```
​
