# queryRolePermissions

返回文档查询角色权限。

## 请求参数


| 字段 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| roleUid | string | 是 | 角色 UID。 |


## 返回参数


| 字段 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| total | int | 是 | 查询结果总数。 |
| pageIndex | int | 是 | 当前行。 |
| pageSize | int | 是 | 页行数。 |
| permisssions | Permission | 是 | 查询结果集。 |


## 示例


```JavaScript
const { Auth } = require("@alipay/faas-biz-server-sdk");

exports.main = async (event, context) => {
const auth = new Auth();
const result = await auth.queryRolePermissions(event.uid);
return result;
};
```
​
