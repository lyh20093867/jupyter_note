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
# 对列表中的元素排序
print(names)
names.sort()
print(names)
```

    ['zhangsan', 'lisi', 'wangwu', 'zhangsan']
    ['lisi', 'wangwu', 'zhangsan', 'zhangsan']



```python

```


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
    
# 下面的代码，隐含一个知识点：如果前面判断大于2000成立后，就执行之前的分支，不再做后面的分支判断了    
# 另外，input函数获取的是一个字符串，需要使用int()转换后才能跟int进行比较
a=int(input('year:'))
if a > 2000:
    print("00后")
elif a> 1990:
    print("90后")
elif a > 1980:
    print("80后")
else:
    print("其他")
    

# 在python中，if else可以有结果，但是写法跟scala不一致，如下，但是只能接一个分支
aa="older" if age > 80 else "adult"
print(aa)
# if判断式简写：下面的x只要是非零数值，非空的字符串，非空的list等就判断为True，否则就为False
x=2
if x :
    print("True:",x)
else :
    print("False:",x)
```

    older
    year:40
    其他
    older
    True: 2



```python
# python中**表示多少次方
print(5**2)
print(5**3)
# 判断体重
height=1.75
weight = 80.5
bmi = weight/(height ** 2)
if bmi < 18.5:
    print("过轻")
elif bmi>=18.5 and bmi < 25:
    print('正常')
elif bmi>=25 and bmi <28:
    print('过重')
elif bmi >= 28 and bmi <32:
    print('肥胖')
else:
    print('严重肥胖')
```

    25
    125
    过重



```python
# 循环
names= ['zs','ls','ww']
for name in names:
    print(name)
# 从1+到100的结果,需要注意的是，range是前闭后开range(0,2)只有0,1两个元素
sum = 0
for i in range(1,11):
    sum = sum + i
print(sum)
sum=0
for i in [1,2,3,4,5,6,7,8,9,10]:
    sum = sum + i
print("two:",sum)  
# range()函数用于生成一个整数序列，list()函数将整数序列转换成列表
sum = 0
for i in list(range(101)):
    sum = sum +i
print('three',sum)   

# while 循环
sum = 0
n = 100
while n > 0:
    sum = sum +n
    n = n -1
print(sum) 

# 在循环中，可以使用break语句提前退出循环
n = 1
while n <100:
    if n > 10:
        break # 当n>10的时候直接退出循环
    print(n)
    n = n +1
print('END')    
# 在循环中使用continue语句跳过当前的循环，直接进入下一次循环

```

    zs
    ls
    ww
    55
    two: 55
    three 5050
    5050
    1
    2
    3
    4
    5
    6
    7
    8
    9
    10
    END



```python
# 使用dict和set 
# python内置了字段，也就是map，k-v存储
# lsit列表
names = ['mick','licky','tracy']
scores = [95,75,85]
# dict,map
d = {'mick':95,'Bob':75,'Tracy':85}
# 获取字典中的值
print(d['mick'])
print(len(d))
# 向字段中添加元素，多次对一个key放入value，后面的值会被前面的值冲掉
d['A'] = 45
print(d['A'])
d['A'] = 54
print(len(d))
print(d['A'])
# 如果key不存在，dict就会报错
if a in d:
    print(d['a'])
else:
    print("a is not in d")
# d['a'] = 23    
if d.get('a'):
    print(d['a'])
else:
    print('a is not in d')
# 也可以通过get()方法指定默认值
print(d.get('a',43))
# 使用pop(key)删除字典中的元素，并且把删除的元素返回
print(d['A'])
print('删除A元素，并且把A的值返回：',d.pop('A'))
print('获取删除后的元素，没有获取了默认值：',d.get('A',33))
# dict 内部存放的顺序和key放入的顺序没有关系,并且dict的key是不可变的
# 因此字符串和整数都可以作为dict的key，但是list是可变的，不能作为dict的key

# set,set中存放的元素不能有重复，但是可以有不同类型的元素
# 要创建一个set，需要将一个list作为输入集合
s = set(['2',2,3,'5','3'])
print(len(s))
print(s)
# 创建一个空set

m = set()
print(len(m))
# 向集合中插入元素
m.add('3')
m.add(3)
m.add('3')
m.add("zangsna")
m.add((1,24,3))
# 在集合中不能存入list,因为set中只能存入不可变对象，而list是可变的，可以插入元祖，因为元祖是不可变的
# m.add(['zs','li',23])
print(m)
# ss = set(['sdf'],[343,'34'])
# print(ss)
# 集合中通过remove()删除元素,并且没有返回值
print(m.remove('zangsna'))
print(m)
# 对集合求交集
joins = s & m
print(type(joins))
# 对集合求并集
unions = s | m 
print(unions)
```

    95
    3
    45
    4
    54
    a is not in d
    a is not in d
    43
    54
    删除A元素，并且把A的值返回： 54
    获取删除后的元素，没有获取了默认值： 33
    5
    {'5', 2, 3, '2', '3'}
    0
    {'3', 3, 'zangsna', (1, 24, 3)}
    None
    {'3', 3, (1, 24, 3)}
    <class 'set'>
    {'5', 2, 3, '2', '3', (1, 24, 3)}



