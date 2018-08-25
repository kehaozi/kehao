---
title: python的可变变量和不可变变量
tags: python,可变变量,不可变变量
grammar_cjkRuby: true
---

#### python可变变量与不可变变量

1. 可变变量

> 顾名思义，就是可以被改变的变量，比如int float string类型都是可变变量
> 可变变量作为函数的参数时，是不会被真正改变的
> 举例

``` python?linenums
a = 1

def setvalue(a):
    a = 100
    print(a)
    
setvalue(a)
print(a)
```
> 打印结果分别是 100  1
> 为什么不同呢
> 这里到底是变量作用域的问题还是可变变量的问题呢？
> 是可变变量的问题
> 函数被执行的时候，a作为参数传给函数，函数内部因为更改了这参数的值，其实是新创建了一个引用或者说内存指向到100这个数。如果函数内部不更改这个值，比如只打印，则是不会创建新对象的。
> 在函数内部，打印这个变量，则是作用域的问题，找到这个变量是在局部空间，则打印100
> 最后一个print(a) ，由于是在函数外部，则依据LEGB(location- enclosure - global - builtin的变量查找顺序）规则，在global空间找到a，且a并没有被函数内部所改变，这则是可变变量和不可变变量的问题，则打印1


2. 可变变量
> list 类型，dict类型都是可变变量

``` python?linenums
a = [1]

def setvalue(a):
    a[0] = 100
    print id(a[0])
    print(a[0])
    
setvalue(a)
print id(a[0])
print(a[0])
```
> 这个的打印结果是100 100
> 因为List类型是可变变量 ，在函数内部执行的时候，作为参数传入的list类型的a，的确被改变了
> 因此，两处打印是一个结果
