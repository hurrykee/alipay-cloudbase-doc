# getCurrentUser

返回文档获取当前登录用户对象，如果未登录，则返回 null。

## 请求参数

无

## 返回参数


| 字段 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| user | User | 是 | 用户对象。 |


## 示例


```JavaScript
import { Auth } from "@alipay/faas-biz-web-sdk";

const userPoolConfig = {
envId: 'your-env-id',
userPoolUid: 'your-userPool-uid',
};
const auth = new Auth(userPoolConfig);
auth.getCurrentUser()
.then((res) => {
//获取当前登录用户对象成功
});
```
​
