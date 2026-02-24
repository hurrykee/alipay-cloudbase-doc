# getCurrentUser

返回文档获取当前登录用户对象。

## 请求参数

无。

## 返回参数


| 字段 | 类型 | 参数 | 说明 |
| --- | --- | --- | --- |
| user | User | 是 | 用户对象。 |


## 示例


```JavaScript
import { Auth } from '@alipay/faas-biz-mini-sdk';

const userPoolConfig = {
envId: 'your-env-id',
userPoolUid: 'your-userPool-uid',
};
const auth = new Auth(userPoolConfig);
await auth.getCurrentUser();
```
​
