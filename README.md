# Python技術手冊筆記

##  ​資料型別

Pyhon中的物件可分為可變物件\(mutable object\)及不可變物件\(immutable object\)

### 數字

二進位表示法，以0b開頭，後續接二進位值

```text
b1 = 0b01 #1
b2 = 0b110010 #50
```

八進位表示法以，0o開頭，後續接八進位值

```text
o1 = 0o1 #1
o2 = 0o27 #23
```

十六進位表示法，0x開頭，後續接十六進位值

```text
x1 = 0x1 #1
x2 = 0x2CA #714
```

### 元組 tuple <a id="tuple"></a>

tuple是由項目\(items\)所組成的不可變的有序序列，每個項目可以是不同型別。

可以使用可變序列當作tuple的項目，但實務上最好不要這麼做。

```text
#tuple宣告
t1 = (1,2,3)
t2 = tuple([1,2,3]) #tuple()宣告,參數必須為可迭代的(iterable),或單一值
t3 = tuple() #空tuple,也可單獨使用()
print(t1) #(1,2,3)
print(t2) #(1,2,3)
print(t3) #()
```

### 串列 list 

list是由項目\(items\)所組成的不可變的有序序列

```text
#list宣告
l1 = [1,2,3]
l2 = list('wow') #list()宣告,參數必須為可迭代的(iterable),或單一值
l3 = list() #空list, 也可單獨使用[]
print(l1) #[1,2,3]
print(l2) #['w', 'o', 'w']
print(l3) #[]
```

### 集合 set

集合有set和frozenset\(凍結集\)，frozenset是不可變的

set是任意順序的唯一項目群集。項目可以是不同型別，但它們必須是可雜湊的。set的項目不可是set，但可以是frozenset

```text
#set宣告
s1 = {1,2,2,3}
s2 = set('wow') #set()宣告,參數必須為可迭代的(iterable),或單一值
s3 = set() #空set, 不可使用{},{}是空字典
print(s1) #{1,2,3}
print(s2) #{'w', 'o'}
print(s3) #set()
```

### 字典 dict

```text
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

任何非零或非空容器\(string、tuple、list、set、dict\)為true。0\(任何數值型別的\)、None以及空容器為false

## 指定述句

```text
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

## Docstrings

用來描述函式\(類別、模組\)

當在函式\(類別、模組\)中第一個述句為字串時，該字串為docstring屬性

* 第一行: 簡要說明函式\(類別、模組\)用途
* 第二行: 空白行
* 其餘行: 描述函式\(類別、模組\)參數、先決條件、回傳值以及副作用，以空白行隔開

## 

