```python
print("注释") #单行注释
'''
区间注释
区间注释
区间注释
'''

"""
区间注释
区间注释
区间注释
"""
```


```python
#运算符
print(1+1)
print(2-3)
print(4*5)
print(5/6)
print(6//7)  #取整
print(7//6)
print(7%8)  #取余
print(8%7)
print(2*4)  #幂
```

    2
    -1
    20
    0.8333333333333334
    0
    1
    7
    1
    8
    


```python
#比较运算符
print(2>3)
print(2>=2)
print(2>=3)
print(2==1)
print(2!=1)
print(2<3)
```

    False
    True
    False
    False
    True
    True
    


```python
#逻辑运算符
print((1==1)and(1==2))
print((1==1)or(1==2))
print(not(1==1))
```

    False
    True
    False
    


```python
#三元运算符
x,y=1,2
big=1 if x>=y else y
print(big)
"""
x,y=1,2
if x>y:
    big=x
else:
    big=y
print(big)
"""
```

    2
    




    '\nx,y=1,2\nif x>y:\n    big=x\nelse:\n    big=y\nprint(big)\n'




```python
#其他运算符
dic = ['a','b','c']
if "a" in dic:
    print("a"+" exists")
if "A" not in dic:
    print("A"+" not exists")

a = 'hello'
b = 'hello'
c = "hello"
print(a is b , a is c , ":" , a==b , a==c)
print(a is not b ,a is not c ,":" , a!=b , a!=c)

d = ["hello"]  #两个变量均指向可变类型（is和is not 对比的是两个变量的内存地址，==和！=对比的是两个变量的值）
e = ["hello"]
print(d is e , ":" , d==e )
print(d is not e ,":" , d!=e)

#比较的两个变量，指向的都是地址不可变的类型（str等），那么is，is not 和 ==，！= 是完全等价的。
#对比的两个变量，指向的是地址可变的类型（list，dict，tuple等），则两者是有区别的。
```

    a exists
    A not exists
    True True : True True
    False False : False False
    False : True
    True : False
    


```python
#运算符的优先级
#一元运算符高于二元运算符
print(-2**2 , (-2)**2 , 2**-2)
#先算术运算，后移位运算，最后位运算
print(1 << 3 + 2 & 7 , (1 << (3 + 2)) & 7)
print( 1 + 2 * 3 )
#逻辑运算最后结合
print( 3 < 4 and 4 < 5 , (3 < 4) and (4 < 5) )
```

    -4 4 0.25
    0 0
    7
    True True
    


```python
#数据类型及转换
print(bin(1024))  #转化为二进制
print("1024".bit_length)
```

    0b10000000000
    


    ---------------------------------------------------------------------------

    AttributeError                            Traceback (most recent call last)

    <ipython-input-17-8b27678f7aac> in <module>
          1 #数据类型及转换
          2 print(bin(1024))  #转化为二进制
    ----> 3 print("1024".bit_length)
    

    AttributeError: 'str' object has no attribute 'bit_length'



```python
a=1024
print(a.bit_length())
```

    11
    


```python
import decimal
from decimal import Decimal
dir(decimal)
```




    ['BasicContext',
     'Clamped',
     'Context',
     'ConversionSyntax',
     'Decimal',
     'DecimalException',
     'DecimalTuple',
     'DefaultContext',
     'DivisionByZero',
     'DivisionImpossible',
     'DivisionUndefined',
     'ExtendedContext',
     'FloatOperation',
     'HAVE_THREADS',
     'Inexact',
     'InvalidContext',
     'InvalidOperation',
     'MAX_EMAX',
     'MAX_PREC',
     'MIN_EMIN',
     'MIN_ETINY',
     'Overflow',
     'ROUND_05UP',
     'ROUND_CEILING',
     'ROUND_DOWN',
     'ROUND_FLOOR',
     'ROUND_HALF_DOWN',
     'ROUND_HALF_EVEN',
     'ROUND_HALF_UP',
     'ROUND_UP',
     'Rounded',
     'Subnormal',
     'Underflow',
     '__builtins__',
     '__cached__',
     '__doc__',
     '__file__',
     '__libmpdec_version__',
     '__loader__',
     '__name__',
     '__package__',
     '__spec__',
     '__version__',
     'getcontext',
     'localcontext',
     'setcontext']




```python
a=decimal.getcontext()
print(a)
```

    Context(prec=28, rounding=ROUND_HALF_EVEN, Emin=-999999, Emax=999999, capitals=1, clamp=0, flags=[], traps=[InvalidOperation, DivisionByZero, Overflow])
    


```python
b=Decimal(1)/Decimal(3)
bb=Decimal(1/3)
bbb=1/3
print(b)
print(bb)
print(bbb)

```

    0.3333333333333333333333333333
    0.333333333333333314829616256247390992939472198486328125
    0.3333333333333333
    


```python
decimal.getcontext.prec=4
c=Decimal(1)/Decimal(3)
cc=Decimal(1/3)
print(c)
print(cc)

```


    ---------------------------------------------------------------------------

    AttributeError                            Traceback (most recent call last)

    <ipython-input-13-d82d901c4c33> in <module>
    ----> 1 decimal.getcontext.prec=4
          2 c=Decimal(1)/Decimal(3)
          3 cc=Decimal(1/3)
          4 print(c)
          5 print(cc)
    

    AttributeError: 'builtin_function_or_method' object has no attribute 'prec'



