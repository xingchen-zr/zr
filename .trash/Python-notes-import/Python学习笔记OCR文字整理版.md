---
title: Python学习笔记OCR文字整理版
created: 2026-07-07
source: YinXiangBiJi.notes.html
tags: [Python, OCR, 学习笔记, AI应用开发]
---

# Python学习笔记OCR文字整理版

> 说明：这份笔记由 `YinXiangBiJi.notes.html` 中的 97 张截图通过本地 OCR 识别整理而来。OCR 可能存在少量错字，关键代码和概念以你实际课程/代码为准。

## 一、主题整理版

### Python基础语法与类型转换

图片范围：`yinxiangbiji-001.png` 到 `yinxiangbiji-009.png`

重点：

- 字符串、整数、浮点数是最常见的基础类型。
- `input()` 得到的内容默认是字符串；需要计算时要先用 `int()` 或 `float()` 转换。
- Python 3 字符串默认支持 Unicode，源码中有中文时要注意 UTF-8 编码。
- f-string 用来把变量嵌入字符串，例如 `f"我叫{name}，今年{age}岁"`。

OCR关键词：f-string、Unicode、UTF-8、tuple、list

### 元组、列表、字典等容器

图片范围：`yinxiangbiji-010.png` 到 `yinxiangbiji-020.png`

重点：

- 单元素元组必须写成 `(123,)`，不加逗号就只是普通整数。
- 元组和列表都可以用下标索引，从 0 开始。
- 元组本身不可变，但如果元组里放的是列表，列表内部内容仍然可以修改。
- 字典通过 `key` 获取和修改值，写法是 `dict[key]`。
- 合并字典时，如果 key 重复，后面的值会覆盖前面的值。

OCR关键词：tuple、list、dict

### 函数、lambda与代码组织

图片范围：`yinxiangbiji-021.png` 到 `yinxiangbiji-057.png`

重点：

- 函数用于封装重复逻辑，基本结构是 `def 函数名(参数):`。
- `return` 用来把函数内部算出的结果交给外部。
- `lambda` 适合一行简单函数，常和 `sorted(..., key=lambda item: item[1])` 一起使用。
- `if __name__ == "__main__"` 可以限制某些代码只在当前文件直接运行时执行。
- 模块用于拆分代码，避免所有功能堆在一个文件里。

OCR关键词：tuple、list、dict、lambda、return、module

### API调用与大模型应用开发

图片范围：`yinxiangbiji-058.png` 到 `yinxiangbiji-079.png`

重点：

- API 调用本质是：程序向某个服务发送请求，然后拿到返回结果。
- 大模型对话通常包含 `system`、`user`、`assistant` 三类角色。
- `system` 是系统提示词，用来规定 AI 的身份、语气和行为规则。
- 云端大模型通常需要 API Key；本地 Ollama 一般通过 `localhost:11434` 调用。
- 流式输出会一段一段返回内容，需要用 `for chunk in response` 循环接收。

OCR关键词：dict、return、system、API

### SQL与MySQL基础

图片范围：`yinxiangbiji-080.png` 到 `yinxiangbiji-097.png`

重点：

- SQL 是操作数据库的语言，核心是增删改查。
- MySQL 命令行里语句必须用英文分号 `;` 结束。
- `show databases;` 用来查看数据库。
- MySQL 字符串类型常用 `varchar`、`char`、`text`，不是 Python 里的 `str`。
- `char` 固定长度，可能浪费空间；`varchar` 可变长度，更常用。
- `tinyint` 是小整数类型，适合保存状态、性别、年龄等小范围数字。

OCR关键词：list、return、API、varchar、char、tinyint、MySQL、SQL

## 二、当前复习优先级

你现在不需要把这些截图全部重新背一遍。优先级应该是：

1. SQL / MySQL 基础：`show databases;`、建表、字段类型、主键、基础查询。
2. ORM：理解 ORM 如何把 Python 类映射成数据库表。
3. FastAPI + 数据库：把成绩管理系统从 JSON 改成数据库保存。
4. 大模型 API：把 AI 调用接入自己的应用。

暂时只需要回看 Python 基础中自己容易错的部分，比如：类型转换、字典、函数、`return`、`lambda`。

## 三、OCR原文归档

> 下面按图片顺序保留 OCR 文本，方便你核对原图。

### 001. yinxiangbiji-001.png

![[attachments/yinxiangbiji-001.png]]

练习5/9·用f-string拼一句话
题目有问题？
已经给你定义了
name='水哥
和
age=28
请用f-string拼成
我叫水哥，今年28岁。，赋值给变量
intro
，再打印它。
注意：
必须用f-string（不能用+手动拼）
中文逗号
，、句号。，全角
今年和[age}
之间有一个半角空格
输出应该是：

### 002. yinxiangbiji-002.png

![[attachments/yinxiangbiji-002.png]]

1
name
'水哥
7
age = 28
3
#用+
f-string
拼成一句话，赋值给
intro
并打印
4
intro:
(f"我叫{name}，今年{age}岁。‘)
5
print(intro)

### 003. yinxiangbiji-003.png

![[attachments/yinxiangbiji-003.png]]

Unicode通常用两个字节表示一个字符，原有的英文编码从单字节变成双字节，只需要把高字节全部填为0就可以。
因为Python的诞生比Unicode标准发布的时间还要早，所以最早的Python只支持ASCll编码，普通的字符串'ABC
在Python内部都是ASCll编码的。
Python在后来添加了对Unicode的支持，以Unicode表示的字符串用u"...表示。
不过在最新的Python3版本中，字符串是以Unicode编码的，也就是说，Python的字符串支持多语言。就像上面的
例子一样，我的代码中没有加u'..，也能正常显示。
不过由于Python源代码也是一个文本文件，所以，当你的源代码中包含中文的时候，在保存源代码时，就需要务必指
定保存为UTF-8编码。当Python解释器读取源代码时，为了让它按UTF-8编码读取，我们通常在文件开头写上这两
行：
PYTHON
复制
试运行
#!/usr/bin/envpython3
#-*-coding:utf-8-#
第一行注释是为了告诉Linux/OS×系统，这是一个Python可执行程序，Windows系统会忽略这个注释；
第二行注释是为了告诉Python解释器，按照UTF-8编码读取源代码，否则，你在源代码中写的中文输出可能会有乱
码。
申明了UTF-8编码并不意味着你的.py文件就是UTF-8编码的，必须并且要确保文本编辑器正在使用UTF-8without
BOM编码

### 004. yinxiangbiji-004.png

![[attachments/yinxiangbiji-004.png]]

五、基本数据类型转换
Python中基本数据类型转换的方法有下面几个。
方法
说明
int(x [base ])
将x转换为一个整数
float(x)
将x转换到—个浮点数
complex(real [imag ])
创建一个复数
str(x)
将对象×转换为字符串
repr(x)
将对象×转换为表达式字符串
eval(str)
用来计算在字符串中的有效Python表达式，并返回一个对象
tuple(s)
将序列s转换为一个元组
list(s)
将序列s转换为一个列表
chr(x)
将一个整数转换为一个字符
unichr(x)
将一个整数转换为Unicode字符
ord(x)
将一个字符转换为它的整数值
hex(x)
将一个整数转换为一个十六进制字符串
oct(x)
将一个整数转换为一个八进制字符串
注：在Python3里，只有一种整数类型int，表示为长整型，没有python2中的Long。

### 005. yinxiangbiji-005.png

![[attachments/yinxiangbiji-005.png]]

OCLX
注：在Python3里，只有一种整数类型int，表示为长整型，没有python2中的Long。
这里我们可以尝试一下这些函数方法。
比如int（）函数，将符合规则的字符串类型转化为整数。
PYTHON
复制
试运行
str1='100'
str2='300"
print(str1 + str2)
print(int(str1)+ int(str2))
输出结果：
100300
400

### 006. yinxiangbiji-006.png

![[attachments/yinxiangbiji-006.png]]

·练习2/7·索引和切片
题目有问题？
已经给你定义了fruits =['apple'，‘banana'，'cherry'，‘date'，'fig']
请：
1.
用索引print出第3个元素（也就是
cherry
2.用切片
print出fruits[1:4]
输出应该是：
cherry
['banana'，'cherry',‘date']
提示（0/3)
main.py
√已通过 (只读)
全屏
fruits = ['apple', 'banana',
. 'cherry',
'date','fig']
#1.print第·3个元素（索引从0开始）
#=2.~print=切片~fruits[1:4]
print (fruits[2])
print (fruits[1:4])

### 007. yinxiangbiji-007.png

![[attachments/yinxiangbiji-007.png]]

·练习3/7·修改+追加
题目有问题？
已经给你定义了colors=['red'，‘green'，‘blue']
请：
1.把索引1处的元素（green）改成大写GREEN
2.用append在末尾追加
'yellow'
3.
print(colors)
输出应该是：
[’red’，GREEN'，‘blue'，‘yellow']
提示（0/3)
main.py
√已通过 (只读)
全屏
[.anIq. “,uaaus. *.pau,] = suoto)
# 1. colors[1] = 'GREEN"
# 2. colors.append('yellow')
# 3. print(colors)
colors[1] = "GREEN"
colors.append('yellow')
print (colors)