```python
# 调用函数，在调用函数的时候，如果传入的参数不对，会报类型错误，typeError 求绝对值abs()
print('求绝对值：',abs(-20))
# print('求绝对值',abs(-20,0.2))#TypeError: abs() takes exactly one argument (2 given)
print('求最大值：',max(23,44,54,12),'求最小值：',min(23,44,54,12))
# 数据类型转换 int()转成整数类型,float()转成浮点数类型，str()转成字符串，bool()转成布尔值类型
print('对空字符串转bool类型：',bool(''),'对None转bool类型：',bool(None),'对0转bool类型：',bool(0),'对0.0转bool类型：',bool(0.0),)
print('对\'3\'串转bool类型：',bool('3'),'对0.3转bool类型：',bool(0.3),'对3.0转bool类型：',bool(3.0),)

# 对函数取别名
aa = abs
print('通过别名aa，调用绝对值函数:',aa(-23))
# hex()把一个整数转成十六进制数
print('255转十六进制：',hex(255),'1000转十六进制：',hex(1000))
# 将十六进制转成10进制
# print(int('0xff'))

```

    求绝对值： 20
    求最大值： 54 求最小值： 12
    对空字符串转bool类型： False 对None转bool类型： False 对0转bool类型： False 对0.0转bool类型： False
    对'3'串转bool类型： True 对0.3转bool类型： True 对3.0转bool类型： True
    通过别名aa，调用绝对值函数: 23
    255转十六进制： 0xff 1000转十六进制： 0x3e8
    23
    自定义函数my_abs: None



```python
# 定义函数，定义一个函数要使用def语句，依次写出函数名、括号、括号中的参数和冒号:，然后，在缩进块中编写函数体，函数的返回值用return语句返回
# 如果没有return语句，函数执行完毕后也会返回结果，只是结果为None。return None可以简写为return
def my_abs(x):
    if x >= 0:
        return x
    else:
        return -x

# 调用自己定义的函数
print('自定义函数my_abs:',my_abs(23))
# print('自定义函数my_abs:',my_abs('-24')) # 会报TypeError
# 对参数类型进行检查
def my_abs2(x):
    if not isinstance(x,(int,float)):
        # 此处抛出了一个错误
        raise TypeError('wrong type,input int or float!')
    if x>= 0:
        return x
    else:
        return -x
    
# print('自定义参数2：',my_abs2('-25'))

# 定义空函数，如果想定义一个什么事也不做的空函数，可以用pass语句
# pass可以用来作为占位符，比如现在还没想好怎么写函数的代码，就可以先放一个pass，让代码能运行起来
# pass可以放在任何位置
def nop():
    if age > 18:
        pass

print(nop())    
```

    自定义函数my_abs: 23



    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-3-c756f7123133> in <module>
         19         return -x
         20 
    ---> 21 print('自定义参数2：',my_abs2('-25'))
         22 
         23 # 定义空函数，如果想定义一个什么事也不做的空函数，可以用pass语句


    <ipython-input-3-c756f7123133> in my_abs2(x)
         13 def my_abs2(x):
         14     if not isinstance(x,(int,float)):
    ---> 15         raise TypeError('wrong type,input int or float!')
         16     if x>= 0:
         17         return x


    TypeError: wrong type,input int or float!



