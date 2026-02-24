# loginWithUserIdAndPassword

返回文档用户名密码登录。

## 请求参数


| 字段 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| idpUserId | string | 是 | 用户 UID。 |
| password | string | 是 | 密码。 |


## 返回参数


| 字段 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| user | User | 是 | 用户信息。 |
| loginType | string | 是 | 登录方式。 |
| isAlipayAuth | boolean | 是 | 支付宝三方登录。 |
| isUsernameAuth | boolean | 是 | 账密登录。 |


## 示例


```JavaScript
import { Auth } from "@alipay/faas-biz-web-sdk";

const userPoolConfig = {
envId: 'your-env-id',
userPoolUid: 'your-userPool-uid',
};
const auth = new Auth(userPoolConfig);
auth.loginWithUsernameAndPassword(username, password).then((res) => {
// 登录成功
});
```
​
