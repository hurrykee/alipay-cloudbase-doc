# getAlipayContext

返回文档获取云函数运行上下文信息。

## 请求参数

无。

## 返回参数

### AlipayContext


| 字段名 | 类型 | 说明 |
| --- | --- | --- |
| unionId | string | 小程序用户 unionId。 |
| clientIp | string | 小程序客户端 IPv4 地址。 |
| clientIpv6 | string | 小程序客户端 IPv6 地址。 |
| userAgent | string | 用户设备信息。 |
| fromAppId | string | 调用来源方小程序 appId。 |
| fromOpenId | string | 调用来源方小程序用户 openId。 |
| fromUnionId | string | 调用来源方用户 unionId。 |
| openDataInfo | string | 空。 |
| appId | string | 小程序 appId。 |
| openId | string | 小程序用户 openId，目前功能处于灰度中，需要手动开启。详情可参考 openid 升级指南。 |
| env | string | 云函数所在环境的 id。 |
| source | string | 调用来源。 |
| traceId | string | 调用 traceId。 |
| rpcId | string | 空。 |
| requestId | string | 空。 |


## 示例


```PHP
<?php
use Cloud\Context\AlipayContext;
function main($event, $context): AlipayContext
{
$logger = $context->getLogger();
$alipayContext = $context->getAlipayContext();
$logger->info("getAlipayContext", "getAlipayContext response:%s", json_encode($alipayContext));
return $alipayContext;
}
```
​
