# 1. Tutorial



## 1.1 哲学

SIMPLE IS GOOD



**Do The Right Thing!**



## 1.2 应用领域

- Web

Django\pyramid\Flask\WebPy

- 网络编程

Twisted\Scrapy

- 科学运算

Pandas\SciPy\NumPy\Matplotlib

- GUI图形开发

PyQT\wxPython\TkInter

- 运维自动化

OpenStack\腾讯蓝鲸

## 1.3 encoding

ASCII 255 1byte 8bit

--> 1980 在ASCII码预留的位置进行扩展，gb2312  中文 7k+个汉字

--> 1995 GBK1.0 20k+个汉字

--> 2000 GB18030 27k+个汉字

--> unicode 统一2bytes

--> 在unicode基础上，变长存储，en:1byte , zh:3bytes



基于拉丁字母的一套电脑编码系统，主要用于显示现代英语和其他西欧语言，其最多只能用 8 位来表示（一个字节），即：2**8 = 256-1，所以，ASCII码最多只能表示 255 个符号。



Unicode（统一码、万国码、单一码）是一种在计算机上使用的字符编码。它为每种语言中的每个字符设定了统一并且唯一的二进制编码，规定虽有的字符和符号最少由 16 位来表示（2个字节），即：2 **16 = 65536。
注：此处说的的是最少2个字节，可能更多



UTF-8，是对Unicode编码的压缩和优化，不再使用最少使用2个字节，而是将所有的字符和符号进行分类：ascii码中的内容用1个字节保存、欧洲的字符用2个字节保存，东亚的字符用3个字节保存。



python解释器在加载 .py 文件中的代码时，会对内容进行编码（默认ascill）

指定编码格式

```pyt
# -*- encoding:utf-8 -*-
# -*- coding: utf-8 -*-
```



Strings can be encoded to bytes,  and bytes can be decoded back to strings.



## 1.4 语言类型

几个角度

- 编译型和解释型

源码 -> 编译器 -> 二进制文件

源码 -> 解释器 -> 字节码文件 -> 虚拟机 -> 边翻译边执行

编译型：C、C++、golang

解释型：js、python、Ruby、perl、erlang

混合型：java、c#

- 静态语言和动态语言

动态类型语言是指在运行期间才去做数据类型检查的语言

静态类型语言与动态类型语言刚好相反，它的数据类型是在编译其间检查

- 强类型定义语言和弱类型定义语言

强类型定义语言：强制数据类型定义的语言

弱类型定义语言：数据类型可以被忽略的语言



**python是动态解释性的强类型定义语言**

可扩展，内嵌C/C++代码

可移植

可嵌入，嵌入其他语言当作脚本执行



## 1.5 解释器

IPython 交互式解释器

CPython 官方解释器

PyPy 采用JIT编译技术，对代码进行动态编译，提升执行速度

Jython 运行在Java平台上的Python解释器，可以直接把Python代码编译成Java字节码执行

IronPython 和Jython类似，只不过IronPython是运行在微软.Net平台上的Python解释器，可以直接把Python代码编译成.Net的字节码



## 1.6 Hello World

```pytho
# print("Hello World")

## script
#!/usr/bin/env python3
print("Hello World")
```

## 1.7 Variables

变量名只能是 字母、数字或下划线的任意组合

变量名的第一个字符不能是数字

关键字不能声明为变量名

```py
# -*- encoding:utf-8 -*-
a1 = "aaa"
a2 = a1
print(a1, a2) # aaa aaa
a1 = "bbb"
print(a1, a2) # bbb aaa
```

## 1.8 注释

单行注释  #

多行注释  '''.....'''   """..."""

## 1.9 用户输入

```pyth
#!/usr/bin/env python
# -*- coding:utf-8 -*-
import getpass
name = input("please input your name")
passwd = getpass.getpass("please input your passwd")
print("%s %s" % (name, passwd))
```

## 1.10 模块

自定义模块

my.py

只能在当前目录下导入，如果想在系统的何何一个地方都使用，要把这个tab.py放到python全局环境变量目录里，一般都放在site-packages 目录下 。

用 print(sys.path) 可以查看python环境变量列表。

```pyt
import sys,os
res = os.system("dir") # 执行命令，不保留结果
print(res) # 0
res = os.popen("dir").read() # 保留结果
print(res) # dir's result

print(sys.path) # 打印环境变量
print(sys.argv) # 打印参数值
```



## 1.11 .pyc文件

Python是一门先编译后解释的语言。

两个概念，PyCodeObject和pyc文件。

PyCodeObject是Python编译器真正编译成的结果。

当python程序运行时，编译的结果是保存在位于内存中的PyCodeObject中，当Python程序运行结束时，Python解释器则将PyCodeObject写回到pyc文件中。

当python程序第二次运行时，首先程序会在硬盘中寻找pyc文件，如果找到，则直接载入，否则就重复上面的过程。

pyc文件其实是PyCodeObject的一种持久化保存方式。



## 1.12  格式化字符串

```pyth
print("%s" % a2)
print("%s %s" % (a1, a2))
print("{} {}".format(a1, a2))
print("{_a1} {_a2}".format(_a1=a1, _a2=a2))
b1 = 100
b2 = 1.1
print("%d %.2f" %(b1, b2))
```

## 1.13 运算符

逻辑运算符：and  or  not

成员运算符： in  not in

身份运算： is  is not

比较运算符：!=  ==  <>

## 1.14 表达式

```pytho
if True:
	print("True")
elif 2 > 1:
	print("True")
else:
	print("False")
	
for i in range(10):
	print("loop:", i)
	# continue
	# break

for i in range(0, 10, 3):
    print(i)

# 三元运算
result = 值1 if 条件 else 值2

if True: t1 = 100
print(t1)

# 循环中删除一个元素的坑
a = ["11","22","33","44","55","66"]
for i in a:
    a.remove(i)
    print(i)
for i in a[:]:
    a.remove(i)
    print(i)
```



## 1.15 一切皆对象

对于Python，一切事物都是对象，对象基于类创建

字符串类

数字类

列表类



## 1.16 十六进制

计算机内存地址和为什么用16进制？

**为什么用16进制**

1、计算机硬件是0101二进制的，16进制刚好是2的倍数，更容易表达一个命令或者数据。十六进制更简短，因为换算的时候一位16进制数可以顶4位2进制数，也就是一个字节（8位进制可以用两个16进制表示）

2、最早规定ASCII字符集采用的就是8bit(后期扩展了,但是基础单位还是8bit)，8bit用2个16进制直接就能表达出来，不管阅读还是存储都比其他进制要方便

3、计算机中CPU运算也是遵照ASCII字符集，以16、32、64的这样的方式在发展，因此数据交换的时候16进制也显得更好

4、为了统一规范，CPU、内存、硬盘我们看到都是采用的16进制计算

**16进制用在哪里**
1、网络编程，数据交换的时候需要对字节进行解析都是一个byte一个byte的处理，1个byte可以用0xFF两个16进制来表达。通过网络抓包，可以看到数据是通过16进制传输的。

2、数据存储，存储到硬件中是0101的方式，存储到系统中的表达方式都是byte方式

3、一些常用值的定义，比如：我们经常用到的html中color表达，就是用的16进制方式，4个16进制位可以表达好几百万的颜色信息。