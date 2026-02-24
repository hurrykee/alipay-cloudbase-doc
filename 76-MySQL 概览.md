# MySQL 概览

返回文档获取 MySQL 数据库对象。
```
function mysql(): MySQL;
```


## 请求参数

无。

## 返回值 MySQL


| 字段 | 备注 |
| --- | --- |
| MySQL.query | 执行 sql 语句。 |
| MySQL.insert | 插入数据。 |
| MySQL.update | 更新数据。 |
| MySQL.select | 查询数据。 |
| MySQL.get | 查询数据。 |
| MySQL.delete | 删除数据。 |


## 示例


```JavaScript
const cloud = require("@alipay/faas-server-sdk");
// 获取 cloud 环境中的 mysql 数据库对象
const mysql = cloud.mysql();
```
​
