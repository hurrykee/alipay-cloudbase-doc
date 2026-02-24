# callFunction

返回文档用于发起对云函数的调用。说明：若云函数要调用数据库或对象存储等线上资源，都需要加 init 初始化函数，详情请参见初始化函数 init。
```
function callFunction<ResultData=any>(param: CallFunctionParam): Promise<CallFunctionResult<ResultData>>
```


## 请求参数

### CallFunctionParam


| 字段名 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| name | string | 是 | 无 | 云函数名 |
| data | object \| string \| number \| boolean | 是 | 无 | 传递给云函数的参数，在被调用的云函数中可通过 event.requestData 参数获取 |
| config | CallFunctionConfig | 否 | 无 | 调用配置 |


### CallFunctionConfig


| 字段名 | 类型 | 必填 | 默认值 | 说明 |
| --- | --- | --- | --- | --- |
| env | string \| symbol | 否 | 无 | 环境 ID，指定云函数调用所需访问的云环境 |


## 返回参数

### CallFunctionResult<T>


| 字段名 | 类型 | 备注 |
| --- | --- | --- |
| requestID | string | 云函数执行 traceId，用于日志查询 |
| result | any | 云函数执行的返回值 |


## 示例

实现一个云函数echo，功能为将调用参数直接返回。
```JavaScript
exports.main = async (event, context) => {
const param = event;
return param;
};
```
在另一个云函数中，发起对echo的调用的完整示例代码。
```JavaScript
const cloud = require("@alipay/faas-server-sdk");

exports.main = async (event, context) => {
const res = await cloud.callFunction({
name: 'echo',
data: 'hello world',
});
return res;
};
```
​
