# 第12章 函数——把代码打包成积木

> **难度**：⭐⭐⭐  
> **所属教程**：Python 零基础入门到 MicroPython 嵌入式实战  
> **前置章节**：第11章（字典与元组）

---

### 12.1 为什么要用函数

想象你需要在程序中 5 次计算圆的面积，每次都写一遍 `3.14 * r ** 2`？太麻烦了。函数让你把一段代码打包，取个名字，以后随时调用。

### 12.2 定义和调用函数

```python
def greet():
    print("你好！")
    print("欢迎学习 Python")

greet()   # 调用函数
greet()   # 再调用一次
```

### 12.3 参数——给函数传递数据

```python
def greet(name):
    print(f"你好，{name}！")

greet("小明")   # 你好，小明！
greet("小红")   # 你好，小红！
```

### 12.4 返回值——让函数"算出一个结果"

```python
def circle_area(radius):
    area = 3.14 * radius ** 2
    return area    # 把结果"还回去"

a = circle_area(5)
print(a)  # 78.5
```

### 12.5 多参数 + 多返回值

```python
def rectangle(length, width):
    area = length * width
    perimeter = 2 * (length + width)
    return area, perimeter

mianji, zhouchang = rectangle(10, 5)
print(f"面积：{mianji}，周长：{zhouchang}")
```

---

### 练习任务

**任务（简单部分）**：定义一个函数 `is_even(num)`，接收一个整数，如果是偶数返回 `True`，奇数返回 `False`。然后用 for 循环测试 1~10 中的每个数，输出"X 是偶数"或"X 是奇数"。

**任务（挑战部分）**：定义一个函数 `is_prime(n)`，判断一个数是否为**质数**（只能被 1 和自己整除的数）。然后写一个程序，输出 2~100 之间所有的质数。

> 提示：判断质数的方法——用 for 循环从 2 试到 `n-1`（或 `sqrt(n)`），看看是否有能整除的。
