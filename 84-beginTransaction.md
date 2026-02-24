# beginTransaction

返回文档新建 mysql 事务。beginTransaction 方法类型定义：
```
function beginTransaction(): Promise<MySQLTransaction>;
```


## 请求参数

无。

## 返回值 MySQLTransaction

mysql 事务实例，通过该实例的方法进行 CRUD 操作，即会在同一事务中进行。事务完成后，可进行 commit 或 rollback 操作。MySQLTransaction 类提供的方法如下表所示。
| 字段 | 说明 |
| --- | --- |
| query | 执行 sql 语句。 |
| insert | 插入数据。 |
| update | 更新数据。 |
| select | 查询数据。 |
| get | 查询数据。 |
| delete | 删除数据。 |
| count | 统计行数。 |
| commit | 提交事务。 |
| rollback | 回滚事务。 |


## 示例


```TypeScript
const cloud = require("@alipay/faas-server-sdk");

exports.main = async (event, context) => {
const mysql = cloud.mysql();
const transaction = await mysql.beginTransaction();
try {
await transaction.insert(
'some-table',
{ user_id: '001', name: 'someone' },
);
await transaction.update(
'some-table',
{ id: '999', name: 'updated name' },
);
await transaction.commit();
return { message: '事务执行成功' };
} catch(e) {
console.log(e);
await transaction.rollback();
return { message: '事务执行失败，回滚' };
}
};
```
​
