title: 解决Windows下msys-git不支持长文件名的问题
date: 2016-05-16 14:46:31
tags:
---

　　在Linux下编写的文件，push到github再clone到Windows下时出现了问题，在git status时出现'Filename too long'。Windows下用的是msys-git，查资料有的说msys用的是老的Windows API，不支持长文件名，但实际上是可以通过配置打开长文件名功能的。

```bash
git config --system core.longpaths true
```

reference: [stackoverflow](http://stackoverflow.com/questions/22575662/filename-too-long-in-git-for-windows)