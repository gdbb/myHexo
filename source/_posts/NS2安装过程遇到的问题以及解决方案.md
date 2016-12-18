title: NS2安装过程遇到的问题以及解决方案.md
date: 2016-12-14 16:54:36
tags: [NS2]
---

#### OS：openSuSE Leap-42.1


* ##### can't find X includes

	解决方案：

	安装libxt-dev

* ##### ‘erase’ was not declared in this scope ns2
　　
	解决方案：

	修改ls文件：ns-2.35/linkstate/ls.h 

	第137行

	void eraseAll() { erase(baseMap::begin(), baseMap::end()); }

	改为：void eraseAll() { this->erase(baseMap::begin(), baseMap::end()); }

	然后重新 ./install


* ##### 在nam文件夹下 make 说找不到 X11/xmu/winutil.h

	ns2安装好之后运行“exec nam”是提示“couldn't execute "nam": no such file or directory
”
	在网上查说nam没有安装好，但在ns2下的nam文件夹中编译时又提示找不到 “X11/xmu/winutil.h”

	解决方案：

	在32位系统中 安装  libXmu-dev

	在64位系统中 安装yum  install  libXmu-devel.i686

	reference：[stackoverflow](http://blog.csdn.net/zhoujunbuaa/article/details/7181785)

* ##### Tcl版本问题

	nam编译安装好之后运行发现Tcl版本不对。

	如下

	nam:
	[code omitted because of length]
	: version conflict for package "Tcl": have 8.6.1, need exactly 8.5.10
	while executing
	"package require -exact Tcl 8.5.10"

	我印象中电脑里和Tcl有关的python（Tk有用到），但不管怎样现在需要将其替换成Tcl 8.5.10。

	用update-alternatives将/usr/bin下的tclsh替换成ns2目录下的Tcl 8.5.10中的tclsh。

	之后重新编译安装nam，运行nam成功。

