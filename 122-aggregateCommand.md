# aggregateCommand

返回文档mongoDB 数据库聚合操作符，通过 db.command.aggreag 可以便捷地获取。

## 方法


| 方法 | 说明 |
| --- | --- |
| pipeline() | 生成聚合操作流水线，用于 lookup 聚合操作。 |


## 操作符


| 操作符 | 说明 |
| --- | --- |
| avg(val: string): AvgAggregateCommand | 聚合操作符，返回指定字段的平均值。 |
| count(): CountAggregateCommand | 聚合操作符，返回 doc 数量。 |
| max(val: string): MaxAggregateCommand | 聚合操作符，返回指定字段的最大值。 |
| min(val: string): MinAggregateCommand | 聚合操作符，返回指定字段的最小值。 |
| sum(val: string): SumAggregateCommand | 聚合操作符，返回指定字段的加和总数。 |
| and(...val: Array<object \| AggregateCommand>): AndAggregateCommand | 聚合操作符，用于表示逻辑“与”关系，即同时满足所有条件。 |
| or(...val: Array<object \| AggregateCommand>): OrAggregateCommand | 聚合操作符，用于表示逻辑“或”关系，即满足所有条件中的至少一个。 |
| eq(val: [string, string]): EqAggregateCommand | 聚合操作符，比较两个字段的值，若相等返回 true，否则返回 false。 |
| neq(val: [string, string]): NeqAggregateCommand | 聚合操作符，比较两个字段的值，若不相等返回 true，否则返回 false。 |
| lt(val: [string, string]): LtAggregateCommand | 聚合操作符，比较两个字段的值，若前者小于后者返回 true，否则返回 false。 |
| lte(val: [string, string]): LteAggregateCommand | 聚合操作符，比较两个字段的值，若前者小于或等于后者返回 true，否则返回 false。 |
| gt(val: [string, string]): GtAggregateCommand | 聚合操作符，比较两个字段的值，若前者大于后者返回 true，否则返回 false。 |
| gte(val: [string, string]): GteAggregateCommand | 聚合操作符，比较两个字段的值，若前者大于或等于后者返回 true，否则返回 false。 |
​
