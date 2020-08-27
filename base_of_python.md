```python
# 调用print方法输出hello world
print("hello world!")
# 直接进行计算
print(100+1230+200)
# 进行幂运算
print(2**10)
# print()函数会将传递的参数标准输出
# 也可以使用input()函数等待用户输入内容，下面将输入的内容赋值给一个变量name
name = input()
# 同时，print()函数可以接受多个参数，参数之间使用,进行隔开
print("name:",name)
```

    hello world!
    1530
    1024
    lisi
    name: lisi



```python
# 打印一个数的绝对值
# a=input()
# a=-25
a=23
if a >= 0:
    print(a)
else:
    print(-a)
```

    23



```python
# 需要注意的是python中是大小写敏感的，并且必须要每次是4个空格缩进
# 数据类型和变量，在python中分为整数、浮点数、字符串、空值、变量、常量、
print(1)
# 0x表示16进制的数
print(0xff00)
# 浮点数
print(1.23e9)
print(3.2)
# 字符串
print("I\'m \'OK\'.")
print('I\'m \"OK\".')
# r''表示''内部的字符串默认不转义，跟scala中的""""""类似
print(r'\t,\r\n,\,\\')
```

    1
    65280
    1230000000.0
    3.2
    I'm 'OK'.
    I'm "OK".
    \t,\r\n,\,\\
    zhangsan
    shuo
    sm
    
    dfkjs
    	
    \
    fdsfj
    ... 第武行 ...
    ... 结束
    
    zhangsan
    shuo
    sm
    
    dfkjs
    \t
    \\
    fdsfj
    ... 第武行 ...
    ... 结束
    



```python
# """"""可以分为多行书写,并且可以在前面添加r，让""""""中的数据不发生转义，另外""""""也可以换成''''''
print("""zhangsan
shuo
sm

dfkjs
\t
\\
fdsfj
... 第武行 ...
... 结束
""")
print(r"""zhangsan
shuo
sm

dfkjs
\t
\\
fdsfj
... 第武行 ...
... 结束
""")
```


```python
# 布尔值，只有为True和False,此处的大小写不能chucuo 
print(True)
print(False)
print(3>2)
print(4<2)

print("or运算:",4 < 3 or 5>3)
print("not运算:",not 4<3)

age=17
if age>18:
    print("成年人...")
else:
    print("未成年人...")
```

    True
    False
    True
    False
    or运算: True
    not运算: True
    未成年人...



```python
# 空值 None，跟scala中的Unit或者null有什么区别?
# 变量本身类型不固定，为弱类型语言，也称为动态语言，而java为强类型语言
# a='ABC'  1、在内存中创建了一个'ABC'的字符串;2、在内存中创建了一个a的变量，指向了'ABC'
a= 'ABC'
print(a)
b=a # 此处是指将b这个变量指向a这个变量指向的'ABC'，b最终是指向的'ABC'而不是a这个变量
a='XYZ'
print(b)#需要注意的是，此处打印的是'ABC'而不是'XYZ'
```

    ABC
    ABC



```python
# python中有两种除法:/和//,//永远为整数,并且只会舍弃，不会入
print(10/3)
print(10/2)
print("-----------------")
print(10//3)
print(10//2)
print(10//6)
print(13//5)
print("-----------------")
print(10%3)
# python中对整数没有大小限制，对浮点数也没有大小限制，但是超出一定范围的浮点数就表示为inf，意为无限大
print(12.231122222222222222222222223)
print(234444444444444444344444444444433333333333336.3)
```

    3.3333333333333335
    5.0
    -----------------
    3
    5
    1
    2
    -----------------
    1
    12.231122222222222
    2.3444444444444444e+44



```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python


```


```python
print(name)
```

    lisi



```python

```


```python

```


```python

```


```python

```


```python

```
