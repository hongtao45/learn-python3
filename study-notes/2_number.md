# Numbers 学习笔记

2022.04.18

## 计算精度问题

- 底层技术细节对上层带来的影响

```python
val = 0.1 + 0.1 + 0.1
print(val == 0.3)
print(val)

# 结果：
False
0.30000000000000004
```

- 三个关键符号

```python
# // 整除
# % 取模（余数
# ** 平方
```



##  [`decimal.Decimal`](https://docs.python.org/3/library/decimal.html)

- python的计算精度处理问题:

​	[Python decimal模块使用方法详解](https://zhuanlan.zhihu.com/p/157227878)
