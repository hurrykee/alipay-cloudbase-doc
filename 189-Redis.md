# Redis

返回文档获取 Redis client。
```
<?php
public function redis(): RedisClient
```


## 请求参数

无。

## 返回参数

### RedisClient


| API | 类别 | 说明 |
| --- | --- | --- |
| redis->set() | 方法 | 写数据。 |
| redis->get() | 读数据。 |  |


## 示例


```PHP
<?php

use Cloud\Cloud;
function redis($event, $context)
{
$logger = $context->getLogger();
$cloud = new Cloud();
$redis = $cloud->redis();
$key = "test_key";
$status = $redis->set($key, "test_value");
$logger->info("set", "set response:%s", $status);

$value = $redis->get($key);
$logger->info("get", "get response:%s", $value);

return $value;
}
```
​
