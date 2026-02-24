# modifyRole

返回文档修改角色。

## 请求参数


| 字段 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uid | string | 是 | 角色 UID。 |
| name | string | 否 | 角色编码。 |
| displayName | string | 否 | 角色名称。 |
| description | string | 否 | 备注。 |


## 返回参数


| 字段 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| result | boolean | 是 | 修改角色是否成功。 |


## 示例


```JavaScript
const { Auth } = require("@alipay/faas-biz-server-sdk");

exports.main = async (event, context) => {
const auth = new Auth();
const result = await auth.modifyRoleInfo(event.uid, event.name, event.displayName, event.description);
return result;
};
```
​
