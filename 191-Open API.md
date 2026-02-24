# Open API

返回文档

## 请求参数

### OpenApiRequest


| 字段名 | 类型 | 说明 |
| --- | --- | --- |
| name | string | 目标 API 名称。 |
| version | string | 目标 API 版本，不填则为空，服务端会自动填写为1.0版本。 |
| body | string | 请求体内容。 |


## 返回参数

mixed.

## 示例


```PHP
<?php
use Cloud\Cloud;
use Cloud\OpenApi\OpenApiRequest;
function openapi($event, $context)
{
$logger = $context->getLogger();
$cloud = new Cloud();
$openapi = $cloud->openapi();
$name = "alipay.open.app.qrcode.create";
$version = "";
$array = array(
"url_param" => "page/component/component-pages/view/view",
"query_param" => "x=1",
"describe" => "二维码描述",
"color" => "0x00BFFF",
"size" => "s"
);
$arrayEntity = array(
"biz_content" => json_encode($array)
);
$openapiParam = new OpenApiRequest($name, $version, $arrayEntity);
$result = $openapi->openapi($openapiParam);
$logger->info("openapi", "openapi response:%s", json_encode($result));
return $result;
}
```
​
