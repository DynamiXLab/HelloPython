# 第11章 参考答案

## ⭐ 容易

```python
total = 0
while True:
    num = int(input("请输入数字（0结束）："))
    if num == 0:
        break
    total += num
print(f"总和：{total}")
```

## ⭐⭐ 中等

```python
import random
target = random.randint(1, 100)
guesses = 0
while True:
    guess = int(input("猜数字（1~100）："))
    guesses += 1
    if guess > target:
        print("猜大了")
    elif guess < target:
        print("猜小了")
    else:
        print(f"猜对了！共猜了{guesses}次")
        break
```

## ⭐⭐⭐ 困难

```python
import random

while True:
    target = random.randint(1, 100)
    guesses = 0
    while True:
        try:
            guess = int(input("猜数字（1~100）："))
        except ValueError:
            print("请输入数字！")
            continue
        guesses += 1
        if guess > target:
            print("猜大了")
        elif guess < target:
            print("猜小了")
        else:
            print(f"猜对了！共猜了{guesses}次")
            if guesses <= 3:
                print("天才！")
            elif guesses <= 7:
                print("不错！")
            else:
                print("继续加油！")
            break
    again = input("是否再玩一次？(y/n)：")
    if again != "y":
        break
```
