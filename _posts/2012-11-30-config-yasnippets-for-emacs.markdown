---
layout: post
title: Emacs配置yasnippet
category: tech
---
适用版本: Emacs 24+

1. 添加package源，将如下代码加到`.emacs` 或者 `.emacs.d/init.el`
{% highlight cl linenos %}
;; set packages
(require 'package)
(setq package-archives
      '(("original"    . "http://tromey.com/elpa/")
        ("gnu"         . "http://elpa.gnu.org/packages/")
        ("marmalade"   . "http://marmalade-repo.org/packages/")
        ("melpa"       . "http://melpa.milkbox.net/packages/")))
(package-initialize)
{% endhighlight %}


2. `M-x eval-buffer`
3. `M-x package-list-packages` 按照你的网速快慢，可能需要半分钟左右.
4. 在打开的Packages Buffer中，找到`yasnippet` `yasnippet-bundle` `yas-jit`, 并按`i`(install)
   标记安装.最后按`x`安装。
   PS:
   + `yasnippet-bundle`(可选) -- 自动编译snippets
   + `yas-jit`(可选) -- 按需加载snippets

5. 配置yasnippet,这里分两种情况: 安装yas-jit和没有安装yas-jit:

   * 如果安装了`yas-int`
{% highlight cl linenos %}
(require 'yas-jit)
(require 'dropdown-list)
(setq yas/prompt-functions '(
                             yas/ido-prompt
                             yas/dropdown-prompt
                             yas/completing-prompt))
(setq yas/root-directory '(
                           "~/.emacs.d/snippets" ;; 自己的snippets
                           "~/.emacs.d/elpa/yasnippet-20121127.25/snippets" ;; yasnippet提供的
                           "~/.emacs.d/vendor/yasnippets-rails/rails-snippets" ;; 其他
                           "~/.emacs.d/vendor/yasnippets-shoulda"))
(yas/jit-load)
{% endhighlight %}

   * 如果没有安装`yas-jit`
{% highlight cl linenos %}
(require 'yasnippet)
(yas-global-mode 1)
(require 'dropdown-list)
(setq yas/prompt-functions '( yas/ido-prompt
                              yas/dropdown-prompt
                              yas/completing-prompt))
(yas/load-directory "~/.emacs.d/vendor/yasnippets-rails/rails-snippets")
(yas/load-directory "~/.emacs.d/vendor/yasnippets-shoulda")
{% endhighlight %}

6. 完了.

欢迎参考我的[emacs-config](http://github.com/lenage/emacs-config)

### Known issue

1. markdown-mode 下由于 `TAB` 被绑定到了 `markdown-cycle`上，所以无法展开snippets。
   查看键绑定`C-h k RET TAB`

> TAB runs the command markdown-cycle, which is an interactive compiled Lisp function in 'markdown-mode.el'.
