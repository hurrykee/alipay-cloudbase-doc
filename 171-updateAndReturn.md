# updateAndReturn

返回文档用于向指定集合中查询一条数据并更新。
```
<?php
public function updateAndReturn(UpdateData $data): UpdateAndReturnDocumentResult
```


## 请求参数

### UpdateData


| 字段名 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| data | array | 是 | 无 | 文档数据。 |


## 返回参数

### UpdateAndReturnDocumentResult


| 字段名 | 类型 | 说明 |
| --- | --- | --- |
| updated | int | 操作状态 成功 1，失败 0。 |
| doc | - | 更新后文档数据。 |


## 示例


```PHP
<?php

use Cloud\Cloud;
use Cloud\Mongodb\UpdateData;
use Cloud\Mongodb\UpdateAndReturnDocumentResult;
function updateAndReturn($event, $context): UpdateAndReturnDocumentResult
{
$logger = $context->getLogger();
$cloud = new Cloud();
$database = $cloud->database();
$data = new UpdateData(
array(
"some-field-name" => "updateValue"
)
);
$result = $database
->collection("collectionName")
->doc("some-doc-id")
->updateAndReturn($data);
$logger->info("updateAndReturn", "updateAndReturn response:%s", json_encode($result));
return $result;
}
```
​