```python
decimal.getcontext().prec=4
c=Decimal(1)/Decimal(3)
cc=Decimal(1/3)
print(c)
print(cc)
```

    0.3333
    0.333333333333333314829616256247390992939472198486328125
    


```python
decimal.getcontext().prec=4
c=Decimal(1)/Decimal(3)
cc=Decimal(1/3)
ccc=Decimal(1)/Decimal(3)
print(c)
print(cc)
print(ccc)
#Decimal对象的精度与舍入操作仅参与算数运算实现，对于Decimal(1/3)返回的是Decimal(1/3)的准确表示，一般为53位及以上.
```

    0.3333
    0.333333333333333314829616256247390992939472198486328125
    0.3333
    


```python
print(True+True,True+False,True*False)
```

    2 1 0
    


```python
print(bool(2),bool(a),bool(True))
```

    True True True
    


```python
#基本类型：整型、浮点型、布尔型
#容器类型：字符串、元组、列表、字典和集合
#bool 作用在基本类型变量：X 只要不是整型 0、浮点型 0.0，bool(X) 就是 True，其余就是 False
#bool 作用在容器类型变量：X 只要不是空的变量，bool(X) 就是 True，其余就是 False。

print(type(''), bool(''), bool('python'))

print(type(()), bool(()), bool((10,)))

print(type([]), bool([]), bool([1, 2]))

print(type({}), bool({}), bool({'a': 1, 'b': 2}))

print(type(set()), bool(set()), bool({1, 2}))
```

    <class 'str'> False True
    <class 'tuple'> False True
    <class 'list'> False True
    <class 'dict'> False True
    <class 'set'> False True
    


```python
print(isinstance(1,int))  #判断一个对象是否是一个已知的类型
print(isinstance(5.2, float))
print(isinstance("5.2", float))

#type() 不会认为子类是一种父类类型，不考虑继承关系
#isinstance() 会认为子类是一种父类类型，考虑继承关系
#如果要判断两个类型是否相同推荐使用 isinstance()
```

    True
    True
    False
    


```python
#类型转换
print(str(10+2))
print(int(1.66),int(1.22222))
print(float("10"))

```

    12
    1 1
    10.0
    


```python
shoplist = ['apple', 'mango', 'carrot', 'banana']
print("This is printed without 'end'and 'sep'.")
for item in shoplist:
    print(item)
```

    This is printed without 'end'and 'sep'.
    apple
    mango
    carrot
    banana
    


```python
shoplist = ['apple', 'mango', 'carrot', 'banana']
print("This is printed with 'end='&''.")
for item in shoplist:
    print(item, end='&')
print('hello world')
```

    This is printed with 'end='&''.
    apple&mango&carrot&banana&hello world
    


```python
shoplist = ['apple', 'mango', 'carrot', 'banana']
print("This is printed with 'sep='&''.")
for item in shoplist:
    print(item, 'another string', sep='&')
```

    This is printed with 'sep='&''.
    apple&another string
    mango&another string
    carrot&another string
    banana&another string
    

###### 通过 <<，>> 快速计算2的倍数问题。
<code>
n << 1 -> 计算 n*2
n >> 1 -> 计算 n/2，负奇数的运算不可用
n << m -> 计算 n*(2^m)，即乘以 2 的 m 次方
n >> m -> 计算 n/(2^m)，即除以 2 的 m 次方
1 << n -> 2^n
</code>

###### 通过 ^ 快速交换两个整数。
<code>
a ^= b
b ^= a
a ^= b
</code>
首先 ^是位异或运算，对应的二进制位同为0或同为1 结果为0 。
比如 a = 2 ,b =1 对应的二进制为a = 10 ,b=01 ,^异或操作
所以 ,a^=b 即 a= a^b 也就是 10^01 = 11 ,a变成11
b^=a 即 b=b^a 也就是 01^11= 10 ,b变成 10
a^=b 即 a=a^b 也就是 11^10 = 01 ,a变为01
a和b完成交换。 

##### 通过 a & (-a) 快速获取a的最后为 1 位置的整数。

00 00 01 01 -> 5
&
11 11 10 11 -> -5
结果：
00 00 00 01 -> 1

00 00 11 10 -> 14
&
11 11 00 10 -> -14
结果：
00 00 00 10 -> 2




```python
a=0b000
print(bin(a))
b=a|(1<<2)  #a|(1<<i)  -> 把 i 插入到集合中
c=b|(1<<5)
print(bin(b))
print(bin(c))
print(c&(1<<2),c&(1<<3))   #a & (1<<i)  -> 判断 i 是否属于该集合（零不属于，非零属于）
d=c&~(1<<2)
print(bin(d))  #a & ~(1<<i) -> 把 i 从集合中删除
```

    0b0
    0b100
    0b100100
    4 0
    0b100000
    


```python
def singleNumber(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        self=0b0
        for i in nums:
            if(self & (1<<i)):
                self = self &~ (1<<i)
                print(bin(self))
            else:
                self = self | (1<<i)
                print(bin(self))
        a=self&(-self)
        print(bin(a))
singleNumber(0,[2,2,1])
```

    0b100
    0b0
    0b10
    0b10
    


```python
a=0b000001000
b=5
print(a)
print(a&(-a))
print(b&(-b))
```

    8
    8
    1
    


```python

```
