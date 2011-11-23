---
layout: post
title: vim小指南
category: tech
---
这篇文章是关于stackoverflow上[what is the vim feature that you like the most](http://stackoverflow.com/questions/80386/what-is-the-vim-feature-that-you-like-the-most)
的总结，有很多非常有用的feature:

1.  `[ shift + i` 查看当前文件中当前光标下出现的所有词，比如你想知道该单词
    是否唯一则不用`/xxxxx`搜索，而是直接`[ shift+i`就可以搞定。
2.  `dat/dit` tag-block motions,比如在编辑html或xml时，`dit`可以删除包含在标签
    里面的内容，`dat`可以删除当前光标下的标签。
3.  `:tabe` 直接在新的tab里面打开文件，比平时先新建tab然后在`:e`方便多了。
4.  `d[number]d` 删除多行
5.  `Text Object(type :h text-objects)` 可以让你多光标所在位置的整个区块操作，
    如:可以使用`d`或者`c`，后面跟`i`或者`a`(inside a block or a whole block)加区块
    符号如`{(<"pw`，其中`p`是指整个段落，`w`是指一个单词。

    * `ca{`  :Delete a block of code delimited by curly braces.
    * `ci(`  :Change the content inside parenthesis.
    * `ci"`  :Change the content inside a String
    * `da<`  :Delete an html tag
    * `dap`  :Delete current paragraph (handy to delete a whole function)
    * `daw`  :Delete a word

6.  `w/])` 移动，`w`可以以单词为单位移动，`]`是以section为单位移动，`)`以句子为单位
    移动。
