# bucket

返回文档聚合阶段，根据指定的表达式和边界将文档分类为不同的 bucket 组。
```
function bucket(bucket: bucketParam): Aggregate;
```


## 请求参数

bucketParam 参数结构为：
| 属性 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| groupBy | AggregateExpression | 是 | 用于对文档进行分组的表达式。要指定字段路径，请在字段名称前添加美元符号$并将其括在引号中。 |
| boundaries | Array<number> | 是 | 是一个数组，指定每个分组边界的表达式。每对相邻的值都充当分组的下边界和排它上边界。必须指定至少两个边界。数组值必须是同类型递增的值。 |
| default | string | 否 | 可选，指定之后，不符合任何分组记录将都进入一个默认分组，这个分组记录的 _id 即由 default 决定。 |
| output | object | 否 | 可选，主要作用是填加输出字段，各个字段的值必须用累加器表达式指定。当 output 没有输出count字段，count 是不会被默认输出的，必须手动指定。 |
参数结构示例如下：
```JSON
{
_id: "1",
year_born: 1868
}
{
_id: "2",
year_born: 1968
}
{
_id: "3",
year_born: 1844
}
{
_id: "4",
year_born: 1864
}
{
_id: "5",
year_born: 1852
}
```


## 返回参数

Aggregate 聚合流水线构建对象。

## 云函数示例

假设集合 places 有如下记录：
```JSON
const cloud = require('@alipay/faas-server-sdk');
exports.main = async (event, context) => {
// 初始化
cloud.init();
const db = cloud.database();
const $ = db.command.aggregate
db.collection('places').aggregate()
.bucket({
groupBy: '$year_born',
boundaries: [1840, 1850, 1860, 1870, 1880],
default: 'other',
output: {
count: $.sum(1),
ids: $.push('$_id')
}
})
.end()
};
```
对上述记录进行分组，将 [1840, 1850) ，[1850, 1860)...等等分组，其他分为一组：：
```
[
{
"_id": 1840,
"count": 1,
"ids": [
"3"
]
},
{
"_id": 1850,
"count": 1,
"ids": [
"5",
]
},
{
"_id": 1860,
"count": 2,
"ids": [
"1",
"4"
]
},
{
"_id": "other",
"count": 1,
"ids": [
"2"
]
}
]
```
返回结果如下：  ​
