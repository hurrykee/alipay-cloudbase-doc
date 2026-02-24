# Command

返回文档MongoDB 数据库操作符，通过 db->command() 可以便捷地获取。

## 属性


| 操作符 | 说明 |
| --- | --- |
| AggregateCommandFactory $aggregate | MongoDB 数据库聚合操作符。 |


## 方法


| 操作符 | 说明 |
| --- | --- |
| addToSet($value): AddToSetCommand | 更新操作符，只向集合中不存在的元素添加数组元素。 |
| max($max): MaxCommand | 指定值大于字段的当前值。 |
| min($min): MinCommand | 指定值小于字段的当前值。 |
| mul(int $num): MulCommand | 将指定字段的值乘以数字。 |
| pop(int $value): PopCommand | 更新操作符，删除数组的第一个或最后一个元素。给 $value 传递一个值-1来更新操作符，删除数组中的第一个元素，1来删除数组中的最后一个元素。 |
| pull($value): PullCommand | 更新操作符，从现有数组中删除一个值或与指定条件匹配的值的所有数组元素。 |
| pullAll($values): PullAllCommand | 更新操作符，从数组中移除所有匹配的值。 |
| push($value, ...$args): PushCommand | 更新操作符，将特定的元素或值添加到数组中。 |
| remove(): RemoveCommand | 删除特定字段。 |
| rename(string $name): RenameCommand | 更新字段的名称。 |
| expr(AggregateCommand $cmd): ExprCommand | 在查询语句中允许使用聚合表达式查询文档。 |
| set($data): SetCommand | 更新操作符，用于设置字段为指定值。 |
| inc(int $number): IncCommand | 更新操作符，用于指示字段值做累加。 |
| and(...$cmd): QueryChain | 逻辑运算符，用于表示逻辑“与”关系，即同时满足所有条件。 |
| or(...$cmd): QueryChain | 逻辑运算符，用于表示逻辑“或”关系，即满足所有条件中的至少一个。 |
| nor(...$cmd): QueryChain | 逻辑运算符，用于表示逻辑“都不”关系，即需要不满足所有条件。 |
| not($cmd): QueryChain | 逻辑运算符，用于表示逻辑“非”关系，即需要不满足指定条件。 |
| eq($val): QueryChain | 比较运算符，用于指定字段等于给定值。 |
| neq($val): QueryChain | 较运算符，用于指定字段不等于给定值。 |
| lt($val): QueryChain | 比较运算符，用于指定字段小于给定值。 |
| lte($val): QueryChain | 比较运算符，用于指定字段小于或等于给定值。 |
| gt($val): QueryChain | 比较运算符，用于指定字段大于给定值。 |
| gte($val): QueryChain | 比较运算符，用于指定字段大于或等于给定值。 |
| in($val): QueryChain | 比较运算符，用于指定字段值在给定数组内。 |
| nin($val): QueryChain | 比较运算符，用于指定字段值不在给定数组内。 |
| exists(bool $exists): QueryChain | 查询操作符，用于判断字段是否存在。 |
| mod(int $divisor, int $remainder): QueryChain | 查询操作符，用于指定字段值除以 divisor 余数需为 remainder。 |
| all($val): QueryChain | 数组查询操作符，用于指定数组字段需要包含给定数组的所有元素。 |
| elemMatch($cmd): QueryChain | 数组查询操作符，用于指定数组字段至少包含一个满足给定的所有条件的元素。 |
| size(int $size): QueryChain | 数组查询操作符，用于指定数组字段长度等于给定值。 |
​
