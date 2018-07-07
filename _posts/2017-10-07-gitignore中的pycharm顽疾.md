---
layout: post
title: Pycharm顽疾
date: 2017-10-07 11:42:06
categories: 工具
tags: Pycharm
---

* content
{:toc}

Pycharm非常强大

## gitignore中未忽略pycharm中的workspace.xml
```
.gitignore 中要写上 workspace.xml，如果已经不幸之前commit workspace.xml 的话，必须执行
以下命令 git rm --cached .idea/workspace.xml;还可以直接在.gitignore中写上.idea，会忽
略所有pycharm产生的文件
```

```
注意： git的本地忽略设置必须保证git的远程仓库分支上没有这个要忽略的文件，如果远程分支
上存在这个文件，本地在设置ignore这个文件，将会失败，无法commit忽略
```

```
目前解决方法：删除远程仓库;新建远程仓库;克隆远程仓库到本地，将以前的文件复制到本地仓库，
在提交前切记在.gitignore中添加.idea（血的教训）
```
