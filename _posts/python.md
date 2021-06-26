## 题型

**1-6章**

选择题 10 1‘

判断题 10 1‘

填空题 30 1’

代码理解题 30 3‘——特殊表达式（嵌套加条件表达式）

代码写作题 20 10’——代码模块

## 复习

### 第一章

语言特性

基础知识（对象）

python变量（基于值的内存管理/字符串引号/数字/内置函数）

### 第二章 python序列（40%）

#### 列表

- 创建：注意字符串

  ```python
  aList = list('hello world')
  print(aList)
  ['h', 'e', 'l', 'l', 'o', ' ', 'w', 'o', 'r', 'l', 'd']
  ```

  2中xrange()返回可迭代对象——节省空间（和3中range相同，type为range）,range()返回列表

- 增加

  +：创建新列表

  append：原地修改（更快）

  <u>通过下标修改序列中元素，起始地址一直不变，即id(a)不变</u>

  extend：原地修改，尾部添加可迭代对象

  inset：原地修改，指定位置添加（尽量避免）

  乘法：创建新列表（其他数据结构也这样）

  ```python
  a = [1,2,3]
  print(id(a))
  a = [1,2]
  print(id(a))
  a = [1,2,4]
  b = [1,2,3]
  print(a == b)
  print(id(a) == id(b))
  print(id(a[0]) == id(b[0]))
  
  '''2588242162432
  2588242162368
  False
  False
  True'''
  ```

- 删除

  del/pop(默认最后，基于下标)/remove(基于值)

  ```python
  #remove 循环
  def rvfunc(x):
      for i in x:
          if i == 1:
              x.remove(i)
      return x
  ###测试例
  def eg9():
      x = [1,2,1,2,1,2,1,2,1]
      rvfunc(x)
      print(x)
      x = [1,2,1,2,1,1,1]
      rvfunc(x)
      print(x)
     
  '''[2, 2, 2, 2]
  [2, 2, 1]
  改成切片或者倒序'''
  ```

- 访问计数

  count()

- 成员资格

  in/count/zip——将列表对应位置元素以元组形式合并

- 切片

  原地修改,返回浅复制

  a[len(a):]=[1]==a.append(1)

  I.eg13

  **深浅拷贝**：切片拷贝字典拷贝都是浅拷贝，而有些内置函数可以生成拷贝(list)，属于深拷贝

  浅拷贝只复制一层，而深拷贝全部复制，所以深拷贝不被影响，而浅拷贝可能被影响

- 排序

  shuffle随机排序

  sort默认升序（reverse=True降序）：原地修改，返回None

  sorted：返回新列表——同理reverse和reversed（返回可迭代对象）

- 杂

  zip/enumerate返回元组（zip返回对象，需要list()）

- **<font color='cornflowerred'>列表推导式！！！</font>**

  map(f,x)将x中元素一次传入f中运算，返回列表
  
  for循环中对临时变量修改不会改动原列表
  
  ```python
  vec = [[1,2,3], [4,5,6], [7,8,9]] 
  aList = [num for elem in vec for num in elem]
  '''实现嵌套序列的平铺
  [1, 2, 3, 4, 5, 6, 7, 8, 9]'''
  ```
  
  ```python
  aList = [(x, y) for x in [1, 2, 3] for y in [3, 1, 4] if x != y]
  '''组合输出而非对应位置输出
  [(1, 3), (1, 4), (2, 3), (2, 1), (2, 4), (3, 1), (3, 4)]
  '''
  ```
  
  ```python
  matrix = [ [1, 2, 3, 4], [5, 6, 7, 8], [9, 10, 11, 12]] 
  aList = [[row[i] for row in matrix] for i in range(4)] 
  '''矩阵转置
  [[1, 5, 9], [2, 6, 10], [3, 7, 11], [4, 8, 12]]'''
  list(zip(*matrix))
  '''zip+list也可以实现
  此处zip(*)解压——zip()压缩
  [(1, 5, 9), (2, 6, 10), (3, 7, 11), (4, 8, 12)]'''
  ```
  
  ```python
  aList=[ p for p in range(2, 100) if 0 not in [ p% d for d in range(2, int(math.sqrt(p))+1)] ]
  '''生成100以内所有素数'''
  ```

#### 元组

- 创建：只含一个元素时后要加逗号，如a=(1,)或a=1, +创建新列表

  删除只能用del（**不可变序列**——但当其中包含可变序列时，对其原地修改时有效的）

- 和列表区别：tuple()冻结 list()融化

  ​						操作速度更快

  ​						可作字典键（不可变，如字符串，整数）

- 序列解包

  字典：默认对键操作，键—值items(),值values()，**{}

  元组/列表：*

- **<font color='cornflowerred'>生成器推导式!!!</font>**

  结果是一个生成器对象，需要转化为列表或元组，或next()方法或作为迭代器使用

  **一次生命周期**

  ```python
  g=((i+2)**2 for i in range(10))
  print(g)
  print(tuple(g))
  print(tuple(g))
  '''
  <generator object eg22.<locals>.<genexpr> at 0x000001B7C58369E0>
  (4, 9, 16, 25, 36, 49, 64, 81, 100, 121)
  ()'''
  ```



#### 字典

无序可变序列，键为不可变序列，值可以重复，键不可

globals()返回全局字典，locals()返回局部

