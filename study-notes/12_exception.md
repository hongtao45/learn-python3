# Exception学习

2022.05.01

> 处理预期或者可能出现异常的代码



- 简单的使用案例——处理异常

  ```python
  def sum_of_list(values):
      res = 0
      for val in values:
          try:
              numeric_val = float(val)
          except Exception as e:
              continue
          res += numeric_val
      return res
  
  
  list1 = [1, 2, 3]
  list2 = ['1', 2.5, '3.0']
  list3 = ['', '1']
  list4 = []
  list5 = ['John', 'Doe', 'was', 'here']
  nasty_list = [KeyError(), [], dict()]
  
  assert sum_of_list(list1) == 6
  assert sum_of_list(list2) == 6.5
  assert sum_of_list(list3) == 1
  assert sum_of_list(list4) == 0
  assert sum_of_list(list5) == 0
  assert sum_of_list(nasty_list) == 0
  ```

  

- 使用案例——自定义异常处理

  ```python
  import math
  
  # Define your own exception
  class NegativeNumbersNotSupported(Exception):
      pass
  
  # Dummy example how to use your custom exception
  def secret_calculation(number1, number2):
      if number1 < 0 or number2 < 0:
          msg = 'Negative number in at least one of the parameters: {}, {}'.format(
              number1, number2)
          raise NegativeNumbersNotSupported(msg)
  
      return math.sqrt(number1) + math.sqrt(number2)
  
  # Uncomment to see the traceback
  # result = secret_calculation(-1, 1)
  
  result = secret_calculation(-1, 1)
  ```

- 自己搭建的异常处理

  ```python 
  # Your implementation here
  class TooLongString(Exception):
      pass
  
  def verify_short_string(str):
      if len(str)>10:
          msg = 'Too Long String'
          raise TooLongString(msg)
  
  # These should not raise
  verify_short_string('short') 
  verify_short_string('10   chars')
  
  # This should raise
  try:
      verify_short_string('this is long')
  except TooLongString as e:
      # This is ok
      pass
  else:
      # This means that there was no exception
      assert False 
  ```

  