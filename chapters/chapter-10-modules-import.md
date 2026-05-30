# 第10章 导入模块——借用别人的代码

> **难度**：⭐⭐  
> **所属教程**：Python 零基础入门到 MicroPython 嵌入式实战  
> **前置章节**：第9章（for 循环）

---

### 10.1 一个问题：随机数从哪来？

你学到现在，已经会写不少代码了。但如果想写一个"猜数字游戏"——让程序随机出一个数字，用户来猜——你会怎么办？

`print()`、`input()`、`if`、`for`、`while`……翻遍前面学过的所有东西，没有一个能生成随机数。你需要的是别人已经写好的**模块**。

Python 自带了很多内置模块，就像工具箱里的各种工具，装好 Python 就有了，不需要额外安装。你想用的时候，只需要用 `import` 把它"拿进来"。

### 10.2 `import`——导入整个模块

最简单的用法：`import 模块名`，然后通过 `模块名.函数名()` 来调用：

```python
import random

num = random.randint(1, 100)   # 在 1~100 之间随机生成一个整数
print(num)                     # 每次运行结果不同
```

`random.randint(1, 100)` 的含义是：从 `random` 模块里调用 `randint` 函数，参数 `1, 100` 表示随机范围。`random` 是模块名，`randint` 是它里面的函数——中间用 `.` 隔开。

另一个常用模块 `math`：

```python
import math

print(math.pi)          # 3.141592...  圆周率
print(math.sqrt(16))    # 4.0          开平方
print(math.ceil(3.14))  # 4            向上取整
```

`time` 模块可以做延时：

```python
import time

print("请等待...")
time.sleep(2)           # 程序暂停 2 秒
print("2 秒过去了！")
```

### 10.3 `from ... import ...`——只导入需要的

`import 模块名` 会把整个模块都拿进来。但有时候你只想要模块里的一个函数，不想每次写 `模块名.` 前缀——这时用 `from ... import ...`：

```python
from random import randint

num = randint(1, 100)     # 不用写 random. 前缀了
print(num)
```

一次导入多个：

```python
from math import sqrt, pi, ceil

print(sqrt(25))    # 5.0
print(pi)          # 3.141592...
print(ceil(2.3))   # 3
```

**`import 模块名` vs `from 模块名 import 函数名`的区别：**

| 写法 | 调用方式 | 适用场景 |
|------|---------|---------|
| `import random` | `random.randint(1, 100)` | 需要用到模块里很多函数 |
| `from random import randint` | `randint(1, 100)` | 只需要一两个函数 |

两种写法没有好坏，看具体情况选。`from ... import ...` 更省打字，但如果有同名的函数容易冲突。

### 10.4 常见内置模块速查

Python 安装后自带这些常用模块，不需要额外安装：

| 模块 | 常用功能 | 示例 |
|------|---------|------|
| `random` | 随机数 | `random.randint(1, 10)` |
| `math` | 数学运算 | `math.sqrt(25)` |
| `time` | 时间/延时 | `time.sleep(1)` |
| `os` | 操作系统相关 | `os.listdir(".")` |

### 10.5 import 的几个规则

**规则 1：import 必须写在文件最上方**

```python
import random    # ✅ 写在最上面

print(random.randint(1, 10))
```

这不是语法强制要求（写中间也能跑），但这是所有 Python 程序员的习惯——方便一眼看出文件用到了哪些模块。

**规则 2：import 只在第一次执行**

如果你同一个程序里写了两次 `import random`，Python 只会执行第一次——第二次不会重复加载。

**规则 3：`from 模块 import *` 要谨慎**

```python
from random import *   # 导入 random 里的所有东西
```

这样用起来很方便，但会污染命名空间——你分不清哪个函数从哪里来的。除非临时测试，正式项目里不推荐。

---

### 练习任务

**任务（⭐ 容易）**：导入 `math` 模块，计算并输出 `π` 的值（`math.pi`）和 2 的平方根（`math.sqrt(2)`）。

**任务（⭐⭐ 中等）**：写一个"骰子模拟器"。用 `random.randint(1, 6)` 模拟掷一个六面骰子 10 次，输出每次的结果，最后统计每个面出现的次数。

```
输出参考：
第1次：3
第2次：5
...
1 出现了 2 次
2 出现了 1 次
...
```

> 提示：用一个列表 `counts = [0, 0, 0, 0, 0, 0]` 来记录 1~6 各面出现的次数。

**任务（⭐⭐⭐ 困难）**：写一个"简易密码生成器"。用 `random.choice()` 从字符列表中随机选取字符，生成一个 8 位随机密码。

```python
import random

chars = "abcdefghijklmnopqrstuvwxyz0123456789!@#$%"
# 随机选 8 个字符拼接成密码字符串
```

> 综合运用：import 模块（第10章）+ for 循环（第9章）+ 列表（第8章）+ 字符串拼接（第5章）。

---

💡 **思考延续**

你刚刚用 `import random` 时可能没有意识到——这行代码背后，Python 做了很多看不见的工作。

当你写 `import random` 时，Python 会在好几个位置依次搜索名叫 `random.py` 的文件：先搜当前文件夹，然后搜 Python 安装目录里一个叫 `site-packages` 的文件夹。找到之后，Python 会把整个文件读入内存、编译成字节码、执行模块里的代码，最后把模块里的函数变成你可以通过 `random.randint()` 调用的东西。这整个过程在你按下回车的那一瞬间就完成了。

这个机制的力量在于：**世界上任何人写的 Python 代码，只要你能在当前目录或标准路径里访问到，你就可以 import 它**。你今天用的 `random` 是 Python 官方写的，但将来你可以在自己的项目里创建 `my_utils.py` 文件，然后在另一个文件里写 `import my_utils` 来调用你之前写的函数。这意味着你写的代码可以跨文件复用——这是 Python 模块系统给你的最强大的能力。
