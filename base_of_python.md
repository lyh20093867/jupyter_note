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
# 字符编码问题，ASCII编码、GB2312编码、UTF-8编码、Unicode编码
# ASCII是一个字节，Unicode通常是2个字节，一个中文至少两个字节
# Unicode编码可以解决所有的编码问题，但是如果是英文的用Unicode就浪费空间，UTF-8是可变长的编码。
# UTF-8编码把一个Unicode字符根据不同的数字大小编码成1-6个字节，常用的英文字母被编码成1个字节，汉字通常是3个字节，
# 只有很生僻的字符才会被编码成4-6个字节。如果你要传输的文本包含大量英文字符，用UTF-8编码就能节省空间
# 在计算机内存中，统一使用Unicode编码，当需要保存到硬盘或者需要传输的时候，就转换为UTF-8编码。
# 用记事本编辑的时候，从文件读取的UTF-8字符被转换为Unicode字符到内存里，编辑完成后，保存的时候再把Unicode转换为UTF-8保存到文件
# python3中是使用unicode编码的，支持多语言
print('包含中文的字符串str')
# ord()函数获取字符的整数表示，chr()将编码转成对应的字符
print(ord('中'))# 输出的结果为20013
print(chr(ord('中')))
print(ord('文'))# 25991
print(chr(25991))

print('\u4e2d')# 中
print('\u6587') # 文

# python中，bytes类型在前面用前缀b表示,bytes的每个字符只占用一个字节
print('ABC')
print(b'ABC')
print(ord('B'))
print(type(b'ABC'))
```

    包含中文的字符串str
    20013
    中
    25991
    文
    中
    文
    ABC
    b'ABC'
    66
    <class 'bytes'>



```python
# encode()和decode()进行编解码,通过encode编码后就将字符串变成了bytes类型了,在python中无法显示为ASCII字符的字节，用\x##表示
print('ABC'.encode('ascii'))
print('你好'.encode('utf-8'))
# 解码
print(b'\xe4\xbd\xa0\xe5\xa5\xbd'.decode('utf-8'))
print(b'\xe4\xbd\xa0\xe5\xa5\xbd')
# print(b'\xe4'.decode('utf-8')) # 无法解码，会报错
# 使用ignore对小部分错误进行忽略
# print(b'中') # bytes can only contain ASCII literal characters
# print(b'\xe4\xb8\xad\xff'.decode('utf-8'))
print(b'\xe4\xb8\xad\xff'.decode('utf-8',errors='ignore'))
# 在编写代码时，如果包含了中文，一定要使用中文编码，并且在另存为进行保存的时候也一定要使用utf-8进行保存  
# #!/usr/bin/env python3
# -*- coding: utf-8 -*-


# 格式化 在python中使用%的方式进行格式化，也可以使用format()函数进行格式化,里面使用{0} {1}等进行占位
# 在字符串内部,%s表示字符串替换，%d表示整数替换,%f表示浮点数，%x表示十六进制数，%?表示占位的意思，如果只有一个占位，括号可以不用写
# 如果%是一个普通字符，需要使用%%来进行转义 
print('Hello,%s!' % 'zhangsan')
print('hello,%s,your age is %d? your height is %f ?' % ('zhangsan',18,173.5))# 默认保留小数点后6位

