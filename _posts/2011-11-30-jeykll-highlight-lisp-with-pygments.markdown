---
layout: post
title: Jekyll利用pygments高亮lisp代码
category: tech
---
主要是找对language关键词，高亮lisp的话用langauge用cl就ok了，比如
{% highlight cl linenos %}
;;{% highlight cl linenos %}
(require 'package)
(setq package-archives
      '(("original"    . "http://tromey.com/elpa/")
        ("gnu"         . "http://elpa.gnu.org/packages/")
        ("marmalade"   . "http://marmalade-repo.org/packages/")
        ("melpa"       . "http://melpa.milkbox.net/packages/")))
(package-initialize)
;;{% endhighlight %}
{% endhighlight %}
