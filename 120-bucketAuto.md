# bucketAuto

返回文档聚合阶段，根据指定的表达式将传入文档分类为特定数量的组。自动确定 bucket 组边界，以尝试将文档均匀分布到指定数量的组中。
```
function bucketAuto(bucketAuto: bucketAutoParam): Aggregate;
```


## 请求参数

bucketAutoParam 参数结构为：
| 属性 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| groupBy | AggregateExpression | 是 | 用于对文档进行分组的表达式。要指定字段路径，请在字段名称前添加美元符号$并将其括在引号中。 |
| bucket | number | 是 | 指定分组数量，是正整数。 |
| granularity | string | 否 | 可选枚举值字符串，根据给定的规则，自动计算组的边界。这个字段仅可在所有 groupBy 值都是数字并且没有 NaN 的情况下使用。枚举值包括：R5、R10、R20、R40、R80、1-2-5、E6、E12、E24、E48、E96、E192、POWERSOF2。 |
| output | object | 否 | 可选，主要作用是填加输出字段，各个字段的值必须用累加器表达式指定。当 output 没有输出 count 字段，count 是不会被默认输出的，必须手动指定。 |


## 返回参数

Aggregate 聚合流水线构建对象。

## 云函数示例

假设集合 places 有如下记录：
```JSON
{
_id: "1",
length: 10.5
}
{
_id: "2",
length: 50.3
}
{
_id: "3",
length: 20.8
}
{
_id: "4",
length: 80.2
}
{
_id: "5",
length: 200.3
}
```
根据 length 字段值分成3个不同大小的组。这个分组是自动的，尽力保持桶的大小近似相等，并且按照特定的规则（R20粒度）来确定桶的边界。每个桶会输出一个 count 字段，用来计数该桶中有多少文档：
```JSON
const cloud = require('@alipay/faas-server-sdk');
exports.main = async (event, context) => {
// 初始化
cloud.init();
const db = cloud.database();
const $ = db.command.aggregate
db.collection('places').aggregate()
.bucketAuto({
groupBy: '$length',
buckets: 3,
granularity: 'R20',
output: {
count: $.sum(1),
},
})
.end()
};
```
返回结果如下：
```
[
{
_id: {
min: 10,
max: 22.400000000000002,
},
count: 2,
},
{
_id: {
min: 22.400000000000002,
max: 90,
},
count: 2,
},
{
_id: {
min: 90,
max: 224,
},
count: 1,
},
]
```
​
