---
layout: post
title: Github Pages and DNS settings
category: tech
---

Github Pages 给所有托管在 Github 上的项目提供静态网站和基于 Jekyll 的博客服务。
如果项目在 Github 上，并且需要一个简单的展示页面的话， Github Pages 是最好的选择，
同时，Github Pages 也提供自定义域名绑定服务, 但是官方的文档说的不是很明白，本文基
于我自己的实践说一下如何绑定主域名 (lenage.com) 和多个子域名到 Github 的不同项目。

## 目的

lenage.com 和 blog.lenage.com 都放在 Github 上，并且分别在不同的 Repository.

* [lenage.com](http://lenage.com) => [lenage/lenage.github.com](https://github.com/lenage/lenage.github.com)
* [blog.lenage.com](http://blog.lenage.com) => [lenage/blog.lenage.com](https://github.com/lenage/blog.lenage.com)

另外，如果其他的项目用 Github Pages, 只是 `/example-project` 的方式访问, 比如 [lenage/react-talk](https://github.com/lenage/react-talk)
可以通过 http://lenage.com/react-talk 访问. ![react-talk](/assets/images/posts/2.png)

## [lenage.com](http://lenage.com) 设置

1. lenage.com 添加 A 记录, `192.30.252.153` 和 `192.30.252.154`. ![A record](/assets/images/posts/1.png)
2. 修改 lenage.com 要指向的项目名称为 `yourusername.github.com`, 这不和重要，如果使用其他名字的话，另外项目将不能通过 lenage.com/example-project
的方式访问
3. 新建 `CNAME` 文件， 并添加到`youusername.github.com`, 这里需要注意的是`CNAME` 文件中只能有一个domain.
4. `git push` 更新项目, 然后在项目的 settings 里面查看 Github Pages 项，如果 ok， 会显示 `Your site is published at http://yourdomain.justadded.com`,
如果显示的是 `Your site is ready to publish at http://a.example.com`, 则需要你 update 项目来触发 Github Pages 绑定，随便加一个 commit, 然后 `git push`。

## [blog.lenage.com](http://blog.lenage.com) 设置

Github Pages 支持给任何项目绑定子域名， 只有添加 CNAME 文件和设置 DNS，下面看看 blog.lenage.com 的设置:

1. 添加 CNAME 文件, `echo 'blog.lenage.com' > CNAME`
2. 设置 DNS，添加 CNAME 到 `lenage.github.io`, 注意这里是 `lenage.github.io`, 虽然不是项目的名字，但是 lenage.com 会处理，这就是为什么前面一定要把 lenage.com
的项目命名为 `lenage.github.com` 的原因. ![blog](/assets/images/posts/3.png)
3. Push 一个 Commit 到 Github，然后到 Settings 查看结果. ![blog](/assets/images/posts/4.png)

[到 Github 查看具体代码](https://github.com/lenage)

PS. Github 最近[升级了 Pages 的架构](http://githubengineering.com/rearchitecting-github-pages/)，生成页面比以前又快了很多 :)
