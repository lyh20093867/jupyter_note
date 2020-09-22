```python

# 函数是Python内建支持的一种封装，我们通过把大段代码拆成函数，通过一层一层的函数调用，就可以把复杂任务分解成简单的任务，这种分解可以称之为面向过程的程序设计。函数就是面向过程的程序设计的基本单元。
# 而函数式编程（请注意多了一个“式”字）——Functional Programming，虽然也可以归结到面向过程的程序设计，但其思想更接近数学计算。
# 在计算机的层次上，CPU执行的是加减乘除的指令代码，以及各种条件判断和跳转指令，所以，汇编语言是最贴近计算机的语言。
# 而计算则指数学意义上的计算，越是抽象的计算，离计算机硬件越远。
# 对应到编程语言，就是越低级的语言，越贴近计算机，抽象程度低，执行效率高，比如C语言；越高级的语言，越贴近计算，抽象程度高，执行效率低，比如Lisp语言。
# 函数式编程就是一种抽象程度很高的编程范式，纯粹的函数式编程语言编写的函数没有变量，因此，任意一个函数，只要输入是确定的，输出就是确定的，这种纯函数我们称之为没有副作用。而允许使用变量的程序设计语言，由于函数内部的变量状态不确定，同样的输入，可能得到不同的输出，因此，这种函数是有副作用的。
# 函数式编程的一个特点就是，允许把函数本身作为参数传入另一个函数，还允许返回一个函数！
# Python对函数式编程提供部分支持。由于Python允许使用变量，因此，Python不是纯函数式编程语言。

# 高阶函数，函数本身也是可以赋值给变量的，即变量指向函数
# 函数名也是变量，指向函数这个对象的，如果将函数名修改为指向了其他的对象，就会出错
import builtins
# 例如：
print('abs指向求绝对值的函数，结果：',builtins.abs(-123))
# 修改abs指向新的对象
# abs = 10
# print(abs(-23))# 此处会报TypeError: 'int' object is not callable，因为abs这会不再指向执行绝对值这个函数了

# 注：由于abs函数实际上是定义在import builtins模块中的，所以要让修改abs变量的指向在其它模块也生效，要用import builtins; builtins.abs = 10

# 传入函数,将函数作为一个参数，传递给另外一个函数，这种参数也是一个函数的函数就是高阶函数
def add(x,y,f):
    return f(x)+ f(y)
print(add(2,-3,builtins.abs))
```

    abs指向求绝对值的函数，结果： 123
    5



```python
# map函数，map()函数接收两个参数，一个是函数，一个是Iterable，map将传入的函数依次作用到序列的每个元素，并把结果作为新的Iterator返回
from collections import Iterable,Iterator
def f(x):
    return x * x
l=[12,3,4,5,2,6,3]
m=map(f,l)
print(isinstance(m,Iterable))
print(isinstance(m,Iterator))
# list会迭代m这个迭代器，迭代器只能被迭代一遍
print(list(m))
# print(len(m) 
for n in m:
    print(n)

ll=[12,3,4,5,2,6,3] 
# 将ll中的所有元素转换成字符串
lm = list(map(str,ll))
print(lm)
```

    True
    True
    [144, 9, 16, 25, 4, 36, 9]
    ['12', '3', '4', '5', '2', '6', '3']


    /Users/yihong.li/opt/anaconda3/lib/python3.7/site-packages/ipykernel_launcher.py:2: DeprecationWarning: Using or importing the ABCs from 'collections' instead of from 'collections.abc' is deprecated since Python 3.3,and in 3.9 it will stop working
      



```python
# reduce函数 reduce的第一个参数是函数，第二个参数是一个序列
from functools import reduce
# 对一个list作求和运算
def myadd(x,y):
    return x +y
def mymultiply(x,y):
    return x * y
def prod(ll):
    return reduce(mymultiply,ll)

print('3 * 5 * 7 * 9 =', prod([3, 5, 7, 9]))
if prod([3, 5, 7, 9]) == 945:
    print('测试成功!')
else:
    print('测试失败!')
    
lll = reduce(myadd,ll)

print('对列表中所有元素求和，使用reduce进行累计计算：',lll)
llm = reduce(mymultiply,ll)

print('reduce函数对列表中的所有元素求乘积:',llm)
def myconcat(x,y):
    return str(x)+str(y)
lln = reduce(myconcat,ll)
print(lln)

# 自己实现一个将字符串转成int的函数

DIGITS = {'0':0,'1':1,'2':2,'3':3,'4':4,'5':5,'6':6,'7':7,'8':8,'9':9}
def myint(x):
    if isinstance(x,int):
        return x
    def char2int(x):
        return DIGITS[x]
    return reduce(lambda x,y:x*10+y,map(char2int,x))
a=myint('123')
print(isinstance(a,int))
print(type(a))
print(a)
print('abc'.upper())
```

    3 * 5 * 7 * 9 = 945
    测试成功!
    对列表中所有元素求和，使用reduce进行累计计算： 35
    reduce函数对列表中的所有元素求乘积: 25920
    12345263
    True
    <class 'int'>
    123
    ABC



