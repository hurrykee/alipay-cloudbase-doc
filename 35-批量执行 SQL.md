# 批量执行 SQL

返回文档批量执行 SQL 是指一次性执行多条 SQL 语句，通常用于批量数据的导入、备份或删除等操作。本文主要介绍批量执行 SQL 的方法。

## 操作步骤

1在数据库管理页面，左侧库表资源区选择要批量执行 SQL 的目标库，右击打开功能菜单，选择批量执行 SQL，打开批量执行 SQL 弹框。
2在批量执行 SQL 弹窗中配置参数，配置完成后单击确定。参数说明如下：
| 参数 | 说明 |
| --- | --- |
| 数据库 | 默认填入无法更改。若想更改，请在左侧库表资源区找到相应数据库重新打开功能。 |
| 批量 SQL | ●上传 SQL 文件：单击上传文件，即可上传附件。○文件类型当前支持 TXT、SQL，最大不能超过 3 GB，每条 SQL 不能超过 3 MB。●填入 SQL 文本：在 SQL 文本框中，输入可直接执行的 SQL 语句。○多条 SQL 之间，请用英文分号（;）隔开。○SQL 文本最大不能超过 2 MB。 |
| 兼容MySQL语法 | 默认开启。开启语法兼容将自动忽略或转换您的部分 SQL，请仔细阅读以下影响：●忽略所有 DCL，如CREATE USER、GRANT、REVOKE、LOCK 等。●忽略所有 TCL，如BEGIN、COMMIT、ROLLBACK 等。●忽略 CREATE TABLE 语句中的 MySQL 特有 OPTION 参数，如 ENGINE 等。●自动转换字符集和排序规则。●字符集转换：○gb2312、gbk：转换成 gbk。○utf16、utf16le、utf32：转换成 utf16。○其他：转换成 utf8mb4。●排序规则转换：○utf16、utf32：有 bin 则转换成 utf16_bin，没有 bin 则转换成 utf16_general_ci。○gbk：有 bin 则转换成 gbk_bin，没有 bin 则转换成 gbk_chinese_ci。○其他：有 bin 则转换成 utf8mb4_bin，没有 bin 则转换成 utf8mb4_general_ci。 |
| 开启事务 | 默认关闭。事务说明：●仅支持 dml 的整体事务。●ddl 不支持事务,事务回滚 ddl 也不会回滚。●不支持内嵌事务。 |
| 失败处理 | ●失败报错：无法继续执行。●自动跳过，继续执行：只有错误的跳过，其他继续执行，直到结束。 |


## 支持的 SQL 类型

●CREATE TABLE●DROP TABLE●ALTER TABLE●RENAME TABLE●CREATE FUNCTION●DROP FUNCTION●DROP TABLE_GROUP●ALTER TABLE_GROUP●DROP INDEX●SET COMMENT●INSERT●REPLACE●INSERT SELECT●REPLACE SELECT●UPDATE●DELETE●TRUNCATE TABLE​
