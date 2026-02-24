# assignPermissionToRole

返回文档为角色添加权限。

## 请求参数


| 字段 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| roleUid | string | 是 | 权限 UID。 |
| permissionName | string | 是 | 权限编码。 |


## 返回参数


| 字段 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| result | boolean | 是 | 添加权限是否成功。 |


## 示例


```JavaScript
const { Auth } = require("@alipay/faas-biz-server-sdk");

exports.main = async (event, context) => {
const auth = new Auth();
const result = await auth.assignPermissionForRole(event.uid, event.permissionName);
return result;
};
```
​
