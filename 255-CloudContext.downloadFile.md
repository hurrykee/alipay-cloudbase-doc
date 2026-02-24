# CloudContext.downloadFile

返回文档

## CloudContext.downloadFile(Object object)

基础库2.8.8或更高版本； 支付宝客户端10.3.60或更高版本； 若版本较低，建议采取兼容处理。以 Promise 风格调用： 支持。主体： 企业支付宝小程序 、 个人支付宝小程序。

## 简介

从云存储空间下载文件。使用 downloadFile 之前，需要首先调用 init 完成云环境初始化。

## 接入准备

使用接口之前，请先到支付宝小程序云

开通云开发服务，并已经有文件上传至云存储空间。

## 入参

### Object object

查看示例
| 属性 | 类型 | 默认值 | 必填 | 描述 |
| --- | --- | --- | --- | --- |
| fileID | String | - | 是 | 云文件 ID，上传文件到云存储空间时返回。 |
| filePath | String | - | 否 | 指定文件下载后存储的路径，目前只支持传入本地用户文件，若不指定此参数，下载的文件会被存储为本地临时文件。 |
| timeout | Number | 60000 | 否 | 超时时间，单位ms。 |
| success | Function | - | 否 | 调用成功的回调函数。 |
| fail | Function | - | 否 | 调用失败的回调函数。 |
| complete | Function | - | 否 | 调用结束的回调函数（调用成功、失败都会执行）。 |


### success 回调函数

#### 参数

Object res查看示例
| 属性 | 类型 | 描述 |
| --- | --- | --- |
| tempFilePath | String | 临时文件路径，入参未指定 filePath 的情况下返回。 |
| filePath | String | 下载文件保存的路径。 |
| statusCode | Number | 服务器返回的 HTTP 状态码。 |
| requestID | String | 云存储执行 ID，暂不支持通过该 ID 进行日志查询。 |


## 错误码

fail 回调的参数为 Object，error 属性为错误码，errorMessage 属性为错误消息。
| 错误码 | 错误消息 | 解决方案 |
| --- | --- | --- |
| 60001 | 无效入参，请传入合法的参数 fileID。 | 确认传入的 fileID 参数是否合法。 |
| 无效入参，请传入合法的参数 filePath。 | 确认传入的 filePath 参数是否合法。 |  |
| 60002 | 调用前，请先初始化云环境。 | 请先调用 init 方法进行云环境初始化。 |
| 60003 | 请求超时。 | 请检查网络环境是否正常。 |
| 60004 | 网络异常。 | 请检查网络环境是否正常。 |
| 60005 | 云调用失败。 | 请稍后重试。 |
| 60006 | 存储写文件失败。 | 请稍后重试。 |


## 示例

Promise 风格：
```JSON
const c1 = my.cloud.createCloudContext({
env: 'env-file', // 云环境 id
});
// 云环境初始化
await c1.init();
// 调用云存储下载接口
const res = await c1.downloadFile({
fileID: 'cloud://env-file/example.png',
});
```
callback 风格：
```JSON
const c1 = my.cloud.createCloudContext({
env: 'env-file', // 云环境 id
});
// 云环境初始化
c1.init({
success: () => {
// 调用云存储下载接口
c1.downloadFile({
fileID: 'cloud://env-file/example.png',
success: (res) => {
console.log(res);
}
});
}
});
```
success 回调：
```
{
"filePath": 'https://resource/8951dba439b1aa07c.other',
"tempFilePath": 'https://resource/8951dba439b1aa07c.other',
"statusCode": 200,
"requestID": '6BA5F274-1BAE-4CF6-xxxxxx',
}
```
​