```python
# 函数中返回多个值，python中返回的多个值，是一个tuple，如果是一个tuple，可以将()省略
import math
def move(x,y,step,angle=0):
    nx = x + step * math.cos(angle)
    ny = y + step * math.sin(angle)
    return nx,ny

nx,ny= move(100,100,60,math.pi / 4)
print(nx,ny)
ne = move(100,100,60,math.pi/4)
print(ne)

```

    142.42640687119285 142.42640687119285
    (142.42640687119285, 142.42640687119285)
    (1.0, 1.0)
    该函数不是一元二次函数
    0.5
    该函数不是一元二次函数
    函数无解
    None
    quadratic(2, 3, 1) (2.25, -3.75)
    quadratic(2, 3, 1) = (2.25, -3.75)
    quadratic(1, 3, -4) = (1.5, -4.5)
    测试失败



```python
import math
# 请定义一个函数quadratic(a, b, c)，接收3个参数，返回一元二次方程 ax^2+bx+c=0 ax 
# 2+bx+c=0 的两个解
def quadratic(a,b,c):
    if(a== 0):
        print('该函数不是一元二次函数')
        if(b==0):
            if(c!=0):
                print('函数无解')
                return
            else:
                print('函数有无数解')
                return
        else:
            return -c/b
     # 判断函数是否有解
    m = math.pow(b,2) - 4*a*c
    o = math.sqrt(m)/(2*a)
    n = -b/(2*a)
    if(m<0):
        print('函数无解')
        return
    if(m == 0):
        return n,n
    if(m>0):
        return n +o,n-o
# print(math.pow(2,10))
print(quadratic(1,-2,1))
# print(quadratic(0,-2,1))
# print(quadratic(0,0,1))
print('quadratic(2, 3, 1):',quadratic(2, 3, 1))
# 测试
print('quadratic(2, 3, 1) =', quadratic(2, 3, 1))
print('quadratic(1, 3, -4)=', quadratic(1, 3, -4))

if quadratic(2, 3, 1) != (-0.5, -1.0):
    print('测试失败')
elif quadratic(1, 3, -4) != (1.0, -4.0):
    print('测试失败')
else:
    print('测试成功')
```

    (1.0, 1.0)
    quadratic(2, 3, 1): (-0.5, -1.0)
    quadratic(2, 3, 1) = (-0.5, -1.0)
    quadratic(1, 3, -4)= (1.0, -4.0)
    测试成功



```python

# 函数定义中的默认参数、可变参数、关键参数
# 下面的函数power(x)必须要传入一个参数，且只能传递一个参数
# def power(x):
#     return x * x
# print(power(3))

# 下面的n为默认参数，默认参数必须要在所有的必选参数的后面；
# 如果一个函数中定义了多个默认参数的时候，要用定义的默认参数的顺序调用
# 如果不用默认参数的顺序调用，需要显式指定默认参数，如:age=23
# 默认参数必须要指向不可变的对象
def power(x,n=2):
    s = 1
    while n>0:
        s = s * x
        n = n -1
    return s    
print('计算2的10次方:',power(2,10))
print('计算2的2次方：',power(2))


# 定义一个传入list的带默认参数的函数
# 下面这种定义方式不对，L指向了[]这个可变的对象
# def add_end(L=[]):
#     L.append('END')
#     return L

def add_end(L=None):
    if L is None:
        L = []
    L.append('END')
    return L


print(add_end())
print(add_end())
print(add_end())

# 定义一个带可变参数的函数，在python中，可变参数使用*开头表示，scala中使用变量*表示
def calc(*numbers):
    sum = 0
    for n in numbers:
        sum = sum + n*n
    return sum
print(calc(2))
print(calc(1,2))
print(calc(1,2,3))
nums = [1,2,3,4,5]
num=(1,2,3,4,5)
# 在python中，可以将list和tuple作为可变参数传递到函数中，在前面添加*即可
print(calc(*nums))
print(calc(*num))
```

    计算2的10次方: 1024
    计算2的2次方： 4
    ['END']
    ['END']
    ['END']
    4
    5
    14
    55
    55



