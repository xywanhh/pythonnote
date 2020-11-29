# 1. 列表、元组

```pyt
a = ["11","22","33","44","55","66"]
# 取元素
print(a[0])
print(a[-1])
print(a[1:3])
print(a[:])
print(a[1:-1])
print(a[:3])
print(a[1:])
print(a[1:-1])
print(a[0::2])
print(a[::2])
# 追加
a.append("aaa")
# 插入
a.insert(1, "bbb")
# 修改
a[1] = "ccc"
# 删除
del a[1]
a.remove("22")  # 删除指定元素，如果不存在，报错
a.pop() # 删除最后一个值
# 扩展
b = [1, 2, 3]
a.extend(b)
print(a)
# 拷贝 （浅拷贝）
a1 = a.copy()
print(a1)
a[0] = "00"
print(a1)
# 统计
print(a.count("00"))
# 排序
# a.sort() # 不同数据类型不能排序
# 反转
a.reverse()
print(a)
# 获取下标
print(a.index("33")) # 下标不存在报错，只返回找到的第一个下标
```



元组也是存一组数据，不过一旦创建，就不能在修改，又叫只读列表。

只有两个方法 count， index

```py
b = (1, "b", "cc", 4)
print(b[2])
print(b.count("cc"))
print(b.index(1))
```



# 2. 字符串

**不可修改**

```pyth
name = "aa, bb, cc, dd"
# 首字母大写
print(name.capitalize())
# 返回索引
print(name.index("aa")) # 不存在报错
# 大写全部变小写
print(name.casefold())
name.center(10, "*")
# 统计
print(name.count("a"))
# 将字符串编码成bytes格式
print(name.encode())
print(name.endswith("dd"))
print("bb\taa".expandtabs(10))
# 查找，返回索引，否则返回-1
print(name.find("cc"))

# 格式化
msg = "%s %d"
msg1 = "%s"
print(msg % ("aa", 11))
print(msg1 % "aa")

msg2 = "{} {}"
print(msg2.format("aa","bb"))
print(msg2.format("aaa", 111))

msg3 = "{1} {0}"
print(msg3.format("aa", "bbb"))

msg4 = "{a},{b}"
print(msg4.format(a=11, b="bbbb"))
print(msg4.format_map({"a":"aaa", "b":100}))

print('9aA'.isalnum())   # True
print('9'.isdigit()) # 是否整数
print(name.isnumeric()) 
print(name.isprintable())
print(name.isspace())
print(name.istitle())
print(name.isupper())

# join
print("||".join(name))

intab = "aeiou"
outtab = "12345"
print(str.maketrans(intab, outtab))
trantab = str.maketrans(intab, outtab)
str = "this is string example....wow!!!"
print(str.translate(trantab))

msg.partition('is')

# replace
print(msg.replace('a', 'b', 1))

# zfill
print(msg.zfill(40))

print(msg.ljust(10,"-"))
print(msg.rjust(10,"*"))

# 检测一段字符串可否被当作标志符，即是否符合变量命名规则
print(name.isidentifier())
```





# 3. 字典

key-value数据结构

特点：

- **无序**

- **key唯一**

```pyth
b = {
    "key1" : "111",
    "key2" : "2222"
}
# 增加
b["key3"] = "333"
# 修改
b["key1"] = "111111"
# 删除
b.pop("key1")
del b["key2"]
print(b)
b["key5"] = "key555"
b.popitem() # 随机删除
print(b)

# 查找
print("key3" in b)
print("aa" in b)

#如果一个key不存在，就报错，get不会，不存在只返回None
print(b.get("key3"))
# print(b["key333"])

print(type(b.values())) # <class 'dict_values'>
print(b.values()) # dict_values(['333'])

print(type(b.keys())) # <class 'dict_keys'>
print(b.keys()) # dict_keys(['key3'])

# setdefault
b.setdefault("aa", "cccc")
print(b.get("aa"))
print(b)

# update
c = {"key3":"ckey3", "bb" : "bbb"}
b.update(c)
print(b)

# item
print(type(b.items())) # <class 'dict_items'>
print(b.items()) # dict_items([('key3', 'ckey3'), ('aa', 'cccc'), ('bb', 'bbb')])

# loop dict
for key in b:
    print(key, b.get(key))

# 会先把dict转成list,数据里大时莫用
for k,v in b.items(): 
    print(k, v)
```



