# 使用 TypeScript

返回文档函数运行入口是 index.js 文件，您可以通过 TypeScript 编译创建出这个入口文件。

## 新建 index.ts


```
type MyEvent = {
a: number;
b: number;
};

export async function main(event: MyEvent) {
return {
result: event.a + event.b,
};
}
```


## 添加 tsconfig.json 构建配置


```
{
"compilerOptions": {
"target": "ES2021",
"module": "Node16",
"moduleResolution": "Node",
"declaration": false
},
"exclude": [
"node_modules"
]
}
```


## 添加 typescript 依赖到 devDependencies

同时设置 scripts.postinstall 用于函数构建阶段执行 tsc 编译命令。
```
{
"description": "CloudFunction TypeScript Demo",
"main": "index.js",
"scripts": {
"postinstall": "tsc"
},
"dependencies": {
"@alipay/faas-server-sdk": "^1.1.12"
},
"devDependencies": {
"typescript": "^5.1.6"
}
}
```


## 完整的目录结构


```Bash
.
|____package.json
|____tsconfig.json
|____index.ts
```


## 本地执行 npm install


```Bash
npm install
```
●执行完成后，会看到已经成功构建出 index.js 文件。●删除 node_modules 目录后，将当前目录打包成 zip，上传到函数平台即可。​
