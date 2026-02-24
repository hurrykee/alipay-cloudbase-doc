# beginTransactionScope

返回文档新建事务运行作用域，在该作用域中的所有数据库操作将在同一事务中执行。当执行成功后，将自动提交事务；当执行异常时，将自动回滚事务。beginTransactionScope 方法类型定义：
```
function beginTransactionScope(scope: (transaction: MySQLTransaction) => Promise<any>): Promise<any>;
```


## 请求参数

(transaction: MySQLTransaction) => Promise<any> 执行事务的作用域函数。

## 返回参数

any 执行结果。

## 示例

在 beginTransactionScope 中执行的数据库操作，将在同一事务中进行。
```TypeScript
const cloud = require("@alipay/faas-server-sdk");

exports.main = async (event, context) => {
const mysql = cloud.mysql();
return await mysql.beginTransactionScope(async (transaction) => {
const res1 = await transaction.insert(
'some-table',
{ user_id: '001', name: 'someone' },
);
const res2 = await transaction.update(
'some-table',
{ id: '999', name: 'updated name' },
);
return { res1, res2 };
});
};
```
若并发调用多次 beginTransactionScope，将执行多个相互隔离的事务。
```TypeScript
const cloud = require("@alipay/faas-server-sdk");

exports.main = async (event, context) => {
const mysql = cloud.mysql();
return await Promise.all(
// 事务1 执行成功
mysql.beginTransactionScope(async (transaction) => {
const res1 = await transaction.insert(
'some-table',
{ user_id: '001', name: 'someone' },
);
const res2 = await transaction.update(
'some-table',
{ id: '999', name: 'updated name' },
);
return { res1, res2 };
}),
// 事务 2 执行失败不会导致事务 1 回滚
mysql.beginTransactionScope(async (transaction) => {
await transaction.insert(
'unknown-table',
{ user_id: '002', name: 'somebody' },
);
}),
});
};
```
​
