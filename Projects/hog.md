# Project 1: The Game of Hog

## Introduction

In this project, you will develop a simulator and multiple strategies for the dice game Hog. 

## Rules

俩人交换扔骰子，谁先100分谁赢。每轮玩家可以扔多个骰子（至多10个），其得分是骰子的总和。

- Pig Out. If any of the dice outcomes is a 1, the current player's score for the turn is 1.（骰子结果里有1，玩家的分数就是1）

- Free Bacon. A player who chooses to roll zero dice scores k+3 points, where k is the nth digit of pi after the decimal point, and n is the total score of their opponent. As a special case, if the opponent's score is n = 0, then k = 3 (the digit of pi before the decimal point). 选择不扔骰子的玩家分数会是： k+3 ,k是pi的第n位数，n是对手的分数。特殊情况下（n=0时）k = 3

- Pig Pass. After points for the turn are added to the current player's score, if the current player's score is lower than the opponent's score and the difference between them is less than 3, the current player takes another turn. 得分计算后要是当前玩家的分数比对手的分数低，并且差值小于3，则当前玩家继续扔骰子。

## Download starter files

只要修改 `hog.py`就可以了

## Logistics
If you do not want us to record a backup of your work or information about your progress, you can run
```
python3 ok --local
```
With this option, no information will be sent to our course servers. If you want to test your code interactively, you can run
```
 python3 ok -q [question number] -i 
```
with the appropriate question number (e.g. 01) inserted. This will run the tests for that question until the first one you failed, then give you a chance to test the functions you wrote interactively.
You can also use the debug printing feature in OK by writing
```
 print("DEBUG:", x) 
```
which will produce an output in your terminal without causing OK tests to fail with extra output.

## Graphical User Interface

写完可以运行
```
python3 hog_gui.py
```
启动gui来玩耍

## Phase 1: Simulator

In the first phase, you will develop a simulator for the game of Hog.

### Problem 0 (0 pt)

