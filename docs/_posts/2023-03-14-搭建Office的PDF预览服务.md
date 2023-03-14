---
layout: post
title:  "搭建Office的pdf预览服务"
date:   2023-03-14 16:24:08 +0800
categories: tools
---

# 搭建Office的pdf预览服务

我们有时会有使用java来进行pdf进行预览服务，目前线上有多个包提供类似服务，但是很多时候转的pdf文件会有样式错误。
最后发现使用jodconvertor配合open office可以较为完美的实现pdf预览的功能。

## 环境

- 系统: docker
- open office: LibreOffice
- 格式转换包: jodconveror 

## 描述

本项目主要是将java进程和openoffice放到一个docker容器中，进而在本地调用LibreOffice实现office转pdf的服务。
相关样例代码在这个repo中[office-converter]

1. 使用repo中提供的Dockerfile来构建包含LibreOffice的java jdk环境
2. 使用repo中的样例springboot代码来构建，部署一个转换服务
3. 详细过程见readme

[office-converter]: https://github.com/zhtangsh/office-converter