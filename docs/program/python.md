# Python
Chinese :utf-8
` #-*- coding:utf-8 -*- `

list []
dict {}
tuple ()

character using ""

identifier:
character number unerline, but start of the identifier can't is number!
Python Retain Character
and	exec not assert	finally	or break	for	pass class	from	print continue	global	raise def
if	return del	import	try elif in while else	is	with except	lambda	yield

variable assignable:
	a = 1
	b =2
	c = 3
	name = "Xiekers";

	a,b,c,name = 1,2,3,"Xiekers";

	a=b=c=1;

print a
print b
print c
print "name"

standard data type:
number
string
tuple
list
dictional

support number type:
int float long complex

print str:
str = "Hello World"
print str 			complete string
print str[1]		first character
print str[2:5]		the second to fifth character input
print str[2:]		input from second character to end
print str[* 2]		twice input str

### list type [] :
can update element content ;
list[1] = 100
### tuple type ():

### dictional type {}:

### Bitwise Operators:
& if two number is same, result is 1
| if two number have a same, result is 1
^ two number is differently ,result is 1
~ << >>

import modules:
```
import modname
import folder.modname
from modname import variable
from modname import *
from folder.modname import * (or modname or variable)
```

__init__.py

```
import modname
import modname2
```

### call method: demo.py
```
import folder.modname or folder_name
```

### Exception Exit

```python
os._exit(0) # 会直接将python程序终止，之后的所有代码都不会继续执行。

# 0为正常退出，其他数值（1-127）为不正常，可抛异常事件供捕获。
sys.exit(0) # 会引发一个异常：SystemExit，若被捕获，将会退出。若捕获此异常，代码继续执行
exit('End')
quit('End')
```

# Module
### request
pip install requests
import requests
HTTP请求：GET、POST、PUT、DELETE、HEAD、OPTIONS

可作为module的文件类型 .py .pyo .pyc .pyd .so .dll

### module来源有3种：
	①Python内置的模块（标准库）；
	②第三方模块；
	③自定义模块。
### module 模块 可看作一个工具类 Class
### package 包 是含有Python模块的文件夹 Project

当一个文件夹下有 __init__.py时，意为该文件夹是一个包（package），其下的多个模块（module）构成一个整体，而这些模块（module）都可通过同一个包（package）导入其他代码中。

其中 __init__.py文件 用于组织包（package），方便管理各个模块之间的引用、控制着包的导入行为。
该文件可以什么内容都不写，即为空文件（为空时，仅仅用import [该包]形式 是什么也做不了的），存在即可，相当于一个标记。



## Python 字符处理

str = ' hello world '
### 去除两端空白字符
str.strip()
### 删除左边空字符
str.rstrip()
### 删除右边空字符
str.lstrip()

## 切割重组 ( 切片 + 拼接)
```python
# str[1:6] 第一个字符开始 第 6 个字符结束 不包括第六个
# str[7:11] 同上
newstr = str[1:6] + str[7:11]
$ helloworld # new string
```

## Python 赋值与copy deepcopy （import copy ,copy.deepcopy）
```python
import copy
a = {'user':'runoob','num':[1,2,3]}
b = a # 直接赋值 a 的任何操作都会影响 b 反之亦然
c = a.copy 直接 copy a 的值修改与 append 都不会影响 但删除会
d = copy.deepcopy(a) 不论增删改 都不会受影响
```

popitem()  删除字典最后一个值