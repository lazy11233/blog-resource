---
title: 从URL到页面展示
date: 2018-10-31 10:49:44
thumbnail: http://phgcrbrst.bkt.clouddn.com/weburl01.jpg
categories:
- [Web, URL]
tags:
- URL
---
> 用户在输入一个网址，比如` www.baidu.com `，从网址输入到页面的展示到底经历了什么？
<!-- more -->
## 从输入网址开始
在浏览器地址栏输入了` www.baidu.com `
## 域名解析
对于` http://baidu.com `的URL，浏览器实际上不知道` baidu.com `到底是什么东西，需要查找` baidu.com `网站所在服务器的IP地址，才能找到目标
- 为什么要发明域名，不直接使用IP? 每个域名都对应着一个IP地址，使用域名有语义，IP地址是一堆数字，不利于用户的使用。
-  域名是什么？ 对于` http://baidu.com:8080/blog `,` baidu.com `就是域名
- IP地址是什么？
  每个处于互联网中的设备都有IP地址，形如` 192.168.0.1 `
  局域网IP和公网IP是有差别的
  ` 127.0.0.1 `代表本机的IP

## 域名解析的流程
1. 浏览器的缓存 - 浏览器会缓存DNS记录一段时间
2. 系统缓存 - 从Hosts文件查找是否有该域名和对应的IP
3. 路由器缓存 - 一般路由器也会缓存域名信息
4. ISP DNS缓存 - 比如到电信的DNS中查找缓存。
5. 如果都没有找到，则向向根域名服务器查找域名对应IP。
  - ` 问题：电脑上不了网，为什么修改dns为8.8.8.8或者114.114.114.114？ `
` 8.8.8.8 `是Google提供的域名服务器，用户修改了DNS之后，每一次http请求都会直接到这个域名服务器查找。` 114 `为国内类似Google 的域名服务器。

## 建立TCP链接(三次握手)
甲：你能听到我吗？

乙：听得到，你听得到我吗？

甲：听得到，我们可以开始对话了

## 发送HTTP请求

请求的四个部分：

1.  请求行
2. 请求头部
3. 空行
4. 请求数据


## 服务器处理
服务器安装了web server处理请求的域名。

1. 监听端口
2. 路由
3. 生成响应
4. 返回响应内容

##  关闭TCP链接(四次挥手)



## 浏览器处理
 HTML字符串被浏览器接收后被一句句读取解析，解析到link标签后重新发出请求获取CSS，解析到script标签或img标签时，发出请求获取js文件和图片文件。

## 绘制页面
浏览器根据html和css计算得到渲染树，绘制到屏幕上，js会被执行。
