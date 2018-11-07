---
layout: post
title: Apache服务器上CSS不被正常解析，解决方法
date: 2018-11-07 15:32:24.000000000 +09:00
catalog: 	 true
categories: 服务器管理
tags:
    - Centos
---

Html上
<!doctype html> <--这一行删除，就会解决css无法解析的问题了。

但是还是有警告信息
1 Resource interpreted as Stylesheet but transferred with MIME type text/plain:
2 The provided value 'moz-chunked-arraybuffer' is not a valid enum value of type XMLHttpRequestResponseType.
没有解决，查找中...
