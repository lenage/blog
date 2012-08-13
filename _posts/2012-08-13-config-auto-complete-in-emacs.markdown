---
layout: post
title: 为emacs 配置auto-complete
category: tech
---
早上写了一半又删掉了，因为写着写着突然感觉这么简单的问题大家都会懂，
但晚上又觉得还是要写出来， 仅仅作为记录。

起初是使用smart-tab 这个函数[github连接](https://github.com/lenage/emacs-config/blob/master/lenage/tabs.el)来做补全的
一般情况下都是够用的， 直到后来ruby-mode只有indent没有补全(不知道是什么原因，求指点)，一定
是我打开的方式不对。于是安装了auto-complete：

1. install, 如果是>emacs24 的话，直接 `M-x package-install RET auto-complete`
   PS: 没有实测，我自己是苦逼的 `M-x package-list-packages` 然后搜索 complete 安装的。

2. 使用， 在`.emacs` 添加

       (require 'auto-complete)
       (require 'auto-complete-config)
       (ac-config-default)

    就能出现如下图的效果![效果图不是我的截图](http://cx4a.org/software/auto-complete/ac.png)

3. 然后想关掉popup的话 `(setq ac-auto-show-menu nil)`, 想在popup(严格的说是menu)上面使用
   `C-n, C-p`来选词的话, auto-complete的完整配置[在这里](https://github.com/lenage/emacs-config/blob/master/lenage/auto-complete.el)

       (define-key ac-completing-map (kbd "C-n") 'ac-next)
       (define-key ac-completing-map (kbd "C-p") 'ac-previous)



4. 要clone的话，`git clone https://github.com/lenage/emacs-config.git ~/.emacs.d`

----
Update1: 在这里贴大段的代码还是很丑的，改用github文件连接
Update2: 更加详细的文档 http://cx4a.org/software/auto-complete/manual.html

Mon Aug 13 22:49:49 2012
