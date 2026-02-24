# unlockUser

返回文档解锁用户。

## 请求参数


| 字段 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uid | string | 是 | 用户 UID。 |


## 返回参数


| 字段 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| result | boolean | 是 | 修改是否成功。 |


## 示例


```JavaScript
const { Auth } = require("@alipay/faas-biz-server-sdk");

exports.main = async (event, context) => {
const auth = new Auth();
const result = await auth.unlockUser(event.uid);
return result;
};
```
​
