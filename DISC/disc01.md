Discussion 1 Control and Environments

# 1 Control 

巴拉巴拉

## Qusetion 

Alfonso will only wear a jacket outside if it is below 60 degrees or it is raining.
阿方索只有在低于60度或下雨时才会在外面穿夹克。

Write a function that takes in the current temperature and a boolean value telling if it is raining and returns True if Alfonso will wear a jacket and False otherwise.
编写一个函数，该函数接收当前温度和布尔值，指示是否下雨，如果Alfonso将穿上夹克，则返回True，否则返回False。

First, try solving this problem using an if statement.
首先，尝试使用 if 语句解决此问题。

```
def wears_jacket_with_if(temp, raining):
"""
>>> wears_jacket_with_if(90, False)
False
>>> wears_jacket_with_if(40, False)
True
>>> wears_jacket_with_if(100, True)
True
"""

```

```
def wears_jacket_with_if(temp, raining):
    if (temp < 60 or raining):
        return True
    else:
        return False
```
Note that we’ll either return True or False based on a single condition, whose
truthiness value will also be either True or False. Knowing this, try to write this
function using a single line.

```
def wears_jacket_with_if(temp, raining):
    return temp>=60 or raining

```

