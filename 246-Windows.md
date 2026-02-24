# Windows

返回文档本文主要介绍在 Windows 系统中安装安装 CPT CLI 的方法。

## 操作步骤

### 配置变量环境（安装）

说明：配置变量环境前请下载安装包 windows_amd64

。将cpt.exe文件所在目录的路径添加到 Path 环境变量中。1进入环境变量图形界面，在用户变量集中，选择键为 Path 的环境变量，并单击 编辑。
2输入cpt.exe文件所在目录的路径。3单击两次确定，应用更改后，完成安装。

### 验证安装

执行cpt命令，验证安装是否成功。
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
