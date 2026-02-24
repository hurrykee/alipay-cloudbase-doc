# resetUserPassword

返回文档需当前密码，直接重置用户密码。

## 请求参数


| 字段 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uid | string | 是 | 用户 UID。 |
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
const result = await auth.resetUserPassword(event.uid, event.newPassword);
return result;
};
```
​
