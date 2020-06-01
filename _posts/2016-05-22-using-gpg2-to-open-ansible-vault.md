---
layout: post
title: 使用 gpg2 自动给 Ansible Vault 解密密码
category: ansible
---

1. 如果遇到 gpg-agent is not available in this session, 用 gpg2
2. 如果不能自动记住密码, 用 gpg2
3. 如果 Emacs 里面也不能自动记住密码，用 gpg2

总之 gpg2 千搬好

## 安全! 安全! 安全!

1. 不要在 git 里面提交任何密码
2. 不要明文存储未经加密的密码