```python
# 将不规则的英文名字变为首字母大写，其他小写的规范名字；输入：['adam', 'LISA', 'barT']，输出：['Adam', 'Lisa', 'Bart']：
# 输入一个list
from functools import reduce
import math
def myF(x):
    # 第一步获取首字母
    f=str(x[0]).upper()
    en = str(x[1:]).lower()
    # 第二步将首字母转大写，其他的转小写
    return f + en
def mylist(f):
    return list(map(myF,f))
li = ['adam', 'LISA', 'barT']
print(mylist(li))

DIGITS = {'0':0,'1':1,'2':2,'3':3,'4':4,'5':5,'6':6,'7':7,'8':8,'9':9}
def char2Int(x):
    return DIGITS[x]

v = reduce(lambda x,y:x*+y,map(char2Int,'123'))
print(v)
# 利用map和reduce编写一个str2float函数，把字符串'123.456'转换成浮点数123.456
def str2float(s):
    
    i = str(s).find('.')
    b = math.pow(10,len(s)-i-1)
    if i == -1:
        return myint(s)
    else:
        m = i +1
        a = s[0:i]
        c = s[m:]
        return myint(a)+myint(c)/b
print(str2float('1323.22'))

```

    ['Adam', 'Lisa', 'Bart']
    6
    1323.22



```python
# filter 函数，接收一个函数和列表，函数需要返回Boolean类型；filter结果返回一个Iterator迭代器
# is_odd 判断是否为奇数
def is_odd(n):
    return n % 2 ==1
l = list(filter(is_odd,[2,4,3,5,6,9]))
print(l)
# 
def not_empty(s):
    return s and s.strip()
print(not_empty("    sd dfs "))
print(not_empty(None))# 此处不会报错，如果s 为None，就不会执行s.strip()，直接返回s，因为s为False了
ll = list(filter(not_empty,['A','','   ',None,'C']))
print(ll)

```

    [3, 5, 9]
    sd dfs
    None
    ['A', 'C']



```python
# 用filter求素数，构建从2开始的所有自然数序列，第一步筛除2的倍数的数，然后筛除3开始的后面的所有3的倍数
lll = [2,3,4,5,6,7,8,9,10,11,12,22,23,24,30,100,120]
# 构建一个从3开始的奇数序列,下面构建的是全体的奇数序列
def _odd_iter():
    n = 1
    while True:
        n = n+2
        yield n

# 构建一个从2开始的所有自然数序列
def _number():
    m = 1
    while True:
        m = m+1
        yield m
nn = _number()
# 遍历2到10以内的所有数
# for i in nn:
#     if i < 10:
#         print(i)
#     else:
#         break
        
a = _odd_iter()
# print(a)
# print(next(a))
# 打印generator，所有yield返回的都是一个生成器
print(type(a))
# 定义一个筛选函数，此函数是一个高阶函数，返回的结果是一个函数，该结果函数会将传递进的n作为除数，跟被除数求余，如果余数大于0就返回True
def _not_divisible(n):
    return lambda x: x % n >0
print(_not_divisible(3)(6))
# 定义一个生成器
def primes():
    yield 2
    it = _odd_iter() # 初始化序列
    while True:
        n = next(it) # 迭代初始化序列生成器，返回第一个数
        # 第一个数是3 ，是一个素数
        yield n
        # 根据it构造新的序列
        it = filter(_not_divisible(n),it)

# 遍历100以内所有奇数素数
# for i in primes():
#     if i <= 100:
#         print(i)
#     else:
#         break

# 利用filter筛选出回数，回数是指从右向左和从左向右读都是一样的数，比如121,12321,909等，是对称的
def is_palindrome(n):
    l = len(str(n))
    if l ==1:
        return True
    elif l == 2 and n % 11 ==0:
        return True
    else:
        s = str(n)
        head = s[0]
        tail = s[-1]
        return int(head) == int(tail) and is_palindrome(int(s[1:-1]))
# mm = 123454321
# s= str(mm)
# print(s)
# print(s[0])
# print(s[-1])
# print(s[1:-1])
print(is_palindrome(mm))
output = filter(is_palindrome,range(1,200))
print(list(output))



```

    <class 'generator'>
    False
    True
    [1, 2, 3, 4, 5, 6, 7, 8, 9, 11, 22, 33, 44, 55, 66, 77, 88, 99, 101, 111, 121, 131, 141, 151, 161, 171, 181, 191]



