---
layout: post
title: archlinux+openbox使用笔记本的多媒体键
category: tech
---

需要说明的是：这里指的多媒体键是指，笔记本上除Fn+\*之外的独立按键，一般用来静音，加大减小音量，打开DVD光驱等。

`PC：cq45-203tx`

背景：之前用ubuntu+gnome的时候快捷键有效，切换到archlinux+openbox后快捷键失灵，只能用alsamixer调节音量，
安装过volwheel，但还是不好用，后来在#ubuntu-cn频道找到了解决办法，如下：

1.确定内核是否支持，在终端中运行 xev，然后触摸按键，看输出：
    KeyRelease event, serial 40, synthetic NO, window 0×2600001,
    root 0x15a, subw 0×0, time 20902899, (240,92), root:(387,402),
    state 0×0, keycode 121 (keysym 0x1008ff12, XF86AudioMute), same\_screen YES,
    XLookupString gives 0 bytes:
    XFilterEvent returns: False

如果能得到如上的输出，你得到的不一定和我的完全一样，但至少要能在其中找到按键标识，即上面红色指出的部分。

2.从上面的输出我们可以看出，该按键市静音按钮，用vim或者你喜欢的编辑器打开 `~/.config/openbox/rc.xml`文件，
找到keybind部分；然后设置按键`XF86AudioMute`运行`amixer sset Master,0 toggle：`

{% highlight xml %}
<keybind key=”XF86AudioMute”>
<action name=”Execute”>
<startupnotify>
<enabled>true</enabled>
<name>Audio mute</name>
</startupnotify>
<command>amixer sset Master,0 toggle</command>
</action>
</keybind>
{% endhighlight %}

3.用第一步的方法得到增大音量和减小音量的按键标识分别是`XF86AudioRaiseVolume`和`XF86AudioLowerVolume`；
分别绑定为`amixer sset Master 2%+`（增加音量）`amixer sset Master 2%-`（减小音量），如下：

{% highlight xml %}
<keybind key=”XF86AudioMute”>
<keybind key=”XF86AudioRaiseVolume”>
<action name=”Execute”>
<startupnotify>
<enabled>true</enabled>
<name>Audio raise</name>
</startupnotify>
<command>amixer sset Master 2%+</command>
</action>
</keybind>
<keybind key=”XF86AudioLowerVolume”>
<action name=”Execute”>
<startupnotify>
<enabled>true</enabled>
<name>Audio lower</name>
</startupnotify>
<command>amixer sset Master 2%- </command>
</action>
</keybind>
{% endhighlight %}


4. 在终端中运行$-> `openbox –reconfigure done`,现在可以享受快捷键带来的快感了。
