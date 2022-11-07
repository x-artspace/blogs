---
title: python列表小练习
date: 2022-11-03 17:35:48
categories: python
tags: python
comments: true
---

描述: 战舰游戏。初始一个二维列表，初始化战舰的随机位置。
输入一个坐标，若为战舰位置，则成功击沉战舰，游戏结束。标记每次输入
坐标，若重复输入，提示。若三次未能击沉战舰，结束游戏。

<!--more-->

```python
#!/usr/bin/python3                                                                                                                    
# -*- coding: utf-8 -*-
"""
# Author: EricRay
# File Name: shipgame.py
# Description: 战舰游戏。初始一个二维列表，初始化战舰的随机位置。
输入一个坐标，若为战舰位置，则成功击沉战舰，游戏结束。标记每次输入
坐标，若重复输入，提示。若三次未能击沉战舰，结束游戏

"""
from random import randint

board = []

for x in range(0, 5): 
    board.append(["O"] * 5) #初始化战舰可以出现的区域

def print_board(board):
    for row in board:
        print (" ".join(row))  #以空格分开

#战舰可行区域
print_board(board)

#初始化战舰位置
def random_row(board):
    return randint(0, len(board) - 1)

def random_col(board):
    return randint(0, len(board) - 1)

ship_row = random_row(board)
ship_col = random_col(board)
print (ship_row)
print (ship_col)
#游戏开始
for turn in range(8):
    print ("The turn is:" , turn + 1)
    shoot_row = int(input("Shoot Row:"))
    shoot_col = int(input("Shoot_Col:"))

    if shoot_row == ship_row and shoot_col == ship_col:
        print ("Congratulations! You sank my battleship!")
        break
    else:
        if shoot_row not in range(5) or shoot_col not in range(5):
            print ("Oooooops, it is not even in the ocean")
        elif board[shoot_row][shoot_col] == "X":  #之前已经输入过该坐标
            print ("You have shootted that one already")
        else:
            print ("You missed my battleship!!")
            board[shoot_row][shoot_col] = "X"
            if (turn == 3):
                print ("Game Over!")
                break
            print_board(board)
```

