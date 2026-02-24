# getRole

返回文档获取角色。

## 请求参数


| 字段 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uid | string | 是 | 角色 UID。 |


## 返回参数


| 字段 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uid | string | 是 | 角色 UID。 |
| userPoolUid | string | 是 | 用户池 ID。 |
| name | string | 是 | 角色编码。 |
| displayName | string | 是 | 角色名。 |
| description | string | 否 | 备注。 |


## 示例


```JavaScript
const { Auth } = require("@alipay/faas-biz-server-sdk");

exports.main = async (event, context) => {
const auth = new Auth();
const result = await auth.getRoleInfo(event.uid);
return result;
};
```
​
