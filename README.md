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

十六進位表示法0x1, 0xDA5

```text
x1 = 0x1 #1
x2 = 0x2CA #714
```

### 元組 tuple <a id="tuple"></a>

tuple是由項目\(items\)所組成的不可變的有序序列，&lt;br&gt;每個項目可以是不同型別。

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

## Docstrings

用來描述函式\(類別、模組\)

當在函式\(類別、模組\)中第一個述句為字串時，該字串為docstring屬性

* 第一行: 簡要說明函式\(類別、模組\)用途
* 第二行: 空白行
* 其餘行: 描述函式\(類別、模組\)參數、先決條件、回傳值以及副作用，以空白行隔開

## 

