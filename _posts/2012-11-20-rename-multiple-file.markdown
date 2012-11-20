---
layout: post
title: Linux Rename Multiple Files
category: tech
---
不是常用到会容易忘记，在这里记一下:

1. rename 用法(Mac下需要先安装`brew install rename`)

    rename 正则 files # rename s/alice/bob/g *.html
    rename oldname newname *.files

2. 用`find`找出需要rename的文件，然后用`-exec` 参数重命名，
   比如将当前文件夹下面的说有html.erb文件改为 html:

    find . -name "*html.erb" -exec rename s/html\.erb/html/ {} \;

3. 搞完收工
