---
layout: post
title: 一些有用的linux命令
category: tech, blog
---

linux下的一些命令记录：有些命令可能在安装好系统之后再也不会用到，但需
要的时候却经常想不起来，在这里记录一下，以备后用，语言描述不准确指出
还望指正。

1.xev:运行一个gtk窗口，并在终端输出按键输入时的反馈，可以用来测试笔记
  本上的多媒体按键是否被内核支持；
2.`sed -i “s/A/B/g” grep A -rl yourdir` :用sed将youdir目录下所有
  文件中的A字符替换为B字符；
3.tmux ：和screen相当的终端多个screen显示程序，可以在屏幕下端显示窗口
  列表（screen不会），不知道怎么使用？ man一下
4.gmrun :在openbox下提供和gonme-do一样的alt+f2功能。
5.flexget :archlinux下载podcast的工具，使用yaourt安装。
