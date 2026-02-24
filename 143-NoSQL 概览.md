# NoSQL 概览

返回文档获取 MongoDB client。
```
<?php
public function database(GetDatabaseParam $param = null): Database
```


## 请求参数

### GetDatabaseParam


| 字段名 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| env | string | 否 | 无 | 环境 ID，不填则使用 cloud 中的值。 |
| throwOnNotFound | boolean | 否 | true | doc(id)->get() 为空时，是否抛出异常。 |
| ignoreCollectionExists | boolean | 否 | false | createCollection 时，若 collection 已存在，是否直接返回已存在的 collection。若为 false，则抛出异常。 |
| timeout | int | 否 | 5000 | 请求超时时间（单位：毫秒），默认为5秒。 |


## 返回参数

### Database


| API | 类别 | 说明 |
| --- | --- | --- |
| database->command() | 属性 | 数据库操作符 client。 |
| database->collection() | 方法 | 获取 Collection client。 |
| database->createCollection() | 新建集合。 |  |
| database->getCollection() | 查询集合信息。 |  |
| database->listCollection() | 查询集合列表。 |  |
| database->deleteCollection() | 删除集合。 |  |
| database->runTransaction() | 新建事务并在事务中执行回调函数。 |  |
| database->startTransaction() | 新建事务。 |  |


## 示例

●无参，访问当前云函数所在云环境的 MongDB 数据库
```PHP
<?php
use Cloud\Cloud;
$cloud = new Cloud();
$database = $cloud->database();
```
●有参，访问指定云函数所在云环境的 MongDB 数据库
```PHP
<?php
use Cloud\Cloud;
$cloud = new Cloud();
$getDatabaseParam = new GetDatabaseParam("envId");
$database = $cloud->database($getDatabaseParam);
```
​
