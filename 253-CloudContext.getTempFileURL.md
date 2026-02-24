# CloudContext.getTempFileURL

返回文档

## CloudContext.getTempFileURL(Object object)

基础库2.8.9或更高版本； 支付宝客户端10.3.70或更高版本； 若版本较低，建议采取兼容处理。以 Promise 风格调用： 支持。主体： 企业支付宝小程序 、 个人支付宝小程序。

## 简介

●获取云文件临时链接。●使用 getTempFileURL 之前，需要先调用 init 完成云环境初始化。

## 接入准备

使用接口之前，请先到支付宝小程序云

开通云开发服务，并已经有文件上传至云存储空间。

## 入参

### Object object

查看示例
| 属性 | 类型 | 默认值 | 必填 | 描述 |
| --- | --- | --- | --- | --- |
| fileList | Array<String>\|Array<Object> | - | 是 | 要获取临时链接的云文件 ID 数组，默认有效期为1小时，一次最多可传入50个。数组支持两种入参形式，['cloud://..',{fileID:'cloud://..',maxAge:600}] |
| fileID | String | - | - | 云文件 ID。 |
| maxAge | Number | - | - | 临时链接有效时长，单位秒。 |
| timeout | Number | 60000 | 否 | 超时时间，单位 ms。 |
| success | Function | - | 否 | 调用成功的回调函数。 |
| fail | Function | - | 否 | 调用失败的回调函数。 |
| complete | Function | - | 否 | 调用结束的回调函数（调用成功、失败都会执行） |


### success 回调函数

#### 参数

Object res查看示例
| 属性 | 类型 | 描述 |
| --- | --- | --- |
| fileList | Array<Object> | 结果数组。 |
| fileID | String | 云文件 ID。 |
| tempFileURL | String | 云文件临时链接。 |
| maxAge | Number | 临时链接有效时长，单位秒。 |
| status | Number | 状态码，返回0为成功。 |
| resultMessage | String | 结果描述。 |
| resultMessage | String | 结果描述。 |
| requestID | String | 云存储执行 ID，暂不支持通过该 ID 进行日志查询。 |


## 错误码

fail 回调的参数为 Object，error 属性为错误码，errorMessage 属性为错误消息。
| 错误码 | 错误消息 | 解决方案 |
| --- | --- | --- |
| 60001 | 无效入参，请传入合法的参数 fileList。 | 确认传入的 fileList 参数是否合法。 |
| 60002 | 调用前，请先初始化云环境。 | 请先调用 init 方法进行云环境初始化。 |
| 60003 | 请求超时。 | 请检查网络环境是否正常。 |
| 60004 | 网络异常。 | 请检查网络环境是否正常。 |
| 60005 | 云调用失败。 | 请稍后重试。 |
| 60006 | 请检查传入 fileList 项数量，最大限制为 50。 | 请确认 fileList 传入数量小于 50。 |


# 代码示例

### promise 风格


```JSON
const c1 = my.cloud.createCloudContext({
env: 'env-file', // 云环境 id
});
// 云环境初始化
c1.init({
success: () => {
// 获取云文件临时链接
c1.getTempFileURL({
fileList: [
'cloud://env-xxxx/example1.png',
{  fileID: 'cloud://env-xxxx/example2.png', maxAge: 3600 }
],
success: (res) => {
console.log(res);
}
});
}
});
```


### callback 风格


```JSON
{
"fileList": [
{
"fileID": "cloud://env-xxxx/example1.png",
"status": 0,
"resultMessage": "Request success",
"maxAge": 86400,
"tempFileURL": "https://env-xxxx.normal.cloudstatic.cn/example1.png?OSSAccessKeyId=LTAI5tBsNU6B3txfCA7Afjxn&amp;Expires=1680268901&amp;Signatur=UmHOhE1cMkI2MqJjjWopRBlobFg"
},
{
"fileID": "cloud://env-xxxx/example2.png",
"status": 1,
"resultMessage": "获取临时链接失败",
"maxAge": 3600,
"tempFileURL": ""
}
],
"requestID": "6BA5F274-1BAE-4CF6-xxxxxx",
"resultMessage": "success"
}
```


### success 回调

​
