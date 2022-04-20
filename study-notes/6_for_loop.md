# Loop 学习笔记

2022.04.20

## 循环结构

- enumerate()

```python
for idx, val in enumerate(my_list):
    print('idx: {}, value: {}'.format(idx, val))
```

- 一行for 循环
```python
magic_dict = dict(val1=44, val2='secret value', val3=55.0, val4=1)

sum_of_values = sum([x for x in magic_dict.values() if type(x)!= type("2")])
```


