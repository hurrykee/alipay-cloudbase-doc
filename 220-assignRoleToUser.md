# assignRoleToUser

返回文档为用户添加角色。

## 请求参数


| 字段 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userUid | string | 是 | 用户 UID。 |
| roleName | string | 是 | 角色编码。 |


## 返回参数


| 字段 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| result | boolean | 是 | 添加角色是否成功。 |


## 示例


```JavaScript
const { Auth } = require("@alipay/faas-biz-server-sdk");

exports.main = async (event, context) => {
const auth = new Auth();
const result = await auth.assignRoleForUser(event.uid, event.roleName);
return result;
};
```
​
