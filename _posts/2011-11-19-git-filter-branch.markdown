---
layout: post
title: git filter-branch
category: tech
---
需求: 在某次不小心将超大的文件加入了Git，或者deatabase.yml 等不想公开的文件，虽然在后面
的提交中删除了文件，但在git的历史记录中还是存在的。

要删除它，可以使用`git filter-branch` 命令
[link1](http://stackoverflow.com/questions/4444091/git-filter-branch-to-delete-large-file)
比如要删除以前用来测试的sql文件 `git filter-branch --index-filter 'git rm --cached --ignore-unmatch *.sql' HEAD`
更多内容请看 `git help filter-branch`
