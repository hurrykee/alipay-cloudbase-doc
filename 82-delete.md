# delete

返回文档删除数据。get 方法类型定义：
```
function get(table: string, where?: object): Promise<DeleteResult>;
```


## 请求参数


| 字段名 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| table | string | 是 | 无 | 删除操作表名。 |
| where | object | 否 | 无 | 删除条件。 |


## 返回参数

DeleteResult.
| 字段名 | 类型 | 说明 |
| --- | --- | --- |
| count | number | 删除数据行数。 |


## 示例


```TypeScript
const cloud = require("@alipay/faas-server-sdk");

exports.main = async (event, context) => {
const mysql = cloud.mysql();
return await mysql.delete(
'some-table',
{
name: 'to-be-deleted',
},
);
};
```
​
