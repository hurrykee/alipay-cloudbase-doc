# queryUserRoles

返回文档查询用户角色。

## 请求参数


| 字段 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userUid | string | 是 | 用户 UID。 |
| pageIndex | int | 否 | 起始页索引。 |
| pageSize | int | 否 | 每页条数。 |


## 返回参数


| 字段 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| total | int | 是 | 查询结果总数。 |
| pageIndex | int | 是 | 当前行。 |
| pageSize | int | 是 | 页行数。 |
| roles | Roles | 是 | 查询结果集。 |


## 示例


```JavaScript
const { Auth } = require("@alipay/faas-biz-server-sdk");

exports.main = async (event, context) => {
const auth = new Auth();
const result = await auth.queryUserRoles(event.uid, event.pageIndex, event.pageSize);
return result;
};
```
​
