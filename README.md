# Python技術手冊筆記

## Chapter 3

### 資料型別

* Pyhon中的物件可分為可變物件\(mutable object\)及不可變物件\(immutable object\)

### 數字

* 二進位表示法，以0b開頭，後續接二進位值

```text
b1 = 0b01 #1
b2 = 0b110010 #50
```

* 八進位表示法以，0o開頭，後續接八進位值

```text
o1 = 0o1 #1
o2 = 0o27 #23
```

* 十六進位表示法，0x開頭，後續接十六進位值

```text
x1 = 0x1 #1
x2 = 0x2CA #714
```

### 元組 tuple

* tuple是由項目\(items\)所組成的不可變的有序序列，每個項目可以是不同型別。
* 可以使用可變序列當作tuple的項目，但實務上最好不要這麼做。

```python
#tuple宣告
t1 = (1,2,3)
t2 = tuple([1,2,3]) #tuple()宣告,參數必須為可迭代的(iterable),或單一值
t3 = tuple() #空tuple,也可單獨使用()
print(t1) #(1,2,3)
print(t2) #(1,2,3)
print(t3) #()
```

### 串列 list 

* list是由項目\(items\)所組成的不可變的有序序列

```python
#list宣告
l1 = [1,2,3]
l2 = list('wow') #list()宣告,參數必須為可迭代的(iterable),或單一值
l3 = list() #空list, 也可單獨使用[]
print(l1) #[1,2,3]
print(l2) #['w', 'o', 'w']
print(l3) #[]
```

### 集合 set

* 集合有`set`和`frozenset(凍結集)`，frozenset是不可變的
* set是任意順序的唯一項目群集。項目可以是不同型別，但它們必須是可雜湊的。set的項目不可是set，但可以是frozenset

```python
#set宣告
s1 = {1,2,2,3}
s2 = set('wow') #set()宣告,參數必須為可迭代的(iterable),或單一值
s3 = set() #空set, 不可使用{},{}是空字典
print(s1) #{1,2,3}
print(s2) #{'w', 'o'}
print(s3) #set()
```

### 字典 dict

```python
#dict宣告
d1 = {'a':1, 'b':2, 'c':3, 'a':4}
d2 = dict(a=1,b=2,c=3)
d3 = dict([('a',1),('b',2),('c',3)])
d4 = dict() #空字典, 也可單獨使用{}
print(d1) #{'a': 4, 'b': 2, 'c': 3}
print(d2) #{'a': 1, 'b': 2, 'c': 3}
print(d3) #{'a': 1, 'b': 2, 'c': 3}
print(d4) #{}
```

### Boolean值

* 任何非零或非空容器\(string、tuple、list、set、dict\)為true。0\(任何數值型別的\)、None以及空容器為false

### 指定述句

```python
a = 2
b = 3
a = b = c = 0

x = (1,2)
a, b = x

x = [1,2,3,4,5]
first, *middle, last = x
#上述句等同
first, middle, last = x[0], x[1:-1], x[-1]
```

### 比較鍊串 Comparison Chaining

* Python允許比較運算是串連起來，其中以含and的意思

```python
a < b <= c < d
#等同 a<b and b<=c and c<d
#a!=b!=c 不代表a!=c
```

### 短路運算子

* and : 右邊的運算元只會在**左邊的運算元皆為ture時**才會被估算
* or : 右邊的運算元只會在**左邊的運算元皆為false時**才會被估算

```python
x, y, z=5, 0, 2
_and = x and y and z #估算至y就停止,並回傳y
print(_and) #0
_or = x or y or z #估算至x就停止,並回傳x
print(_or) #5
```

### 三元運算子

* whentrue if condition else whenfalse

```python
x = 12
y = 20
result = x if (x>y) else y #result=y
print(result) #20
```

### 序列切片

* S是一個串列的話，可以用`S[i : j : k]`表式一個子序列
  * i = 起始位置\(包含\)，等於0可省略
  * j = 結束位置\(不包含\)， j大於或等於序列長度可省略
  * k = 步伐，預設為1
  * i, j, k必為整數
  * k &gt; 1 時，i 必須小於 j。 k &lt; 0時， i 必須大於 j。否則回傳空序列

```python
ls = [0,1,2,3,4,5,6] #list
tp = (0,1,2,3,4,5,6) #tuple
print(ls[:]) #[0, 1, 2, 3, 4, 5, 6]
print(ls[1:4]) #[1, 2, 3]
print(ls[-3:]) #[4, 5, 6]
print(tp[1:5:2]) #(1, 3)
print(tp[5:2:-2]) #(5, 3)
print(tp[5:2:2]) #()
```

### in-place運算

