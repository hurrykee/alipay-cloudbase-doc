# API 概览

返回文档

## 服务端 NodeJS SDK

### 云函数初始化


| API | 描述 |
| --- | --- |
| Cloud | 云开发 SDK 实例。 |
| Cloud.init | 初始化 SDK 实例。 |


### 常量


| API | 描述 |
| --- | --- |
| Symbol DYNAMIC_CURRENT_ENV | 云开发 SDK 实例。 |


### 调用云函数


| API | 描述 |
| --- | --- |
| Cloud.callFunction | 用于发起对云函数的调用。 |


### 文件存储


| API | 描述 |
| --- | --- |
| Cloud.uploadFile | 上传本地资源到云存储空间。 |
| Cloud.downloadFile | 下载云存储空间上的文件。 |
| Cloud.deleteFile | 删除云存储空间中的文件。 |
| Cloud.getTempFileURL | 通过云文件 ID 获取文件链接，所获取的公有读文件链接不会过期，私有文件链接为10分钟有效期。一次最多获取50个。 |


### 开放能力

如需了解开放能力 API，请参见云调用 OpenAPI。

### 数据库

#### MySQL


| API | 描述 |
| --- | --- |
| Cloud.mysql | 获取 MySQL 数据库操作对象。 |
| MySQL.query | 执行 SQL 语句。 |
| MySQL.insert | 插入数据。 |
| MySQL.update | 更新数据。 |
| MySQL.select | 查询数据。 |
| MySQL.get | 查询数据。 |
| MySQL.delete | 删除数据。 |
| MySQL.count | 统计行数。 |
| beginTransaction | 新建 MySQL 事务。 |
| beginTransactionScope | 新建事务运行作用域，在该作用域中的所有数据库操作将在同一事务中执行。 |


#### NoSQL


| API | 描述 |
| --- | --- |
| Cloud.database | 获取 MongoDB 数据库操作对象。 |
| command | MongoDB 数据库操作符。 |
| aggregateCommand | MongoDB 数据库聚合操作符。 |
| Geo | 构造一个地理位置 “点”。 |
Database：
| API | 描述 |
| --- | --- |
| Database.collection | 获取集合对象。 |
| Database.createCollection | 新建集合。 |
| Database.getCollection | 查询集合信息。 |
| Database.listCollection | 查询集合列表。 |
| Database.deleteCollection | 删除集合。 |
| Database.runTransaction | 新建事务并在事务中执行回调函数。 |
| Database.startTransaction | 新建事务。 |
| Database.RegExp | 查询符合条件的数据。 |
collection：
| API | 描述 |
| --- | --- |
| doc | 文档对象。 |
| add | 新增文档。 |
| get | 获取文档列表。 |
| count | 统计文档数量。 |
| aggregate | 新建聚合操作。 |
| where | 指定查询条件。 |
| limit | 限制查询结果数量上限。 |
| skip | 进行查询操作时，指定跳过的数量，返回指定位置后的文档。 |
| orderBy | 指定查询的排序规则。 |
| projection | 指定返回结果中文档的字段。 |
Document：
| API | 描述 |
| --- | --- |
| get | 获取文档数据。 |
| set | 替换一条文档数据。 |
| update | 更新一条文档数据。 |
| remove | 删除一条文档数据。 |
Transaction：
| API | 描述 |
| --- | --- |
| commit | 结束事务并进行提交。 |
| rollback | 终止事务并进行回滚。 |
| collection | 获取当前事务下的集合对象并行相应操作。 |
Aggregate：
| API | 描述 |
| --- | --- |
| match | 聚合流水线的条件过滤阶段，根据条件过滤文档后把符合条件的文档传递给下一流水线阶段。 |
| group | 聚合流水线的分组统计阶段，通过参数 _id 指定分组字段，返回结果一条记录为一个分组。 |
| sample | 聚合流水线的抽样阶段，从文档列表中随机选取指定数量的文档。 |
| end | 标记聚合流水线完结，发起实际的聚合操作请求。 |
| lookup | 聚合流水线的连表查询聚合阶段，与同一数据库下的一个指定 collection 进行左外连接。 |
| geoNear | 聚合阶段，按照距离指定点从最近到最远的顺序输出文档。 |
| bucket | 聚合阶段，根据指定的表达式和边界将文档分类为不同的 bucket 组。 |
| bucketAuto | 聚合阶段，根据指定的表达式将传入文档分类为特定数量的组。自动确定 bucket 组边界，以尝试将文档均匀分布到指定数量的组中。 |


### 工具方法


| API | 描述 |
| --- | --- |
| Cloud.getAlipayContext | 获取云函数运行上下文信息。 |


### 缓存服务

通过开源 Redis 客户端访问 Redis 缓存服务，请参见访问 Redis 缓存服务。

### 使用 TypeScript

函数运行入口是 index.js 文件，您可以通过 TypeScript 编译创建出这个入口文件，请参见使用 TypeScript。

## 服务端 PHP SDK

### Cloud

#### Cloud 说明

●获取各类云上服务的 client，通过 client 可以访问对应的服务。●提供直接访问云上服务的 API。●如果要访问云上服务，首先得获取 Cloud 实例。

#### 获取 Cloud 实例


