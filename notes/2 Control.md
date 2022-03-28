# 2 Control

注意 demo 演示无知识的没有写在笔记里

## 2.1 Print and None

### 2.1.1 None Indicates that Nothing is Returned

1. The special value **None** represents nothing in Python

2. A function that does not explicitly return a value will return None

3. Careful: None is not displayed by the interpreter as the value of an expression

### 2.1.2 Pure Functions & Non-Pure Functions

- Pure Functions ：just return values
- Non-Pure Functions ：have side effects and return None

```
>>> print(print(1),print(2)) 
1
2
None None
```
### 2.1.3 Nested Expressions with Print

画出调用树：
![](https://raw.githubusercontent.com/biepin7/CloudForImg/master/20220327004719.png)

## 2.2 Multiple Environments

### 2.2.1 Life Cycle of a User-Defined Function

![](https://raw.githubusercontent.com/biepin7/CloudForImg/master/20220327004926.png)

这里可以结合 HW01 Q5 进行思考

Every expression is evaluated in the context of an environment.

A name evaluates to the value bound to that name in the earliest frame of the current environment in which that name is found.

“Each frame can have a different binding for the same name”

A call expression and the body of the function being calledare evaluated in different environments

```
>>> from operator import mul
>>> def square(square):       
...     return mul(square,square)
... 
>>> square(4)
16

```

## 2.3 Conditional Statements 条件语句
A statement is executed by the interpreter to perform an action ,like bind a name to a value, or denfine a new function.

a conditional statement 可以被 header 分为 不同的 clause



![](https://raw.githubusercontent.com/biepin7/CloudForImg/master/20220327202424.png)
![](https://raw.githubusercontent.com/biepin7/CloudForImg/master/20220327202906.png)




The first header determines a statement’s type
The header of a clause “controls” the suite that follows
def statements are compound statements


A suite is a sequence of statements
To “execute” a suite means to execute its sequence of statements, in order
