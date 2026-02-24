# getAlipayContext

返回文档获取云函数运行上下文信息。getAlipayContext 方法类型定义：
```
function getAlipayContext(): AlipayContext;
```


## 返回参数

AlipayContext.
| 字段名 | 类型 | 说明 |
| --- | --- | --- |
| UNIONID | string | 小程序用户 unionid。 |
| CLIENTIP | string | 小程序客户端 IPv4 地址。 |
| CLIENTIPV6 | string | 小程序客户端 IPv6 地址。 |
| FROM_APPID | string | 调用来源方小程序 AppID。 |
| FROM_OPENID | string | 调用来源方小程序用户 openid。 |
| FROM_UNIONID | string | 调用来源方用户 unionid。 |
| OPEN_DATA_INFO | string | 空。 |
| APPID | string | 小程序 AppID。 |
| OPENID | string | 小程序用户 openid，目前功能处于灰度中，需要手动开启。详情可参考 openid 升级指南。 |
| ENV | string | 云函数所在环境的 ID。 |
| SOURCE | string | 调用来源。 |
| TRACEID | string | 调用 traceid。 |
| RPCID | string | 空。 |
| REQUESTID | string | 空。 |


## 示例


```JavaScript
const cloud = require("@alipay/faas-server-sdk");
/**
* 只有小程序开通 OPENID 才可以通过这种方式获取到，OPENID 使用处于灰度阶段
* @param {*} event
* @param {*} context
*/
exports.main = async (event, context) => {

// 从小程序过来的请求可以获取到可信的 openId 和 appId
let { OPENID, APPID } = cloud.getAlipayContext();
if(!OPENID){
console.log(" 未获取到 OPENID ，在 O 站检查是否开启 OPENID ")
}
return cloud.getAlipayContext();
};
```
​
