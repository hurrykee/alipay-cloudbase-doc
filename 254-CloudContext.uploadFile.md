# CloudContext.uploadFile

返回文档

## CloudContext.uploadFile(Object object)

基础库2.8.8或更高版本； 支付宝客户端10.3.60或更高版本； 若版本较低，建议采取兼容处理。以 Promise 风格调用： 支持。主体： 企业支付宝小程序 、 个人支付宝小程序。

## 简介

将文件资源上传至云存储空间。使用 uploadFile 之前，需要首先调用 init 完成云环境初始化。

## 接入准备

使用接口之前，请先到支付宝小程序云

开通云开发服务。

## 入参

### Object object

查看示例
| 属性 | 类型 | 默认值 | 必填 | 描述 |
| --- | --- | --- | --- | --- |
| cloudPath | String | - | 是 | 云存储路径。 |
| filePath | String | - | 是 | 要上传文件资源的路径（本地路径）
注意：目前 IDE 暂不支持本地用户文件。建议使用真机测试。 |
| timeout | Number | 60000 | 否 | 超时时间，单位ms。 |
| success | Function | - | 否 | 调用成功的回调函数。 |
| fail | Function | - | 否 | 调用失败的回调函数。 |
| complete | Function | - | 否 | 调用结束的回调函数（调用成功、失败都会执行）。 |


### cloudPath 命名限制

●不能为空●不能以/开头●不能出现连续/●使用 UTF-8 编码●推荐使用大小写英文字母、数字，即[a-z，A-Z，0-9]和符号 -，_及其组合●不建议使用的特殊字符: ` ^ " \ { } [ ] ~ # \ > < 及 ASCII 128-255 十进制●文件全路径名长度最大为 1024 字符●文件路径每一级长度最大为 255 字符

### success 回调函数

#### 参数

Object res查看示例
| 属性 | 类型 | 描述 |
| --- | --- | --- |
| fileID | String | 云文件 ID。 |
| statusCode | Number | 服务器返回的 HTTP 状态码。 |
| requestID | String | 云存储执行 ID，暂不支持通过该 ID 进行日志查询。 |


## 错误码

fail 回调的参数为 Object，error 属性为错误码，errorMessage 属性为错误消息。
| 错误码 | 错误消息 | 解决方案 |
| --- | --- | --- |
| 60001 | 无效入参，请传入合法的参数 cloudPath。 | 确认传入的 cloudPath 参数是否合法。 |
| 无效入参，请传入合法的参数 filePath。 | 确认传入的 filePath 参数是否合法。 |  |
| 60002 | 调用前，请先初始化云环境。 | 请先调用 init 方法进行云环境初始化。 |
| 60003 | 请求超时。 | 请检查网络环境是否正常。 |
| 60004 | 网络异常。 | 请检查网络环境是否正常。 |
| 60005 | 云调用失败。 | 请稍后重试。 |
| 60006 | 文件不存在。 | 请确认上传文件资源路径是否正确。 |
| 60007 | 无权限读取 filePath。 | 请确认是否有上传文件资源路径的读权限 |


## 示例

Promise 风格：
```JSON
const c1 = my.cloud.createCloudContext({
env: 'env-file', // 云环境 id
});
// 选择图片
const imgRes = await my.chooseImage();
// 云环境初始化
await c1.init();
// 调用云存储上传接口
const res = await c1.uploadFile({
cloudPath: 'example.png',
filePath: imgRes.tempFilePaths[0],
});
console.log(res);
```
callback 风格：
```JSON
const c1 = my.cloud.createCloudContext({
env: 'env-file', // 云环境 id
});
// 选择图片
my.chooseImage({
success: (imgRes) => {
// 云环境初始化
c1.init({
success: () => {
// 调用云存储上传接口
c1.uploadFile({
cloudPath: 'example.png',
filePath: imgRes.tempFilePaths[0],
success: (res) => {
console.log(res);
}
});
}
});
}
});
```
success 回调：
```
{
"fileID": 'cloud://env-file/example.png',
"requestID": '6BA5F274-1BAE-4CF6-xxxxxx',
"statusCode": 200
}
```
​
