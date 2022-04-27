# Class 学习笔记

2022.04.27

## 类的初始化

- `__init__()`函数用来初始化设置类(class)的参数

  ```python
  class Example:
      def __init__(self, var1, var2):
          self.first_var = var1
          self.second_var = var2
          
      def print_variables(self):
          print('{} {}'.format(self.first_var, self.second_var))
          
  e = Example('abc', 123)
  e.print_variables()
  ```

  

- `__str__()`用来设置打印类对象(instance)的时候，显示的信息，需要返回一个string

  ```python
  class Person:
      def __init__(self, name, age):
          self.name = name
          self.age = age
          
      def __str__(self):
          return 'Person: {}'.format(self.name)
      
  jack = Person('Jack', 82)
  print('This is the string presentation of jack: {}'.format(jack))
  ```

- 类的变量和类对象的变量

  ```python
  ## Class variables vs instance variables
  Class variables are shared between all the instances of that 
  class whereas instance variables can hold different values between different instances of that class.
  ```

  示例

  ```python
  class Example:
      # These are class variables
      name = 'Example class'
      description = 'Just an example of a simple class'
  
      def __init__(self, var1):
          # This is an instance variable
          self.instance_variable = var1
  
      def show_info(self):
          info = 'instance_variable: {}, name: {}, description: {}'.format(
              self.instance_variable, Example.name, Example.description)
          print(info)
  
  
  inst1 = Example('foo')
  inst2 = Example('bar')
  
  # name and description have identical values between instances
  assert inst1.name == inst2.name == Example.name
  assert inst1.description == inst2.description == Example.description
  
  # If you change the value of a class variable, it's changed across all instances
  Example.name = 'Modified name'
  inst1.show_info()
  inst2.show_info()
  ```

  

- 类对象变量的获取和修改

  ```python
  class Person:
      def __init__(self, age):
          self._age = age
          
  example_person = Person(age=15)
  # 以下两行代码都会报错，或者无效修改
  # print(example_person.age)
  # example_person.age = 16
  ```

- 想要参数可读，但不可以修改可以添加`@property`

  ```python
  class Person:
      def __init__(self, age):
          self._age = age
          
      @property
      def age(self):
          return self._age
          
  example_person = Person(age=15)
  # Now you can do this:
  print(example_person.age)
  # But not this:
  # example_person.age = 16
  ```

- 继承关系

  ```python
  class Animal:
      def greet(self):
          print('Hello, I am an animal')
  
      @property
      def favorite_food(self):
          return 'beef'
  
  
  class Dog(Animal):
      def greet(self):
          print('wof wof')
  
  
  class Cat(Animal):
      @property
      def favorite_food(self):
          return 'fish'
      
  dog = Dog()
  dog.greet()
  print("Dog's favorite food is {}".format(dog.favorite_food))
  
  cat = Cat()
  cat.greet()
  print("Cat's favorite food is {}".format(cat.favorite_food))
  
  
  # wof wof
  # Dog's favorite food is beef
  # Hello, I am an animal
  # Cat's favorite food is fish
  ```

  
