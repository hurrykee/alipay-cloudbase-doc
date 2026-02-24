# getAlipayAuthProvider.login

返回文档支付宝登录。

## 请求参数

无。

## 返回参数


| 字段 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| user | User | 是 | 用户信息。 |
| loginType | string | 是 | 登录方式。 |
| isAlipayAuth | boolean | 是 | 支付宝三方登录。 |


## 示例


```JavaScript
import { Auth } from '@alipay/faas-biz-mini-sdk';

const userPoolConfig = {
envId: 'your-env-id',
userPoolUid: 'your-userPool-uid',
};
const auth = new Auth(userPoolConfig);
const alipayAuthProvider = auth.getAlipayAuthProvider();
alipayAuthProvider.login().then(res => {
//登录成功
});
```
​
