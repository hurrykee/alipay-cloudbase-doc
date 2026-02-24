# modifyPermission

返回文档修改权限。

## 请求参数


| 字段 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uid | string | 是 | 权限 UID。 |
| name | string | 否 | 权限编码。 |
| displayName | string | 否 | 权限名称。 |
| description | string | 否 | 备注。 |


## 返回参数


| 字段 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| result | boolean | 是 | 修改是否成功。 |


## 示例


```JavaScript
const { Auth } = require("@alipay/faas-biz-server-sdk");

exports.main = async (event, context) => {
const auth = new Auth();
const result = await auth.modifyPermissionInfo(event.uid, event.name, event.displayName, event.description);
return result;
};
```
​
