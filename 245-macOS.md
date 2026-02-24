# macOS

返回文档本文主要介绍在 macOS 上安装 CPT CLI 的方法。1下载安装包，下载地址如下：○通用：universal

○m1：darwin_arm64

○非m1：darwin_amd64

2执行以下命令，给安装包添加执行权限。
```Go
chmod +x cpt
xattr -d com.apple.quarantine cpt
```
3执行以下命令，将 cpt 程序复制到 /usr/local/bin 目录中。
```Go
cp cpt /usr/local/bin
```
4执行 cpt 命令，验证安装是否成功。
```Go
% cpt
支付宝小程序云CLI工具

Usage:
cpt [command]

Available Commands:
cloudrun    云托管命令
login       登录小程序云
logout      登出小程序云
migrate     云迁移命令
version     打印CPT版本号

Flags:
--config string   config file (default is $HOME/.cpt.yaml)
-h, --help            help for cpt

Use "cpt [command] --help" for more information about a command.
```
注意：如果报“无法打开 cpt，因为无法验证开发者”错误，需要前往“安全与隐私”授权 cpt 可执行。5选择系统偏好设置>安全与隐私。
6在安全性与隐私弹窗中，单击仍然允许。
7重新执行cpt命令，弹窗中单击打开。
​
