# modifyUserPassword

返回文档修改用户密码。

## 请求参数


| 字段 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uid | string | 是 | 用户 UID。 |
| curPassword | string | 是 | 当前密码。 |
| newPassword | string | 是 | 新密码。 |


## 返回参数


| 字段 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| result | boolean | 是 | 修改是否成功。 |


## 示例


```JavaScript
const { Auth } = require("@alipay/faas-biz-server-sdk");

exports.main = async (event, context) => {
const auth = new Auth();
const result = await auth.modifyUserPassword(event.uid, event.curPassword, event.newPassword);
return result;
};
```
​
