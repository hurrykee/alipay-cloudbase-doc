# cloudbaserc.json 函数配置文件

返回文档cloudbaserc.json 为云函数项目的配置文件，一个项目可以包括多个云函数。当云开发 CLI 在项目文件目录下执行时，cloudbaserc.json 中配置的值会为命令执行提供默认值或者所需的上下文信息。

## 示例

说明：在设置 env 字段后，当 cpt cloudbase 命令在含有 cloudbaserc.json 的项目目录下执行时，会默认使用该 env 字段值（可以传入 --env 覆盖该默认行为）。
```JSON
{
// 配置文件的版本，默认为 1.0
"version": "1.0",
// 云开发环境名称
"env": "yourEnvName",
// 函数代码存放的文件夹路径，相对于项目根目录的路径。
"functionRoot": "./functions",
// 函数配置项组成的数组
"functions": [
{
// 云函数名称
"name": "yourFuncName",
// 部署云函数时打包忽略的文件
"ignore":[
// 忽略 markdown 文件
"*.md",
// 忽略 node_modules 文件夹
"node_modules",
"node_modules/**/*"
],
// CLI 调用云函数时使用的参数
"params":{
"foo1": "bar1",
"foo2": "bar2"
}
}
]
}
```

```JavaScript
{
"version": "1.0",
"env": "yourEnvName",
"functionRoot": "./functions",
"functions": [
{
"name": "yourFuncName",
"ignore":[
"*.md",
"node_modules",
"node_modules/**/*"
],
"params":{
"foo1": "bar1",
"foo2": "bar2"
}
}
]
}
```
​