# 4. 集合

无序，不重复

作用：

- 对列表进行去重set(list)
- 取交并补运算



```py
b1 = set([1, 2, 3, 4])
b2 = set("abcdef")

# 并集
print(b1 | b2)
# 交集
print(b1 & b2)
# 差集
print(b1 - b2)
# 对称差集
print(b1 ^ b2)

# 添加
b1.update([11, 12])
b2.add("ee")

# 删除
b2.remove("a")

print(len(b2))

print("aa" in b2)

print(b1.issubset(b2))
print(b1.issuperset(b2))

# 返回一个新的 set 包含 s 和 t 中的每一个元素
print(b1.union(b2))

# 返回一个新的 set 包含 s 和 t 中的公共元素  
print(b1.intersection(b2))

# 返回一个新的 set 包含 s 中有但是 t 中没有的元素
print(b1.difference(b2))

# 返回一个新的 set 包含 s 和 t 中不重复的元素
print(b1.symmetric_difference(b2))

# 浅复制 
print(b1.copy())
```





# 5. 文件

```py
# 打开文件
f = open('lyrics') 
first_line = f.readline()
print('first line:',first_line) # 读一行
print('***'.center(50,'-'))
data = f.read() # 读取剩下的所有内容,文件大时不要用
print(data)
f.close() #关闭文件

# with管理文件打开上下文
with open('log','r') as f:
    pass
# python27后，支持打开多个文件
with open('log1') as obj1, open('log2') as obj2:
    pass
```



打开文件的模式有：

- r，只读模式（默认）。
- w，只写模式。【不可读；不存在则创建；存在则删除内容；】
- a，追加模式。【可读；  不存在则创建；存在则只追加内容；】

"+" 表示可以同时读写某个文件

- r+，可读写文件。【可读；可写；可追加】
- w+，写读
- a+，同a

"U"表示在读取时，可以将 \r \n \r\n自动转换成 \n （与 r 或 r+ 模式同使用）

- rU
- r+U

"b"表示处理二进制文件（如：FTP发送上传ISO镜像文件，linux可忽略，windows处理二进制文件时需标注）

- rb
- wb
- ab

# 6. 字符编码与转码

1.在python2默认编码是ASCII, python3里默认是unicode

2.unicode 分为 utf-32(占4个字节),utf-16(占两个字节)，utf-8(占1-4个字节)， so utf-16就是现在最常用的unicode版本， 不过在文件里存的还是utf-8，因为utf8省空间

3.在py3中encode,在转码的同时还会把string 变成bytes类型，decode在解码的同时还会把bytes变回string



![img](https://images2015.cnblogs.com/blog/720333/201608/720333-20160805105601403-2095217232.png)

上图仅适用于py2



```pyth
in python2
#-*-coding:utf-8-*-

import sys
print(sys.getdefaultencoding())


msg = "我爱北京天安门"
msg_gb2312 = msg.decode("utf-8").encode("gb2312")
gb2312_to_gbk = msg_gb2312.decode("gbk").encode("gbk")

print(msg)
print(msg_gb2312)
print(gb2312_to_gbk)
```



```pyt
in python3
#-*-coding:gb2312 -*-   #这个也可以去掉

import sys
print(sys.getdefaultencoding())


msg = "我爱北京天安门"
#msg_gb2312 = msg.decode("utf-8").encode("gb2312")
msg_gb2312 = msg.encode("gb2312") #默认就是unicode,不用再decode,喜大普奔
gb2312_to_unicode = msg_gb2312.decode("gb2312")
gb2312_to_utf8 = msg_gb2312.decode("gb2312").encode("utf-8")

print(msg)
print(msg_gb2312)
print(gb2312_to_unicode)
print(gb2312_to_utf8)
```

