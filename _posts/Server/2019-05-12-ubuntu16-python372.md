---
layout: post
title: "Ubuntu16.04安装Python3.7的方法"
subtitle: "阿里云ECS（Ubuntu16.04）安装Python3.7的手动操作方法"
date: 2019-05-12 18:00:00
author: "Lester Tan"
tags: 
    - Ubuntu
    - Python
    - 流程
	- 服务器
---

由于阿里云ECS（Ubuntu16.04版本）中自带的Python最新版本为3.5，无法使用`apt-get`命令获取Python最新版本3.7.2，需要手动更新，以下为实测可行的流程。

## 第一步

更新apt-get并配置依赖环境

```shell
apt-get update
apt-get install zlib1g-dev libbz2-dev libssl-dev libncurses5-dev libsqlite3-dev libreadline-dev tk-dev libgdbm-dev libdb-dev libpcap-dev xz-utils libexpat1-dev liblzma-dev libffi-dev libc6-dev
```

## 第二步

在当前路径下载指定版本的安装包并解压

```shell
wget https://www.python.org/ftp/python/3.7.2/Python-3.7.2.tgz
tar zxvf Python-3.7.2.tgz
```

## 第三步

进入解压目录，建立安装目录

```shell
cd Python-3.7.2
mkdir /opt/python3.7
```

## 第四步

编译安装

```shell
./configure --prefix=/opt/python3.7  --enable-optimizations
make && make install
```

## 第五步

建立软链接（已有的链接要删除）

```shell
rm /usr/bin/python3
ln -s /opt/python3.7/bin/python3.7 /usr/bin/python3
```

## 第六步

检查版本

```shell
python3 -V
```

