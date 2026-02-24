# createUser

返回文档创建用户。

## 请求参数


| 字段 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userPoolUid | string | 是 | 用户池 ID。 |
| idpUid | string | 是 | 身份提供商 ID。 |
| idpUserId | string | 是 | 用户ID，在此供应商范围内唯一。 |
| username | string | 是 | 用户名。 |
| password | string | 是 | 密码。 |
| mobile | string | 否 | 手机号。 |
| email | string | 否 | 邮箱地址。 |
| avatar | string | 否 | 头像。 |


## 返回参数


| 字段 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uid | string | 是 | 用户 UID。 |


## 示例


```JavaScript
const { Auth } = require("@alipay/faas-biz-server-sdk");

exports.main = async (event, context) => {
const auth = new Auth();
const result = await auth.createUser(event.userPoolUid, event.idpUid, event.idpUserId, event.userName, event.password, event.mobile, event.email, event.avatar);
return result;
};
```
​
