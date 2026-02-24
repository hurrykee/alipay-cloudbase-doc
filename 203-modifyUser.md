# modifyUser

返回文档修改用户信息。

## 请求参数


| 字段 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uid | string | 是 | 用户 UID。 |
| username | string | 否 | 用户名。 |
| mobile | string | 否 | 手机号。 |
| email | string | 否 | 邮箱地址。 |
| avatar | string | 否 | 头像。 |


## 返回参数


| 字段 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| result | boolean | 是 | 修改是否成功。 |


## 示例


```JavaScript
const { Auth } = require("@alipay/faas-biz-server-sdk");

exports.main = async (event, context) => {
const auth = new Auth();
const result = await auth.modifyUserInfo(event.uid, event.userName, event.mobile, event.email, event.avatar);
return result;
};
```
​
