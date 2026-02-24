# createPermission

返回文档创建权限。

## 请求参数


| 字段 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userPoolUid | string | 是 | 用户池 ID。 |
| name | string | 是 | 权限编码。 |
| displayName | string | 是 | 权限名称。 |
| description | string | 否 | 备注。 |


## 返回参数


| 字段 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uid | string | 是 | 权限 UID。 |


## 示例


```JavaScript
const { Auth } = require("@alipay/faas-biz-server-sdk");

exports.main = async (event, context) => {
const auth = new Auth();
const result = await auth.createPermission(event.userPoolUid, event.name, event.displayName, event.description);
return result;
};
```
​
