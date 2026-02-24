# Linux

返回文档本文主要介绍在 Linux 系统中安装 CPT CLI 的方法。1下载安装包 linux_amd64

。2执行以下命令，给安装包添加执行权限。
```
chmod +x cpt
```
3执行以下命令，将cpt程序复制到/usr/local/bin目录中。
```Go
cp cpt /usr/local/bin
```
4执行cpt命令，验证安装是否成功。
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
​
