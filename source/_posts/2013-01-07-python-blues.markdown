---
layout: post
title: "Python Blues"
date: 2013-01-07 09:47
comments: true
categories: 
---

So you want to use PyGame on OSX, but this is happening:

<!-- more -->

``` bash
doctor@The-Doctors-iMac . ~ . python
Python 2.7.1 (r271:86882M, Nov 30 2010, 10:35:34)
[GCC 4.2.1 (Apple Inc. build 5664)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> import pygame
Traceback (most recent call last):
File "", line 1, in
File "/Library/Frameworks/Python.framework/Versions/2.7/lib/python2.7/site-packages/pygame/__init__.py", line 95, in
from pygame.base import *
ImportError: dlopen(/Library/Frameworks/Python.framework/Versions/2.7/lib/python2.7/site-packages/pygame/base.so, 2): no suitable image found. Did find:
/Library/Frameworks/Python.framework/Versions/2.7/lib/python2.7/site-packages/pygame/base.so: no matching architecture in universal wrapper
```
Basically you are using the wrong version of python. To fix it you have to say. Hey, OSX you stupid head, use the 32bit version.
``` bash
arch -x86_64 /usr/bin/python
Python 2.6.1 (r261:67515, Jun 24 2010, 21:47:49)
[GCC 4.2.1 (Apple Inc. build 5646)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> import pygame
>>> ^D
```
Now every time you want to run your program (or a script does!) you don.t want to have to change .python name.py. to .arch -x86_64 /usr/bin/python name.py. so a little bash magic I learnt from Linux comes into play

``` bash ~/.bashrc (or in my case ~/.zshrc)
alias python='arch -i386 /usr/bin/python'
```

For those of you who don't want to edit your bashrc I can do it for you with this little command

``` bash
echo "alias python='arch -i386 /usr/bin/python'" >> ~/.bashrc
```

Make sure to source your .bashrc or restart your terminal emulator of choice (iTerm2!)