```python
l1, L2 = [12,3], [1,2]
l1+=l2 #效果等同l1.extend(l2)
print(l1) #[12,3,1,2]

L = [5,4]
L *= 3 #把n-1個L加到L尾端
print(L) #[5,4,5,4,5,4]
L *= 0
print(L) #[]
```

### 破壞性迭代 destructive iteration

* 在破懷性迴圈主體內，可以修改S\(修改、移除項目\)，而非破壞性是不允許的
* 在大型集合的迴圈處理，可以節省記憶體\(如果項目用完就不需要了的話\)

```python
#破壞性迴圈
while S:
	itme = S.pop()
	# do something..

#非破壞性迴圈
for item in S:
	# do something..
```

### 串列概括式 list comprehension

* 語法: \[expression for target in iterable clauses\]
  * clauses為一個或多個字句

```python
result = [i*5 for i in range(5)]
print(result) #[0, 5, 10, 15, 20]

result = [i*5 for i in range(5) if i>2]
print(result) #[15, 20]
```

### 集合概括式

* 同串列概括式
* '\[ \]' 改為 '{ }'

```python
result = {i*5 for i in range(5)}
print(result) #{0, 5, 10, 15, 20}
```

### 字典概括式

* 同串列概括式
* expression必須包含`key:value`。
* '\[ \]' 改為 '{ }'

```python
result = {i:i//2 for i in range(5)}
print(result) #{0: 0, 1: 0, 2: 1, 3: 1, 4: 2}
```

### 參數

* `*args`: 將任何額外參數收集到一個tuple中，並對應到args變數名稱
  * **在其之前**的參數**不能以指定名稱**方式傳入
  * **在其之後**的參數**必須以指定名稱**方式傳入
* `**kwds`: 將任何額外具名參數收集到一個dict中，並對應到kwds變數名稱
  * 在其之後不可有任何參數

```python
#*args test
def args(a,*middle,b): 
	print(a)
	print(middle)
	print(b)
args(1,2,3,4,b=5) #b必須指定
#1
#(2,3,4)
#5
```

```python
#**kwds test
def kwds(a,**kwds): 
	print(a)
	print(kwds)
kwds(1,b=2,c=3)
#1
#{'b': 2, 'c': 3}
```

* 僅限關鍵字\(keyword-only parameters\)
  * 僅限python3版本
  * 使參數必須以指定名稱方式傳入
  * 必須出現在`*args`之後，`**kwds`之前

```python
def f(a, *, b, c=56): #b為僅限關鍵字
    return a, b, c
f(12, b=34) #(12, 34, 56)
f(12) #TypeError
#missing 1 required keyword-only argument: 'b'

def g(x, *a, b=23, **k): #b為僅限關鍵字
    return x, a, b, k
g(1,2,3,c=99) #(1, (2,3), 23, {'c': 99})
```

### 參數傳遞

* `*args`: 將序列項目逐一傳入
* `**kwds`: 將字典,以指定名稱方式逐一傳入
* `*kwds`: 將字典的key逐一傳入
* `*kwds.values()`:將字典的value逐一傳入

```python
tp = [1,2,3,]
d = {'x':1, 'y':1, 'z':1}
sum_args(*tp)
#等同於sum_args(tp[0],tp[1],tp[2])
showkey(**d)
#等同於sum_args(x=d['x'], y=d['y'], z=d['z'])
```

### Docstrings

用來描述函式\(類別、模組\)

當在函式\(類別、模組\)中第一個述句為字串時，該字串為docstring屬性

* 第一行: 簡要說明函式\(類別、模組\)用途
* 第二行: 空白行
* 其餘行: 描述函式\(類別、模組\)參數、先決條件、回傳值以及副作用，以空白行隔開

### 函式注釋與型別提示

* 在**參數後面**加入 `:type` 添加型別提示
* 再**函式參數與 : 之間**加入`->type`添加函式回傳值提示
* 函式物件的`__annotations__`屬性會將每個提示以dict方式儲存

```python
def returnStr(string:str) -> str:
	return string

print(returnStr('Hi')
print(returnStr(12)) #不強制使用行別提示的型別
print(returnStr.__annotations__)
#{'string': <class 'str'>, 'return': <class 'str'>}
```

### 巢狀函式

```python
def percent1(a, b, c):
	def pc(target, total=a+b+c):
		return (target*100.0)/ total
	print(pc(a), pc(b), pc(c))

def percent2(a, b, c):
	def pc(target):
		return (target*100.0)/ (a+b+c)
	print(pc(a), pc(b), pc(c))
#percent1 與 percent2 的差別在於percent只會計算一次a+b+c
#但還是要依情況使用
```

### 閉包\(closure\)

* 當希望某些參數在建構時就固定下來時，除了物件導向，也可以使用`closure`的方式，將資料與方法包在一起。

