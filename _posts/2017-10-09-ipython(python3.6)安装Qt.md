---
layout: post
title: ipython(python3.6)安装Qt
date: 2017-10-09 11:42:06
categories: 工具
tags: Qt
---

* content
{:toc}

使用Ipython的时候会用到

### ipython(python3.6)安装Qt console
```
pip install qtconsole
# 虚拟环境中安装
pip install PyQt5

# 非虚拟环境中安装
sudo apt-get install python3-pyqt5 # PyQt5 on Python 3
sudo apt-get install python3-pyqt4 # PyQt4 on Python 3
sudo apt-get install python-qt4    # PyQt4 on Python 2

# 启动
jupyter qtconsole

# 这个工具在使用matlab时非常有用
```
