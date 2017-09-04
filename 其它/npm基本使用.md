title: npm基本使用
tags:
  - Linux
categories:
  - Linux
author: ''
date: 2017-09-01 09:17:00
---
##  npm 淘宝镜像安装
```
$  npm install -g cnpm --registry=https://registry.npm.taobao.org
```

## npm初始化
```
$ npm init
```

## npm 版本号
```
$ npm -v
```

## npm install 安装

### 全局安装
```
$ npm install package -g
```

### 本地安装
```
//写入package.json文件安装
$ npm install

//安装到生产环境需要的dependencies中
$ npm install package --save(-S)

//安装到开发环境需要的devDependencies中
$ npm install package --save-dev(-D)

//安装指定版本
$ npm install package@3.2.1 --save

//安装到可选依赖optionalDependencies中
$ npm install package --save-optional(-O)

//精确安装模块
$ npm install package --save-exact(-E)
```

## npm uninstall 卸载
```
$ npm unninstall gulp -g
$ npm uninstall gulp
$ npm uninstall --save
$ npm uninstall gulp --save-dev
```

## npm update 更新模块
```
//更新当前目录模块
$ npm update pageage

//更新全局模块
$ npm update -g package
```
### 检查模块是否已经过时
```
$ npm outdated package
$ npm outdated package -g
```

## npm 查看安装模块
```
$ npm ls

$ npm ls -g

//查看版本号
$ npm list package

//查看具体信息
$ npm info package

//查看模块的注册信息
$ npm view 
```

## npm 搜索
```
$ npm search express 
```

## 管理模块的缓存
```
$ npm cache ls [<path>]
$ npm cache clean [<path>]
```

## npm 启动、停止、重启模块
```
$ npm start [-- <args>]

$ npm stop [-- <args>]

$ npm restart [-- <args>]
```

