print('Hello,{0},your age is {1}? your height is {2:.6f} ?'.format('zhangsan',18,173.5))
```

    b'ABC'
    b'\xe4\xbd\xa0\xe5\xa5\xbd'
    你好
    b'\xe4\xbd\xa0\xe5\xa5\xbd'
    中
    Hello,zhangsan!
    hello,zhangsan,your age is 18? your height is 173.500000 ?
    Hello,zhangsan,your age is 18? your height is 173.500000 ?



```python
# list list中可以允许重复,可以存储不同类型的值，可以存list等复杂类型的元素,并且保留了存入的先后顺序了的
name=['zhangsan','lisi','wangwu','zhangsan']
print(name)
# 创建一个空列表并添加元素,需要注意的是append()方法返回的是None类型的object,append是将元素追加到列表末尾
names = []
names.append('zhangsan')
names.append('lisi')
names.append('wangwu')
names.append('zhangsan')
print(names)
print(name == names) # True，在python中==是比较值大小，如果相同则为真
# print(name.length()) # 报错
print(len(name))
print('---------取值------------')
# 根据index取值
print(name[0])
# 取最后一个元素，有如下写法：-1默认是取一个列表的最后一个元素,整数是从前向后取，并且从0开始，负数是从后向前取，并且是从-1开始
print(name[-1])
print(name[len(name)-1])
# 取倒数第二个数
print('倒数第二个数:',name[-2])
print('-------------插入元素到指定位置----------')
print(name.insert(3,'Mike'))
name.insert(0,'ligang')
print(name)
print('-------------使用pop删除元素,pop()方法会将被弹出的元素作为值返回----------')
print('删除最后一个元素，最后一个元素是:',name.pop())
print(name)
name.pop(0)
print(name)
print('--------存入一个复合元素--------------')

mingxing=['huangxiaoming','fanbingbing','licheng']
name.insert(2,mingxing)
print(name)
# 在name中获取mingxing中的第二个元素
print('mingxing中第二个元素为:',name[2][1])
print('--------遍历--------------')
#遍历列表
for a in name:
    print(a)
# for i in 0  len(name):
#     print(name[i])
    
```

    ['zhangsan', 'lisi', 'wangwu', 'zhangsan']
    ['zhangsan', 'lisi', 'wangwu', 'zhangsan']
    True
    4
    ---------取值------------
    zhangsan
    zhangsan
    zhangsan
    倒数第二个数: wangwu
    -------------插入元素到指定位置----------
    None
    ['ligang', 'zhangsan', 'lisi', 'wangwu', 'Mike', 'zhangsan']
    -------------使用pop删除元素,pop()方法会将被弹出的元素作为值返回----------
    删除最后一个元素，最后一个元素是: zhangsan
    ['ligang', 'zhangsan', 'lisi', 'wangwu', 'Mike']
    ['zhangsan', 'lisi', 'wangwu', 'Mike']
    --------存入一个复合元素--------------
    ['zhangsan', 'lisi', ['huangxiaoming', 'fanbingbing', 'licheng'], 'wangwu', 'Mike']
    mingxing中第二个元素为: fanbingbing
    --------遍历--------------
    zhangsan
    lisi
    ['huangxiaoming', 'fanbingbing', 'licheng']
    wangwu
    Mike



```python
# 元祖 tuple，使用需要被初始化，并且一旦被初始化后就不能修改，是一种有顺序的列表
zs=('zhangsan',23,176.23,'上海')
print('zs的几个元素分别是，第一个:%s,第二个:%d,第三个:%.3f,四:%s' % (zs[0],zs[1],zs[2],zs[3]))
print('空tuple:',())
# 需要注意的是，如果只有一个元素的元祖时，一定要在元素后面添加,以跟运算符(1)进行区分
print('1元祖',(23,))
print('--------元祖中存入复合元素--------------')
# 需要注意的是，元祖中的元素不可变是指引用的内存的地址不可变（指向不可变），但是如果元祖中存储的数复合元素比如列表时，是可以修改这个复合元素中的内容的，不过此时复合元素引用的内存地址是没有变化的
kebian=('1','A',['zs','lis'])
print(kebian)
kebian[2][1]='zhangsan'
print(kebian)
```

    zs的几个元素分别是，第一个:zhangsan,第二个:23,第三个:176.230,四:上海
    空tuple: ()
    1元祖 (23,)
    --------元祖中存入复合元素--------------
    ('1', 'A', ['zs', 'lis'])
    ('1', 'A', ['zs', 'zhangsan'])



```python
# 条件判断
age = 90
if age > 80:
    print("older")
elif age> 18:
    print("adult")
elif age >= 6:
    print("teenager")
else:
    print("baby")
    
    
a=int(input('year:'))
if a > 2000:
    print("00后")
elif a> 1990:
    print("90后")
elif a > 1980:
    print("80后")
else:
    print("其他")
```

    older
    year:2010
    00后



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