```python
# 定义关键字参数，
#可变参数允许你传入0个或任意个参数，这些可变参数在函数调用时自动组装为一个tuple。
#而关键字参数允许你传入0个或任意个含参数名的参数，这些关键字参数在函数内部自动组装为一个dict
# *args是可变参数，args接收的是一个tuple；
# **kw是关键字参数，kw接收的是一个dict。
def person(name,age,**kw):
    kw['city']='tianjing' # 此处修改传递进来的城市，此处的修改不会影响函数外面的dict
    print('name:',name,'age:',age,'other:',kw)

person('ls',34)
person('Bob',23,city='BJ',gend='男')
extra={'city':'Bj','job':'teacher','home':'shang','interests':'足球，篮球'}
person('ll',24,**extra)#此处传入的关键字参数是对外面定义的dict的拷贝，里面的修改不会改变外面的内容
print(extra['city'])

# 使用命名关键字参数限制名字
# 定义命名的关键字参数在没有可变参数的情况下不要忘了写分隔符*，否则定义的将是位置参数。
extra2={'city':'Bj','job':'teacher'}
def person2(name,age,*,city,job):
    print(name,age,city,job)
person2('lsa',23,**extra2)
# person2('lsa',23,**extra)    # 此处会报错

# python中可以是多种参数的组合，但是参数定义的顺序必须是：必选参数、默认参数、可变参数、命名关键字参数和关键字参数。
def f2(a, b, c=0, *, d, **kw):
    print('a =', a, 'b =', b, 'c =', c, 'd =', d, 'kw =', kw)
def f1(a, b, c=0, *args, **kw):
    print('a =', a, 'b =', b, 'c =', c, 'args =', args, 'kw =', kw)
    
args = (1, 2, 3, 4)
args2 = (1, 2, 3)
kw = {'d': 99, 'x': '#'}
f1(*args,**kw)
# f2(*args,**kw)# 此处会报错
f2(*args2,**kw)
```

    name: ls age: 34 other: {'city': 'tianjing'}
    name: Bob age: 23 other: {'city': 'tianjing', 'gend': '男'}
    name: ll age: 24 other: {'city': 'tianjing', 'job': 'teacher', 'home': 'shang', 'interests': '足球，篮球'}
    Bj
    lsa 23 Bj teacher
    a = 1 b = 2 c = 3 args = (4,) kw = {'d': 99, 'x': '#'}
    a = 1 b = 2 c = 3 d = 99 kw = {'x': '#'}



```python
# 接收一个或多个数并计算乘积
def product(*numbers):
    res = 1
    if len(numbers)<=0:
        raise TypeError
    for n in numbers:
        res = res * n
    return res
print('product(5) =', product(5))
print('product(5, 6) =', product(5, 6))
print('product(5, 6, 7) =', product(5, 6, 7))
print('product(5, 6, 7, 9) =', product(5, 6, 7, 9))
# print(product())
if product(5) != 5:
    print('测试失败!')
elif product(5, 6) != 30:
    print('测试失败!')
elif product(5, 6, 7) != 210:
    print('测试失败!')
elif product(5, 6, 7, 9) != 1890:
    print('测试失败!')
else:
    try:
        product()
        print('测试失败!')
    except TypeError:
        print('测试成功!')
```

    product(5) = 5
    product(5, 6) = 30
    product(5, 6, 7) = 210
    product(5, 6, 7, 9) = 1890
    测试成功!



```python
# 递归函数，下面的fact不是尾递归
def fact(n):
    if n == 1:
        return 1
    return n * fact(n -1)
print(fact(5))
# 理论上，所有的递归函数都可以写成循环的方式，但循环的逻辑不如递归清晰。
# 解决递归调用栈溢出的方法是通过尾递归优化，事实上尾递归和循环的效果是一样的，
# 所以，把循环看成是一种特殊的尾递归函数也是可以的。
# 尾递归是指，在函数返回的时候，调用自身本身(只是会修改传入的参数)，并且，return语句不能包含表达式

# 将上面的函数修改为尾递归函数

def fact2(n):
    return fact3(n,1)

def fact3(n,product):
    if n == 1:
        return product
    return fact3(n-1,n * product) #
print(fact2(5))
# 大多数编程语言没有针对尾递归做优化，Python解释器也没有做优化，所以，即使把上面的fact(n)函数改成尾递归方式，也会导致栈溢出

# 编写一个汉诺塔移动 
# 编写move(n, a, b, c)函数，它接收参数n，表示3个柱子A、B、C中第1个柱子A的盘子数量，然后打印出把所有盘子从A借助B移动到C的方法

def move(n,a,b,c):
    

```

    120
    120



```python
# 但是在Python中，代码不是越多越好，而是越少越好。代码不是越复杂越好，而是越简单越好。
# python中的高级特性：切片、迭代、列表生成式、生成器、迭代器
```


