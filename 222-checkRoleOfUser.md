# checkRoleOfUser

返回文档检查用户是否拥有角色。

## 请求参数


| 字段 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userUid | string | 是 | 用户 UID。 |
| roleName | string | 是 | 角色编码。 |


## 返回参数


| 字段 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| result | boolean | 是 | 用户是否拥有角色。 |


## 示例


```JavaScript
const { Auth } = require("@alipay/faas-biz-server-sdk");

exports.main = async (event, context) => {
const auth = new Auth();
const result = await auth.checkRoleForUser(event.uid, event.roleName);
return result;
};
```
​
