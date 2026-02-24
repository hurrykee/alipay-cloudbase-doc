# projection

返回文档指定返回结果中文档的字段。
```
<?php
public function projection(array $projection): Document
```


## 请求参数


| 字段名 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| projection | array | 是 | 无 | 字段是否返回的配置，对象 key 为字段名，value 为 true 或1表示需要返回，value 为 false 或0表示不需要返回。 |


## 返回参数

Document client.

## 示例


```PHP
<?php

use Cloud\Cloud;
function projection($event, $context): array
{
$logger = $context->getLogger();
$cloud = new Cloud();
$database = $cloud->database();
$projection = array(
"some-field-name" => false,
"some-field-name-two" => true
);
$result = $database
->collection("collectionName")
->doc("some-doc-id")
->projection($projection)
->get();
$logger->info("projection", "projection response:%s", json_encode($result));
return $result;
}
```
​
