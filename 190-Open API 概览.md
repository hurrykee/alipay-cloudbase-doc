# Open API 概览

返回文档获取 OpenAPI client。
```
<?php
public function openapi(): OpenApiClient
```


## 请求参数

无。

## 返回参数

### OpenApiClient


| API | 类别 | 说明 |
| --- | --- | --- |
| openapi->openapi() | 方法 | 调用 Open API 的通用方法。 |


## 示例


```PHP
<?php
use Cloud\Cloud;

$cloud = new Cloud();
$openapi = $cloud->openapi();
```
​
