title: 从VCF文件中提取信息
date: 2016-05-16 00:48:38
tags: [VCF, python]
---

　　从手机自带的通讯录导出工具导出VCF文件后，打开发现里面中文部分变成了十六进制的编码，例如：

```python
'=48=53'
```

　　利用python提取想要的信息并利用binascii模块进行转换，如

```python
name = binascii.a2b_hex(name)
```

　　最后完成的VCF提取工具[vcf info extractor](https://github.com/gdbb/vcfInfoExtractor)