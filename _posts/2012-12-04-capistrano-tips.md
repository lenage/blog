---
layout: post
title: Capistrano 技巧
category: tech
---
1. `%x{command}` 在本地执行命令
2. `stream "cd #{shared_path} && tail -f log/production.log"` 查看服务器log
