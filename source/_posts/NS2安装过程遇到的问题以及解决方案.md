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