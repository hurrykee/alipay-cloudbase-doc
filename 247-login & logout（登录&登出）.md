# login & logout（登录&登出）

返回文档

## 登录云开发

CPT CLI 使用控制台生成的 CPT 密钥登录云开发，此处主要介绍 cpt login 命令的基本用法和登录云开发的操作步骤。1登录云开发平台

，依次选择全局设置>全局管理后，单击页面右上方生成密钥。2在生成密钥弹窗中，输入密钥名称，单击确定，生成密钥。说明：密钥名称支持任意字符，最多32字符。（一个中文占2个字符）。3生成密钥后，复制 APPID 和密钥并保存。注意：为保障账号安全，平台不保存密钥，生成后请妥善保管。4在命令窗口中，执行 cpt login 命令，根据提示输入之前已保存的 APPID 和 CPT 密钥，即可登录云开发。

## 基本用法


```
{
"appId": $yourAppId
"privateKey": $yourPrivateKey
}
```
说明：●执行 login 命令时，需要输入 CPT 密钥，填入该密钥即可。登录8小时后会失效，失效后请重新登录。●appid 以及 private_key 的加载优先级如下（从高到低）：○由命令行 flag 显式传递。■使用 --appid 以及 --private-key。■或者使用 --config 传递登录配置文件。○环境变量，appid 会读取 CPT_APPID，private_key 会读取 CPT_PRIVATE_KEy。○交互式命令行。

## 登录配置文件

json 文件示例：
```
appId: $yourAppId
privateKey: $yourPrivateKey
```
yaml 文件示例：
```Plain Text
Flags:
-a, --appid string         小程序 appid
--config string        登录配置文件，文件扩展名应该为 json 或者 yaml，文件中包含的配置项名称分别为 appId 以及 privateKey
-h, --help                 help for login
-k, --private_key string   CPT密钥
```


## 命令行参数



## 登出云开发

登录云开发后，在命令窗口中，执行 cpt logout 命令，即可登出云开发。​
