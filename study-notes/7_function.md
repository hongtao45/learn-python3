# Function 学习笔记

2022.04.22

## 函数参数

- 避免使用可变的数据类型作为函数的参数

```python
def append_if_multiple_of_five(number, magical_list=[]):
    if number % 5 == 0:
        magical_list.append(number)
    return magical_list

print(append_if_multiple_of_five(100))
print(append_if_multiple_of_five(105))
print(append_if_multiple_of_five(123))
print(append_if_multiple_of_five(123, []))
print(append_if_multiple_of_five(123))

#[100]
#[100, 105]
#[100, 105]
#[]
#[100, 105]
```

- 帮助信息
```python
def calculate_sum(val1, val2):
    """This is a longer docstring defining also the args and the return value. 

    Args:
        val1: The first parameter.
        val2: The second parameter.

    Returns:
        The sum of val1 and val2.
        
    """
    return val1 + val2

print(help(calculate_sum))
```

```python
Help on function calculate_sum in module __main__:

calculate_sum(val1, val2)
    This is a longer docstring defining also the args and the return value. 
    
    Args:
        val1: The first parameter.
        val2: The second parameter.
    
    Returns:
        The sum of val1 and val2.

None
```

## pass语法

Python pass 是空语句，是为了保持程序结构的完整性。

**pass** 不做任何事情，一般用做占位语句。

Python 语言 pass 语句语法格式如下：
