# lab 01

## What Would Python Display? (Part 1)
### Q1: WWPD: Control

上来
```
python3 ok -q control -u

```
然后答题就行

#### xc()
```

>>> xk(10, 10)
? 23
-- OK! --

>>> xk(10, 6)
? 23
-- OK! --

>>> xk(4, 6)
? 6
-- OK! --

>>> xk(0, 0)
? 25
-- OK! --
```

#### how_big()

这里有个小坑，注意 x>5 的return

```
? big 
-- Not quite. Try again! --

? 'big' 
-- OK! --

>>> how_big(12)
? huge
-- OK! --

>>> how_big(1)
? small
-- OK! --

>>> how_big(-1)
? nothin
-- OK! --
```
#### n while
注意是一行一行打印

```
(line 1)? 2
(line 2)? 1
(line 3)? 0
(line 4)? -1
-- OK! --
```
#### positive while

这里需要注意，对 python 来说什么时候是 true 什么是 false
做这里时候应该只学到 Control ，那么已知的 False 值有 ： False, 0, '', None


```
Infinite Loop
```

#### positive negative 
```
(line 1)? -12
(line 2)? -9
(line 3)? -6
```

### Q2: WWPD: Veritasiness Veritasiness

PS:视频里是让你去阅读材料

To evaluate the expression `<left> and <right>`:

1. Evaluate the subexpression <left>.
2. If the result is a false value v, then the expression evaluates to v.
3. Otherwise, the expression evaluates to the value of the subexpression <right>.

对 and ：
1. 先求 left 的值
2. 如果 left 是 false ，那么就返回 left
3  否则，返回 right 的值

To evaluate the expression <left> or <right>:

1. Evaluate the subexpression <left>.
2. If the result is a true value v, then the expression evaluates to v.
3. Otherwise, the expression evaluates to the value of the subexpression <right>.

对 or ：
1. 先求 left 的值
2. 如果 left 是 true ，那么就返回 left
3. 否则，返回 right 的值

To evaluate the expression not <exp>:
    
    Evaluate <exp>; The value is True if the result is a false value, and False otherwise.

对 not ：
1. 先求 exp 的值
2. 如果 exp 是 false ，那么就返回 true
3. 否则，返回 false



```
>>> True and 13
? 13
-- OK! --

# and -> left 是 T -> 返回 13 的值：13

>>> False or 0
? 0
-- OK! --

# or -> left 是 F -> 返回 0 的值：0

>>> not 10
? False
-- OK! --

# not -> 10 是 T -> 返回 F

>>> not None
? True  
-- OK! --

# not -> None 是 F -> 返回 T
```

```
>>> True and 1 / 0 and False  # If this errors, just type Error.
? Error
-- OK! --

# and -> left 是 T -> 返回 1 / 0 的值：Error

>>> True or 1 / 0 or False  # If this errors, just type Error.
? True
-- OK! --

# or -> left 是 T -> 返回 True 的值：True

>>> True and 0  # If this errors, just type Error.
? 0
-- OK! --

# and -> left 是 T -> 返回 0 的值：0

>>> False or 1  # If this errors, just type Error.
? 1
-- OK! --

# or -> left 是 F -> 返回 1 的值：1

>>> 1 and 3 and 6 and 10 and 15  # If this errors, just type Error.
? 15
-- OK! --

# left 均是 T -> 返回 15 的值：15

>>> -1 and 1 > 0 # If this errors, just type Error.
? True  
-- OK! --

# and -> left 是 T -> 返回 1>0 的值：True

>>> 0 or False or 2 or 1 / 0  # If this errors, just type Error.
? 2
-- OK! --

# or -> left 是 F -> 返回 False or 2 or 1 / 0 的值-> of -> left 是 Flase -> 返回 2 or 1/0  的值 -> of -> left 是 True -> 返回 2 的值：2

```

```

>>> not 0
? True
-- OK! --

# 0:False -> 返回 T

>>> (1 + 1) and 1  # If this errors, just type Error. If this is blank, just type Nothing.
? 1
-- OK! --

# and -> left 1+1 = 2 是 T -> 返回 1 的值：1

>>> 1/0 or True  # If this errors, just type Error. If this is blank, just type Nothing.
? Error
-- OK! --

# or -> left 1/0 是 Error-> Error

>>> (True or False) and False  # If this errors, just type Error. If this is blank, just type Nothing.
? False
-- OK! --

# () -> T or F -> or -> left 是 T -> 返回 T 表达式变为 T and F -> letf 是 T -> 返回 F 的值：F

```

### Q3 Debugging Quiz!

首先要听话阅读 ： https://inst.eecs.berkeley.edu/~cs61a/fa20/articles/debugging.html

```
Q: In the following traceback, what is the most recent function call?
Traceback (most recent call last):
    File "temp.py", line 10, in <module>
      f("hi")
    File "temp.py", line 2, in f
      return g(x + x, x)
    File "temp.py", line 5, in g
      return h(x + y * 5)
    File "temp.py", line 8, in h
      return x + 0
  TypeError: must be str, not int
Choose the number of the correct choice:
0) g(x + x, x)
1) h(x + y * 5)
2) f("hi")
? 1
-- OK! --
```
第一行表示 f 有错
第二行表示 f 中 g 有错
第三行表示 g 中 h 有错
最近调用的应是 h

当然要是好好看了文档或者对报错有一定了解：“with the most recent function call at the bottom. ”

