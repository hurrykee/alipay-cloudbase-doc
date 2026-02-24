# getCurrentUser

返回文档获取当前用户信息。

## 请求参数

无。

## 返回参数


| 字段 | 类型 | 必填 | 描述 |
| --- | --- | --- | --- |
| uid | string | 是 | 用户 UID。 |
| userPoolUid | string | 是 | 用户池 ID。 |
| idpUid | string | 是 | 身份提供商 ID。 |
| idpUserId | string | 是 | 用户ID，在此供应商范围内唯一。 |
| username | string | 是 | 用户名。 |
| mobile | string | 否 | 手机号。 |
| email | string | 否 | 邮箱地址。 |
| avatar | string | 否 | 头像。 |
| locked | boolean | 是 | 是否锁定，默认 false。 |


## 示例


```JavaScript
const { Auth } = require("@alipay/faas-biz-server-sdk");

exports.main = async (event, context) => {
const auth = new Auth();
const user = await auth.getCurrentUser();
return user;
};
```
​