### 008. yinxiangbiji-008.png

![[attachments/yinxiangbiji-008.png]]

教学05/08
6、List（列表）运算符
列表对+和￥的操作符与字符串相似。
号用于组合列表，
号用于重复列表。
Python表达式
结果
描述
len([1,2,3])
3
计算元素个数
[1，2,3]+[4,5,6]
[1，2,3,4,5,6]
组合
['Hi!']*4
['Hi!'，'Hi!'，'Hi!'，'HI!']
复制
3 in[1,2,3]
True
元素是否存在于列表中
for x in [1，2，3]:print（x)
123
迭代

### 009. yinxiangbiji-009.png

![[attachments/yinxiangbiji-009.png]]

最常用的几个：
函数/方法
描述
len(list)
列表元素个数
max(list)
返回列表元素最大值
min(list)
返回列表元素最小值
list.append(obj)
在列表末尾添加新的对象
list.insert(index,obj)
将对象插入指定位置
list.pop()
移除并返回列表最后一个元素
list.pop(i)
移除并返回索引1处的元素
list.remove(obj)
移除列表中第一次出现的指定元素（按值删）
list.index(obj)
从列表中找出某个值第一次匹配的索引位置
list.count(obj)
统计某个元素在列表中出现的次数
list.reverse()
反向列表中元素（原地）
list.sort()
对原列表排序（原地）
记不住没关系，常用的就是
len
append
pop
sort这几个，用多了自然熟。

### 010. yinxiangbiji-010.png

![[attachments/yinxiangbiji-010.png]]

二、tuple(元组)
1、什么是元组(tuple)
上一节刚说了一个有序列表List，现在说另一种有序列表叫元组：tuple。
tuple和List非常类似，但是tuple一旦初始化就不能修改。也就是说元组（tuple）是不可变的—一它没有
append()
insert（）这样的方法，可以通过索引读，但不能赋值。
那么为什么要有tuple呢？
那是因为tuple是不可变的，所以代码更安全。所以建议能用tuple代替list就尽量用tuple。
2、怎样创建元组（tuple）
元组创建很简单，只需要在括号中添加元素，并使用逗号隔开即可。
PYTHON
复制
试运行
tuple1=（'两点水'，'twowter'，'liangdianshui'，123，456)
tuple2=‘两点水'，‘twowter'，'liangdianshui'，123，456#括号也可以省
创建空元组：
PYTHON
复制
试运行
tuple3= ()

### 011. yinxiangbiji-011.png

![[attachments/yinxiangbiji-011.png]]

PYTHON
复制
试运行
tuple4 =(123,)

### 012. yinxiangbiji-012.png

![[attachments/yinxiangbiji-012.png]]

修改元组（tuple）
可能看到这个小标题有人会疑问，上面不是说tuple是不可变的吗？这里怎么又来修改tuple了？
那是因为元组中的元素值不允许直接修改，但我们可以通过修改它内部嵌套的列表的值，间接影响tuple的「内容]。
具体看下面这个例子：
PYTHON
复制
试运行
1ist1=[123，456]
tuple1=（'两点水'，'twowater'，'liangdianshui'，list1)
print(tuplel)
1ist1[0]=789
list1[1] = 100
print(tuple1)
输出的结果：
（'两点水'，'twowater'，'liangdianshui'，[123，456])
（'两点水'，'twowater'，'liangdianshui'，[789，100])

### 013. yinxiangbiji-013.png

![[attachments/yinxiangbiji-013.png]]

6、tuple（元组）运算符
与字符串和列表一样，元组之间可以使用+号和*号进行运算。这就意味着他们可以组合和复制，运算后会生成
一个新的元组。
Python表达式
结果
描述
len((1,2,3))
计算元素个数
(1,2,3)+(4,5,6)
(1,2,3,4,5,6)
连接
（'Hi!',）*4
（iTH‘iTH*iFH‘iTH）
复制
3 in (1,2,3)
True
元素是否存在
for xin (1,2,3):print（x)
123
迭代
7、元组内置函数
函数
描述
len(tuple)
计算元组元素个数
max(tuple)
返回元组中元素最大值
min(tuple)
返回元组中元素最小值
tuple(seq)
把可选代对象（如list）转换为元组

### 014. yinxiangbiji-014.png

![[attachments/yinxiangbiji-014.png]]

·教学03/08·已读
4、修改dict（字典）
向字典添加新内容、修改值，都是用key直接赋值：
PYTHON
复制
试运行
dict1={'liangdianshui'：'111111'，'twowater'：'222222'，'两点水':'333333'}
print(dict1)
#新增一个键值对
dict1['jack']='444444'
print(dict1)
#修改键值对(key已存在时会覆盖)
dict1['liangdianshui']='555555
print(dict1)
输出的结果：
{'liangdianshui'：'111111'，'twowater'：'222222'，'两点水'：'333333'}
{'liangdianshui'：'111111'，'twowater':'222222'，'两点水'：'333333'，'jack'：'444444'}
{'liangdianshui'：'555555'，'twowater'：'222222'，'两点水'：'333333'，'jack'：'444444'}

### 015. yinxiangbiji-015.png

![[attachments/yinxiangbiji-015.png]]

