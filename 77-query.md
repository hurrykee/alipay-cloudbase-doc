# query

返回文档执行 sql 语句。
```
function query<T=any>(sql: string, values?: object | any[]): Promise<T>;
```


## 请求参数


| 字段名 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| sql | string | 是 | 无 | sql 语句模版。 |
| values | object \| any[] | 否 | 无 | 渲染到 sql 语句中的参数。 |


## 返回参数

sql 语句执行结果。

## 示例

### 无参数


```JavaScript
const cloud = require("@alipay/faas-server-sdk");

exports.main = async (event, context) => {
const mysql = cloud.mysql();
return await mysql.query('SELECT * FROM your_table where id = ?', ['some-id']);
};
```


### 数组类型渲染参数


```JavaScript
const cloud = require("@alipay/faas-server-sdk");

exports.main = async (event, context) => {
const mysql = cloud.mysql();
return await mysql.query('SELECT * FROM your_table WHERE id=:id', { id: 123 });
};
```


### 对象类型渲染参数

​
