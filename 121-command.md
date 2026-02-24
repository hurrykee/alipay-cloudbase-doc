# command

返回文档mongoDB 数据库操作符，通过 db.command 可以便捷地获取。

## 属性


| 操作符 | 说明 |
| --- | --- |
| aggregate: AggregateCommand | mongoDB 数据库聚合操作符。 |


## 方法


| 操作符 | 说明 |
| --- | --- |
| set(data: object): SetCommand | 更新操作符，用于设置字段为指定值。 |
| inc(num: number): IncCommand | 更新操作符，用于指示字段值做累加。 |
| and(...cmd: Array<object \| QueryCommand \| QueryChain>): QueryChain | 逻辑运算符，用于表示逻辑“与”关系，即同时满足所有条件。 |
| or(...cmd: Array<object \| QueryCommand \| QueryChain>): QueryChain | 逻辑运算符，用于表示逻辑“或”关系，即满足所有条件中的至少一个。 |
| not(cmd: QueryCommand \| QueryChain): QueryChain | 逻辑运算符，用于表示逻辑“非”关系，即需要不满足指定条件。 |
| nor(...cmd: Array<object \| QueryCommand \| QueryChain>): QueryChain | 逻辑运算符，用于表示逻辑“都不”关系，即需要不满足所有条件。 |
| eq(val: any): QueryChain | 比较运算符，用于指定字段等于给定值。 |
| neq(val: any): QueryChain | 较运算符，用于指定字段不等于给定值。 |
| lt(val: any): QueryChain | 比较运算符，用于指定字段小于给定值。 |
| lte(val: any): QueryChain | 比较运算符，用于指定字段小于或等于给定值。 |
| gt(val: any): QueryChain | 比较运算符，用于指定字段大于给定值。 |
| gte(val: any): QueryChain | 比较运算符，用于指定字段大于或等于给定值。 |
| in(val: any[]): QueryChain | 比较运算符，用于指定字段值在给定数组内。 |
| nin(val: any[]): QueryChain | 比较运算符，用于指定字段值不在给定数组内。 |
| exists(exists: boolean): QueryChain | 查询操作符，用于判断字段是否存在。 |
| mod(divisor: number, remainder: number): QueryChain | 查询操作符，用于指定字段值除以 divisor 余数需为 remainder。 |
| all(val: any[]): QueryChain | 数组查询操作符，用于指定数组字段需要包含给定数组的所有元素。 |
| elemMatch(cmd: object \| QueryChain \| QueryCommand): QueryChain | 数组查询操作符，用于指定数组字段至少包含一个满足给定的所有条件的元素。 |
| size(size: number): QueryChain | 数组查询操作符，用于指定数组字段长度等于给定值。 |
​