```python
# 切片 python针对列表等需要取其中的多个元素提供的操作，不需要遍历就可以直接取结果
# 对列表进行切片
l = ['zs','ls','ww','jack']
# 使用倒数切片，-1表示获取最后一个元素，从后向前数第0个元素
print(l[-1])
# 切片操作中，是前闭后开,不包含最后的一个元素
print(l[0:2])
print(l[0:-1])
print(l[0:-2])
print(l[:-1])
# 0: 表示取0到最后一个元素，获取所有的元素
print(l[0:])
L= list(range(100))
print('L的长度:',len(L),'获取最后一个元素:',L[-1],'获取最后两个元素：',L[-2:])
print('获取L的前10个元素：',L[:10],'获取最后10个元素:',L[-10:])
# 切片还可以指定步长
print('获取1前面10个数，每3个取一个数:',L[:10:3])
print('所有数，每5个取一个：',L[::5])
print('获取所有的数据：',L[:])
```

    jack
    ['zs', 'ls']
    ['zs', 'ls', 'ww']
    ['zs', 'ls']
    ['zs', 'ls', 'ww']
    ['zs', 'ls', 'ww', 'jack']
    L的长度: 100 获取最后一个元素: 99 获取最后两个元素： [98, 99]
    获取L的前10个元素： [0, 1, 2, 3, 4, 5, 6, 7, 8, 9] 获取最后10个元素: [90, 91, 92, 93, 94, 95, 96, 97, 98, 99]
    获取1前面10个数，每3个取一个数: [0, 3, 6, 9]
    所有数，每5个取一个： [0, 5, 10, 15, 20, 25, 30, 35, 40, 45, 50, 55, 60, 65, 70, 75, 80, 85, 90, 95]
    获取所有的数据： [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30, 31, 32, 33, 34, 35, 36, 37, 38, 39, 40, 41, 42, 43, 44, 45, 46, 47, 48, 49, 50, 51, 52, 53, 54, 55, 56, 57, 58, 59, 60, 61, 62, 63, 64, 65, 66, 67, 68, 69, 70, 71, 72, 73, 74, 75, 76, 77, 78, 79, 80, 81, 82, 83, 84, 85, 86, 87, 88, 89, 90, 91, 92, 93, 94, 95, 96, 97, 98, 99]



```python
# 对元祖进行切片
t=tuple(range(100))
print('获取元祖前两个：',t[:2])
print('获取元祖的后两个:',t[-2:])
print('获取元祖的前10个，步长3：',t[:10:3])
print('获取元祖的所有元素，每隔8取出:',t[::8])
print('获取所有元素：',t[:])
# 对字符串进行切片，字符串也可以看成list,每个元素就是一个字符
s='ABCDEFG'
print('对字符串切片操作，获取字符串的前5位：',s[:5])
print('对字符串切片操作，获取字符串的后5位：',s[-5:])
ss = ' ABCDE '
print('对字符串切片操作，获取字符串的后1位：'ss[:5])#  此处会报错

```


      File "<ipython-input-85-c38d99807ccd>", line 13
        print('对字符串切片操作，获取字符串的后1位：'ss[:5])
                                    ^
    SyntaxError: invalid syntax




```python
# 利用切片操作，实现一个trim()函数，去除字符串首尾的空格，注意不要调用str的strip()方法
def trim(s):
    
```


