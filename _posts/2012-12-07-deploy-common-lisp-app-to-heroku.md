---
layout: post
title: 部署Common Lisp应用到heroku
category: tech
---
Heroku暂时还没有支持cl的stack，不过可以使用[第三方的build-package][1],

1.按照Github上的[exapmle project][2]创建app:
{% highlight bash %}
$ heroku create -s cedar --buildpack http://github.com/jsmpereira/heroku-buildpack-cl.git
Creating fierce-ravine-4120... done, stack is cedar
BUILDPACK_URL=http://github.com/jsmpereira/heroku-buildpack-cl.git
http://fierce-ravine-4120.herokuapp.com/ | git@heroku.com:fierce-ravine-4120.git
{% endhighlight %}
2. 启用[user-env-compile][3]
2. 使用sbcl `heroku config:add CL_IMPL=sbcl --app {app_name}`
3. 使用hunchentoot做web server `heroku config:add CL_WEBSERVER=hunchentoot`
4. 添加heroku到git remote host
   {% highlight bash %}
   cd myapp
   git init  && git add .
   git commit -m "first commit"
   git remote add heroku git@heroku.com:fierce-ravine-4120.git
   git push heroku master
   {% endhighlight %}

5. 修改`heroku-setup.lisp`, 将example修改为自己的app-name, 我这里是`myapp`
6. `git push heroku master`

PS: 另外可以重写 `heroku-toplevel` 函数来自定义启动app

[1]: https://devcenter.heroku.com/articles/third-party-buildpacks
[2]: https://github.com/jsmpereira/heroku-cl-example
[3]: https://devcenter.heroku.com/articles/labs-user-env-compile
