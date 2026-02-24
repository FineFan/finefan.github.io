---
layout: post
title: "Better Chinese Input on Fedora 43"
description: "Jianhong Yin shared me a link showing how to get better Chinese input on Fedora"
date: 2026-02-24
feature_image: images/Chinese_input_fedora.jpg
tags: [tips, fedora, ChineseInput]
---

There were always a pain point there when I using Fedora - The Chinese Input , there is one , but hard to use.

<!--more-->
One Day a link come from Jianhong Yin,  
> https://blog.amyinfo.com/2024-12-28-setup-fcitx5-on-fedora/


It is a quite simple article on that page:

1. Install fcitx5
> sudo dnf install fcitx5 fcitx5-chinese-addons

2. Config .xinitrc
```
cat >> $HOME/.xinitrc <<"EOF"
export XMODIFIERS="@im=fcitx"
export GTK_IM_MODULE=xim
export QT_IM_MODULE=fcitx
EOF
```

3. Enable fcitx for Gnome
```
gsettings set org.gnome.settings-daemon.plugins.xsettings overrides "{'Gtk/IMModule':<'fcitx'>}"
```

After configure with these steps. there are 2 questions come to my mind:
1. How could I know which Input method I am using right now?
2. How to determine my Chinese Input is better than the another one?

1. How to know which input method I'm using right now?


Before
```
fan@ffan-thinkpadt14gen5 ~ $ echo $XMODIFIERS
@im=ibus
ffan@ffan-thinkpadt14gen5 ~ $ echo $GTK_IM_MODULE

ffan@ffan-thinkpadt14gen5 ~ $ echo $QT_IM_MODULE
ibus
ffan@ffan-thinkpadt14gen5 ~ $ 


```
After 

```
ffan@ffan-thinkpadt14gen5 _posts (main) $ echo $XMODIFIERS

ffan@ffan-thinkpadt14gen5 _posts (main) $ echo $GTK_IM_MODULE

ffan@ffan-thinkpadt14gen5 _posts (main) $ echo $QT_IM_MODULE
ibus
ffan@ffan-thinkpadt14gen5 _posts (main) $ 
```
I wonder if it needs a GNOME restart or not


