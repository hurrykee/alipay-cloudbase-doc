# insert

返回文档插入数据。insert 方法类型定义：
```
function insert(table: string, rows: object | object[], option?: InsertOption): Promise<InsertResult>;
```


## 请求参数


| 字段名 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| table | string | 是 | 无 | 插入数据的表名。 |
| rows | object \| object[] | 是 | 无 | 需要插入的一条或多条数据。 |
| options | InsertOption | 否 | 无 | 插入设置。 |
InsertOption.
| 字段名 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| columns | string[] | 否 | 无 | 指定要插入的列名 |


## 返回参数

InsertResult.

## 示例

### 插入一条数据


```JavaScript
const cloud = require("@alipay/faas-server-sdk");

exports.main = async (event, context) => {
const mysql = cloud.mysql();
return await mysql.insert(
'some-table',
[
{
name: 'exmaple1',
email: 'email1@test.com',
},
{
name: 'exmaple2',
email: 'email2@test.com',
},
],
);
};
```


### 插入多条数据


```JavaScript
const cloud = require("@alipay/faas-server-sdk");

exports.main = async (event, context) => {
const mysql = cloud.mysql();
return await mysql.insert(
'some-table',
{
name: 'exmaple',
email: 'email@test.com',
ignoretitle: 'foo title',
},
{
columns: [ 'name', 'email' ],
},
);
};
```


### 指定列名

​
