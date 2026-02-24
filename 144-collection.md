# collection

返回文档获取集合对象，需要通过 collectionName 参数指定集合名。
```
<?php
public function collection(string $collectionName): Collection
```


## 请求参数


| 字段名 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| collectionName | string | 是 | 无 | 集合名。 |


## 返回参数

Collection client.

## 示例


```PHP
<?php
use Cloud\Cloud;
function collection()
{
$cloud = new Cloud();
$collection = $cloud->database()->collection('collectionName');
return $collection;
}
```
​
