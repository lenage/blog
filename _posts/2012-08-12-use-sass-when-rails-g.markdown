---
layout: post
title: 设置rails当运行rails g时默认生成sass文件
category: tech
---
sass-rails gem 默认生成scss文件，当运行rails g 命令的时候, 如果喜欢sass的语法的话
则需要每次都去`mv xxx.scss xxx.sass`,只要在`config/application.rb` 里面加入

    config.sass.preferred_syntax = :sass

这样运行`rails g` 生成样式文件默认使用sass语法。

last modify: Sun Aug 12 12:55:15 2012