- 创建：

  ```python
  keys=['a','b','c','d']
  values=[1,2,3,4]
  dictionary=dict(zip(keys,values))
  '''
  {'a': 1, 'b': 2, 'c': 3, 'd': 4}'''
  d=dict(name='Dong',age=37)
  '''
  {'name': 'Dong', 'age': 37}'''
  adict=dict.fromkeys(['name','age','sex'])
  '''
  {'name': None, 'age': None, 'sex': None}'''
  ```

- 读取：值=dict.get(键)

  ​			下标——键

  ​			items()——键值对/keys()——键/values()——值：返回的都是列表,dict_keys([1, 2])这种	

  ​			若元素不存在则返回None

- 添加与修改：下标

  ​						update():原地修改，类似于列表的extend		

  ​						删除：pop/del/popitem/clear，两个pop都有返回值

- 杂：' '.join(x)返回字符串

  计数：使用

  ```python
  from collections import Counter
  '''返回Counter对象Counter{}'''
  ```

  ```python
  a=['1','2']
  b=['x','y']
  d={i:j for i,j in zip(a,b)}
  '''列表合并'''
  ```

- 有序字典：collections模块的OrdereDict()

#### 集合

无序可变序列{}

- 创建删除：增加add()/删除del(),clear(),remove()/pop(第一个)

  ​					空的字典不可生成集合

- | & - ^ issubset(子集) ：集合运算

#### sorted

<font color='cornflowerblue'>考前练</font>

书上例题

### 第三章 选择与循环

#### 条件表达式

逻辑运算符：惰性求值 and,or not

测试运算符：is in not 组合

条件表达式中不允许使用赋值运算符= ，区分于==

#### 选择结构

双分支表达式：value1 if condition else value2

#### 循环结构

自带else语句，在不满足循环条件自然结束时执行（break不执行）

- 加快循环速率：

  尽量引用局部变量：比如将外部库中的函数转化为局部变量，类似local_sin=math.sin这种

  运算尽量往循环外提

#### break/continute

break:整个循环

continue:本次循环

### 第四章 字符串与正则表达式

#### 字符串

replace/translate都是返回新对象

驻留机制：短字符串共享副本——浅拷贝

```python
x='1234'
y='1234'
id(x)==id(y)
'''True'''
x='1234'*50
y='1234'*50
'''False'''
```

- 格式化：'% [-] [+] [0] [m] [.n] 格式字符  '% x，如

​				字符串->数字 ，不可

​				fomat格式化：字典{：}

- 方法：s1.find(s2)： 查找s2在s1中第一次位置，rfind最后一次位置，若不存在返回-1

​			index()：若不存在返回异常

​			split()：分割字符串，返回列表，rsplit()从右——默认分割空白符号

​			partition()：分割左，分割处，分隔右，同理r~

​			'x'.join(y)：用x拼接y列表中字符串，比+高效

​			strip():删除两端连续字符

​			eval()：表达式转化，可外部调命令

​			startwith/endwith

​			<font color='cornflowerblue'>考前简单看一下</font>

- random库：

```python
random.randint(1,10)
 # 产生 1 到 10 的一个整数型随机数
random.choice(x)
# 从x序列中随机选取一个元素
random.saple(x,3)
# 从x序列中随机选取3个不重复的元素
```

#### 正则表达式

re模块主要方法：

​			compile创建对象，提高处理速度

​			search寻找：返回对象或None

​			match：匹配成功返回对象，反之返回None

​			findall:列出所有

​			split:分割

​			sub:替换

 子模式：()一个整体，对于match和search返回的对象，使用group等函数返回内容位置等			

### 第五章 函数的设计和使用

- 定义：代码复用/封装代码/保证一致/修改同步

- 修改形参不影响实参，但传参是放得是可变序列有时传递会被修改

- 参数类型：默认值——最右端

  ​					<font color='cornflowerblue'>不为默认值参数传递时，只在第一次解释</font>

  ​					通过名字定位，可打乱传递顺序

  ​					*p——元组，**p——字典

  ​					传参时*,自动解包

  ```python
  def mistake(a=1,b,c=3)：
  	print(a,b,c)
  '''错误，默认值不都在最右端'''
  ```

  ```python
  def demo(item,old_list=[])：
  	old_list.append(item)
  '''当old_list无参数参数传入时，只调用一次，之后old_list一直保存之前值'''
  
  def demo(item,old_list=None)：
  	if old_list==None:
          old_list=[]
      old_list.append(item)
  '''修改后可重复初始化'''
  ```

- return：默认None,有返回值直接跳出函数

- global全局变量

- lambda：只可以包含一个表达式，返回值为表达式的值

- 高级话题：map函数合成

  ​					reduce将二个函数累积

  ​					**filter**：和map相似，但只返回值为true的

  ​					**yield**:创建生成器——惰性求值，_ _next _ _()方法

### 第六章 面对对象程序设计

#### OPP

基本原则：程序由多个子程序作用的对象或单元组合而成

面向对象程序设计：合理的定义和组织类和类之间的关系

一切皆对象，不一定是类的实例

属性：变量形式的对象——类属性（类方法之外定义的成员，可通过类名访问），实例属性（__ init __定义，只能通过对象名访问）

方法：函数形式的对象

高级动态编程语言

isinstance()测试实例

#### 函数

pass:空，占位

python可动态添加成员

self参数（对应C++this指针）

属性：@property声明

继承：代码复用，派生

装饰器

调用基类构造的方法：super(Class.self).__ init __(name,age,sex)



