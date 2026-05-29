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

### 练习任务

**任务（⭐ 容易）**：定义一个函数 `is_even(num)`，接收一个整数，偶数返回 `True`，奇数返回 `False`。用 for 循环测试 1~10，输出每个数的奇偶性。

**任务（⭐⭐ 中等）**：定义一个函数 `is_prime(n)`，判断一个数是否为**质数**（只能被 1 和自己整除）。然后输出 2~100 之间所有的质数。

> 提示：用 for 循环从 2 试到 `n-1`，看看有没有能整除的。

**任务（⭐⭐⭐ 困难）**：编写一组"数学工具函数"：

1. `factorial(n)` — 计算 n 的阶乘（n! = 1×2×3×...×n）
2. `fibonacci(n)` — 返回前 n 个斐波那契数（1, 1, 2, 3, 5, 8, 13...）
3. `gcd(a, b)` — 求 a 和 b 的最大公约数（提示：辗转相除法）

然后测试：
```python
print(factorial(5))       # 120
print(fibonacci(8))       # [1, 1, 2, 3, 5, 8, 13, 21]
print(gcd(12, 8))         # 4
```

> 综合运用：函数定义（第12章）+ for/while 循环（第9、10章）+ 列表操作（第8章）。
