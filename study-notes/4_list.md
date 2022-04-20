# Lists 学习笔记

2022.04.20

## 元素操作

- 删除元素，就直接使用`del`函数和`list.remove()`

```python
# remove first value
del my_list[0]
print(my_list)
```

```python
my_list = ['Python', 'is', 'sometimes', 'fun']
my_list.remove('sometimes')
print(my_list)

# If you are not sure that the value is in list, better to check first:
if 'Java' in my_list:
    my_list.remove('Java')
else:
    print('Java is not part of this story.')
    
# ['Python', 'is', 'fun']
# Java is not part of this story.
```



- 是否包含元素，就直接用 `in`就可以了

```python
languages = ['Java', 'C++', 'Go', 'Python', 'JavaScript']
if 'Python' in languages:
    print('Python is there!')
```



## 可变与不可变

- python中的数据，分为mutable 和immutable

  1. mutable : list ,dict

  2. inmutable : int , string , float ,tuple...

```python
# 数字、字符串、tuple都是不可变对象  
# list、dict是可变对象  
#Python函数参数对于可变对象，函数内对参数的改变会影响到原始对象；对于不可变对象，函数内对参数的改变不会影响到原始参数。原因在于：可变对象，参数改变的是可变对象，其内容可以被修改。不可变对象，改变的是函数内变量的指向对象。 

a = 1  
d = [5]  
      
def A(a):  
    a = 3  

A(a)  
print(a)    
# 1 
# a是1（不可变对象）的引用，a存的是1的地址，调用A(a)的时候，会复制一份该引用，然后函数内是操作的复制的这一份引用，将其指向了3，与外面的引用没关系，外面的a还是指向1  

# 字符串和tuple类似,tuple本身就是一旦初始化就不可以进行增删修改的。  
def B(d):  
    d = [6] #这里相当于是一个赋值操作，类似于  
 
B(d)  
print(d)    
# [5]  
# 这里是5是因为B(d)相当于对函数内部复制了一份外面的d，对新复制的d进行赋值，不会影响到外面的d  
      
def C(d):  
    d[0] = 2 
# [2] 
# 这里是2是因为C()方法里面并不是去创建了一个新的变量d而是对原先的d进行修改，而之所以能对原先的d进行修改就是因为list是可变对象  
      
C(d)  
print(d)  
      
# 2
# 为什么上面B()运行了输出还是5而下面C()运行了却变为了2呢？我想是因为上面B函数传进去的是d，同样会复制d，函数内部操作复制的这一份，内部的确实变为了[6],但外部的d并没有改变，但是在C函数中，并没有创建新的d，而是原先的d的进行了修改。  

#总结：重新分配一个对象，是不会改变实参的，但是对对象进行修改，是可以改变实参的。  
      
#可能有人又好奇了，为什么list是可变对象，而str不是呢，list可以遍历，而一个str也可以遍历，这里其实很简单，一个str虽然可以拆分为一个个char但是你不能去对单独的一个char进行修改，你可以试试p = 'www',虽然你可以打印出p[0],但是当你试图p[0] = 's',肯定就报错了。  
```



- 直接等于，相当于取别名了

```python
original = [1, 2, 3]
modified = original
modified[0] = 99
print('original: {}, modified: {}'.format(original, modified))

# original: [99, 2, 3], modified: [99, 2, 3]
```



- 可以副本复制

```python
original = [1, 2, 3]
modified = list(original)  # Note list() 
# Alternatively, you can use copy method
# modified = original.copy()
modified[0] = 99
print('original: {}, modified: {}'.format(original, modified))

# original: [1, 2, 3], modified: [99, 2, 3]
```



## `list.extend()`和`list.append()`

```python
>>> li = ['a', 'b', 'c']  
>>> li.extend(['d', 'e', 'f'])   
>>> li  
['a', 'b', 'c', 'd', 'e', 'f']  
>>> len(li)                      
6  
>>> li[-1]  
'f'  

>>> li = ['a', 'b', 'c']  
>>> li.append(['d', 'e', 'f'])   
>>> li  
['a', 'b', 'c', ['d', 'e', 'f']]  
>>> len(li)                      
4  
>>> li[-1]  
['d', 'e', 'f']  
```

- extend 接受一个参数，这个参数总是一个 list，并且把这个 list 中的每个元素添加到原 list 中。
- append 接受一个参数，这个参数可以是任何数据类型，并且简单地追加到 list 的尾部。
