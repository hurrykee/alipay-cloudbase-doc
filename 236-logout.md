# logout

返回文档退出登录。

## 请求参数

无。

## 返回参数

无。

## 示例


```JavaScript
import { Auth } from "@alipay/faas-biz-mini-sdk";

const userPoolConfig = {
envId: 'your-env-id',
userPoolUid: 'your-userPool-uid',
};
const auth = new Auth(userPoolConfig);
auth.logout();
```
​
