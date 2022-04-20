# Dictionary 学习笔记

2022.04.20

## 新建

- 新建字典，两个形式

```python
dict1 = {'value1': 1.6, 'value2': 10, 'name': 'John Doe'}
dict2 = dict(value1=1.6, value2=10, name='John Doe')
```

- 删除元素
```python
my_dict = dict(food='ham', drink='beer', sport='football')
print('dict before pops: {}'.format(my_dict))
food = my_dict.pop('food')
print('food: {}'.format(food))
print('dict after popping food: {}'.format(my_dict))

# dict before pops: {'food': 'ham', 'drink': 'beer', 'sport': 'football'}
# food: ham
# dict after popping food: {'drink': 'beer', 'sport': 'football'}
```



- 合并字典

```python
dict1 = dict(key1='This is not that hard', key2='Python is still cool')
dict2 = {'key1': 123, 'special_key': 'secret'}
# This is also a away to initialize a dict (list of tuples) 
dict3 = dict([('key2', 456), ('keyX', 'X')])


my_dict = dict1.copy()
my_dict.update(dict2)
my_dict.update(dict3)


assert my_dict == {'key1': 123, 'key2': 456, 'keyX': 'X'}


# Let's check that the originals are untouched
assert dict1 == {
        'key1': 'This is not that hard',
        'key2': 'Python is still cool'
    }

assert dict2 == {'key1': 123, 'special_key': 'secret'}
assert dict3 == {'key2': 456, 'keyX': 'X'}
```


