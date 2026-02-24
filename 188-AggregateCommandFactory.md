# AggregateCommandFactory

返回文档MongoDB 数据库聚合操作符，通过 db->command->aggreag() 可以便捷地获取。

## 属性


| 操作符 | 说明 |
| --- | --- |
| pipeline() | 生成聚合操作流水线，用于 lookup 聚合操作。 |


## 方法


| 操作符 | 说明 |
| --- | --- |
| avg($val): AvgAggregateCommand | 返回指定字段的平均值。 |
| count(): CountAggregateCommand | 返回 doc 数量。 |
| max($val): MaxAggregateCommand | 返回指定字段的最大值。 |
| min($val): MinAggregateCommand | 返回指定字段的最小值。 |
| sum($val): SumAggregateCommand | 返回指定字段的加和总数。 |
| and(...$cmd): AndAggregateCommand | 用于表示逻辑“与”关系，即同时满足所有条件。 |
| or(...$cmd): OrAggregateCommand | 用于表示逻辑“或”关系，即满足所有条件中的至少一个。 |
| eq($val): EqAggregateCommand | 比较两个字段的值，若相等返回 true，否则返回 false。 |
| neq($val): NeqAggregateCommand | 比较两个字段的值，若不相等返回 true，否则返回 false。 |
| lt($val): LtAggregateCommand | 比较两个字段的值，若前者小于后者返回 true，否则返回 false。 |
| lte($val): LteAggregateCommand | 比较两个字段的值，若前者小于或等于后者返回 true，否则返回 false。 |
| gt($val): GtAggregateCommand | 比较两个字段的值，若前者大于后者返回 true，否则返回 false。 |
| gte($val): GteAggregateCommand | 比较两个字段的值，若前者大于或等于后者返回 true，否则返回 false。 |
| addToSet($value): AddToSetAggregateCommand | 返回每个组的唯一表达式值的数组。 |
| arrayElemAt($array, $idx): ArrayElemAtAggregateCommand | 返回指定数组索引处的元素。 |
| indexOfArray($array, $value, $start, $end): IndexOfArrayAggregateCommand | 在数组中搜索指定值的出现位置并返回第一个出现位置的数组索引，数组索引从零开始。 |
| isArray($value): IsArrayAggregateCommand | 确定操作数是否为数组。返回一个布尔值。 |
| size($value): SizeAggregateCommand | 返回数组中的元素数量。 |
| in($target, $key): InAggregateCommand | 返回一个布尔值，表示指定值是否在数组中。 |
| slice($cond, $position, $n): SliceAggregateCommand | 返回数组的子集。 |
| map(MapParam $param): MapAggregateCommand | 将子表达式应用于数组的每个元素并按顺序返回结果值的数组。 |
| ifNull($value, $replacement): IfNullAggregateCommand | 返回第一个表达式的非空结果，或者如果第一个表达式产生空结果，则返回第二个表达式的结果。 |
| cond($value): CondAggregateCommand | 一种三元运算符，用于计算一个表达式，并根据结果返回其他两个表达式之一的值。接受有序列表中的三个表达式或三个命名参数。 |
| switch(SwitchCommandParam $value): SwitchAggregateCommand | 评估一系列 case 表达式。 |
| concat($str, ...$args): ConcatAggregateCommand | 连接任意数量的字符串。 |
| dateToString($value): DateToStringAggregateCommand | 以格式化字符串形式返回日期。 |
| toLower($value): ToLowerAggregateCommand | 将字符串转换为小写。 |
| toUpper($value): ToUpperAggregateCommand | 将字符串转换为大写。 |
| split($value, $splitter): SplitAggregateCommand | 根据分隔符将字符串拆分为子字符串。返回子字符串数组。如果在字符串中找不到分隔符，则返回包含原始字符串的数组。 |
| substr($value, $start, $length): SubstrAggregateCommand | 返回字符串的子字符串。 |
| substrBytes($value, $start, $length): SubstrBytesAggregateCommand | 返回字符串的子字符串。 |
| first($value): FirstAggregateCommand | 返回结果中的第一个文档。 |
| last($value): LastAggregateCommand | 返回结果中的最后一个文档。 |
| push($value): PushAggregateCommand | 返回每组中文档的表达式值数组。 |
| let(LetCommandParam $value): LetAggregateCommand | 定义在子表达式范围内使用的变量并返回子表达式的结果。 |
| add($arr, ...$val): AddAggregateCommand | 添加数字以返回总和，或添加数字和日期以返回新日期。 |
| subtract($numOne, $numTwo): SubtractAggregateCommand | 返回第一个值减去第二个值的结果。 |
| multiply($arr, ...$val): MultiplyAggregateCommand | 将数字相乘以返回乘积。 |
| divide($numOne, $numTwo): DivideAggregateCommand | 返回第一个数字除以第二个数字的结果。 |
| abs($value): AbsAggregateCommand | 返回数字的绝对值。 |
| ceil($value): CeilAggregateCommand | 返回大于或等于指定数字的最小整数。 |
| exp($value): ExpAggregateCommand | 将e升高到指定的指数。 |
| floor($value): FloorAggregateCommand | 返回小于或等于指定数字的最大整数。 |
| ln($value): LnAggregateCommand | 计算数字的自然对数。 |
| log($numOne, $numTwo): LogAggregateCommand | 计算指定底数中数字的对数。 |
| log10($value): Log10AggregateCommand | 计算数字以 10 为底的对数。 |
| mod($numOne, $numTwo): ModAggregateCommand | 返回第一个数字除以第二个数字的余数。 |
| pow($numOne, $numTwo): PowAggregateCommand | 将数字提高到指定的指数。 |
| sqrt($val): SqrtAggregateCommand | 计算平方根。 |
| trunc($value): TruncAggregateCommand | 将数字截断为整数或指定的小数位。 |
| mergeObjects($value): MergeObjectsAggregateCommand | 将多个文档合并为一个文档。 |
| month($value): MonthAggregateCommand | 以 1（一月）和 12（十二月）之间的数字形式返回日期的月份。 |
| year($value): YearAggregateCommand | 以数字形式返回日期的年份。 |
| week($value): WeekAggregateCommand | 以 0（一年中第一个星期日之前的部分周）和 53（闰年）之间的数字形式返回日期的周数。 |
| isoWeek($value): ISOWeekAggregateCommand | 返回 ISO 8601 格式的周数，范围从 1到53。 |
| not($cmd): NotAggregateCommand | 返回与其参数表达式相反的布尔值。 |
| cmp($values, $other): CMPAggregateCommand | 比较值是否相等，返回0：两个值是否相等，1：第一个值大于第二个值，-1：第一个值小于第二个值。 |
​
