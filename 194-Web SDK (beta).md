# Web SDK (beta)

返回文档您可以通过 Web SDK 在 Web 端（如 PC Web 页面、支付宝公众平台 H5 等）使用 JavaScript 访问 Cloudbase 服务，目前 Web SDK 支持调用云函数以及访问云存储。

## 安装依赖


```
npm i @alipay/faas-web-sdk
```


## CDN 地址

1.1.20：https://registry.npmmirror.com/@alipay/faas-web-sdk/1.1.20/files/dist/index.js

## 支付宝小程序配置

小程序配置 mini.project.json 开启 enableNodeModuleBabelTransform。
```
{
"enableNodeModuleBabelTransform": true
}
```


## 使用

### 初始化


```TypeScript
export interface RequestParams {
method: HttpMethod;
body?: string;
headers?: Record<string, string>;
}

export interface RequestResult {
status: number;
headers: Record<string, string>;
data: any;
}

export interface Fetch {
request(url: string, options?: RequestParams): Promise<RequestResult>;
}
```


### 调用云函数


```TypeScript
const cloud = require('@alipay/faas-web-sdk');
const request = require('some-third-party-request');

class CustomFetch {
async request(url: string, options?: RequestParams): Promise<RequestResult> {
const res = await request({
url,
method: options?.method || 'GET',
data: options?.body,
headers: options?.headers,
dataType: 'json',
});
return {
status: res.statusCode,
data: res.data,
headers: res.header,
};
}
}

const sdk = new cloud.Cloud({
secretId: '',
secretKey: '',
appId: '',
envId: '',
runtime: 'WEICHAT_MINI',
fetch: new CustomFetch(),
});
```


### 访问云存储

#### 上传文件

##### web 环境上传文件示例。

说明：web 环境，webSDK 默认使用浏览器内置的 fetch 进行文件上传，若有兼容性等需求，无法使用 fetch 时，可参考小程序环境上传文件示例，自定义 fileUploader。

##### 小程序环境上传文件示例

由于 webSDK 目前仅内置了浏览器环境文件上传操作，因此在小程序环境，需要自行实现文件操作逻辑。  初始化 sdk 时，将自定义 fileUploader 传给 sdk。  调用 uploadFile 方法完成文件上传。

#### 下载文件

##### web 环境下载文件示例。

说明：web 环境，webSDK 在下载文件时，默认直接返回文件的临时下载链接，若有其他需求，可参考小程序环境下载文件示例自定义文件下载逻辑。

##### 小程序环境下载文件示例。

由于 webSDK 目前仅内置了浏览器环境文件下载操作，因此在小程序环境，需要自行实现文件操作逻辑。  初始化 sdk 时，将自定义 fileUploader 传给 sdk。  调用 downloadFile 方法下载文件。

#### 删除文件



#### 获取文件临时访问链接



### 自定义 fetch

特殊场景，可能需要自定义 fetch 函数，传给 Cloud 使用。Fetch 的类型定义如下：  自定义时，需要实现 Fetch 对象，并通过构造器传给 Cloud 对象。  ​
