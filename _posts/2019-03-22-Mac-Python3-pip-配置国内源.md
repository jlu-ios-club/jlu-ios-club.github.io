---
layout: post
title:  "Mac-Python3-pip-配置国内源"
author: "陆子旭"
date:   2019-03-22
desc: ""
keywords: "Python3"
categories: [Code]
tags: [Python3]
icon: fa-apple
---

# Mac-Python3-pip-配置国内源（推荐用阿里云的）

## 国内源

1. [阿里云](http://mirrors.aliyun.com/pypi/simple/)
2. [中国科技大学](https://pypi.mirrors.ustc.edu.cn/simple/)
2. [豆瓣 (douban)](http://pypi.douban.com/simple/)
2. [清华大学](https://pypi.tuna.tsinghua.edu.cn/simple/)
2. [中国科学技术大学](http://pypi.mirrors.ustc.edu.cn/simple/)

## 安装时指定

```shell
~ pip install ipython -i http://mirrors.aliyun.com/pypi/simple/ --trusted-host mirrors.aliyun.com


```

## 永久指定

```shell
# Mac OS
~ mkdir .pip	# 在家目录下创建一个.pip目录
~ cd pip
~ touch pip.conf # 创建一个pip配置文件
# 写入配置
[global]
index-url = http://mirrors.aliyun.com/pypi/simple/
[install]
trusted-host = mirrors.aliyun.com


```

[参考](https://blog.csdn.net/qq_43340659/article/details/82948529)