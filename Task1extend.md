# Python 基础教学  

## 使用kaggle  
kaggle是数据科学社区，拥有大量竞赛、数据集、案例代码、以及代码运行环境（Notebook）  
注册kaggle账号后，`Create` -> `New notebook` 通过Notebook进行Python代码运行及交互  
## Python介绍
Python 的设计具有很强的可读性，并且拥有庞大的运行库，可以拓展很多功能，几乎任何需求都可以方便地使用python进行开发。  
我们会先跳过Python的运行环境搭建，以及相关的计算机知识，聚焦如何使用python语言本身，通过在线的notebook一键运行，更多内容大家自行补充（要学会使用网络检索、官方文档检索来查找自己需要的功能）  
推荐网站：https://www.runoob.com/python3/python3-tutorial.html

## Python基础语法
用print()函数进行输出
```
print('Hello World')
```

输出别的变量
```
a = 1
b = 2
c = a + b
d = 'GTIIT'
print(c)
print(d)
```
认识函数
```
# 定义一个函数
def myFunction(input_value):
  return input_value * 20


print('Hello Python')
input('Please enter anything')
ans = myFunction(20)  # 调用函数，输入20，并获得返回值（函数的输出值），赋值给ans
print(ans)
```
进行一些数学公式计算：斐波那契数列 f(n) = f(n-2) + f(n-1) 
```
a,b = 1,1
for i in range (3,10):
  print(f'The {i}-th num is {a+b}')
  a = b
  b = a+b
```
也可以用递归的方式实现

```
def fibo(n):
  if n == 1:
    return 1
  return fibo(n-1) + fibo(n-2)

print(fibo(10))
```

## 数据类型
Python3 中常见的数据类型有：
Number（数字）
String（字符串）
bool（布尔类型）
List（列表）
Tuple（元组）
Set（集合）
Dictionary（字典）

常用：数字、字符串、布尔、列表、字典


## 循环
```
for <variable> in <sequence>:
    <statements>
```
打印列表中的所有元素
```
a = ['1', 123, 'GTIIT', 4, 5, 6]
for i in a:
  print(i)
```
自动生成一个（迭代器）递增数列
```
for i in range(10):
  print(i)
```

## 导入模块和新函数
```
import os
file_list = os.listdir('')
print(file_list)
```

## 通过kaggle数据集Titanic熟悉更多数据相关的Python技术



