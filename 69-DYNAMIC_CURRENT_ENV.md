# DYNAMIC_CURRENT_ENV

返回文档当前云函数所在云环境的常量标识，该值为 Symbol 类型，因此该值不是云环境 ID 的字符串。可用于在 cloud.init 方法中显示指定 API 请求当前云函数所在的云环境资源；也可以在调用云函数或获取数据库等对象时，显示指定需要访问的云环境。

## 用于 cloud.init 方法


```
const cloud = require('@alipay/faas-server-sdk');

// cloud 实例默认即请求当前云函数所在云环境，因此通常情况下无需此设置
cloud.init({
env: cloud.DYNAMIC_CURRENT_ENV,
});
```


## 用于调用云函数

设置 database 对象的环境。
```TypeScript
const cloud = require('@alipay/faas-server-sdk');

const custom = new cloud.Cloud();
// custom 默认请求 test-a1b2c3 环境资源
custom.init({
env: 'test-a1b2c3',
});

// 对于 echo 云函数的调用，将会请求当前云环境，而非 test-a1b2c3 环境
const res = await custom.callFunction({
name: 'echo',
data: {},
config: {
env: cloud.DYNAMIC_CURRENT_ENV,
},
});
```


## 用于设置 database 对象


```TypeScript
const cloud = require('@alipay/faas-server-sdk');

const custom = new cloud.Cloud();
// custom 默认请求 test-a1b2c3 环境资源
custom.init({
env: 'test-a1b2c3',
});

// db 对象将会请求当前云环境中的 mongoDB，而非 test-a1b2c3 环境
const db = custom.database({
env: cloud.DYNAMIC_CURRENT_ENV,
});
```
​