```python
def make_adder(augend):
	def add(addend):
		return addend+augend
	return add

adder = make_adder(7)
print(adder(3)) #10
```

### 用closure做一個計數器

```python
def make_counter():
	count = 0
	def counter():
		nonlocal count #nonlocal類似global, 但範圍只到所有外層函式
		count+=1
		return count
	return counter

c1 = make_counter() #各自獨立的counter
c2 = make_counter() #各自獨立的counter
print(c1(), c1(), c1())
print(c2())
print(c1(),c2())
```

### lambda

* lambda函式是主體為單一return述句的匿名函式
* 語法: `lambda target: return value`

```python
ls = [1,2,3,4,5]
low = 2
result = [r for r in filter(lambda x: low<x, ls)]
print(result)
```

* 等同於

```python
ls = [1,2,3,4,5]
low = 2
def bound(x, low=low):
	return low<x
result = [x for x in filter(bound, ls)]
print(result)
```

### 產生器 generator

* 當一個函式主體裡面出現關鍵字`yield`一次或多次，那函式就是一個產生器
* 太多了不想打，直接看圖

![](.gitbook/assets/s__11059225.jpg)

![](.gitbook/assets/s__11059226.jpg)

![](.gitbook/assets/s__11059227.jpg)

![](.gitbook/assets/s__11059228.jpg)

## Chapter 3 Python物件導向

### 定義類別

```text
class classname(base-class1,base-class2,...):
    statement..
```

* classname: 類別名稱
* base-class: 父類別,可以零到多個
* base-class可以是一個具名參數metaclass=..., 代別元類別
* 每個class都是object的子類別，class C1\(\) = class C1\(object\)

### 類別隱含屬性

* `__name__`: class名稱
* `__bases__`: class所有父類別的名稱\(tuple\)
* `__dict__`:是用來儲存屬性的

```python
class C1():
	x = 10
	def get_x(self):
		return x

class C2(C1):
	x = 20

print(C2.__name__)
print(C2.__bases__)
print(C2.__dict__)
```

### 私有變數

* 在變數名稱前加上兩個底線\_\_value就是私有變數，避免子類別的屬性命名衝突，或是直接存取屬性

### 描述器

```python
class Integer(object):
	"""
	descriptor描述器
	如果類別裡面包含了 __set__、__get__、__delete__其中一(多)種methods，那就是一个描述器
	通常用於對類別的操作進行hook(掛勾)
	描述器不會單獨存在，通常會附加於其他類別之中
	"""
	def __init__(self, name):
		self.name = name

	def __set__(self, instance, value):#修改屬性時，先進行一些操作
		if not isinstance(value, int):
			raise TypeError('Expected an int')
		instance.__dict__[self.name] = value
 
class Point(object):
	x = Integer('x')
	y = Integer('y')
	def __init__(self, x, y):
		self.x = x
		self.y = y

p = Point(2, 3)
p.x = 9
p.y = 9.9#這句會拋出TypeError: Expected an int錯誤.這就是描述器的作用
# p.x = 9 等同於p.__dict__['x'] = 9
```

## 繼承

* 覆寫
* 委派父類別
  *  在類的繼承中，如果重定義某個方法，該方法會覆蓋父類的同名方法，但有時，我們希望能同時實現父類的功能，这時，我們就需要調用父類的方法了，可通使用 `super` 來實現

```python
class Animal(object):
    def __init__(self, name):
        self.name = name
    def greet(self):
        print 'Hello, I am %s.' % self.name

class Dog(Animal):
    def greet(self):
        super(Dog, self).greet()   # Python3 可使用 super().greet()
        print 'WangWang...'
```

```python
class Base(object):
    def __init__(self):
        print "enter Base"
        print "leave Base"

class A(Base):
    def __init__(self):
        print "enter A"
        super(A, self).__init__()
        print "leave A"

class B(Base):
    def __init__(self):
        print "enter B"
        super(B, self).__init__()
        print "leave B"

class C(A, B):
    def __init__(self):
        print "enter C"
        super(C, self).__init__()
        print "leave C"
```

```python
>>> c = C()
enter C
enter A
enter B
enter Base
leave Base
leave B
leave A
leave C
```

*  如果你認為 `super` 代表『調用父類別的方法』，那你很可能會疑惑為什麼 enter A 的下一句不是 enter Base 而是 enter B。原因是，**`super` 和父類沒有實質性的關聯，**而是根據**MRO**運作的。
* 事實上，對於定義的每一个類，Python 會計算出一个**方法解析順序（Method Resolution Order, MRO）列表**，**它代表了類繼承的順序**，我們可以使用下面的方式獲得某個類的 MRO 列表：

