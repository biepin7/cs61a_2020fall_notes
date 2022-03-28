# 2 Control

## 2.1 Print and None

### 2.1.1 None Indicates that Nothing is Returned "无"表示未返回任何内容

The special value **None** represents nothing in Python

Python 里讲这个 `None`它代表 nothing

A function that does not explicitly return a value will return None

未显式返回值的函数将返回 None

Careful: `None` is not displayed by the interpreter as the value of an expression

**解释器不会将`Node`  displayed 为表达式的值**

### 2.1.2 Pure Functions & Non-Pure Functions

这两个函数区别就不用多说了

- Pure Functions ：just return values
- Non-Pure Functions ：have side effects and return None

```
>>> print(print(1),print(2)) 
1
2
None None
```
### 2.1.3 Nested Expressions with Print 带 print 的嵌套表达式

画出调用树：
![](https://raw.githubusercontent.com/biepin7/CloudForImg/master/20220327004719.png)

## 2.2 Multiple Environments

### 2.2.1 Life Cycle of a User-Defined Function

![](https://raw.githubusercontent.com/biepin7/CloudForImg/master/20220327004926.png)

这里可以结合 HW01 Q5 ，还有 1 Functions 里说的“An environment is a sequence of frames.”

Every expression is evaluated in the context of an environment.每个表达式都在环境的上下文中进行计算。

A name evaluates to the value bound to that name in the earliest frame of the current environment in which that name is found.

这句话就翻不动，还好有我大哥：“一个名字（变量）的取值是，在当前环境中能找到这个名字的最早的一帧中 这个名字绑定到的值”

A call expression and the body of the function being calledare evaluated in different environments调用表达式和被调用的函数主体在不同的环境中被评估。

视频中提到“Each frame can have a different binding for the same name”（大致可以按局部变量的理念理解）

```
>>> from operator import mul
>>> def square(square):       
...     return mul(square,square)
... 
>>> square(4)
16

```

## 2.3 Conditional Statements 条件语句

新的名称定义又出现了：

A **statement** is executed by the interpreter to perform an action ,like bind a name to a value, or denfine a new function.

一个 statement，是解释器执行的某些操作

上彩色的：

![](https://raw.githubusercontent.com/biepin7/CloudForImg/master/20220328170220.png)

当然 statement 可以不只一行：

![](https://raw.githubusercontent.com/biepin7/CloudForImg/master/20220327202424.png)
![](https://raw.githubusercontent.com/biepin7/CloudForImg/master/20220327202906.png)

将 statement 以 header 分为 Clause，Clause由 header 和 Suite 构成

The first header determines a statement’s type 第一个 haeder 确定了statement的类型

The header of a clause “controls” the suite that follows

def statements are compound statements



A suite is a sequence of statements. 非常熟悉的套路,我愿意称 suite为子句

To “**execute**” a suite means to execute its sequence of statements, **in order**

插入一句题外话，在视频里，老师写了一个 ex.py 文件，在 python 的交互式里加载了，使用的是：

```
python3 -i -ex.py
```

```
-i     : inspect interactively after running script; forces a prompt even if stdin does not appear to be a terminal; also PYTHONINSPECT=x
```

### Boolean Contexts

![](https://raw.githubusercontent.com/biepin7/CloudForImg/master/20220328171533.png)

又多了一个新名词： boolean contexts

## Iteration 循环

Execution Rule for While Statements:

1. Evaluate the header’s expression.
2. If it is a true value, execute the (whole) suite, then return to step 1.



PS:在视频的最后，讲了一个Prime Factorization，非常推荐初学者学习如何组织自己的代码