```python
# 排序算法
aa = [234,343,3,34,324,-343.23]
print(sorted(aa))
# 使用key函数来排序
print(sorted(aa,key=abs))
bb= ['bob','about','Zoo','Credit']
print(bb)
print(sorted(bb))
#忽略字母大小写
print(sorted(bb,key=str.lower))
# 使用反向排序，就是原来是升序改为降序
print(sorted(bb,key=str.lower,reverse=True))
# 对下面的l按照人名区分不区分大小写排序
L = [('Bob',75),('Adam',92),('Bart',66),('Lisa',88)]
def by_name(t):
    return str(t[0])
def by_score(t):
    return t[1]
LL = sorted(L,key=by_name)
print(LL)
print(sorted(L,key=by_score,reverse=True))




```

    [-343.23, 3, 34, 234, 324, 343]
    [3, 34, 234, 324, 343, -343.23]
    ['bob', 'about', 'Zoo', 'Credit']
    ['Credit', 'Zoo', 'about', 'bob']
    ['about', 'bob', 'Credit', 'Zoo']
    ['Zoo', 'Credit', 'bob', 'about']
    [('Adam', 92), ('Bart', 66), ('Bob', 75), ('Lisa', 88)]
    [('Adam', 92), ('Lisa', 88), ('Bob', 75), ('Bart', 66)]



```python
# 返回函数，函数作为结果值返回
def lazy_sum(*args):
    def sum():
        total= 0
        for a in args:
            total = total + a
        return total
    return sum

# f返回sum()这个函数，sum函数传递一个空参，lazy_sum中传递的参数都保存在返回的函数中，sum函数是一个闭包
f= lazy_sum(1,2,3,4,5)
print(type(f))

print(f())
# 闭包 此处count函数中在for循环下又定义了一个函数，有引用i这个变量，但是并没有立即执行，最后i在遍历完后就是3，所以f1，f2，f3调用的结果都是9
# 因为在执行的时候i都是3
# 返回闭包时牢记一点：返回函数不要引用任何循环变量，或者后续会发生变化的变量。
def count():
    fs = []
    for i in range(1,4):
        def f():
            return i * i
        fs.append(f)
    return fs
f1,f2,f3 = count()
print(f1)
print(count())
print(count()[0])
print(count()[0]())
print(count()[1])
print(count()[1]())
print(count()[2])
print(count()[2]())
print(f1())

# 如果真的要引用循环变量，需要再创建一个函数，用该函数的参数绑定循环变量的当前值
def count2():
    def f(j):
        def g():
            return j * j
        return g
    fs = []
    for i in range(1,4):
        fs.append(f(i))
    return fs
print(count2()[0]())
print(count2()[1]())
print(count2()[2]())
# count2()返回的是一个函数的列表，分别将3个函数赋值给f1，f2，f3，此处有点类似scala中的模式匹配
f1,f2,f3=count2()
print(f1())
print(f2())
print(f3())
# 返回一个函数时，该函数并未执行，返回函数中不要引用任何可能会变化的变量。

# 利用闭包返回一个计数器函数，每次调用它返回递增整数
def createCounter():
    def counter():
        return 1
    return counter
aa=createCounter()






```

    <class 'function'>
    15
    <function count.<locals>.f at 0x7ff138ad5830>
    [<function count.<locals>.f at 0x7ff138b4f8c0>, <function count.<locals>.f at 0x7ff138b4f290>, <function count.<locals>.f at 0x7ff138b4fb00>]
    <function count.<locals>.f at 0x7ff138b4f8c0>
    9
    <function count.<locals>.f at 0x7ff138d17830>
    9
    <function count.<locals>.f at 0x7ff138d17e60>
    9
    9
    1
    4
    9
    1
    4
    9
    1