```python
# 迭代 给定一个list或tuple，我们可以通过for循环来遍历这个list或tuple，这种遍历我们称为迭代（Iteration）
# 对dict进行迭代,默认是对key进行迭代
d = {'a':1,"b":2,"c":3,'d':4}
for key in d:
    print('key:',key,",value:",d[key])

# 对value进行迭代
for v in d.values():
    print('value:',v)
# 对k和v同时进行迭代
for k,v in d.items():
    print('k:%s,v:%s' % (k,v))
    
# 判断一个对象是否是可迭代的对象,需要通过collections模块中的Iterable进行判断
# list\tuple\字符串是可迭代的，数字不可迭代
from collections import Iterable
s2 = 'ABC'
print(s2,'是否可迭代？',isinstance(s2,Iterable))
print('124是否可迭代？',isinstance(124,Iterable))
print('124.0是否可迭代？',isinstance(124.0,Iterable))
print('\'124\'是否可迭代？',isinstance('124',Iterable))
# python中可以使用enumerate函数可以将list编程元素索引对
for i,value in enumerate(['A','c','B']):
    print(i,value)

for k,v in [('a',1),('b',2),('c',3)]:
    print(k,v)
    
print('请使用迭代查找一个list中最小和最大值，并返回一个tuple：')
def findMinAndMax(L):
    if (L is None) or (len(L) <= 0):
        return None,None
    mi = L[0]
    mx = L[0]
    for a in L:
        if mi >= a:
            mi = a
        if mx <= a:
            mx = a
    return mi,mx
L = [12,45,3,55,89,12,2]
print(findMinAndMax(L))
print(findMinAndMax([]))
# 测试
if findMinAndMax([]) != (None, None):
    print('测试失败!')
elif findMinAndMax([7]) != (7, 7):
    print('测试失败!')
elif findMinAndMax([7, 1]) != (1, 7):
    print('测试失败!')
elif findMinAndMax([7, 1, 3, 9, 5]) != (1, 9):
    print('测试失败!')
else:
    print('测试成功!')
```

    key: a ,value: 1
    key: b ,value: 2
    key: c ,value: 3
    key: d ,value: 4
    value: 1
    value: 2
    value: 3
    value: 4
    k:a,v:1
    k:b,v:2
    k:c,v:3
    k:d,v:4
    ABC 是否可迭代？ True
    124是否可迭代？ False
    124.0是否可迭代？ False
    '124'是否可迭代？ True
    0 A
    1 c
    2 B
    a 1
    b 2
    c 3
    请使用迭代查找一个list中最小和最大值，并返回一个tuple：
    (2, 89)
    (None, None)
    测试成功!



