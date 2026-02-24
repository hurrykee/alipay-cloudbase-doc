# RegExp

返回文档构造正则表达式，用于查询符合条件的数据。RegExp 方法类型定义：
```
function RegExp(param: RegExpParam): Regex;
```


## 请求参数

RegExpParam.
| 字段名 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| regexp | string | 是 | 无 | 正则表达式字符串。 |
| options | string | 否 | 无 | i: 忽略大小写。m: 跨行匹配。s: . 可匹配所有字符。 |


## 返回参数

Regex 正则表达式对象。

## 示例

### 单条件查询


```TypeScript
const cloud = require('@alipay/faas-server-sdk');

exports.main = async (event, context) => {
const db = cloud.database();

const alipayNames = await db.collection('product').where({
// 查询字段name中名称以 alipay 开头的数据
name: db.RegExp({
regexp: '^alipay',
}),
}).get();

const newDocs = await db.collection('product').where({
// 忽略大小写，查询tag字段中标签包含 new 的数据
tag: db.RegExp({
regexp: 'new',
options: 'i',
}),
}).get();

return {
alipayNames,
newDocs,
};
};
```


### 多条件查询


```JavaScript
const cloud = require("@alipay/faas-server-sdk");

exports.main = async (event, context) => {
const db = cloud.database();

return await db.collection('Attraction').where({
//$or 或者 $and
$or: [
{grad: db.regex({regexp: '5A'})},
{grad: db.regex({regexp: '4A'})},
],
}).get();
};
```
​