```python
# 匿名函数
def f(x):
    return x * x
print(f(3))
# 使用匿名函数改造上面的函数
f = lambda x : x * x
print(f(3))

# 判断一个数是否为奇数
def is_odd(n):
    return n % 2 == 1

print(is_odd(3))
o= lambda x: x % 2 ==1
print(o(3))


```

    9
    9
    True
    True



```python
# 装饰器 函数也是一个对象，而且函数对象可以被赋值给变量，所以，通过变量也能调用该函数
def printtime():
    print('hello')
# 下面的f是调用函数后的返回值    
f = printtime()
# 下面的a是一个函数
a = printtime
print(f)
print(a())
print(type(a))
# __closure获取函数的闭包
print(a.__closure__)
# __name__属性是获取函数的名称
print(a.__name__)
print(a.__str__)
```

    hello
    None
    hello
    None
    <class 'function'>
    None
    printtime
    <method-wrapper '__str__' of function object at 0x7faa31e0dc20>



```python
# 在代码运行期间动态增加功能 装饰器本质是一个返回函数的高阶函数
# 下面定一个在函数调用之前打印日志的函数，该函数接收一个函数作为参数，返回一个函数
# log函数使用wrapper对传入的func函数进行了包装
def log(func):
    def wrapper(*args,**kw):
        print('logs:call %s()' % func.__name__)
        return func(*args,**kw)
    return wrapper

# log2函数对传入的func函数没有做任何的改变，只是在调用之前添加了一些逻辑，然后将函数返回
def log2(func):
    print('logs2:call %s()' % func.__name__)
    return func
@log
def printtime():
    print('hello')
printtime()

@log2
def printtime2():
    print('hello')
printtime2()
# 上面的log和log2都可以当作装饰函数,接收一个参数函数后没有对函数做任何的改变，仅仅是添加了一些任务，再把传递的函数原样返回，这相当于java中的装饰者模式，或者包装者模式
log=log(printtime)
print(log)
log()   



```

    logs:call printtime()
    hello
    logs2:call printtime2()
    hello
    <function log.<locals>.wrapper at 0x7faa3181d200>
    logs:call wrapper()
    logs:call printtime()
    hello



```python
# 装饰器函数传入参数
# 引入functools模块
import functools

def log3(text):
    def decorator(func):
        @functools.wraps(func)
        def wrapper(*args,**kw):
            print('%s %s()' % (text,func.__name__))
            return func(*args,**kw)
        return wrapper
    return decorator

@log3('execute')
def printtime3():
    print('hello3')
printtime3()
 
```

    execute printtime3()
    hello3



```python
# 请编写一个decorator，能在函数调用的前后打印出'begin call'和'end call'的日志
# 该函数既支持
# @log
# def f():
#     pass
# # 又支持
# @log('execute')
# def f():
#     pass

```


```python
# 偏函数，此处的偏函数跟数学中的偏函数不一样，跟scala中的偏函数也不一样  int()函数将字符串转成整数，可以传入一个base参数，表示按多少进制转换
print('''将'124'按8进制转换，结果为：%d''' % int('124',base=8))
print('''将'124'按10进制转换，结果为：%d''' % int('124',base=10))
print('''将'124'按16进制转换，结果为：%d''' % int('124',base=16))
print('''将'124'按6进制转换，结果为：%d''' % int('124',base=6))
print('''将'124'按5进制转换，结果为：%d''' % int('124',base=5))
print('''将'101'按2进制转换，结果为：%d''' % int('101',base=2))
print('''将'101'按16进制转换，结果为：%d''' % int('101',base=16))
print('''将'101'按10进制转换，结果为：%d''' % int('101',base=10))
# 使用functools中的partial定义偏函数 partial的作用就是将可传参数按指定的值设定，而不需要再定义一个函数
import functools
int2=functools.partial(int,base=2)
print(int2('101'))
```

    将'124'按8进制转换，结果为：84
    将'124'按10进制转换，结果为：124
    将'124'按16进制转换，结果为：292
    将'124'按6进制转换，结果为：52
    将'124'按5进制转换，结果为：39
    将'101'按2进制转换，结果为：5
    将'101'按16进制转换，结果为：257
    将'101'按10进制转换，结果为：101
    5

