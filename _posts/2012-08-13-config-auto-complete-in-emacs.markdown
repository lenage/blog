---
layout: post
title: 为emacs 配置auto-complete
category: tech
---
早上写了一半又删掉了，因为写着写着突然感觉这么简单的问题大家都会懂，
但晚上又觉得还是要写出来， 仅仅作为记录。

起初是使用smart-tab 这个函数来做补全的：

    ;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
    ;; Hippie expand.  Groovy vans with tie-dyes.

    (setq hippie-expand-try-functions-list
        '(yas/hippie-try-expand
            try-expand-dabbrev
            try-expand-dabbrev-all-buffers
            try-expand-dabbrev-from-kill
            try-complete-file-name
            try-complete-lisp-symbol))

    ;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
    ;; Smart Tab
    ;; Borrowed from snippets at
    ;; http://www.emacswiki.org/emacs/TabCompletion
    ;; TODO: Take a look at https://github.com/genehack/smart-tab

    (defvar smart-tab-using-hippie-expand t
        "turn this on if you want to use hippie-expand completion.")

    (defun smart-tab (prefix)
        "Needs `transient-mark-mode' to be on. This smart tab is minibuffer compliant: it acts as usual in the minibuffer.
        In all other buffers: if PREFIX is \\[universal-argument], calls `smart-indent'. Else if point is at the end of a symbol,
        expands it. Else calls `smart-indent'."
        (interactive "P")
        (labels ((smart-tab-must-expand (&optional prefix)
        (unless (or (consp prefix)
            mark-active)
        (looking-at "\\_>"))))
        (cond ((minibufferp)
            (minibuffer-complete))
            ((smart-tab-must-expand prefix)
                (if smart-tab-using-hippie-expand
                (hippie-expand prefix)
                (dabbrev-expand prefix)))
            ((smart-indent)))))

    (defun smart-indent ()
        "Indents region if mark is active, or current line otherwise."
        (interactive)
        (if mark-active
            (indent-region (region-beginning)
        (region-end))
        (indent-for-tab-command)))
    ;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;

    (global-set-key (kbd "TAB") 'smart-tab)

一般情况下都是够用的， 直到后来ruby-mode只有indent没有补全(不知道是什么原因，求指点)，一定
是我打开的方式不对。于是安装了auto-complete：

1. install, 如果是>emacs24 的话，直接 `M-x package-install RET auto-complete`
   PS: 没有实测，我自己是苦逼的 `M-x package-list-packages` 然后搜索 complete 安装的。

2. 使用， 在`.emacs` 添加

       (require 'auto-complete)
       (require 'auto-complete-config)
       (ac-config-default)

就能出现如下图的效果![效果图不是我的截图](http://cx4a.org/software/auto-complete/ac.png)

3. 然后想关掉popup的话 `(setq ac-auto-show-menu nil)`, 想在popup(严格的说是menu)上面使用
`C-n, C-p`来选词的话:

    (define-key ac-completing-map (kbd "C-n") 'ac-next)
    (define-key ac-completing-map (kbd "C-p") 'ac-previous)

我的完整配置的[话](https://github.com/lenage/emacs-config/blob/master/lenage/auto-complete.el)

4. 要clone的话，`git clone https://github.com/lenage/emacs-config.git ~/.emacs.d`

-EOF-  Mon Aug 13 22:40:53 2012
