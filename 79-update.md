# update

返回文档更新数据update 方法类型定义：
```
function insert(table: string, row: object, option?: UpdateOption): Promise<UpdateResult>;
```


## 请求参数


| 字段名 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| table | string | 是 | 无 | 更新操作表名。 |
| row | object | 是 | 无 | 更新数据。 |
| options | UpdateOption | 否 | 无 | 更新设置。 |
UpdateOption.
| 字段名 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| where | object | 否 | 无 | 更新条件。 |
| columns | string[] | 否 | 无 | 指定更新列名。 |


## 返回参数

UpdateResult.
| 字段名 | 类型 | 说明 |
| --- | --- | --- |
| count | number | 更新数据行数。 |


## 示例

### 更新一条数据


```JavaScript
const cloud = require("@alipay/faas-server-sdk");

exports.main = async (event, context) => {
const mysql = cloud.mysql();
return await mysql.update(
'some-table',
{
name: 'exmaple-update',
email: 'email1@test.com',
},
{
where: {
name: 'example',
},
},
);
};
```


### 条件更新


```JavaScript
const cloud = require("@alipay/faas-server-sdk");

exports.main = async (event, context) => {
const mysql = cloud.mysql();
return await mysql.update(
'some-table',
{
name: 'exmaple-update',
email: 'email1@test.com',
},
{
where: {
name: 'example',
},
},
);
};
```


### 指定列名

​