```python
# 列表生成式
l = list(range(0,10))
print(l)
l = list(range(1,10))
print(l)
# 用两种方式生成：[1x1, 2x2, 3x3, ..., 10x10] 即[1,4,9,16...100]
# 方法一：
l = []
for i in range(1,11):
    l.append(i * i)
print('第一种方法:',l)
# 方法二：
l = [x * x for x in range(1,11)]
print('第二种方法:',l)
# 列表生成式中添加判断，这个跟scala中的守卫类似
l = [x * x for x in range(1,11) if x % 2 == 0]
print(l)
# 使用双层循环,使用x和y两个变量来生成list
l = [str(x)+str(y) for x in range(1,11) if x % 3 ==0 for y in range(4,8)]
print('使用双层for循环生成列表:',l)

# 列出当前目录的的所有目录和文件
import os # 导入os模块
dirs = [d for d in os.listdir()]
print(dirs)
# 将L中的所有元素全部转成小写
L = ['Hello', 'World', 'IBM', 'Apple']
l = [a.lower() for a in L]
print(l)

# 在一个列表生成式中，for前面的if ... else是表达式，而for后面的if是过滤条件，不能带else
#下面的 for后面的i是过滤条件，不能有else
l = [x for x in range(1,13) if x % 2 ==0]
print(l)
# 下面for前面的内容是表达式，必须要能够求出一个结果
l = [x if x % 2 ==0 else -x for x in range(1,13)]
print(l) # 注意此处的结果

L = ['Hello', 'World', 18, 'Apple', None]
l = [x.lower() if isinstance(x,str) else x for x in L if x is not None]
L2 = [x.lower() for x in L if x is not None and isinstance(x,str)]
# 测试:
print(L2)
if L2 == ['hello', 'world', 'apple']:
    print('测试通过!')
else:
    print('测试失败!')
```

    [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
    [1, 2, 3, 4, 5, 6, 7, 8, 9]
    第一种方法: [1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
    第二种方法: [1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
    [4, 16, 36, 64, 100]
    使用双层for循环生成列表: ['34', '35', '36', '37', '64', '65', '66', '67', '94', '95', '96', '97']
    ['base_of_python.md', 'README.md', '.ipynb_checkpoints', '.git', 'base_of_python.ipynb']
    ['hello', 'world', 'ibm', 'apple']
    [2, 4, 6, 8, 10, 12]
    [-1, 2, -3, 4, -5, 6, -7, 8, -9, 10, -11, 12]
    ['hello', 'world', 'apple']
    测试通过!



```python
# 生成器 在Python中，这种一边循环一边计算的机制，称为生成器：generator
# 方法一：只要把一个列表生成式的[]改成()
L = [x * x for x in range(10)]
print('使用列表生成式生成列表：',L)
# 下面的g是一个generator object 即生成器对象
g = (x * x for x in range(10))
print(g)
print(next(g))
# 下面输出True,说明生成器也是可以迭代的
print(isinstance(g,Iterable))
def iterg(g):
    for a in g:
        print(a)
iterg(g)   

```

    使用列表生成式生成列表： [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
    <generator object <genexpr> at 0x10a372e50>
    0
    True
    1
    4
    9
    16
    25
    36
    49
    64
    81
    3



```python
# 实现斐波拉契数列 1, 1, 2, 3, 5, 8, 13, 21, 34
# 下面的函数获取具体某个元素的值
def fiblaq(n):
    if n <=2 :
        return 1
    return fiblaq(n-1)+fiblaq(n-2)
# print(fiblaq(4))

def printfblaq(n):
    g = (fiblaq(x) for x in range(1,n+1))
    for a in g:
        print(a)
printfblaq(5)    
```

    1
    1
    2
    3
    5



```python
# 如果一个函数定义中包含yield关键字，那么这个函数就不再是一个普通函数，而是一个generator
def fib(max):
    n,a,b = 0,1,1
    while n < max:
        yield b
        a,b = b,a+b
        n = n +1
    return 'done'    
a = fib(3)
print(a)# 此处a是一个生成器generator
for i in fib(5):
    print(i)

# 用for循环调用generator时，发现拿不到generator的return语句的返回值。如果想要拿到返回值，必须捕获StopIteration错误，返回值包含在StopIteration的value
c = fib(6)
while True:
    try:
        x = next(c)
        print('c当前的迭代结果:',x)
    except StopIteration as e:
        print('生成器的返回值为:',e.value)
        break


# 而变成generator的函数，在每次调用next()的时候执行，遇到yield语句返回，再次执行时从上次返回的yield语句处继续执行
def add():
    print('step 1')
    yield 1
    print('step 2')
    yield(3)
    print('step 3')
    yield(5)
o = add()
next(o)
next(o)
next(o)
# next(o) # 在上一步已经将迭代器迭代完成，在报StopIteration的错误
```

    <generator object fib at 0x10a3720d0>
    1
    2
    3
    5
    8
    c当前的迭代结果: 1
    c当前的迭代结果: 2
    c当前的迭代结果: 3
    c当前的迭代结果: 5
    c当前的迭代结果: 8
    c当前的迭代结果: 13
    生成器的返回值为: done
    step 1
    step 2
    step 3





    5




```python
# 生成杨辉三角

```


```python
# 迭代器，下面的两类数据类型都可以用for循环进行遍历
# 一类是集合数据类型，如list、tuple、dict、set、str等；
# 一类是generator，包括生成器和带yield的generator function。
# 可以被next()函数调用并不断返回下一个值的对象称为迭代器：Iterator
# 可以使用isinstance()判断一个对象是不是迭代器
from collections.abc import Iterator
print('[]空列表是不是可迭代的？',isinstance([],Iterable))
print('[]空列表是不是迭代器？',isinstance([],Iterator))
print('{},空的字典是可迭代的吗？',isinstance({},Iterable))
print('{}空的字典是迭代器吗？',isinstance({},Iterator))
g = (x for x in range(10))
print('g的类型为迭代器',g,'生成器是可迭代的吗？',isinstance(g,Iterable),'生成器是迭代器吗？',isinstance(g,Iterator))


# Iterator的计算是惰性的，只有在需要返回下一个数据时它才会计算
# Itreator可以表示一个无限大的数据流，比如自然数，但是list这种就不可能，list这种数据是确定和可知的
# 如果要将一个list转成一个迭代器，可以使用iter()函数
l = [2,3,4,6]
print(isinstance(l,Iterator))
ls = iter(l)
print(isinstance(ls,Iterator))
for a in ls:
    print(a)
# 上面的代码等价于使用next()进行迭代
while True:
    try:
        print(next(ls))
    except StopIteration as e:
        # 遇到错误，说明迭代器中的元素被遍历完成,跳出当前的循环
        break
# 迭代器只能被迭代一遍，一遍将元素遍历完后，迭代器的指针就指向空了，就不会再输出元素了    
```

    []空列表是不是可迭代的？ True
    []空列表是不是迭代器？ False
    {},空的字典是可迭代的吗？ True
    {}空的字典是迭代器吗？ False
    g的类型为迭代器 <generator object <genexpr> at 0x10850dd50> 生成器是可迭代的吗？ True 生成器是迭代器吗？ True
    False
    True
    2
    3
    4
    6

