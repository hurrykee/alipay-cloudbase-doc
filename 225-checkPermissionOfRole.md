# checkPermissionOfRole

返回文档检查角色是否拥有权限。

## 请求参数


| 字段 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| roleUid | string | 是 | 角色 UID。 |
| permissionName | string | 是 | 权限编码。 |


## 返回参数


| 字段 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| result | boolean | 是 | 角色是否拥有权限。 |


## 示例


```JavaScript
const { Auth } = require("@alipay/faas-biz-server-sdk");

exports.main = async (event, context) => {
const auth = new Auth();
const result = await auth.checkPermissionForRole(event.uid, event.permissionName);
return result;
};
```
​
