# lookup

返回文档聚合流水线的连表查询聚合阶段，与同一数据库下的一个指定 collection 进行左外连接。对该 collection 中的每一个 doc，增加一个数组字段，该数组包含满足连接匹配条件的 doc 列表。lookup 有两种使用方式。lookup 方法类型定义：
```
function lookup(sample: LookupAggregateParam): Aggregate;
```


## 方式一：相等匹配

### 参数 EqualityMatchLookupParam


| 字段名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| from | string | 是 | 要连接的 collection 名。 |
| localField | string | 是 | 当前 collection 进行相等匹配的字段。 |
| foreignField | string | 是 | 被连接 collection 进行相等匹配的字段。 |
| as | string | 是 | 连接结果数组字段名。 |


### 示例

假设有 student 以及 course 两个 collection。sutdent collection 有以下数据：
```TypeScript
const res = await db.collection(collectionName)
.aggregate()
.match({
class: 'class-two',
})
.lookup({
from: lookupCollectionName,
let: { studentId: '$id', studentLastScore: '$lastScore' },
pipeline: $.pipeline().match(
_.expr(
$.and([
$.eq([ '$studentNo', '$$studentId' ]), // 学号相等
$.gte([ '$score', '$$studentLastScore' ]), // 课程分数大于或等于上次分数
]),
),
).done(),
as: 'scoreList',
})
.end();
```
course collection 的数据为：
```JSON
[
{
class: 'class-two',
id: 2002,
name: 'student-2',
scoreList: [
{
course: 'chinese',
score: 98,
studentNo: 2002,
},
],
astScore: 95,
},
]
```
通过相等匹配连接，可以查询出每个学生各科成绩的列表。  结果为：

## 方式二：自定义连接

### 参数 JoinLookupParam


| 字段名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| from | string | 是 | 要连接的 collection 名。 |
| let | string | 否 | 指定在 pipeline 中可以使用的变量。 |
| pipeline | string | 是 | 被连接 collection 中执行的流水线操作。 |
| as | string | 是 | 连接结果数组字段名。 |
说明：目前 pipeline 仅支持 match 操作，且 match 操作仅接收 expr 操作符。

### 示例

结果为：  ​
