# 第15章 参考答案

## ⭐ 容易

```python
try:
    a = int(input("请输入第一个整数："))
    b = int(input("请输入第二个整数："))
    print(f"结果：{a / b}")
except ValueError:
    print("请输入数字！")
except ZeroDivisionError:
    print("除数不能为 0！")
```

## ⭐⭐ 中等

```python
import random
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
        print(f"猜对了！共{guesses}次")
        break
```

## ⭐⭐⭐ 困难

```python
while True:
    filename = input("请输入文件名（quit退出）：")
    if filename == "quit":
        break
    try:
        with open(filename, "r", encoding="utf-8") as f:
            print(f.read())
    except FileNotFoundError:
        print("文件不存在！")
    except PermissionError:
        print("没有读取权限！")
    except UnicodeDecodeError:
        print("文件编码不支持！")
    except Exception as e:
        print(f"未知错误：{e}")
```
