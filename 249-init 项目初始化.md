# init 项目初始化

返回文档您可以使用 init 命令初始化一个项目文件夹，命令执行时会在项目文件夹下添加一个 cloudbaserc.json 为配置文件来提供 cpt 命令执行所需要的一些上下文信息，同时会创建 functions/ 作为默认的存放云函数的文件夹。
```
cpt cloudbase init
```


# 参数


```Plain Text
Flags:
-h, --help                 help for init
-e, --initial-env string   使用填写的云开发环境名称作为 cloudbaserc.json 文件 env 字段的初始值。如果不填写，将会使用默认值 prod。 (default "prod")
```


## Examples


```Plain Text
❯ mkdir demoProj
❯ cd demoProj
❯ cpt cloudbase init
INFO  Initialize project in /Users/wubi/demoProj/cloudbaserc.json
INFO  Create default function root directory in /Users/wubi/demoProj/functions
❯ tree
.
├── cloudbaserc.json
└── functions

1 directory, 1 file
```
​
