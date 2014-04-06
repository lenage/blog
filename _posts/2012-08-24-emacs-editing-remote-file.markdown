---
layout: post
title: Emacs 编辑远程文件
category: tech
---
[Tramp](http://savannah.gnu.org/projects/tramp) 是emacs下用来快速编辑远程文件的package, 用起来真的很方便:)
Emacs 24 内置 Tramp 所以不用配置就可以直接使用
![build in screenshot](/assets/images/2012-08/tramp.png)

打开远程文件:
`C-x C-f /myserver:public_html/foo.html`

或者

`C-x C-f /ssh:username@hostname:file`
ps:

1. myserver 是在.ssh/config 里面写好的server name
2. 文件默认路径是~, `:file` 相当于 `:~/file`

[更加全面的User Manual](http://www.gnu.org/software/tramp/#Filename-Syntax)
