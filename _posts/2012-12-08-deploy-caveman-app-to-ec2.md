---
layout: post
title: 部署Caveman到Amazon EC2
category: tech
---
上篇[部署Lisp应用到heroku][1]水分有点大，反正用Caveman框架写的demo没跑起来过。
这篇记录一下部署到Amazon EC2的过程。
> Caveman是一个Common Lisp的web框架, 基于clack, 更多[戳这里][2],作者是个日本人,
> [twitter帐号](https://twitter.com/nitro_idiot)

首先是创建EC2 Instance之类的不多说。

其次, 安装:
1. `sudo apt-get install tmux` 用于跑REPL然后关掉终端但是执行的命令继续跑，[StackOverflow][stackoverflow]上的讨论。
2. `sudo apt-get install sbcl` 详细 http://www.sbcl.org/
3. `quicklisp` 安装看[这里][quicklisp]
4. 设置服务端的git，然后push代码到EC2， 可以参考这篇文章: [How to set up your own private Git server on Linux][setup-git]
   和[HN上的讨论][hn-git-setup]，具体流程看这个[gist](https://gist.github.com/4239048)

然后，启动sbcl, 在tmux中运行`sbcl --load quicklisp.lisp`, 执行`(ql:quickload :myapp)`, 如有报错请检查quicklisp是否
安装正确，或者myapp目录是否在`quicklisp/local_projects/`目录下面，

最后, 在sbcl中运行`(myapp:start)` 启动. 启动后默认端口为5000(参`config/dev.lisp`), 如果想直接用80端口的话，
1. `sudo sbcl --load quicklisp.lisp`
2. `(ql:quickload :myapp)`
3. `(myapp:start :port 80)`

## [Demo](http://llbire.com)

[1]: http://blog.lenage.com/tech/2012/12/07/deploy-common-lisp-app-to-heroku/
[2]: https://github.com/fukamachi/caveman
[setup-git]: http://tumblr.intranation.com/post/766290565/how-set-up-your-own-private-git-server-linux
[hn-git-setup]: http://news.ycombinator.com/item?id=1652414
[stackoverflow]: http://stackoverflow.com/questions/451329/what-is-the-preferred-way-to-run-lisp-web-application
[quicklisp]: http://www.quicklisp.org/beta/
