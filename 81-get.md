# get

返回文档查询数据。
```
function get(table: string, where?: object, option?: SelectOption): Promise<any>;
```


## 请求参数


| 字段名 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| table | string | 是 | 无 | 查询操作表名。 |
| where | object | 否 | 无 | 查询条件。 |
| options | SelectOption | 否 | 无 | 查询设置。 |
SelectOption.
| 字段名 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| columns | string \| string[] | 否 | 无 | 指定查询列名。 |
| orders | string \| any[] | 否 | 无 | 排序规则，类型为 string 时，以 orders 字段升序排序。 |
| limit | number | 否 | 无 | 最大返回数量。 |
| skip | number | 否 | 无 | 跳过 skip 数量。 |


## 返回参数

查询结果列表。说明：Get 只会返回一条数据。

## 示例


```TypeScript
const cloud = require("@alipay/faas-server-sdk");

exports.main = async (event, context) => {
const mysql = cloud.mysql();
return await mysql.get(
'some-table',
{
type: 'target',
},
{
columns: ['author', 'title'],
// orders: 'createTime', 二者等价
orders: [['createTime', 'ASC']],
limit: 20,
skip: 10,
},
);
};
```
​
