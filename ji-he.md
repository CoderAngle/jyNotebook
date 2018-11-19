### 简述

什么是集合？

集合是无序集合，没有重复元素。

有什么用途？

基本用途包括成员资格测试和消除重复条目。

集合对象还支持数学运算，如并集，交集，差异和对称差异

### 创建集合

大括号或set\(\)函数可用于创建集合。注意：要创建一个空集，你必须使用set\(\)，而不是{}; 后者创建一个空字典

```
>>> basket = {'apple', 'orange', 'apple', 'pear', 'orange', 'banana'}
>>> print(basket)                      # 打印，展示是否已删除重复项
{'orange', 'banana', 'pear', 'apple'}
>>> 'orange' in basket                 # 判断元素是否在集合中
True
>>> 'crabgrass' in basket
False

>>> # 创建集合
...
>>> a = set('abracadabra')
>>> b = set('alacazam')
>>> a                                  # 将a集合中数据，去除重复项，留下唯一的数据
{'a', 'r', 'b', 'c', 'd'}
>>> b
{'l', 'a', 'c', 'm', 'z'}

# 差集
>>> a - b                              # 集合数据在a中，而不在b中的数据
{'r', 'd', 'b'}


# 交集
>>> a & b                         
{'a', 'c'}



# 对称差集
>>> a ^ b                              # 去除集合相同的数据，然后将剩下的数据并在一起
{'r', 'd', 'b', 'm', 'z', 'l'}
```

与列表推导类似，也支持集合理解：

```
>>>
>>> a = {x for x in 'abracadabra' if x not in 'abc'}
>>> a
{'r', 'd'}
```

### 添加元素

s.add\( x \) 将元素 x 添加到集合s中，若重复则不进行任何操作

```
>>> a = set('abracadabra')
>>> a
>>> b = set('alacazam')
>>> b
{'l', 'a', 'c', 'm', 'z'}
{'b', 'd', 'a', 'r', 'c'}
>>> a.add(1)
>>> a
{1, 'b', 'd', 'a', 'r', 'c'}
```

### 更新集合

s.update\( x \) 将集合 x 并入原集合s中，x 还可以是列表，元组，字典等，x 可以有多个，用逗号分开

```
>>> a.update(b)
>>> a
{1, 'b', 'l', 'd', 'a', 'r', 'c', 'm', 'z'}
```

### 删除元素

s.discard\( x ）将 x 从集合s中移除，若x不存在，不会引发错误

```
>>> a
{1, 'b', 'l', 'd', 'a', 'r', 'c', 'm', 'z'}
>>> a.discard(1)

>>> a
{'b', 'l', 'd', 'a', 'r', 'c', 'm', 'z'}

>>> a.discard(1)
>>> a
{'b', 'd', 'a', 'r', 'c', 'm', 'z'}
```

s.remove\( x \) 将 x 从集合s中移除，若x不存在，会引发错误

```
>>> a
{'b', 'l', 'd', 'a', 'r', 'c', 'm', 'z'}

>>> a.remove(1)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
KeyError: 1

>>> a.remove('l')
>>> a
{'b', 'd', 'a', 'r', 'c', 'm', 'z'}
```

s.pop\(\) 随机删除并返回集合s中某个值，注意，因为set是无序的，不支持下标操作，没有所谓的最后一个，pop\(\)移除随机一个元素

```
>>> a
{'b', 'd', 'a', 'r', 'c', 'm', 'z'}
>>> a.pop()
'b'
>>> a
{'d', 'a', 'r', 'c', 'm', 'z'}
```

s.clear\(\) 清空

```
>>> a
{'d', 'a', 'r', 'c', 'm', 'z'}
>>> a.clear()
>>> a
set()
```

### 并集

* s.union\( x \) 返回s与集合x的并集集，不改变原集合s，x 也可以是列表，元组，字典

* 可以使用 \| 返回集合之间的并集

```
>>> a=set('123')
>>> b={4,5,6}
>>> a
{'2', '1', '3'}
>>> b
{4, 5, 6}

>>> a.union(b)
{'2', '1', 4, 5, 6, '3'}
>>> a
{'2', '1', '3'}


>>> a | b
{'2', '1', 4, 5, 6, '3'}
```

### 交集

* s.intersection\( x \) 返回s与集合x的交集，不改变s， x 也可以是列表，元组，字典。
* 可以使用 & 返回集合之间的交集

```
>>> a = [1,2,3]
>>> a = set('123')
>>> b = set('234')
>>> a
{'2', '1', '3'}
>>> b
{'2', '3', '4'}

>>> a.intersection(b)
{'2', '3'}


>>> a & b
{'2', '3'}
```

注意不能使用and操作符

### 差集

* s.difference\( x ）返回在集合s中而不在集合 x 中的元素的集合，不改变集合s， x 也可以是列表，元组，字典。
* 可以使用 - 返回集合之间的差集

```
>>> a = [1,2,3]
>>> a = set('123')
>>> b = set('234')
>>> a
{'2', '1', '3'}
>>> b
{'2', '3', '4'}

>>> a.difference(b)
{'1'}

>>> a - b
{'1'}
```

### 对称差集

* s.symmetric\_difference\( x \) 返回s和集合x的对称差集，即只在其中一个集合中出现的元素，不改变集合s， x 也可以是列表，元组，字典。
* 可以使用 ^ 返回集合之间的对称差集

```
>>> a = [1,2,3]
>>> a = set('123')
>>> b = set('234')
>>> a
{'2', '1', '3'}
>>> b
{'2', '3', '4'}

>>> a.symmetric_difference(b)
{'1', '4'}

>>> a^b
{'1', '4'}
```

### 判断

* s.issubset\( x \) 判断 集合s 是否是 集合x 子集
* s.issuperset\( x ） 判断 集合x 是否是集合s的子集

```
>>> a = {1,2,3}
>>> b = {1,3}

>>> a.issubset(b)
True
>>> a.issubset(b)
False

>>> a.issuperset(b)
True
```

### 不可变集合

frozenset是不可变集合，除了不能修改以外，set集合的大部分方法都可以使用
