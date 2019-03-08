---
layout: post
title:  work out the missing dependencies for a Python package
date:   2018-10-15 00:00:00
categories: pip-problem dev-missing
tags: pip-problem dev-missing
---

* content
{:toc}
搬运的一天

- 这是[PyCoders Weekly#337](https://pycoders.com/issues/337)上的一篇博客
- 我觉得对自己的日常开发很有帮助，所以分享一下
- 在日常开发中，很多时候`pip isntall`会报错，提示是缺少一些.so文件
- 很多时候，这些问题的通用解决方案是安装一些*-dev文件，但是这篇博客的作者提出了一个新的思路
- 利用`ldd`和`apt-file`
- 具体步骤如下：
- 1. 找出安装第三方软件的位置，一般是在`path/to/python/dist-packages/<package>/`
- 2. 运行`ls`，找出.so文件
- 3. 运行`ldd *.so`， 可以列出一个程序所需要得动态链接库
- 4. 然后找出哪些是不可用的，具体表现为指向是not found
- 5. 现在就需要找出哪个apt包提供这些文件， 运行`apt-file search *.so`
- 6. 找到后，运行`apt install <package>`来安装就可以了

- 感谢原作者提出的解决思路，在这之前我一直是谷歌搜，然后安装dev文件的，唉，编程果然有意思！[阅读原文](https://blog.piwheels.org/how-to-work-out-the-missing-dependencies-for-a-python-package/)