```
Q: In the following traceback, what is the cause of this error?
Traceback (most recent call last):
    File "temp.py", line 10, in <module>
      f("hi")
    File "temp.py", line 2, in f
      return g(x + x, x)
    File "temp.py", line 5, in g
      return h(x + y * 5)
    File "temp.py", line 8, in h
      return x + 0
  TypeError: must be str, not int
Choose the number of the correct choice:
0) the code looped infinitely
1) there was a missing return statement
2) the code attempted to add a string to an integer
? 2
-- OK! --
```
都写了 `TypeError: must be str, not int` 

```
Q: How do you write a doctest asserting that square(2) == 4?
Choose the number of the correct choice:
0) def square(x):
       '''
       square(2)
       4
       '''
       return x * x
1) def square(x):
       '''
       input: 2
       output: 4
       '''
       return x * x
2) def square(x):
       '''
       >>> square(2)
       4
       '''
       return x * x
3) def square(x):
       '''
       doctest: (2, 4)
       '''
       return x * x
? 2
```
让你判断 doctest 怎么写

```
Q: When should you use print statements?
Choose the number of the correct choice:
0) To investigate the values of variables at certain points in your code
1) For permanant debugging so you can have long term confidence in your code
2) To ensure that certain conditions are true at certain points in your code
? 0
-- OK! --
```
print 嘛，肯定是为了追踪变量

```
Q: How do you prevent the ok autograder from interpreting print statements as output?
Choose the number of the correct choice:
0) You don't need to do anything, ok only looks at returned values, not printed values
1) Print with # at the front of the outputted line
2) Print with 'DEBUG:' at the front of the outputted line
? 2
-- OK! --
```
文档：
"Note: prefixing debug statements with the specific string "DEBUG: " allows them to be ignored 
by the ok autograder used by cs61a. Since ok generally tests all the output of your code, 
it will fail if there are debug statements that aren't explicitly marked as such, 
even if the outputs are identical."

```
Q: What is the best way to open an interactive terminal to investigate a failing test for question sum_digits in assignment lab01?   
Choose the number of the correct choice:
0) python3 ok -q sum_digits --trace
1) python3 -i lab01.py
2) python3 ok -q sum_digits -i
3) python3 ok -q sum_digits
? 2
-- OK! --
```
文档 ： Interactive Debugging

```
Q: What is the best way to look at an environment diagram to investigate a failing test for question sum_digits in assignment lab01? 
Choose the number of the correct choice:
0) python3 ok -q sum_digits
1) python3 ok -q sum_digits --trace
2) python3 ok -q sum_digits -i
3) python3 -i lab01.py
? 1
-- OK! --
```
PythonTutor Debugging

```
Q: Which of the following is NOT true?
Choose the number of the correct choice:
0) It is generally bad practice to release code with debugging print statements left in
1) Debugging is not a substitute for testing
2) It is generally good practice to release code with assertion statements left in
3) Code that returns a wrong answer instead of crashing is generally better as it at least works fine
4) Testing is very important to ensure robust code
? 3
-- OK! --
```

```
Q: You get a SyntaxError. What is most likely to have happened?
Choose the number of the correct choice:
0) You typed a variable name incorrectly
1) You forgot a return statement
2) Your indentation mixed tabs and spaces
3) You had an unmatched parenthesis
? 3
-- OK! --
```

```
Q: You get a IndentationError. What is most likely to have happened?
Choose the number of the correct choice:
0) You had an unmatched parenthesis
1) You typed a variable name incorrectly
2) Your indentation mixed tabs and spaces
3) You forgot a return statement
? 2
-- OK! --
```

```
Q: You get a TypeError: ... 'NoneType' object is not ... . What is most likely to have happened?
Choose the number of the correct choice:
0) You typed a variable name incorrectly
1) Your indentation mixed tabs and spaces
2) You had an unmatched parenthesis
3) You forgot a return statement
? 3
-- OK! --
```

```
Q: You get a NameError. What is most likely to have happened?
Choose the number of the correct choice:
0) You had an unmatched parenthesis
1) You typed a variable name incorrectly
2) You forgot a return statement
3) Your indentation mixed tabs and spaces
? 1
-- OK! --
```
## Coding Practice

答案在最后

### Q4: Falling Factorial

完成函数的body：目的是返回 从 n 开始逐渐减一的阶乘，共 k 个

边界条件是 k == 0 的时候，需要返回 1

### Q5: Sum Digits

我这取巧了，千万不要学啊2333，不喜欢标答的格式

### ANSWER :Q4
```
    return 1 if k == 0 else n * falling(n - 1, k - 1)
```

### ANSWER :Q5
```
    y = str(y)
    res = 0
    for i in y:
        res += int(i)
    return res
``` 

## Extra Practice

### Q6: WWPD: What If?

```python3 ok -q if-statements -u --local```

```
>>> def ab(c, d):
...     if c > 5:
...         print(c)
...     elif c > 7:
...         print(d)
...     print('foo')
>>> ab(10, 20)
(line 1)? 10
(line 2)? foo
-- OK! --
```
```
>>> def bake(cake, make):
...    if cake == 0:
...        cake = cake + 1
...        print(cake)
...    if cake == 1:
...        print(make)
...    else:
...        return cake
...    return make
>>> bake(0, 29)
(line 1)? 1
(line 2)? 29
(line 3)? 29
-- OK! --
```

```
>>> bake(1, "mashed potatoes")
(line 1)? mashed potatoes
(line 2)? "mashed potatoes" 
-- OK! --
```

## More Coding Practice
### Q7: Double Eights

一样的取巧
```
    return "88" in str(n)
```
