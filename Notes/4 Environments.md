# 4 Environment 环境

## 4.1 Multiple environments 

### 4.1.1 Environments for Higher-Order Functions

**Functions are first-class ：** Functions are values in our programming language

**Higher-order function:** A function that takes a function as an argument value or
A function that returns a function as a return value

>  再次强调 first-class 和 higher-order function 的定义

```
def apply_twice(f,x):
    return f(f(x))

def square(x):
    return x*x


>>> square(10)
100
>>> apply_twice(square,3)
81
>>> apply_twice(square,10) 
10000
```

> 这里不得不说 2022sp 的 Slides 是设计更为合理的，回忆Life cycle of a function （）：

![](https://raw.githubusercontent.com/biepin7/CloudForImg/master/20220331095008.png)

后面是代码的解析，可以手推就算学会

> Names have no meanings without environments

那么定义一个以下的执行应该等于多少呢

```
def repeat(f,x):
    while f(x) != x:
        x = f(x)
    return x

def g(y):
    return  (y+5)//3

print(repeat(g,5))
```

## 4.2 Environments for Nested Definitions

本节讲 Nested Definitions 的环境，首先是例子：

```
def make_adder(n):
    def adder(x):
        return x + n
    return adder

add_three = make_adder(3)
print(add_three)

print(add_three(4))

<function make_adder.<locals>.adder at 0x0000018757D3D3A0>
7
```

这里有一句话：”**So what a return statment does is it brings infomation from a  local frame back into the fame that was the current farme when we call this functions in the first place.**"

- Every user-defined **function** has a parent frame(often global)
- The parent of a **function** is the **frame in which it was defined**
- Every local **frame** has a parent frame
- The parent of a **frame** is the **parent of the called function**
- An environment is a **sequence of frames**.

![](https://raw.githubusercontent.com/biepin7/CloudForImg/master/20220331102247.png)

### 4.2.1 How to Draw an Environment Diagram

#### When a function is defined:

1. Create a function value:
    `func <name>(<formal parameters>) [parent=<label>]`
2. Its parent is the current frame.
3. Bind `<name>` to the function value in the current frame

#### When a function is called:

1. Add a local frame, titled with the `<name>` of the function being called.
2. Copy the parent of the function to the local frame: `[parent=>label<]`
3. Bind the `<formal parameters>` to the arguments in the local frame.
4. Execute the body of the function in the environment that starts with the local frame.

## 4.3 Local names

"Formal pararmeters of functions have a local scope."

啊这，我会，不做笔记了

## 4.4 Function composition

```
def happy(text):
    return "☻" + text + "☻"
    
def sad(text):
    return "☹" + text + "☹"

def composer(f, g):
    def composed(x):
        return f(g(x))
    return composed

msg1 = composer(sad, happy)("cs61a!")
msg2 = composer(happy, sad)("eecs16a!")
```

```
def happy(text):
    return "☻" + text + "☻"
    
def sad(text):
    return "☹" + text + "☹"

def make_texter(emoji):
    def texter(text):
        return emoji + text + emoji
    return texter
    
def composer(f, g):
    def composed(x):
        return f(g(x))
    return composed

composer(happy, make_texter("☃︎"))('snow day!')
```

![](https://raw.githubusercontent.com/biepin7/CloudForImg/master/20220331144401.png)

## 4.5 Self-Reference

这里我不是太懂，以后应该多复习几遍

```
def print_sums(n):
    print(n)
    def next_sum(k):
        return print_sums(n + k)
    return next_sum

print_sums(1)(3)(5)
```

## 4.6 Currying

```
def make_adder(n):
    return lambda k:n+k

make_adder(2)(3)

add(2,3)
```

**Currying:** Converting a function that takes multiple arguments into a single-argument higher-order function.

```
def curry2(f):
    def g(x):
        def h(y):
            return f(x, y)
        return h
    return g
    
make_adder = curry2(add)
make_adder(2)(3)

curry2 = lambda f: lambda x: lambda y: f(x, y)
```