```PHP
<?php

use Cloud\Cloud;

// 可用于访问当前云函数所在的云环境中的各种云服务
$cloud1 = new Cloud();

// 可用于访问云环境 env-xxxxxxxxxxx 中的各种云服务
$cloud2 = new Cloud("env-xxxxxxxxxxx");
```
入参
| 字段名 | 类型 | 是否必填 | 默认值 | 备注 |
| --- | --- | --- | --- | --- |
| env | string | 否 | 调用方所在环境 ID | 如果要访问其他环境的云资源，请指定对应环境 ID。 |
返回Cloud 实例，包含如下 API。

#### 示例



### 云函数


| API | 描述 |
| --- | --- |
| cloud->callFunction | 调用云函数。 |


### 文件存储


| API | 描述 |
| --- | --- |
| cloud->getUploadFileURL | 获取文件上传链接。 |
| cloud->uploadFile | 上传本地资源到云存储空间。 |
| cloud->downloadFile | 下载云存储空间上的文件。 |
| cloud->getTempFileURL | 通过云文件 ID 获取文件链接。 |
| cloud->deleteFile | 删除云存储空间中的文件。 |


### 数据库

#### MySQL


| API | 描述 |
| --- | --- |
| cloud->mysql | 获取 MySQL client。 |
| mysql->query | 执行 SQL 语句。 |
| mysql->insert | 插入数据。 |
| mysql->update | 更新数据。 |
| mysql->select | 查询数据。 |
| mysql->delete | 删除数据。 |
| mysql->count | 统计行数。 |
| mysql->beginTransaction | 新建 MySQL 事务。 |
| mysql->beginTransactionScope | 新建事务运行作用域，在该作用域中的所有数据库操作将在同一事务中执行。 |


#### NoSQL


| API | 描述 |
| --- | --- |
| cloud->database | 获取 MongoDB client。 |
| database->command | MongoDB 数据库操作符。 |
| database->command->aggregateCommandFactory | MongoDB 数据库聚合操作符。 |


#### Database


| API | 描述 |
| --- | --- |
| database->collection | 获取 Collection client。 |
| database->createCollection | 新建集合。 |
| database->getCollection | 查询集合信息。 |
| database->listCollection | 查询集合列表。 |
| database->deleteCollection | 删除集合。 |
| database->runTransaction | 新建事务并在事务中执行回调函数。 |
| database->startTransaction | 新建事务。 |


#### Collection


| API | 描述 |
| --- | --- |
| collection->doc | 获取 Document client。 |
| collection->add | 新增文档。 |
| collection->get | 获取文档列表。 |
| collection->count | 统计文档数量。 |
| collection->aggregate | 新建聚合操作。 |
| collection->where | 指定查询条件。 |
| collection->limit | 限制查询结果数量上限。 |
| collection->skip | 进行查询操作时，指定跳过的数量，返回指定位置后的文档。 |
| collection->orderBy | 指定查询的排序规则。 |
| collection->projection | 指定返回结果中文档的字段。 |
| collection->field |  |
| collection->update | 修改集合中全部信息。 |
| collection->updateAndReturn | 用于向指定集合中 find 一条数据并 update。 |
| collection->set | 替换集合中全部信息。 |
| collection->remove | 删除集合中全部信息。 |


#### Document


| API | 描述 |
| --- | --- |
| document->get | 获取文档数据。 |
| document->set | 替换一条文档数据。 |
| document->update | 更新一条文档数据。 |
| document->remove | 删除一条文档数据。 |
| document->updateAndReturn | 用于向指定集合中查询一条数据并更新。 |
| document->projection | 指定返回结果中文档的字段。 |
| document->field |  |


#### Transaction


| API | 描述 |
| --- | --- |
| transaction->commit | 结束事务并进行提交。 |
| transaction->rollback | 终止事务并进行回滚。 |
| transaction->collection | 获取当前事务下的集合对象并行相应操作。 |


#### Aggregate


| API | 描述 |
| --- | --- |
| aggregate->match | 聚合流水线的条件过滤阶段，根据条件过滤文档后把符合条件的文档传递给下一流水线阶段。 |
| aggregate->group | 聚合流水线的分组统计阶段，通过参数 _id 指定分组字段，返回结果一条记录为一个分组。 |
| aggregate->sample | 聚合流水线的抽样阶段，从文档列表中随机选取指定数量的文档。 |
| aggregate->end | 标记聚合流水线完结，发起实际的聚合操作请求。 |
| aggregate->lookup | 聚合流水线的连表查询聚合阶段，与同一数据库下的一个指定 Collection 进行左外连接。 |
| aggregate->addFields | 聚合流水线的输出时，添加输出字段。 |
| aggregate->project | 聚合流水线的输出时，指定字段隐藏或显示。 |
| aggregate->sort | 聚合流水线的输出时，按照指定字段排序。 |
| aggregate->limit | 聚合流水线的输出时，限制输出的文档数量。 |
| aggregate->unwind | 从输入文档解构数组字段以输出每个元素的文档。 |
| aggregate->skip | 聚合流水线的输出时，跳过前 n 个文档。 |


### Redis


| API | 描述 |
| --- | --- |
| cloud->redis | 获取 Redis client。 |


### 开放能力


| API | 描述 |
| --- | --- |
| cloud->openapi | 获取云调用 API client。 |


### 工具方法


| API | 描述 |
| --- | --- |
| context->getAlipayContext | 获取云函数运行上下文信息。 |


## 客户端 Web SDK

通过 Web SDK 在 Web 端（如 PC Web 页面、支付宝公众平台 H5 等）使用 JavaScript 访问 Cloudbase 服务，目前 Web SDK 支持调用云函数以及访问云存储，请参见 Web SDK。

## 小程序 API

包含小程序 API 接口链接，请参见小程序 API。​
