# getPermission

返回文档获取权限信息。

## 请求参数


| 字段 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uid | string | 是 | 权限 UID。 |


## 返回参数


| 字段 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userPoolUid | string | 是 | 用户池 ID。 |
| uid | string | 是 | 权限 UID。 |
| name | string | 是 | 权限编码。 |
| displayName | string | 是 | 权限名称。 |
| description | string | 否 | 备注。 |


## 示例


```JavaScript
const { Auth } = require("@alipay/faas-biz-server-sdk");

exports.main = async (event, context) => {
const auth = new Auth();
const result = await auth.getPermissionInfo(event.uid);
return result;
};
```
​
