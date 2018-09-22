---
title: 解决npm install -g not found
date: 2018-09-22 14:29:36
tags:
---

## 场景

```shell
# npm install hexo -g
```

使用-g命令安装npm全局包，之后就可以在命令行中全局使用。

## 错误

安装成功后提示下面的错误：

```shell
# hexo
-bash: hexo: command not found
```

## 分析

发现hexo并不在`path`目录下：

```shell
# which hexo
/usr/bin/which: no hexo in (/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/root/bin)
```

以hexo为例分析`npm install -g`的安装过程：

1. npm将hexo安装在`/usr/local/lib/node_modules/hexo`目录下
2. 将hexo可执行文件`/usr/local/lib/node_modules/hexo/bin/hexo`链接到`/usr/local/bin/hexo`

那`/usr/local/bin`在`path`中却找不到hexo呢？

因为npm实际上是安装在`prefix`这个目录下，而不是`/usr/local`，如果`prefix`设置错误就找不到了。

## 验证

```shell
npm config get prefix
/data/app/janny-hexo
```

```shell
echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/root/bin:/usr/local/bin/lib
```

## 解决

1. 修改`prefix`【建议】

```shell
npm config set prefix /usr/local
npm install hexo -g
```

2. 或修改`path`

```shell
export PATH=$PATH:/data/app/janny-hexo/bin
npm install hexo -g
```
