# 3 Higher-Order Functions

## Iteration Example 迭代示例
### The Fibonacci Sequence
整了个 Fibonacci 的代码

## Designing Functions
### Characteristics of Functions
A function's domain is the set of all inputs it might
possibly take as arguments.
A function's range is the set of output values it might
possibly return.
A pure function's behavior is the relationship it
creates between input and output.

"三句非常严谨的定义"

### A Guide to Designing Function

- Give each function exactly one job, but make it apply to many related situations
- Don’t repeat yourself (DRY): Implement a process just once, but execute it many times
- Define functions generally

## Generalization
### Generalizing Patterns with Arguments

PS:到这里我开始后悔了，notion上做代码的对比可能会更好一点

首先我们写三个求面积的函数
```
def area_square(r):
    """Return the area of a square with side length R."""
    return r * r

def area_circle(r):
    """Return the area of a circle with radius R."""
    return r * r * pi

def area_hexagon(r):
    """Return the area of a regular hexagon with side length R."""
    return r * r * 3 * sqrt(3) / 2
```
这时候如果输入的 r 为负数，也会进行计算，为了防止这样的问题，使用 `assert`:
```
def area(r, shape_constant):
    """Return the area of a shape from length measurement R."""
    assert r > 0, 'A length must be positive'
    return r * r * shape_constant
```

当然，repeat 三次不够优雅：

```
def area(r, shape_constant):
    """Return the area of a shape from length measurement R."""
    assert r > 0, 'A length must be positive'
    return r * r * shape_constant

def area_square(r):
    return area(r, 1)

def area_circle(r):
    return area(r, pi)

def area_hexagon(r):
    return area(r, 3 * sqrt(3) / 2)

```



## Higher-Order Functions

### Generalizing Over Computational Processes 对计算过程的泛化


```
def sum_naturals(n):
    """Sum the first N natural numbers.

    >>> sum_naturals(5)
    15
    """
    total, k = 0, 1
    while k <= n:
        total, k = total + k, k + 1
    return total

def sum_cubes(n):
    """Sum the first N cubes of natural numbers.

    >>> sum_cubes(5)
    225
    """
    total, k = 0, 1
    while k <= n:
        total, k = total + pow(k, 3), k + 1
    return total
```

 优化之后是：

```
def identity(k):
    return k

def cube(k):
    return pow(k, 3)

def summation(n, term):
    """Sum the first N terms of a sequence.

    >>> summation(5, cube)
    225
    """
    total, k = 0, 1
    while k <= n:
        total, k = total + term(k), k + 1
    return total
```

## Functions as Return Values

```
def make_adder(n):
    """Return a function that takes one argument K and returns K + N.

    >>> add_three = make_adder(3)
    >>> add_three(4)
    7
    """
    def adder(k):
        return k + n
    return adder

make_adder(2000)(20)
```

### Locally Defined Functions && Call Expressions as Operator Expressions

Functions defined within other function bodies are bound to names in a local frame

![](https://raw.githubusercontent.com/biepin7/CloudForImg/master/20220329144031.png)

![](https://raw.githubusercontent.com/biepin7/CloudForImg/master/20220329144219.png)

注意这里的调用，如果只是单纯调用 `make_adder(2000)` 可以看到return的是一个函数

### The Purpose if Higher-Order Functions

 吐槽这一页最重要的PPT居然没有？

Functions are first-class ： Functions can be manipulate as values in our programming language.

> 这里我要插句题外话，之前从来不知道这个概念，偶尔刷知乎的时候会看到 函数是一等公民 的说法，每次都感慨文化人说出来的词都不一样，也没细想什么是一等公民，如今可算是明白了



Higher-Order functions （定义）：

A function that either:

- Takes another function as an argument
- Returns a function as its result

All other functions are considered first-order functions.



Higher-Order functions（功能）：

- Express general methods of computation
- Remove repetition from programs
- Separate concerns among functions



The common structure among functions may be a computational process, not just a number.

函数之间的共同结构可能是一个计算过程，而不仅仅是一个数字。

##  Lambda expressions

> 听了一辈子的Lambda ，第一次学什么是 Lambda expressions

A **lambda expression** is a simple function definition that evaluates to a function.

The syntax:

```
lambda <parameters>: <expression>
```

A function that takes in `parameters` and returns the result of `expression`.

举个例子：

A lambda version of the `square` function:

```
square = lambda x: x * x
```

```
>>> x = 10
>>> square = x*x 
>>> square
100
>>> square = lambda x: x*x
>>> square
<function <lambda> at 0x000001F53834D430>
>>> square(4) 
16
>>> (lambda x:x*x)(3) 
9
```

A function that takes in parameter `x` and returns the result of `x * x`.

A lambda expression does **not** contain return statements or any statements at all. 注意：不包含 return 语句

![](https://raw.githubusercontent.com/biepin7/CloudForImg/master/20220329151014.png)

注意红框部分，lambda 用来定义简单函数

```
def cube(k):
    return k ** 3

summation(5, cube)


summation(5, lambda k: k ** 3)
```



### Lambda Expressions Versus Def Statements  def和lambda的区别

相同：

- Both create a function with the same domain, range, and behavior.
- Both bind that function to the name square.

不同

- Only the `def` statement gives the function an **intrinsic name**（固有名称）, which shows up in environment diagrams but doesn't affect execution (unless the function is printed).
- ![](https://raw.githubusercontent.com/biepin7/CloudForImg/master/20220329151914.png)

可以这么说 lambda 只有赋值结束后才有了名字

def 没有赋值之前就有了名字

## Return

### Return Statements

A return statement completes the evaluation of a call expression and provides its value:

- f(x) for user-defined function f: switch to a new environment; execute f's body
- return statement within f: switch back to the previous environment; f(x) now has a value

Only one return statement is ever executed while executing the body of a function

u1s1 ,略有些废话

## Control

### If Statements and Call Expressions

执行操作什么的就不讲了,在课程里提到一个问题说,为什么不创建一个 `if(a,b,c)`函数来替代 if 语句呢值得想一下

```
lambda x: x if x > 0 else 0
```

A conditional expression has the form

```
<consequent> if <predicate> else <alternative>
```

Evaluation rule:
1. Evaluate the` <predicate>` expression.
2. If it's a true value, the value of the whole expression is the value of the `<consequent>`.
3. Otherwise, the value of the whole expression is the value of the <alternative>.



