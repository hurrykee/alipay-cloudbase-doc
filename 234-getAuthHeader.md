# getAuthHeader

返回文档获取 HTTP 鉴权头部。

## 请求参数

无。

## 返回参数


| 字段 | 类型 | 参数 | 说明 |
| --- | --- | --- | --- |
| x-faas-context-authorization | string | 是 | 鉴权头部信息。 |


## 示例


```JavaScript
import { Auth } from '@alipay/faas-biz-mini-sdk';

const userPoolConfig = {
envId: 'your-env-id',
userPoolUid: 'your-userPool-uid',
};
const auth = new Auth(userPoolConfig);
await auth.getAuthHeader();
```
​