```python
>>> C.mro()   # or C.__mro__ or C().__class__.mro()
[__main__.C, __main__.A, __main__.B, __main__.Base, object]
```

### sup工作原理

```python
def super(cls, inst):
    mro = inst.__class__.mro()
    return mro[mro.index(cls) + 1]
```

其中，cls 代表類，inst 代表實例，上面程式做了兩件事：

* 獲取 inst 的 MRO 列表
* 查找 cls 在當前 MRO 列表中的 index, 並返回它的下一個類，即 mro\[index + 1\]

當你使用 `super(cls, inst)` ，Python 會 inst 的 MRO 列表上搜索 cls 的下一個類。

現在，回到前面的例子。

首先看類 C 的 `__init__` 方法：

```python
super(C, self).__init__()
```

 這裡的 self 是當前 C 的實例，self.**class**.mro\(\) 结果是：

```python
[__main__.C, __main__.A, __main__.B, __main__.Base, object]
```

 可以看到，C 的下一個類是 A，于是，跳到了 A 的 `__init__`，這時會打印出 enter A，並執行下面一行程式：

```python
super(A, self).__init__()
```

 注意，這裡的 self 也是當前 C 的實例，MRO 列表跟上面是一樣的，搜索 A 在 MRO 中的下一個類，這時發現是 B，于是，跳到了 B 的 `__init__`，這時會打印出 enter B，而不是 enter Base。

## 裝飾器  **decorator**

```python
def hello():
    return 'hello world'
```

 我們想增強 `hello()` 函數的功能，希望给返回加上 HTML 標籤，比如 `<i>hello world</i>`，但是有一個要求，不改變原来 `hello()` 函數的定義。那麼可以使用裝飾器的方式實現:

```python
def makeitalic(func):
    def wrapped():
        return "<i>" + func() + "</i>"
    return wrapped
```

 現在，我們就可以不改變 `hello()` 函數的定義，給返回加上 HTML 標籤:

```python
>>> hello = makeitalic(hello)  # 將 hello 函數傳給 makeitalic
>>> hello()
'<i>hello world</i>'
```

### 裝飾器的使用形式

```python
@decorator
def func():
    pass
```

等同下面的形式：

```python
def func():
    pass
func = decorator(func)
```

裝飾器可以定義多個，離函數定義最近的裝飾器先被調用，比如：

```python
@decorator_one
@decorator_two
def func():
    pass
```

等同於下面的形式：

```python
def func():
    pass
func = decorator_one(decorator_two(func))
```

## 抽象類別

* @abstractmethod
* abc模組
* collections.abc模組

## 元類別 Metaclasses

* 在Python中，類別也是一個物件
* 類別創建實例，元類別創建類別，元類別預設是type
* 元類別主要做了三件事：
  * 攔截類別的創建
  * 修改類別的定義
  * 回傳修改後的類別

從一個簡單的例子開始，假設有下面的類別：

```python
class Foo(object):
    name = 'foo'
    def bar(self):
        print 'bar'
```

* 現在我們想给這個類別的方法和屬性名稱前面加上 `my_` 前綴，即 name 變成 my\_name，bar 變成 my\_bar，另外，我們還想加一個 echo 方法。當然，有很多種做法，這裡展示用元類別的做法。

```python
class PrefixMetaclass(type):
    def __new__(cls, name, bases, attrs):
        # 給所有屬性和方法前面加上前綴 my_
        _attrs = (('my_' + name, value) for name, value in attrs.items())  

        _attrs = dict((name, value) for name, value in _attrs)  # 轉化為字典
        _attrs['echo'] = lambda self, phrase: phrase  # 增加了一個 echo 方法

        return type.__new__(cls, name, bases, _attrs)  # 返回創建後的類別
```

 `__new__` 是在 `__init__` 之前被調用的特殊方法，它用来創建對象並返回創建後的對象，對它的參數解釋如下：

* cls：當前準備創建的類別
* name：類別的名字
* bases：類別的父類別集合
* attrs：類別的屬性和方法，是一個字典

```python
class Foo(metaclass=PrefixMetaclass):
    name = 'foo'
    def bar(self):
        print 'bar'
```

```python
>>> f = Foo()
>>> f.name    # name 屬性已經改變
---------------------------------------------------------------------------
AttributeError                            Traceback (most recent call last)
<ipython-input-774-4511c8475833> in <module>()
----> 1 f.name

AttributeError: 'Foo' object has no attribute 'name'
>>>
>>> f.my_name
'foo'
>>> f.my_bar()
bar
>>> f.echo('hello')
'hello'
```

可以看到，Foo 原来的屬性 name 已經變成了 my\_name，而方法 bar 也變成了 my\_bar。

