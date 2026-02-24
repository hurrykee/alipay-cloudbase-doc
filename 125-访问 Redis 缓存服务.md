# 访问 Redis 缓存服务

返回文档本文为您介绍如何通过开源 Redis 客户端访问 Redis 缓存服务。

## 步骤一：配置 Redis 访问信息

1在扩展服务 > Redis 中，可以找到 redis 的访问信息，拷贝代理地址、端口以及密码信息。2在函数列表内，找到单击并进入目标函数。3单击页面顶端的配置页签，将 Redis 的密码配置到函数运行环境变量。

## 步骤二：使用方法

### 方式一：使用免密连接访问（推荐）

注意：免密访问仅适用于 2023年9月15日 之后开通的 Redis 服务。在 js 代码中，直接获取对应环境开通的 Redis 实例并访问，faas-server-sdk兼容开源的 ioredis

接口。
```Diff
{
"name": "redistest",
"version": "1.0.0",
"description": "",
"main": "index.js",
"scripts": {},
"author": "",
"license": "ISC",
"dependencies": {
"@alipay/faas-server-sdk": "^1.0.0",
+    "ioredis": "^5.3.2"
}
}
```


### 方式二：使用账密连接访问

在 package.json 中增加 ioredis

依赖，具体版本号可依据官方发布情况而定。
```JavaScript
const Redis = require('ioredis');
// 初始化 redis 客户端
const redis = new Redis({
// redis 访问信息中的端口号
port: 6379,
// redis 访问信息中的代理地址
host: "proxy-xxxx.redis.antcloud.local",
// 从前面配置的环境变量中读取密码
password: process.env.REDIS_PASSWORD,
});

exports.main = async (event, context) => {
// 通过 redis 客户端 set/get 缓存
await redis.set('key', 'sdfs');
const value = await redis.get('key');

return { value };
};
```
在 js 代码中，引入 ioredis 客户端并访问。  ​
