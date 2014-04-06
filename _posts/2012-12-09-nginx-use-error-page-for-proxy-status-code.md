---
layout: post
title: nginx反向代理自定义error_page
category: tech
---

## 背景
caveman中如果没有找到路由则返回状态码404,但是不任何内容,所以需要nginx提供自定义404页面.
用`error_page 404 /404.html;`没有效果.

## 解决
使用`proxy_intercept_errors`,详细见这里[proxy_intercept_errors](http://wiki.nginx.org/HttpProxyModule#proxy_intercept_errors),
如果设置为`on`, 将捕获>400的状态码，并按照`error_page`的配置返回页面，如果没有配置则抛回给被代理服务器.
所以配置看起来是这样的:

{% gist 4241137 %}
