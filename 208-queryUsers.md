# queryUsers

返回文档查询用户。

## 请求参数


| 字段 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userPoolUid | string | 是 | 用户池 ID。 |
| idpUid | string | 否 | 身份提供商 ID。 |
| idpUserId | string | 否 | 用户 ID，在此供应商范围内唯一。 |
| username | string | 否 | 用户名。 |
| locked | string | 否 | 是否冻结。 |
| pageIndex | int | 否 | 起始页。 |
| pageSize | int | 否 | 页行数。 |


## 返回参数


| 字段 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| total | int | 是 | 查询结果总数。 |
| pageIndex | int | 是 | 当前行。 |
| pageSize | int | 是 | 页行数。 |
| users | User | 是 | 查询结果集。 |


## 示例


```JavaScript
const { Auth } = require("@alipay/faas-biz-server-sdk");

exports.main = async (event, context) => {
const auth = new Auth();
const userList = await auth.queryUsers(event.userPoolUid, event.idpUid, event.idpUserId, event.locked, event.pageIndex, event.pageSize);
return userList;
};
```
​
