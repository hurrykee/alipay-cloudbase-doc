# count

返回文档统计行数。count 方法类型定义：
```
function count(table: string, where?: object): Promise<number>;
```


## 请求参数


| 字段名 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| table | string | 是 | 无 | 操作表名。 |
| where | object | 否 | 无 | 过滤条件。 |


## 返回参数

number 符合条件的行数。

## 示例


```TypeScript
const cloud = require("@alipay/faas-server-sdk");

exports.main = async (event, context) => {
const mysql = cloud.mysql();
return await mysql.count(
'some-table',
{
name: 'foo',
},
);
};
```
​
