---
layout: post
title: Generate ruby(ri) docs
category: tech
---
如果`ri Array`的时候提示`Nothing known about Array`, 那么`rvm docs generate` 之后等10分钟
就能看到了：

{% highlight sh %}
~ ➤ rvm docs generate
    Generating ri documentation, be aware that this could take a *long* time, and depends heavily on your system resources...
    ( Errors will be logged to /Users/lenage/.rvm/log/ruby-1.9.3-p125/docs.log )

~ ➤ tail -f /Users/lenage/.rvm/log/ruby-1.9.3-p125/docs.log
    Generating RI format into /Users/lenage/.rvm/rubies/ruby-1.9.3-p125/share/ri/1.9.1/site...
    Generating Darkfish format into /Users/lenage/.rvm/docs/ruby-1.9.3-p125/rdoc..
{% endhighlight %}