请：
1.新增一项英语"：78
2.把数学的分数改成92
print(scores)
输出应该是：
{语文1：90，数学1：92，英语1：78}
提示（0/2)
main.py
√已通过 (只读）
“全屏
scores ={'语文'：90，‘数学'：85}
# 1.新增scores['英语']= 78
# 2. 修改 scores['数学']= 92
# 3. print(scores)
scores ['英语']= 78
6
scores['数学']= 92
print(scores)
[语文：90，‘数学！：92，‘英语'：78}

### 016. yinxiangbiji-016.png

![[attachments/yinxiangbiji-016.png]]

遍历的顺序就是当初插入的顺序。所以现在大多数情况下，你不再需要
importcollections.OrderedDict，普通
的dict就够用。
·练习3/7·用1合并两个dict
题目有问题？
已经给你定义了：
old ={'a': 1，"b': 2}
new={'b':99,'c:3}
请用把它们合并成merged
(注意：右边覆盖左边，所以‘b应该取99)，然后print（merged）。
输出应该是：
{'a':1,b':99，c':3}
提示(0/3)
main.py
√已通过(只读）
全屏
old = ['a': 1, 'b': 2}
new = {'b': 99, 'c': 3}
# merged = old \| new
# print(merged)
merged = old \| new
print(merged)

### 017. yinxiangbiji-017.png

![[attachments/yinxiangbiji-017.png]]

意思是：把重复的数字去掉，得到不重复的集合。
而：
python
sorted(set(nums))
意思是：
text
先用set(nums）去重
再用sorted（...）排序
最后得到—个list
所以：
python
unique = sorted(set(nums))
print(unique)
输出就是：
python
[1,2, 3,4, 5, 6, 9]
你可以这样记：
text
set()：去重
sorted(）：排序，并返回列表

### 018. yinxiangbiji-018.png

![[attachments/yinxiangbiji-018.png]]

●练习5/7·for+range：求和
题目有问题？
用
for
循环加
range
算1到10的和（包含10），赋给变量
total
然后
print(total)
输出应该是：
55
提示（0/3)
main.py
√已通过（只读）
全屏
total = 0
2
# for n in range(...):
#
total = total + n
4
# print(total)
for n in range(1,11):
6
total = total + n
print(total)

### 019. yinxiangbiji-019.png

![[attachments/yinxiangbiji-019.png]]

3、while 循环
while循环就是「条件为真时一直跑」：
PYTHON
复制
试运行
while条件：
循环体
经典例子—一计算1到100所有整数的和：
PYTHON
复制
试运行
count=1
total=0
while count <= 100:
total=total+ count
count =count +1
print(total)
输出
5050
输出：
5050

### 020. yinxiangbiji-020.png

![[attachments/yinxiangbiji-020.png]]

for和while怎么选？
for：迭代「已知集合」的情况一一遍历list/dict/range，按部就班
while：「条件还没达成就一直做J的情况一一比如等用户输入、读完文件、算到某个值
简单的跑N次J用for+range；条件型的循环用while。

### 021. yinxiangbiji-021.png

![[attachments/yinxiangbiji-021.png]]

1、函数的组成
PYTHON
复制
试运行
def函数名（参数1，参数2，...）：
函数体
return表达式
自定义函数的规则：
用def关键字开头，后接函数名和圆括号（)
任何参数放在圆括号中间
函数内容冒号+缩进起始（跟if、for一样）
return表达式结束函数，并把值返回给调用方
不带表达式的return相当于返回None
例子—一定义一个求和函数：
PYTHON
复制
试运行
def add(num1,num2):
return num1 + num2
#调用
print(add(5,6))
输出：
11

### 022. yinxiangbiji-022.png

![[attachments/yinxiangbiji-022.png]]

·练习2/5·多返回值
题目有问题？
请定义函数
min_max（nums），接收一个list，返回最小值和最大值两个数（用逗号return）。
然后调用
min_max（[3，1，4，1，5，9，2，6]），把结果解包到1o和hi两个变量，再print(1o）和print（hi）
输出应该是：
提示（0/3)
main.py
√已通过 (只读)
全屏
# def min_max(nums) :
2
#
return min(nums), max(nums)
3
# lo, hi = min_max([3, 1, 4, 1, 5, 9, 2, 6])
4
# print(lo)
5
# print(hi)
6
def min_max(nums) :
7
return min(nums), max(nums)
8
lo, hi = min_max([3, 1, 4, 1, 5, 9, 2, 6])
9
print(l0)
10
print(hi)

### 023. yinxiangbiji-023.png

![[attachments/yinxiangbiji-023.png]]

匿名函数vs普通函数
PYTHON
复制
试运行
#普通函数
defadd(a，b):
return a+b
#等价的lambda
add=lambdaa，b:a+b
两种写法效果完全一样。
适合lambda的场景
lambda最常见的用法是当作参数传给别的函数，比如
sorted
的key：
PYTHON
复制试运行
users =[
{'name':'Bob'，'age':25},
{'name':'Carol'，'age':28},
#按年龄排序-临时写个lambda当key
sorted_users = sorted(users,key=lambda u: u['age'])
for u in sorted_users:
print(u['name']，u['age'])
输出：

### 024. yinxiangbiji-024.png

![[attachments/yinxiangbiji-024.png]]

能放进
for
...in
后面的东西，就叫
「可迭代对象]。
字符串、list、tuple、dict、set，
甚至我们后面要讲的
「生成器」，都是可迭代对象。

### 025. yinxiangbiji-025.png

![[attachments/yinxiangbiji-025.png]]

●练习1/5·用for把list累加
题目有问题？
已经给了你一个list：
numbers =[1,2,3,4,5]
请用for
循环把
numbers
里的所有元素加起来，放进变量
total
然后
print(total)
输出应该是：
15
提示(0/3)
main.py
√已通过 (只读)
全屏
1
numbers = [1, 2, 3, 4, 5]
2
total = 0
3
# for n in numbers:
#
total = total + n
5
# print(total)
6
for n in numbers:
total = total + n
8
print(total)

### 026. yinxiangbiji-026.png

![[attachments/yinxiangbiji-026.png]]

上面简单介绍了一下「迭代J。迭代是Python最强大的功能之一，是访问集合元素的一种方式。现在正式进入主题：
迭代器（iterator)。
1、什么是迭代器
“送代器是一个可以记住遍历位置的对象。”
迭代器对象从集合的第一个元素开始访问，直到所有元素被访问完为止。
选代器有两个特点：
只能往前，不能后退。
用iter（）把可迭代对象变成迭代器；用next（）取下一个元素。
字符串、列表、元组都可以用来创建迭代器。迭代器对象既可以用for语句遍历，也可以用next（）函数遍历。

### 027. yinxiangbiji-027.png

![[attachments/yinxiangbiji-027.png]]

3、关键点解释
iter（对象）：把可迭代对象变成迭代器。
next（迭代器）：从迭代器里取出下一个元素。
当迭代器没有元素可取了，再调用
next()
会抛
StopIteration
异常一一所以
whileTrue + try/except
StopIteration
是手动遍历迭代器的标准写法。
其实
for
循环本质上就在帮你做上面这些事，只是它把
StopIteration
给你「悄悄」处理掉了。

### 028. yinxiangbiji-028.png

![[attachments/yinxiangbiji-028.png]]

●练习2/5·用iter和next一个一个取
已通过√
题目有问题？
已经给了你一个list：
nums=[10，20，30]
请：
1.用iter(）把
nums
变成迭代器，赋给变量it。
2.用next（it）连续取3次，分别print出来。
输出应该是：
10
20
30
提示（0 / 3)
main.py
√已通过 (只读)
全屏
nums = [10, 20, 30]
2
# it = iter(nums)
# print(next(it))
#.
nums = [10, 20, 30]
6
it = iter(nums)
print(next(it))
8
print(next(it))
print(next(it))

### 029. yinxiangbiji-029.png

![[attachments/yinxiangbiji-029.png]]

三、List生成式（列表生成式）
1、为什么要有列表生成式
之前我们学过怎么创建一个list。可是有时候用赋值的方式创建list太麻烦了，特别是有规律的list。
比如，要生成一个30个元素的list，里面是1到30这些整数。我们可以这样写：
PYTHON
复制
试运行
list1 = list(range(1，31))
print(list1)
输出：
那如果要生成的不是1-30，而是12～102这样的平方数列表呢？这时候就该「列表生成式」登场了。

### 030. yinxiangbiji-030.png

![[attachments/yinxiangbiji-030.png]]

2、列表生成式的语法
[expr for iter_var in iterable]
[expr for iter_var in iterable if cond_expr]
第一种：迭代iterable里所有内容，把每次的元素放到iter_var
中，再用前面的expr计算出新值，组成
新列表。
第二种：在第一种基础上加了if判断，只有满足条件的元素才会被处理。
要点：因为是list生成式，外层是[］；中间用for循环；可以可选地接if。
3、动手看几个例子
例1：生成1到10的平方
PYTHON
复制
试运行
list1 = [x ￥ x for x in range(1，11)]
print(list1)
输出：
[1，4，9,16,25，36,49,64，81，100]
把要生成的元素××\|放在前面，后面跟for × in range（1，11），就把 list 创建出来了。

### 031. yinxiangbiji-031.png

![[attachments/yinxiangbiji-031.png]]

●练习3/5·列表生成式：偶数的平方
已通过√
题目有问题？
用一行列表生成式，生成1到10（含10）中所有偶数的平方，赋给变量
result，然后
print(result)
输出应该是：
[4，16，36，64，100]
提示（0/3)
main.py
√已通过 (只读)
全屏
# result = [..
in range(...) if ...
# print(result)
result = [x*x for x in range(1,11) if x%2==0]
print(result)

### 032. yinxiangbiji-032.png

![[attachments/yinxiangbiji-032.png]]

四、生成器（generator）
1、为什么需要生成器
通过上面的学习，我们知道用列表生成式可以直接创建一个列表。
但是，受到内存限制，列表容量肯定是有限的。而且，创建一个包含1000万个元素的列表，不仅占用很大的存储空
间；如果我们仅仅需要访问前面几个元素，那后面绝大多数元素占的空间就白白浪费了。
“如果列表元素可以按照某种算法推算出来，那我们能不能在循环的过程中不断推算出后续的元素呢？”
这样就不必创建完整的list，从而节省大量空间。
“在Python中，这种一边循环一边计算的机制，称为生成器（generator）。”
在Python中，使用了yield的函数被称为生成器。
跟普通函数不同的是，生成器是一个返回迭代器的函数，只能用于迭代操作，更简单点理解：生成器就是一种迭代
器。
在调用生成器运行的过程中，每次遇到yield时函数会暂停并保存当前所有的运行信息，返回yield后面的值；
下一次执行next（）方法时，从当前位置继续运行。

### 033. yinxiangbiji-033.png

![[attachments/yinxiangbiji-033.png]]

2、第一种创建方式：把口改成0
最简单的方法就是把一个列表生成式的[］改成（）：
PYTHON
复制
试运行
gen = (x * x for x in range(10))
print(gen)
输出 (地址会不一样)：
<generatorobject<genexpr>at0x0000000002734A40>
创建list和generator的区别仅在于最外层的[］和（）。
但生成器并不真正创建数字列表，而是返回一个生成器对象。这个生成器在每次计算出一个条目后，把这个条目「产
生」（yield）出来。这种「惰性计算（lazyevaluation)」在列表很长时尤其省内存。

### 034. yinxiangbiji-034.png

![[attachments/yinxiangbiji-034.png]]

3、遍历生成器
按我们的思维，遍历当然用
for
循环：
PYTHON
复制
试运行
gen = (x * x for x in range(i0))
fornumingen:
print(num)
也可以用
next()
一个一个取，跟前面的迭代器一模一样。

### 035. yinxiangbiji-035.png

![[attachments/yinxiangbiji-035.png]]

4、第二种创建方式：用函数+yield
实际开发中，大多数生成器都是通过函数来实现的。怎么写？
先看一个普通函数：
PYTHON
复制
试运行
def my_function():
for i in range(10):
print(i)
my_function()
输出0 到9。
如果我们要把它变成生成器，只需要把print（i）改为yieldi就行了：
PYTHON
复制
试运行
def my_function():
for i in range(i0):
yield i
print(my_function())
输出（看到的不是0-9而是generator对象）：
<generator object my_function at Ox...>
成器对象
到值
得用

### 036. yinxiangbiji-036.png

![[attachments/yinxiangbiji-036.png]]

5、generator
的执行流程：暂停+继续
generator
和普通函数的执行流程不一样：
普通函数：顺序执行，遇到
return
或最后一行就返回。
generator：每次调用
next()
时执行，遇到
yield
就暂停，下次再调用
next()
时从上次的
yield
后面继
续。

### 037. yinxiangbiji-037.png

![[attachments/yinxiangbiji-037.png]]

●练习4/5：写一个生成器函数
已通过√
题目有问题？
请定义一个生成器函数
（count_up(n），它依次yield出1，2，
然后用for循环遍历
count_up(5），把每个值print\|出来(每个数占一行)。
输出应该是：
2
3
5
提示（0/3)
main.py
√已通过 (只读)
全屏
1
# def count_up(n):
2
#
for i in range(1, n + 1):
3
#
yield i
4
#
5
# for x in count_up(5):
6
#
print(x)
def count_up(n):
8
for n in range(1, n + 1):
9
yield n
10
for n in count_up(5):
11
print(n)
12

### 038. yinxiangbiji-038.png

![[attachments/yinxiangbiji-038.png]]

1、反向迭代
练
用
教
反向迭代也是常有的需求。比如最开始的例子里，我们顺序输出list的元素1到5：
练用
PYTHON
复制
试运行
教三
1ist1=[1，2，3，4，5]
for numl in listl:
练列
print(num1，end='')
教四
那如果想从5到1呢？很简单，Python中有内置的函数
reversed()
练写
PYTHON
复制
试运行
教五
1ist1=[1，2，3，4，5]
for numl in reversed(listi):
练
print(numl， end= ')
用
输出：
54321

### 039. yinxiangbiji-039.png

![[attachments/yinxiangbiji-039.png]]

2、同时迭代多个序列：zip0
PYTHON
复制
试运行
names =['liangdianshui'，'twowater'，'两点水'］
ages =[18，19，20]
for name,age in zip(names, ages):
print(name， age)
输出：
liangdianshui18
twowater 19
两点水20
zip(a，b）会生成一个返回元组（x，y）的迭代器，其中x 来自a，「y来自丨b。一旦其中某个序列到了结
尾，迭代就结束。因此迭代长度跟参数中最短序列的长度一致。
利用zip（），我们还可以把一个key列表和一个value列表组合成dict:

### 040. yinxiangbiji-040.png

![[attachments/yinxiangbiji-040.png]]

3、还有个常用工具：enumerate
写for的时候，如果你既要值又要下标，可以用
enumerate()
PYTHON
复制
试运行
fruits=［'苹果'，‘香蕉'，‘橘子'］
for i，fruitinenumerate(fruits):
print(i，fruit)
输出：
0苹果
1 香蕉
2橘子
enumerate（可迭代对象）返回一个丨（下标，元素）的迭代器，省去你自己维护一个计数变量的麻烦。

### 041. yinxiangbiji-041.png

![[attachments/yinxiangbiji-041.png]]

●练习5/5·用zip配对两个list
已通过√
题目有问题？
已经给了你两个list:
names =['Alice'，'Bob'，'Cathy']
ages =[18,19，20]
请用zip（）把它们配成对，再用for循环每一对都按
name age
的格式print出来(中间一个空格)。
输出应该是：
Alice 18
Bob 19
Cathy20
提示 (0/ 4)
main.py
√已通过 (只读)
全屏
names = ['Alice', 'Bob', 'Cathy']
2
ages = [18, 19, 20]
3
# for name, age in zip(names, ages):
#
print(name, age)
5
for name, age in zip(names, ages):
6
print(name, age)

### 042. yinxiangbiji-042.png

![[attachments/yinxiangbiji-042.png]]

1、怎么理解类？
类是什么？最直观的理解：类是变量和函数的集合。
类
属性1
数据 （变量）
属性2
方法1
←行为 (函数)
方法2
我们把「同一性质」的数据和行为打包到一起，方便重复使用。

### 043. yinxiangbiji-043.png

![[attachments/yinxiangbiji-043.png]]

3、创建对象（实例化）+调用方法
PYTHON
复制
试运行
class Person:
species ='人类
def greet(self):
print(你好)
#实例化(创建一个Person 对象)
p = Person()
#通过对象访问属性
print(p.species)
#通过对象调用方法
p.greet()
输出：
人类
你好

### 044. yinxiangbiji-044.png

![[attachments/yinxiangbiji-044.png]]

·练习1/4·定义你的第一个类
已通过√
题目有问题？
请定义一个类Animal，类里有一个方法bark，方法体打印
'某种声音！
然后：
1.实例化Animal（）赋给
2.调用
a.bark()
输出应该是：
某种声音
提示 (0/ 3)
main.py
√已通过 (只读)
全屏
1
# class Animal:
2
#
def bark(self) :
3
#
print('某种声音")
4
# a = Animal()
5
# a.bark()
6
class Animal:
7
bark ='某种声音!
8
a= Animal()
9
print(a.bark)
10

### 045. yinxiangbiji-045.png

![[attachments/yinxiangbiji-045.png]]

面
●教学03／05·已读
二、初始化函数
__init_.
上一节我们的 Person
没有名字、没有年龄一一所有Person
都长得一模一样。
实际中我们希望每个对象都带自己的属性一一比如「张三18岁」、「李四25岁」。这时候要用初始化函数
_init.
1、什么是__init_-
_init__在你创建对象时自动被调用一一专门用来初始化新对象的属性。
写法：
PYTHON
复制
试运行
class 类名：
def__init__（self，参数1，参数2，...）:
self.属性1=参数1
self.属性2=参数2
注意：
init__前后各两个下划线一一不是一个
第一个参数永远是
self
在self上设置的属性就是这个对象专属的（不同对象互不影响）

### 046. yinxiangbiji-046.png

![[attachments/yinxiangbiji-046.png]]

PYTHON
复制
试运行
class Person:
def __init__(self, name， age):
self.name=name
self.age = age
def greet(self):
print(f'我叫 {self.name}，今年 {self.age} 岁')
#实例化时传入参数
p1=Person('张三'，18)
p2=Person（'李四'，25)
p1.greet()
p2.greet()
输出：
我叫张三，今年18岁
我叫李四，今年25岁

### 047. yinxiangbiji-047.png

![[attachments/yinxiangbiji-047.png]]

●练习2/4·用__init__给对象传参
题目有问题？
请定义类
Person
Linit__接收name和age]，分别保存到self.name
和
self.age
方法greet]：打印f'我叫{self.name}，今年{self.age} 岁！
然后实例化Person（'张三'，18）
赋给p]，调用p.greet（）
输出应该是：
我叫张三，今年18岁
提示（0/3)
main.py
√已通过 (只读)
全屏
1
#
class Person:
2
#
def _init__(self, name, age):
3
#
self.name = name
4
#
self.age = age
5
#
def greet(self):
6
#
print(f'我叫 {self.name}，今年{self.age} 岁')
7
# p = Person('张三'，18)
8
# p.greet()
9
class Person:
10
def _init_(self, name, age):
11
self.name = name
12
self.age = age
13
def greet(self):
14
returnprint(f'我叫 {self.name}，今年 {self.age} 岁')
15
p = Person('张三'，18)
16
p.greet()

### 048. yinxiangbiji-048.png

![[attachments/yinxiangbiji-048.png]]

「继承」就是子类自动获得父类的所有属性和方法一一可以再加自己的，也可以「重写」父类的。
1、定义继承
PYTHON
复制
试运行
class 子类(父类)：
例子—一
Student
继承
Person
PYTHON
复制
试运行
class Person:
def __init__(self， name， age):
self.name = name
self.age = age
def greet(self):
print(f'我叫{self.name}，今年{self.age}岁')
classStudent(Person):
pass
#啥都不加，但已经继承了__init__和greet
s=Student（'小明'，16)
s.greet()

### 049. yinxiangbiji-049.png

![[attachments/yinxiangbiji-049.png]]

2、子类加自己的属性/方法
PYTHON
复制
试运行
class Student(Person):
def -_init__(self, name, age, school):
super().__init__(name,age)
#调父类的__init_-
self.school = school
def study(self):
print(f'{self.name}正在{self.school} 学习')
S=Student（'小明'，16，‘希望小学"）
s.greet()
s.study()
输出：
我叫小明，今年16岁
小明正在希望小学学习

### 050. yinxiangbiji-050.png

![[attachments/yinxiangbiji-050.png]]

多态的概念其实不难理解：对不同类型的对象做相同的操作，会根据类型的不同表现出不同的行为。
简单说就是「重写父类的方法」一一子类的同名方法盖掉父类的。
例子
PYTHON
复制
试运行
class Animal:
def sound(self):
print('一些声音)
classDog(Animal):
def sound(self):
print('汪汪')
class Cat(Animal):
def sound(self):
print(喵喵')
#注意：调用方都是.sound（），但是行为完全不同
animals=[Dog(），Cat()，Animal()]
forainanimals:
a.sound()
输出：
汪汪
喵喵
一些声音
调用
.sound（）时，实际执行的是哪段代码取决于对象的真实类型。这就是多态一一同一个方法名，不同的类有不同

### 051. yinxiangbiji-051.png

![[attachments/yinxiangbiji-051.png]]

封装函数用def，封装类用
class，封装模块不需要任何关键字-
“在Python中，一个·py文件就是一个模块（Module)。”
为什么要用模块？
1.提高可维护性一一按功能拆分到不同文件，不再是一个巨型脚本
2.代码复用一一别人写好的模块可以直接拿来用，不必从零造轮子
3.避免命名冲突一一相同名字的函数和变量可以分别存在不同模块中
Python自带了很多非常有用的模块（叫标准库），装好Python就能用，比如
math
random
datetime
json
oS，
sys
模块大致分两类：
标准库模块：Python自带，比如
math
自定义模块：你自己写的·Py文件
第三方模块：别人发布到PyPl上、用pipinstall
安装的

### 052. yinxiangbiji-052.png

![[attachments/yinxiangbiji-052.png]]

1、import
最基本的语法：
PYTHON
复制
试运行
import 模块名
也可以一次导入多个：
PYTHON
复制
试运行
import module1，module2，module3
例子一一使用标准库
math模块的pi属性：
PYTHON
复制
试运行
import math
print(math.pi)

### 053. yinxiangbiji-053.png

![[attachments/yinxiangbiji-053.png]]

2、 from --- import
import math
只是把
math这个模块整体引进来，使用里面的东西必须写前缀（math.pi）
math.sqrt(...))。
如果只想用模块里的某一个函数或属性，可以直接挑出来导入：
PYTHON
复制
■试运行
from 模块名import 名字1，名字2，.
对比一下：
PYTHON
复制
试运行
#写法1：import整个模块
import math
print(math.pi)
#必须写math.前缀
#写法2：from···import直接拎出来
from math import pi
print(pi)
#不用写 math.
两种都可以，看场景：
用得多/怕重名→
import math
只用一两个、想少打字→
>from math import pi, sqrt

### 054. yinxiangbiji-054.png

![[attachments/yinxiangbiji-054.png]]

4、起别名（as)
模块名太长？可以起别名：
PYTHON
复制
试运行
importdatetime as dt
today = dt.date(2026，1，1)
print(today)
数据科学圈最常见的两个：
PYTHON
复制
试运行
import numpy as np
import pandas as pd

### 055. yinxiangbiji-055.png

![[attachments/yinxiangbiji-055.png]]

1、定义
主模块：被直接运行的那个［·py】文件
非主模块：被别的模块import进来的那个
类比：你python a.py」，
就是主模块；
a.py
里如果import b，b就是非主模块。
a
属性
._name_-
怎么在代码里判断当前模块到底是被直接运行还是被别人import的？
Python给每个模块都设置了一个特殊变量
._name._.
模块被直接运行时，
name...
的值就是字符串
main_-
模块被import时，
name_
的值就是模块名本身（比如
'mymod'
所以经典写法是：
PYTHON
复制
试运行
# mymod.py
def main():
print('正在运行main逻辑'）
if
._name.
main
main()

### 056. yinxiangbiji-056.png

![[attachments/yinxiangbiji-056.png]]

模块多了，难免会出现重名一一你写了一个
utils.py，别人也写了一个
utils.py，怎么办？
Python的解决方案是包（Package）：用目录来组织模块，不同目录下可以有同名模块。
一个典型的包结构：
myproject/
com/
— learn/
module/
-_init__.py
1name.py
←完整名是com.learn.module.lname
注意每个目录里都有一个-_init__·py」：
“这个文件必须存在（哪怕是空的），Python才会把这个目录当成包，而不是普通目录。
init__·py本身也是一个模块一一它对应的模块名就是包名本身。”
导入包里的模块时，用点号一层层进去：
PYTHON
复制
试运行
import com.learn.module.lname
from com.learn.moduleimport lname
from com.learn.module.lname import some_func
“现代Python（3.3+）也支持命名空间包-一不强制要求-_init__·py。但传统包结构仍然最常见，初学阶段记
住「目录里要有
-_init__·py」就够了。”

### 057. yinxiangbiji-057.png

![[attachments/yinxiangbiji-057.png]]

学过Java/C++的同学知道，类成员可以标
public
private
Python没有真正的访问控制关键字，但有一套约定俗成的命名规则：
命名
含义
例子
abc
MyClass
公开（public)，任何地方都可以用
普通函数、变量
abc
「内部使用」(约定），外部不应该直接引用
内部辅助函数
abc
名字改写（namemangling），主要用于类内部
类的私有属性
abc_.
特殊变量/魔法方法
name...
init...

### 058. yinxiangbiji-058.png

![[attachments/yinxiangbiji-058.png]]

1、math一一数学函数
PYTHON
复制
试运行
import math
print(math.pi)
#圆周率3.141592653589793
print(math.e)
#自然常数e
print(math.sqrt(16))
#平方根→4.0
print(math.floor(3.7))
#向下取整→3
print(math.ceil(3.2))
#向上取整→4
2、random一一随机数
PYTHON
复制
试运行
import random
random.seed(42)
#固定随机种子，结果可复现
print(random.randint(1，10)）#1-10之间的随机整数(含两端)
print（random.choice（['A'，'B'，'C'])）#随机选一个
“在练习里我们会用
random.seed（...）固定结果一一这样判分时输出就稳定了。”

### 059. yinxiangbiji-059.png

![[attachments/yinxiangbiji-059.png]]

3、datetime一一日期与时间
PYTHON
复制
试运行
fromdatetime importdate，datetime
d = date(2026，1，1)
print(d.year，d.month，d.day)
#202611
now = datetime(2026，1，1，12，30，0)
print(now)
#2026-01-0112:30:00

### 060. yinxiangbiji-060.png

![[attachments/yinxiangbiji-060.png]]

4、 json 一一 JSON 序列化
把Python字典/列表转成JSON字符串：
PYTHON
复制
试运行
import json
data={'name':'Alice'，'age':18}
print(json.dumps(data))
输出：
{"name":"Alice"，"age":18}
反过来—一把JSON字符串解析回Python对象：
PYTHON
复制
试运行
import json
=
obj = json.loads(s)
print(obj['name'])
#Alice

### 061. yinxiangbiji-061.png

![[attachments/yinxiangbiji-061.png]]

#相对路径：从当前文件所在目录开始查找
from utils.my_fun import log_separator1，log_separator3
#绝对路径：从项目的根目录下开始查找
from第二章.utils.my_funimportlog_separator1，log_separator3

### 062. yinxiangbiji-062.png

![[attachments/yinxiangbiji-062.png]]

#注意：如果要通过fromutilsimport导入包下的所有模块，需要__init__·py文件中添加__all__=[]
fromutilsimport*

### 063. yinxiangbiji-063.png

![[attachments/yinxiangbiji-063.png]]

多一句没有，少一句不行，用更短的时间，教会更实用的技术
黑马程序员
www.itheima.com
类的定义
定义类的语法如下：
定义类时指定实例属性
#定义类
#定义类
class类名：
class Car:
def
._init__]
（self，参数列表）：
def __init__(self, c_brand, c_name, c_price) :
self.属性名=参数值
self.brand=c_brand
self.属性名=参数值
self.name = c_name
self.price=c_price
#创建对象
#创建对象
对象名=类名（参数列表）
c1=Car("BMW"，"X5"，500000)
print(c1.-_dict__)
_init__：初始化方法，对象创建后自动调用，主要用于设置对象的初始状态（设置对象属性）
说明：定义在类的外面的称之为函数，定义在类中的函数称之为方法。

### 064. yinxiangbiji-064.png

![[attachments/yinxiangbiji-064.png]]

多一句没有，少一句不行，用更短的时间，教会更实用的技术
黑马程序员
www.itheima.com
类的定义
定义类的语法如下:
定义类时指定实例属性
#定义类
#定义类
class类名：
class Car:
def
-_init_
self
参数列表)：
def __init__(self，c_brand,c_name,c_price):
self.属性名=参数值
self.brand=c_brand
self.属性名=参数值
self.name=c_name
self.price=c_price
#创建对象
#创建对象
对象名=类名（参数列表）
c1 = Car("BMW"，"X5"，500000)
print(c1.-_dict_-)
self：方法的第一个参数，表示当前创建的实例对象
__init__：初始化方法，对象创建后自动调用，主要用于设置对象的初始状态（设置对象属性）
说明：定义在类的外面的称之为函数，定义在类中的函数称之为方法。

### 065. yinxiangbiji-065.png

![[attachments/yinxiangbiji-065.png]]

黑马程序员
多一句没有，少一句不行，用更短的时间，教会更实用的技术
www.itheima.com
魔法方法
魔法方法是指Python中提供的以双下划线开头和结尾的特殊方法，用于定义类的特殊行为，比如：__init__。
魔法方法是不需要我们手动调用的，Python会在合适的时机自动调用。
魔法方法
描述
_int--
初始化方法
._str_.
字符串表示的方法
._eq_-
比较两个对象是否相等（equal）
支持比较两个对象的大小（小于(lessthan），小于等于(lessthanorequal），大于(greater
_lt_- ， -_le_- ， --gt_- ， --ge_.
than)，大于等于(greater thanorequal))

### 066. yinxiangbiji-066.png

![[attachments/yinxiangbiji-066.png]]

PowerPoint幻灯片放映-第3章-Python项目实战之Al应用.pptx-PowerPoint
口
黑马程序员
多一句没有，少一句不行，用更短的时间，教会更实用的技术
www.itheima.com
网络基础知识-IP
IP地址可以理解为就是设备在互联网中的地址（唯一身份证），每一个连入网络的设备都有一个自己的IP地址，用来定位设
备在互联网中的位置。
IPv4地址：32位二进制
IPv6地址：128位二进制
132.12.86.125
十进制
10000100
00001100
01010110
01111101
二进制
0~255
0~255
0~255
0~255
注意：127.0.0.1是一个非常特殊的IP地址，表示的是本机地址（也称为本地回环地址）。

### 067. yinxiangbiji-067.png

![[attachments/yinxiangbiji-067.png]]

多一句没有，少一句不行，用更短的时间，教会更实用的技术
黑马程序员
www.itheima.com
HTTP协议
概念：HyperTextTransferProtocol，超文本传输协议，规定了客户端和服务器之间数据传输的规则。（只有
在请求及响应中都遵循了统一的规则，服务端才能读懂客户端发送来的请求，客户端才能解析服务端响应的结果）
请求
HTTP协议
响应数据
响应
请求数据
特点：
1。基于文本的协议：请求和响应的部分的协议内容为文本格式，底层通过TCP协议传输，稳定性强。
2。基于请求-响应模型：一次请求对应一次响应，必须由客户端先发起请求，服务端才会返回响应。
3。无状态：服务端不会记忆与客户端的历史交互信息，每次请求-响应都是独立的。

### 068. yinxiangbiji-068.png

![[attachments/yinxiangbiji-068.png]]

1。TCP/IP四层网络模型？
应用层、传输层、网络层、网络接口层
小结
2。什么是HTTP协议？有什么特点?
超文本传输协议，规定了客户端与服务端数据传输的规则
基于文本的协议、基于请求响应模型、无状态

### 069. yinxiangbiji-069.png

![[attachments/yinxiangbiji-069.png]]

黑马程序员
多一句没有，少一句不行，用更短的时间，教会更实用的技术
www.itheima.com
HTTP协议-请求数据格式
POST/api/courses HTTP/1.1
请求行（请求方式、资源路径、协议）
Accept:application/json，text/plain，*/*
Accept-Encoding: gzip, deflate, br,zstd
Accept-Language:zh-CN,zh;q=0.9,en;q=0.8,en-GB;q=0.7,en-US;q=0.6
Connection:keep-alive
Content-Length:139
Content-Type:application/json
Host:1ocalhost:90
请求头（格式key：value）
Origin:http://localhost:90
Referer:http://localhost:90/resource/course
Sec-Fetch-Dest:empty
Sec-Fetch-Mode:cors
Sec-Fetch-Site:same-origin
User-Agent:Mozi11a/5.0 (Windows NT 10.0;Win64; x64) Chrome/143.0.0.0
["phone':"18808088080","channel":1,"name":"虎饱","gender":1,"age":"32"}
请求体（请求参数部分，GET方式没有，POST可以有）
请求方式：
·GET：请求参数在请求行中，没有请求体。如：/api/courses?name=Python&status=l。GET请求请求参数大小在浏览器中是有限制的。
·POST：请求参数在请求体中，POST请求大小是没有限制的。

### 070. yinxiangbiji-070.png

![[attachments/yinxiangbiji-070.png]]

多一句没有，少一句不行，用更短的时间，教会更实用的技术
黑马程序员
www.itheima.com
HTTP协议-响应数据格式
HTTP/1.1
200
响应行（协议、状态码）
Server: nginx/1.24.0
Date:Tue,16[ec 202512:38:08GMT
Content-Type:application/json
响应头（格式key：value）
Transfer-Encoding:chunked
Connection:keep-alive
{code: 1, msg:
"success",data: null}
200：客户端请求成功
400：请求参数错误
404：请求资源不存在，url输入有误，或者网站资源被删除了
500：服务器发生了不可预期的错误

### 071. yinxiangbiji-071.png

![[attachments/yinxiangbiji-071.png]]

HTTP协议中请求及响应数据的数据格式？
请求格式：请求行(请求方式、资源路径）、请求头(key:value）、请求体(post方式)
响应格式：响应行(状态码)、响应头(key:value)、响应体

### 072. yinxiangbiji-072.png

![[attachments/yinxiangbiji-072.png]]

f"role":
system
content": "You are a helpful
.assistant."},
f"role":
user
content":"Hello!"}

### 073. yinxiangbiji-073.png

![[attachments/yinxiangbiji-073.png]]

Path参数
说明
必填
gt/ge
大于/大于等于
lt/le
小于/小于等于
description
描述
min_length
max_length
长度限制

### 074. yinxiangbiji-074.png

![[attachments/yinxiangbiji-074.png]]

1
from pydantic import BaseModel,Field
2
from fastapi import FastAPI
3
from fastapi.responses import
HTMLResponse
4
5
app = FastAPI()
6
7
class AddBook(BaseModel):
8
book_name:str = Field(...,min_length=2,max_length=10)
9
book_author:str = Field(min_length=2,max_length=10)
10
book_publisher:str = Field(default='黑马出版社')
11
book_price:float = Field(...,gt=0)
12
13
@app.post("/new_book")
14
async def new_book(book:AddBook):
15
return book

### 075. yinxiangbiji-075.png

![[attachments/yinxiangbiji-075.png]]

参数分类
路径参数
查询参数
请求体
位置：URL路径的一部分
位置：URL？之后
位置：HTTP请求的消息体
/book/{id}
k1=v1&k2=v2
(body）中
作用：指向唯一的、特定的
作用：对资源集合进行过滤、
作用：创建、更新资源
资源
排序、分页等操作
携带大量数据，如：
方法：GET
方法：GET
JSON
方法：POST、PUT等
璃继数字人
才增训喷家

### 076. yinxiangbiji-076.png

![[attachments/yinxiangbiji-076.png]]

黑马程序员
多一句没有，少一句不行，用更短时间，教会更实用的技术！
www.itheima.com
响应类型设置方式
装饰器中指定响应类
返回响应对象
场景：固定返回类型（HTML、纯文本等）
场景：文件下载、图片、流式响应
@app.get("/htm",response_class=HTMLResponse)
@app-get("/file")
async def get_html():
async def get_file():
return"<h1>这是标题</h1>"
file_path="./files/1.jpeg"
return FileResponse(file_path)
确级数字
家

### 077. yinxiangbiji-077.png

![[attachments/yinxiangbiji-077.png]]

1
from pydantic import BaseModel,Field
2
from fastapi import FastAPI
3
from fastapi.responses import
HTMLResponse
4
5
app = FastAPI()
6
7
class AddBook(BaseModel):
8
book_name:str = Field(...,min_length=2,max_length=10)
9
book_author:str = Field(min_length=2,max_length=10)
10
book_publisher:str = Field(default='黑马出版社')
11
book_price:float = Field(...,gt=0)
12
13
@app.post("/new_book")
14
async def new_book(book:AddBook):
15
return book

### 078. yinxiangbiji-078.png

![[attachments/yinxiangbiji-078.png]]

响应文件格式
FileResponse是FastAPI提供的专门用于高效返回文件内容（如图片、PDF、Excel、音视频等）的响应类。它能够智能处理文件路径
、媒体类型推断、范围请求和缓存头部，是服务静态文件的推荐方式。
from fastapi.responses import FileResponse
@app.get("/file")
async def get_file():
file_path="./files/1.jpeg"
return FileResponse(file_path)

### 079. yinxiangbiji-079.png

![[attachments/yinxiangbiji-079.png]]

黑马程序员
多一句没有，少一句不行，用更短时间，教会更实用的技术！
www.itheima.com
依赖注入应用场景
处理请求参数
共享业务逻辑
从请求中提取和验证参数
抽取封装多个路由公用的逻辑代码
111
（路径参数、查询参数、请求体）
共享数据库连接
安全和认证
管理数据库会话的创建、使用、
验证用户身份、检查权限和角色要
关闭
求等
稳级数字人才训喷家

### 080. yinxiangbiji-080.png

![[attachments/yinxiangbiji-080.png]]

黑马程序员
多一句没有，少一句不行，用更短时间，教会更实用的技术！
www.itheima.com
使用依赖注入系统来共享通用逻辑，避免代码重复
创建依赖项
asyncdefcommon_parameters(
skip:int=Query(0,ge=0),
limit: int =Query(10,le=60)
：
return{
fromfastapiimportDepends
导入Depends
"skip": skip,
"limit":limit
声明依赖项
@app.get(news/news_list"")
async def get_news_list(
commons=Depends(common_parameters)
return commons
马种经数字人才培训特家
20

### 081. yinxiangbiji-081.png

![[attachments/yinxiangbiji-081.png]]

工具
来自哪里
主要作用
适合用在
Path
fastapi
校验路径参数
/scores/{name}、/books/{i
{p
Quer
fastapi
校验查询参数
?keyword=xxx&page=1
y
Fiel
pydanti
校验请求体里的字
JSONBody
段
d

### 082. yinxiangbiji-082.png

![[attachments/yinxiangbiji-082.png]]

1.MySQL下载及安装
MySQL社区版
2.MySQL启动
net start mysql80
net stop mysql80
3.MySQL客户端连接
MySQL自带的客户端命令行
mysql [-h 127.0.0.1] [-P 3306]  -u root -p
4.MySQL数据模型
数据库
表

### 083. yinxiangbiji-083.png

![[attachments/yinxiangbiji-083.png]]

SQL
SQL分类
分类
全称
说明
DDL
DataDefinition Language
数据定义语言，用来定义数据库对象(数据库，表，字段)
DML
Data Manipulation Language
数据操作语言，用来对数据库表中的数据进行增删改
DQL
Data Query Language
数据查询语言，用来查询数据库中表的记录
DCL
Data Control Language
数据控制语言，用来创建数据库用户、控制数据库的访问权限

### 084. yinxiangbiji-084.png

![[attachments/yinxiangbiji-084.png]]

SQL
DDL-表操作-查询
查询当前数据库所有表
SHOWTABLES;
查询表结构
DESC表名；
查询指定表的建表语句
SHOWCREATETABLE表名；

### 085. yinxiangbiji-085.png

![[attachments/yinxiangbiji-085.png]]

SQL
DDL-表操作-创建
CREATETABLE表名（
字段1字段1类型［COMMENT字段1注释］，
字段2字段2类型[COMMENT字段2注释]，
字段3字段3类型[COMMENT字段3注释]，
字段n字段n类型[COMMENT字段n注释]
)[COMMENT表注释];

### 086. yinxiangbiji-086.png

![[attachments/yinxiangbiji-086.png]]

分类
类型
大小
有符号（SIGNED）范围
无符号（UNSIGNED）范围
描述
TINYINT
1byte
(-128,127)
(0,255)
小整数值
SMALLINT
2bytes
(-32768,32767)
(0,65535)
大整数值
MEDIUMINT
3 bytes
(-8388608,8388607)
(0,16777215)
大整数值
INT或INTEGER
4
bytes
(-2147483648.2147483647)
(0，4294967295)
大整数值
数值类型
BIGINT
8
bytes
（-2~63.2^63-1)
(0，2~64-1)
极大整数值
FLOAT
4
bytes
(-3.402823466 E+38.3.402823466351E+38)
0和（1.175494351E-38.3.402823466B+38)
单精度浮点数值
DOUBLE
8 bytes
(-1.7976931348623157 E+308,1.7976931348623157 E+308)
0和 （2.2250738585072014E-308,1.7976931348623157 E+308)
双精度浮点数值
DECIMAL
依赖于M（精度）和D（标度）的值
依赖于M（精度）和D（标度）的值
小数值（精确定点数）

### 087. yinxiangbiji-087.png

![[attachments/yinxiangbiji-087.png]]

分类
类型
大小
描述
CHAR
0-255 bytes
定长字符串
VARCHAR
0-65535 bytes
变长字符串
TINYBLOB
0-255 bytes
不超过255个字符的二进制数据
TINYTEXT
0-255 bytes
短文本字符串
BLOB
0-65 535 bytes
二进制形式的长文本数据
字符串类型
TEXT
0-65 535bytes
长文本数据
MEDIUMBLOB
0-16 777 215 bytes
二进制形式的中等长度文本数据
MEDIUMTEXT
0-16 777 215 bytes
中等长度文本数据
LONGBLOB
0-4294967 295 bytes
二进制形式的极大文本数据
LONGTEXT
0-4294967295bytes
极大文本数据

### 088. yinxiangbiji-088.png

![[attachments/yinxiangbiji-088.png]]

分类
类型
大小
范围
格式
描述
DATE
3
1000-01-01至9999-12-31
GG-NNXX
日期值
TIME
3
-838:59:59至838:59:59
HH:MM:SS
时间值或持续时间
日期类型
YEAR
1
1901至
2155
年份值
DATETIME
8
1000-01-0100:00:00至9999-12-3123:59:59
YYYY-MM-DD HH:MM:SS
混合日期和时间值
TIMESTAMP
1970-01-0100:00:01至2038-01-1903:14:07
YYYY-MM-DD HH:MM:SS
混合日期和时间值，时间截

### 089. yinxiangbiji-089.png

![[attachments/yinxiangbiji-089.png]]

SQL
DDL-表操作-修改
添加字段
ALTERTABLE表名ADD字段名类型（长度）[COMMENT注释][约束]；

### 090. yinxiangbiji-090.png

![[attachments/yinxiangbiji-090.png]]

DDL-表操作-修改
修改数据类型
ALTERTABLE表名MODIFY字段名新数据类型（长度）
修改字段名和字段类型
ALTERTABLE表名CHANGEI旧字段名新字段名类型（长度）[COMMENT注释][约束]；

### 091. yinxiangbiji-091.png

![[attachments/yinxiangbiji-091.png]]

SQL
DDL-表操作-修改
删除字段
ALTERTABLE表名DROP字段名

### 092. yinxiangbiji-092.png

![[attachments/yinxiangbiji-092.png]]

DDL-表操作-修改
修改表名
ALTERTABLE表名RENAMETO新表名

### 093. yinxiangbiji-093.png

![[attachments/yinxiangbiji-093.png]]

DDL-表操作-删除
删除表
DROPTABE[IFEXISTS]表名;
删除指定表，并重新创建该表
TRUNCATETABLE表名；

### 094. yinxiangbiji-094.png

![[attachments/yinxiangbiji-094.png]]

1.DDL-数据库操作
SHOW DATABASES;
CREATEDATABASE数据库名；
USE数据库名；
SELECTDATABASEO;
DROPDATABASE数据库名：
2.DDL-表操作
SHOW TABLES;
CREATETABLE表名（字段字段类型，字段字段类型）
DESC表名；
SHOWCREATETABLE表名；
ALTERTABLE表名ADD/MODIFY/CHANGE/DROP/RENAMETO..；
DROPTABLE表名；

### 095. yinxiangbiji-095.png

![[attachments/yinxiangbiji-095.png]]

SQL
DML-添加数据
给指定字段添加数据
INSERTINTO表名（字段名1，字段名2,.)VALUES（值1，值2,..);
2.给全部字段添加数据
INSERTINTO表名VALUES（值1，值2,..);
3.批量添加数据
INSERTINTO表名（字段名1,字段名2,..）VALUES（值1,值2,.),（值1,值2,...)（值1,值2..);；
INSERTINTO表名VALUES（值1，值2,..)（值1,值2,.)（值1,值2,..)；

### 096. yinxiangbiji-096.png

![[attachments/yinxiangbiji-096.png]]

修改id为1的数据，将nane修改为itheima
update employee set name ='itheima
whereid=1;
修改id为1的数据，将name修改为小昭，gender修改为女
将所有的员工入职日期修改为2008-01-01
update
employee set entrydate ='2008-01-01';

### 097. yinxiangbiji-097.png

![[attachments/yinxiangbiji-097.png]]

DML-删除数据
DELETEFROM表名[WHERE条件]
注意：
DELETE语句的条件可以有，也可以没有，如果没有条件，则会删除整张表的所有数据。
DELETE语句不能删除某一个字段的值（可以使用UPDATE)。
