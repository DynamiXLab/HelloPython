# Python 零基础入门到 MicroPython 嵌入式实战

> **目标读者**：零编程基础的初学者  
> **编辑器**：Thonny（全章节统一使用）  
> **硬件**：后半部分需一块 ESP32 开发板 + 数据线  
> **学习建议**：每章末尾有练习任务，**先自己尝试，再看参考答案**。遇到报错是正常的学习过程，不要气馁。

---

## 目录

| 章节 | 标题 | 难度 |
|------|------|------|
| 第1章 | Python 是什么 & 安装 Thonny | ⭐ |
| 第2章 | 第一行代码：Hello, World! | ⭐ |
| 第3章 | 变量——给数据取个名字 | ⭐ |
| 第4章 | 数字与运算符 | ⭐ |
| 第5章 | 字符串——文本处理的起点 | ⭐⭐ |
| 第6章 | input()——让程序和用户对话 | ⭐⭐ |
| 第7章 | 条件判断——让程序学会做选择 | ⭐⭐ |
| 第8章 | 列表——一个变量装多个数据 | ⭐⭐ |
| 第9章 | for 循环——重复的事情交给机器 | ⭐⭐⭐ |
| 第10章 | while 循环——不知道要循环多少次？ | ⭐⭐⭐ |
| 第11章 | 字典与元组 | ⭐⭐ |
| 第12章 | 函数——把代码打包成积木 | ⭐⭐⭐ |
| 第13章 | 面向对象入门——把数据和功能打包 | ⭐⭐ |
| 第14章 | 文件读写——让数据"留下来" | ⭐⭐⭐ |
| 第15章 | 异常处理——程序出错了怎么办 | ⭐⭐ |
| 第16章 | 面向对象进阶——继承、多态与魔法方法 | ⭐⭐⭐⭐ |
| 第17章 | 嵌入式是什么 & 认识 ESP32 | ⭐ |
| 第18章 | MicroPython 固件烧录 & Thonny 连接 | ⭐⭐ |
| 第19章 | GPIO 点亮 LED——嵌入式版的 Hello World | ⭐⭐⭐ |
| 第20章 | 按键输入——ESP32 感知物理世界 | ⭐⭐⭐ |
| 第21章 | PWM 呼吸灯——让 LED 像呼吸一样渐变 | ⭐⭐⭐ |
| 第22章 | 综合项目：温湿度计 + OLED 显示 | ⭐⭐⭐⭐ |

---

## 第1章 Python 是什么 & 安装 Thonny

### 1.1 Python 是什么

Python 是一门**解释型**编程语言，语法接近人类语言（英语），非常适合初学者。它可以用来做网站、数据分析、人工智能，也能在指甲盖大小的芯片上运行——这就是我们后半部分要玩的 MicroPython。

### 1.2 为什么要用 Thonny

Thonny 是专门为初学者设计的 Python 编辑器，特点：

- 安装简单，自带 Python，不需要单独配置环境
- 变量值可视化显示
- 支持 MicroPython，可以直接给 ESP32 写代码
- 界面清爽，菜单不吓人

### 1.3 安装 Thonny

1. 打开浏览器访问 **https://thonny.org**
2. 点击首页大大的下载按钮，选择对应你的系统版本（Windows / macOS / Linux）
3. 下载完成后双击安装，一路点"下一步"即可（全部用默认设置）
4. 安装完成后打开 Thonny，你会看到一个白色编辑区和下方的 Shell 窗口

> **验证安装**：在 Thonny 下方的 Shell 区域输入 `print("hello")` 然后按回车，看到输出 `hello` 就说明安装成功了。

### 练习任务

**任务**：成功安装 Thonny，并在 Shell 中输入以下内容然后按回车：

```python
print("我是XXX，今天开始学Python！")
```

把 `XXX` 替换成你的名字。截图保存你的第一个 Python 输出，这是你编程之旅的起点！

---

## 第2章 第一行代码：Hello, World!

### 2.1 编辑区 vs Shell

上一章我们直接在 Shell（交互窗口）里打字。Shell 是"说完就执行"，适合临时测试。但真正的程序要**写在编辑区里保存成文件**。

我们来写第一个 `.py` 文件：

1. 在 Thonny 上方编辑区输入：

```python
print("Hello, World!")
print("这是我的第一个Python程序")
```

2. 点击工具栏的 **运行** 按钮（绿色三角形）
3. Thonny 会提示你保存文件，起个名字比如 `hello.py`，选择保存位置
4. 运行后，Shell 区域会显示输出结果

### 2.2 `print()` 是什么

`print()` 是 Python 的**内置函数**，作用是把括号里的内容输出到屏幕上。你可以把它理解成"让 Python 开口说话"的命令。

> **小贴士**：`#` 开头的是注释，Python 不会运行它，是写给人类看的笔记。
>
> ```python
> # 这是一条注释，Python 会跳过它
> print("这行会被运行")  # 这也是一条注释
> ```

### 练习任务

**任务**：写一个 Python 文件 `about_me.py`，用 `print()` 输出 3 行关于你自己的介绍。例如：

```
大家好，我叫小明
我今年12岁
我喜欢踢足球
```

> 💡 **正向激励**：你刚刚完成了一个完整程序的"编写→保存→运行"流程！这是所有程序员每天都要做的事，恭喜入门。

---

## 第3章 变量——给数据取个名字

### 3.1 什么是变量

变量就像一个**贴了标签的盒子**：你把数据放进去，以后用标签（变量名）就能找到它。

```python
name = "小明"      # 把 "小明" 放进名叫 name 的盒子里
age = 12            # 把 12 放进名叫 age 的盒子里
print(name)         # 输出：小明
print(age)          # 输出：12
```

### 3.2 变量命名规则

- 只能用字母、数字、下划线 `_`
- 不能以数字开头
- 区分大小写：`Name` 和 `name` 是两个不同变量

```python
my_name = "张三"    # ✅ 正确
_name = "李四"      # ✅ 正确
score2 = 95         # ✅ 正确
2score = 95         # ❌ 不能以数字开头
```

### 3.3 变量的值可以变化

```python
count = 10
print(count)   # 输出：10
count = 20     # 重新赋值
print(count)   # 输出：20
count = count + 1  # 在原来的基础上加 1
print(count)   # 输出：21
```

### 练习任务

**任务（简单部分）**：创建变量 `name`（你的名字）、`age`（你的年龄）、`city`（你所在的城市），然后用 `print()` 把它们输出成一句完整的话。

**任务（挑战部分）**：在上面基础题完成后，定义两个变量 `a = 30` 和 `b = 20`，把它们的值**互换**（让 a 变成 20，b 变成 30），然后打印验证。

> 提示：你需要一个"临时盒子"来帮忙中转。

---

## 第4章 数字与运算符

### 4.1 数字类型

Python 中最常用的两种数字类型：

```python
age = 18          # int（整数）
height = 1.75     # float（小数/浮点数）
```

### 4.2 算术运算符

| 运算符 | 含义 | 示例 | 结果 |
|--------|------|------|------|
| `+` | 加 | `3 + 2` | `5` |
| `-` | 减 | `3 - 2` | `1` |
| `*` | 乘 | `3 * 2` | `6` |
| `/` | 除 | `3 / 2` | `1.5` |
| `//` | 整除（向下取整） | `3 // 2` | `1` |
| `%` | 取余数 | `3 % 2` | `1` |
| `**` | 乘方 | `3 ** 2` | `9` |

```python
print(7 / 2)     # 3.5
print(7 // 2)    # 3（商）
print(7 % 2)     # 1（余数）
print(2 ** 10)   # 1024（2的10次方）
```

### 4.3 类型转换

```python
age_str = "18"           # 这是字符串
age_int = int(age_str)   # 转成整数：18
price = float("9.99")    # 转成小数：9.99
text = str(100)          # 转成字符串："100"
```

### 练习任务

**任务（简单部分）**：计算圆的面积。给定半径 `r = 5`，用公式 `面积 = 3.14 * r ** 2` 计算并输出结果。

**任务（挑战部分）**：输入一个三位整数（比如 `357`），分别取出它的百位、十位、个位数字，然后输出。

> 提示：用 `//` 和 `%` 可以做到，不需要学输入函数，直接用变量赋值即可。

```
输入：357
输出：
百位：3
十位：5
个位：7
```

---

## 第5章 字符串——文本处理的起点

### 5.1 字符串的定义

字符串就是一串字符，用单引号或双引号包裹：

```python
s1 = 'hello'
s2 = "你好"
s3 = "It's a book"    # 内容里有单引号，外面用双引号
```

### 5.2 字符串拼接

```python
first = "张"
last = "三"
name = last + first    # "三张"
greeting = "你好，" + name + "！"
print(greeting)        # 你好，三张！
```

### 5.3 f-string——更优雅的拼接方式

```python
name = "小明"
age = 12
print(f"我叫{name}，今年{age}岁")  # 我叫小明，今年12岁
```

`f` 开头的字符串里，`{变量名}` 会被自动替换成变量的值。这是最推荐的写法。

### 5.4 常用字符串方法

```python
text = "  Hello Python  "
print(text.strip())        # "Hello Python"（去掉首尾空格）
print(text.upper())        # "  HELLO PYTHON  "
print(text.lower())        # "  hello python  "
print(text.replace("Python", "World"))  # "  Hello World  "
```

### 练习任务

**任务（简单部分）**：用 f-string 创建一个自我介绍模板，至少包含姓名、年龄、爱好三个变量，打印出一段完整的话。

**任务（挑战部分）**：给定一个姓名变量 `full_name = " zhang san "`（注意前后有空格，且是小写），请用之前学过的字符串方法，把它格式化成 `"Zhang San"`（首字母大写，中间空格保留，去掉两端空格）并输出。

> 提示：可以试试 `title()` 方法和 `strip()` 方法。

---

## 第6章 input()——让程序和用户对话

### 6.1 获取用户输入

```python
name = input("请输入你的名字：")
print(f"你好，{name}！")
```

运行时，程序会停下来等你输入，输入完成后按回车继续。

### 6.2 重点：input() 返回的是字符串！

```python
age = input("请输入年龄：")
print(type(age))   # <class 'str'> —— 是字符串！
print(age + 1)     # ❌ 报错！字符串不能加数字
```

所以需要类型转换：

```python
age = int(input("请输入年龄："))     # 一步到位转成整数
print(f"明年你将是{age + 1}岁")
```

### 6.3 结合前面所学的

现在我们可以写一个完整的交互小程序了：

```python
# 小小计算器
num1 = int(input("请输入第一个数字："))
num2 = int(input("请输入第二个数字："))
print(f"{num1} + {num2} = {num1 + num2}")
print(f"{num1} × {num2} = {num1 * num2}")
```

### 练习任务

**任务（简单部分）**：写一个程序，询问用户的姓名和年龄，然后打印：`"XXX，你好！10年后你将是XX岁。"`

**任务（挑战部分）**：写一个 BMI 计算器。BMI = 体重(kg) / 身高(m)²。让用户输入体重(kg)和身高(m)，计算并输出 BMI 值（保留两位小数）。然后输出评价：

- BMI < 18.5 → "偏瘦"
- BMI 18.5~23.9 → "正常"
- BMI ≥ 24 → "偏胖"

> 提示：`round(数字, 2)` 可以四舍五入保留两位小数；大于等于用 `>=`，小于等于用 `<=` 判断。（判断我们下章细讲，这里先用！）

---

## 第7章 条件判断——让程序学会做选择

### 7.1 if 语句

```python
score = 85
if score >= 60:
    print("及格了！")
```

**关键规则**：`if` 那行以冒号结尾，下一行**必须缩进 4 个空格**（Thonny 会自动帮你缩进）。

### 7.2 if...elif...else

```python
score = 85

if score >= 90:
    print("优秀")
elif score >= 80:
    print("良好")
elif score >= 60:
    print("及格")
else:
    print("不及格")

# 输出：良好
```

程序从上到下检查，碰到第一个满足的条件就执行对应的代码块，后面的都不再检查。

### 7.3 比较运算符

| 运算符 | 含义 |
|--------|------|
| `==` | 等于（注意是两个等号！） |
| `!=` | 不等于 |
| `>` | 大于 |
| `<` | 小于 |
| `>=` | 大于等于 |
| `<=` | 小于等于 |

### 7.4 多个条件组合：and / or

```python
age = 20
has_ticket = True

if age >= 18 and has_ticket:
    print("可以入场")
else:
    print("不能入场")

# and：两边都满足才是 True
# or：任意一边满足就是 True
```

### 练习任务

**任务（简单部分）**：写一个"猜数字结果判断器"。用户输入一个数字（1~10），程序判断：等于 `7` 输出 "猜对了！"，否则输出 "猜错了，答案是7"。

**任务（挑战部分）**：写一个**闰年判断器**。用户输入一个年份，判断是否为闰年。闰年规则：能被 4 整除但不能被 100 整除，**或者**能被 400 整除。

```
输入：2000 → 闰年
输入：1900 → 平年
输入：2024 → 闰年
输入：2023 → 平年
```

---

## 第8章 列表——一个变量装多个数据

### 8.1 什么是列表

列表用 `[]` 表示，里面可以放多个数据，用逗号隔开：

```python
fruits = ["苹果", "香蕉", "橘子", "葡萄"]
scores = [85, 92, 78, 60, 95]
mixed = ["小明", 12, 1.75]          # 可以混合不同类型
```

### 8.2 访问列表元素——用索引

**索引从 0 开始**，这是编程世界的通用规则。

```python
fruits = ["苹果", "香蕉", "橘子", "葡萄"]

print(fruits[0])    # 苹果（第1个）
print(fruits[1])    # 香蕉（第2个）
print(fruits[-1])   # 葡萄（倒数第1个）
print(fruits[-2])   # 橘子（倒数第2个）
```

### 8.3 列表常用操作

```python
nums = [10, 20, 30]

nums.append(40)        # 末尾追加：[10, 20, 30, 40]
nums.remove(20)        # 删除元素 20：[10, 30, 40]
nums.insert(1, 15)     # 在索引1处插入：[10, 15, 30, 40]

print(len(nums))       # 获取长度：4
print(nums[1:3])       # 切片，取索引1~2：[15, 30]
```

### 练习任务

**任务（简单部分）**：创建一个包含 5 个你喜欢的水果名称的列表，然后依次打印出第 1 个、最后一个、以及列表的总长度。

**任务（挑战部分）**：写一个"最高分统计程序"。用户连续输入 5 个同学的成绩（用 input），存入列表，最后输出：最高分、最低分和平均分。

> 提示：Python 内置函数 `max(列表)` `min(列表)` `sum(列表)` 可以直接用。平均分 = sum / 人数。

---

## 第9章 for 循环——重复的事情交给机器

### 9.1 for 循环基础

```python
# 打印 0 到 4
for i in range(5):
    print(i)

# 输出：
# 0
# 1
# 2
# 3
# 4
```

`range(5)` 生成 0, 1, 2, 3, 4 一共 5 个数字。**和索引一样，从 0 开始，不包括 5**。

### 9.2 range() 的三种用法

```python
range(5)          # 0, 1, 2, 3, 4
range(1, 5)       # 1, 2, 3, 4（从1开始）
range(1, 10, 2)   # 1, 3, 5, 7, 9（步长为2）
```

### 9.3 遍历列表

```python
fruits = ["苹果", "香蕉", "橘子"]
for fruit in fruits:
    print(f"我喜欢吃{fruit}")
# 迭代变量 fruit 依次取列表中的每个元素
```

### 9.4 累加器模式

```python
# 计算 1 到 100 的和
total = 0
for i in range(1, 101):
    total = total + i    # 也可以用 total += i
print(total)  # 5050
```

### 练习任务

**任务（简单部分）**：用 for 循环打印 1 到 10 的乘法表（1 × n = n 到 10 × n = 10n，其中 n 为用户输入的任意一个数字）。

**任务（挑战部分）**：用 for 循环输出**9×9 乘法表**，格式如下：

```
1×1=1	1×2=2	...	1×9=9
2×1=2	2×2=4	...	2×9=18
...
9×1=9	9×2=18	...	9×9=81
```

> 提示：你需要**嵌套循环**——外层循环控制行号 i（1~9），内层循环控制列号 j（1~i），每行用 `print(..., end="\t")` 让输出不换行而用制表符分隔，每行结束时打印一个空 `print()` 来换行。

---

## 第10章 while 循环——不知道要循环多少次？

### 10.1 while 循环基础

当你不确定要循环多少次时，用 `while`：

```python
# 打印 1 到 5
count = 1
while count <= 5:
    print(count)
    count += 1    # 每次循环 count 加 1，必须有这行，否则死循环！
```

### 10.2 while vs for

| 场景 | 选哪个 |
|------|--------|
| 遍历列表/固定次数 | `for` |
| 等用户输入正确为止 | `while` |
| 不知道要循环多少次 | `while` |

### 10.3 经典案例：输入验证

```python
password = ""
while password != "123456":
    password = input("请输入密码：")
print("密码正确，登录成功！")
```

### 10.4 break 和 continue

```python
# break：立即跳出循环
while True:
    answer = input("输入 quit 退出：")
    if answer == "quit":
        break

# continue：跳过本次循环的剩余部分，进入下一次
for i in range(10):
    if i % 2 == 0:  # 偶数跳过
        continue
    print(i)  # 只输出奇数：1, 3, 5, 7, 9
```

### 练习任务

**任务（简单部分）**：用 while 循环让用户不断输入数字，输入 `0` 时结束，最后输出所有输入数字的总和。

**任务（挑战部分）**：写一个**猜数字游戏**。程序随机生成一个 1~100 之间的数字，用户猜，每次猜完程序提示"猜大了"或"猜小了"，直到猜对为止，报告猜了多少次。

> 提示：`import random` 导入随机数模块，`random.randint(1, 100)` 生成 1~100 的随机整数。结合 while 和条件判断完成。

---

## 第11章 字典与元组

### 11.1 字典——用"名字"来找数据

列表用数字索引，字典用**键（key）**来索引**值（value）**：

```python
student = {
    "name": "小明",
    "age": 12,
    "city": "北京"
}

print(student["name"])    # 小明
print(student["age"])     # 12

student["score"] = 95     # 新增一个键值对
student["age"] = 13       # 修改已有的值
```

### 11.2 遍历字典

```python
for key, value in student.items():
    print(f"{key}: {value}")
```

### 11.3 元组——不可修改的列表

元组用 `()` 定义，一旦创建就不能修改（增删改都不行）：

```python
colors = ("红", "黄", "蓝")
print(colors[0])   # 红
# colors[0] = "绿"   # ❌ 会报错！元组不可修改
```

元组适合存储**不应该被改变**的数据，比如一周七天、RGB 颜色值等。

### 练习任务

**任务（简单部分）**：创建一个字典存储一首歌的信息，包含：歌名（title）、歌手（artist）、年份（year），然后用 f-string 打印出来。

**任务（挑战部分）**：用字典做一个**简易通讯录**。字典的键是姓名，值是电话号码。提供 3 个功能：①添加联系人 ②按姓名查询电话 ③显示全部联系人。让用户用 `while` 循环反复操作，输入 `quit` 退出。

```
--- 通讯录 ---
1. 添加联系人
2. 查询电话
3. 显示全部
输入 quit 退出
请选择：
```

---

## 第12章 函数——把代码打包成积木

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

### 练习任务

**任务（简单部分）**：定义一个函数 `is_even(num)`，接收一个整数，如果是偶数返回 `True`，奇数返回 `False`。然后用 for 循环测试 1~10 中的每个数，输出"X 是偶数"或"X 是奇数"。

**任务（挑战部分）**：定义一个函数 `is_prime(n)`，判断一个数是否为**质数**（只能被 1 和自己整除的数）。然后写一个程序，输出 2~100 之间所有的质数。

> 提示：判断质数的方法——用 for 循环从 2 试到 `n-1`（或 `sqrt(n)`），看看是否有能整除的。

---

## 第13章 面向对象入门——把数据和功能打包在一起

### 13.1 什么是面向对象

目前为止，我们写的代码都是"面向过程"的——数据是数据，函数是函数，分开处理。面向对象（OOP）换了一个思路：**把数据和操作数据的功能打包在一起**，叫做"对象"。

打个比方：你有一只宠物狗，它有**属性**（名字、年龄、品种）和**行为**（叫、跑、吃）。在面向对象的世界里，狗就是一个"对象"，属性和行为都封装在它身上。

### 13.2 类与对象——蓝图与实物

- **类（class）** 是"蓝图"，描述一类事物有什么属性和行为
- **对象（object）** 是根据蓝图造出来的"实物"，也叫**实例**

```python
# 定义一个"狗"的蓝图
class Dog:
    def __init__(self, name, age):
        self.name = name    # 属性：名字
        self.age = age      # 属性：年龄

    def bark(self):         # 行为：叫
        print(f"{self.name}：汪汪！")

    def sit(self):          # 行为：坐
        print(f"{self.name} 坐下了")

# 根据蓝图创建两只狗
my_dog = Dog("旺财", 3)
your_dog = Dog("小白", 1)

my_dog.bark()       # 旺财：汪汪！
your_dog.sit()      # 小白 坐下了
```

### 13.3 理解 `__init__` 和 `self`

```python
class Dog:
    def __init__(self, name, age):
        self.name = name
        self.age = age
```

- `__init__` 是**初始化方法**，创建对象时自动调用。它负责设置对象的初始属性
- `self` 代表**当前这个对象本身**。`self.name = name` 的意思是把传入的 `name` 参数存到"这个对象"的 `name` 属性里
- `self` 必须写在方法的第一个参数位置，调用时不需要手动传，Python 会自动处理

### 13.4 一个更实用的例子

```python
class Student:
    def __init__(self, name, age, grade):
        self.name = name
        self.age = age
        self.grade = grade
        self.scores = []    # 成绩列表，初始为空

    def add_score(self, score):
        """添加一门成绩"""
        self.scores.append(score)
        print(f"{self.name} 添加了成绩：{score}")

    def average(self):
        """计算平均分"""
        if len(self.scores) == 0:
            return 0
        return sum(self.scores) / len(self.scores)

    def introduce(self):
        """自我介绍"""
        avg = self.average()
        print(f"我叫{self.name}，{self.age}岁，{self.grade}年级")
        print(f"共{len(self.scores)}门成绩，平均分：{avg:.1f}")

# 使用
xiaoming = Student("小明", 13, 7)
xiaoming.add_score(92)
xiaoming.add_score(88)
xiaoming.add_score(95)
xiaoming.introduce()
```

### 13.5 为什么需要面向对象

用第12章的函数写法也能实现同样的功能，但当程序变复杂后：

| 函数式写法 | 面向对象写法 |
|-----------|-------------|
| 数据散落在各个变量里 | 数据和方法封装在一起 |
| 函数和数据没有明确关联 | 一眼看出"学生"能做什么 |
| 改一个功能可能影响多处 | 修改局限在类内部 |

初学时不强求全部用面向对象，但理解它能让你**更轻松地组织和阅读更大规模的代码**。

### 练习任务

**任务（简单部分）**：定义一个 `Book` 类，包含属性：书名（title）、作者（author）、页数（pages）。再写一个 `info()` 方法，打印书籍信息。创建 2 本不同的书并分别调用 `info()`。

**任务（挑战部分）**：定义一个 `BankAccount` 类，包含：

- 属性：`owner`（账户名）、`balance`（余额，初始为 0）
- 方法：`deposit(amount)` 存钱、`withdraw(amount)` 取钱（余额不足时提示）、`show()` 显示余额

创建账户后，存入 500，取出 200，再取出 400（应该提示余额不足），最后显示余额。

```
输出参考：
存入 500 元，余额 500
取出 200 元，余额 300
余额不足！当前余额 300
当前余额：300 元
```

---

## 第14章 文件读写——让数据"留下来"

### 14.1 为什么需要文件

到目前为止，我们程序里的数据只要一关掉程序就全没了。通过文件读写，数据可以**持久保存**。

### 14.2 写入文件

```python
# 'w' 模式：写入（会覆盖原有内容）
with open("mydata.txt", "w", encoding="utf-8") as f:
    f.write("第一行内容\n")
    f.write("第二行内容\n")
```

`with` 语句确保文件用完后自动关闭，是最安全的写法。

### 14.3 读取文件

```python
# 一次性读取全部内容
with open("mydata.txt", "r", encoding="utf-8") as f:
    content = f.read()
    print(content)

# 按行读取
with open("mydata.txt", "r", encoding="utf-8") as f:
    for line in f:
        print(line.strip())   # strip() 去掉末尾的换行符
```

### 14.4 追加内容

```python
# 'a' 模式：追加（不会覆盖，写在文件末尾）
with open("mydata.txt", "a", encoding="utf-8") as f:
    f.write("这是追加的新一行\n")
```

| 模式 | 含义 | 文件不存在时 |
|------|------|-------------|
| `'r'` | 只读 | 报错 |
| `'w'` | 写入（覆盖） | 自动创建 |
| `'a'` | 追加 | 自动创建 |

### 练习任务

**任务（简单部分）**：写一个程序，让用户输入 3 句话，逐行写入 `notes.txt`，然后读出来打印在屏幕上。

**任务（挑战部分）**：把第11章的通讯录程序升级——用户退出时把通讯录保存到 `contacts.txt`，下次启动时自动读取回来。实现数据的**持久化存储**。

> 提示：存储格式可以是一行一个人，如 `姓名:电话`，读取时用 `split(":")` 拆分还原成字典。

---

## 第15章 异常处理——程序出错了怎么办

### 15.1 错误不可怕

编程中遇到报错是**每天都在发生的事情**。重要的是学会理解和处理它。

### 15.2 常见错误类型

```python
# NameError：变量未定义
print(abc)    # ❌ abc 没定义过

# TypeError：类型错误
"hello" + 5  # ❌ 字符串和整数不能相加

# ValueError：值错误
int("abc")   # ❌ "abc" 不能转成整数

# IndexError：索引超出范围
nums = [1, 2, 3]
print(nums[5])   # ❌ 索引只有 0, 1, 2
```

### 15.3 try...except 捕获异常

```python
try:
    age = int(input("请输入年龄："))
    print(f"你输入的是：{age}")
except ValueError:
    print("输入的不是数字，请输入数字！")
```

程序不会崩溃，而是优雅地提示用户重新输入。

### 15.4 完整的异常处理结构

```python
while True:
    try:
        num = int(input("请输入一个整数："))
        break    # 输入成功，跳出循环
    except ValueError:
        print("格式错误，请重新输入！")

print(f"你输入的数字是：{num}")
```

### 练习任务

**任务（简单部分）**：让用户输入两个整数并计算除法。用 `try...except` 处理用户输入非数字和除数为 0 的情况。

**任务（挑战部分）**：改进第10章的猜数字游戏——给用户 `try...except` 保护，输入非数字时提示"请输入数字"，不计入猜测次数。

---

## 第16章 面向对象进阶——继承、多态与魔法方法

> 本章是**强化提高内容**，帮你写出更优雅的代码。如果感觉吃力，先理解概念，以后回头再看也不迟。

### 16.1 继承——"是一个"的关系

继承是面向对象最核心的特性之一。当一个类和另一个类存在"**是一个**（is-a）"的关系时，用继承。

```python
# 父类（基类）
class Animal:
    def __init__(self, name):
        self.name = name

    def speak(self):
        print(f"{self.name} 发出了声音")

# 子类继承父类
class Cat(Animal):
    def speak(self):
        print(f"{self.name}：喵喵喵~")

class Dog(Animal):
    def speak(self):
        print(f"{self.name}：汪汪！")
```

- `Cat` 和 `Dog` **继承**了 `Animal`，自动拥有 `name` 属性和 `speak()` 方法
- 子类可以**重写**（override）父类的方法，实现自己的行为

```python
cat = Cat("咪咪")
dog = Dog("旺财")

cat.speak()   # 咪咪：喵喵喵~
dog.speak()   # 旺财：汪汪！
```

### 16.2 `super()`——调用父类的方法

```python
class Animal:
    def __init__(self, name, age):
        self.name = name
        self.age = age

class Cat(Animal):
    def __init__(self, name, age, color):
        super().__init__(name, age)   # 调用父类的 __init__
        self.color = color            # 子类额外属性

    def info(self):
        print(f"{self.name}，{self.age}岁，{self.color}色")

cat = Cat("咪咪", 2, "白")
cat.info()   # 咪咪，2岁，白色
```

`super()` 让你在子类中调用父类的同名方法，避免重复代码。

### 16.3 多态——同一个接口，不同行为

```python
# 不同的动物，同一套接口
animals = [Cat("咪咪"), Dog("旺财"), Cat("花花"), Dog("大黄")]

for animal in animals:
    animal.speak()    # 同样的调用方式，各自产生不同的行为

# 输出：
# 咪咪：喵喵喵~
# 旺财：汪汪！
# 花花：喵喵喵~
# 大黄：汪汪！
```

这就是**多态**——为不同类型的对象提供统一的接口。它让我们可以写出更通用的代码，加新品种的动物时不需要改循环逻辑。

### 16.4 魔法方法——让对象更"Pythonic"

魔法方法（Magic Methods）是双下划线开头结尾的特殊方法，能让自定义对象支持 Python 内置操作：

```python
class Book:
    def __init__(self, title, author, pages):
        self.title = title
        self.author = author
        self.pages = pages

    def __str__(self):
        """print() 时调用——给用户看的"""
        return f"《{self.title}》作者：{self.author}"

    def __repr__(self):
        """交互环境直接输入变量名时调用——给开发者看的"""
        return f"Book('{self.title}', '{self.author}', {self.pages})"

    def __len__(self):
        """len() 时调用"""
        return self.pages

    def __eq__(self, other):
        """== 比较时调用"""
        return self.pages == other.pages

book1 = Book("三体", "刘慈欣", 300)
book2 = Book("活着", "余华", 200)
book3 = Book("百年孤独", "马尔克斯", 300)

print(book1)           # 《三体》作者：刘慈欣
print(len(book1))      # 300
print(book1 == book2)  # False（页数不同）
print(book1 == book3)  # True（页数相同）
```

常用魔法方法速查：

| 方法 | 触发方式 | 用途 |
|------|---------|------|
| `__str__` | `print(obj)` / `str(obj)` | 给用户看的字符串 |
| `__repr__` | `repr(obj)` / 交互环境直接输入 | 给开发者看的表示 |
| `__len__` | `len(obj)` | 返回长度 |
| `__eq__` | `obj1 == obj2` | 判断相等 |
| `__lt__` | `obj1 < obj2` | 小于比较 |
| `__add__` | `obj1 + obj2` | 加法运算 |

### 16.5 类属性 vs 实例属性

```python
class Student:
    school = "阳光小学"    # 类属性：所有实例共享

    def __init__(self, name):
        self.name = name   # 实例属性：每个实例独有

s1 = Student("小明")
s2 = Student("小红")

print(s1.school)   # 阳光小学
print(s2.school)   # 阳光小学

Student.school = "希望小学"   # 改类属性，所有实例都受影响
print(s1.school)   # 希望小学
print(s2.school)   # 希望小学
```

- **实例属性**（`self.xxx`）：每个对象各自拥有，互不影响
- **类属性**（直接写在 class 下）：所有对象共享同一份

### 16.6 @property——让方法像属性一样使用

```python
class Circle:
    def __init__(self, radius):
        self.radius = radius

    @property
    def area(self):
        """面积——像属性一样访问，但实际是计算出来的"""
        return 3.14 * self.radius ** 2

    @property
    def perimeter(self):
        """周长"""
        return 2 * 3.14 * self.radius

c = Circle(5)
print(c.area)       # 78.5（注意：没加括号！）
print(c.perimeter)  # 31.4
```

`@property` 修饰后，调用方法不需要加括号 `()`，看起来就像一个普通属性——更直观。

### 练习任务

**任务（简单部分）**：定义一个 `Shape` 父类，包含 `name` 属性和 `area()` 方法（返回 0）。再定义两个子类 `Rectangle`（矩形，参数 width, height）和 `Circle`（圆，参数 radius），分别重写 `area()` 方法。创建几个对象，分别调用 `area()` 计算面积。

**任务（挑战部分）**：设计一个**简易图书馆管理系统**：

1. 定义 `Book` 类：属性 `title`、`author`，魔法方法 `__str__` 返回格式化的书名信息
2. 定义 `Library` 类：属性 `books`（列表），方法 `add_book(book)`、`remove_book(title)`、`find_by_author(author)`（返回该作者所有书）、`list_all()`
3. 创建 Library 对象，添加至少 5 本书，测试所有功能

> 提示：`find_by_author` 可以用列表推导式 `[b for b in self.books if b.author == author]`。

```
输出参考：
--- 图书馆藏书 ---
《三体》- 刘慈欣
《流浪地球》- 刘慈欣
《活着》- 余华
《许三观卖血记》- 余华
《三毛流浪记》- 张乐平
--- 搜索：刘慈欣 ---
《三体》- 刘慈欣
《流浪地球》- 刘慈欣
```

---

## 第17章 嵌入式是什么 & 认识 ESP32

> 🎉 **恭喜你！** 从本章起，你已经掌握了 Python 的核心知识（包括面向对象）。接下来我们换个玩法——让代码跑进现实世界。

### 17.1 什么是嵌入式系统

嵌入式系统就是**藏在设备内部的小型计算机**。你的微波炉、遥控器、智能灯泡里都有一颗小芯片在运行程序。和我们日常用的电脑不同，嵌入式系统通常只完成一两个特定的任务。

### 17.2 什么是 ESP32

ESP32 是乐鑫科技（Espressif）推出的一款**低成本、低功耗**的微控制器芯片。它的亮点：

- 双核处理器，主频 240MHz
- 内置 Wi-Fi 和蓝牙
- 价格便宜（开发板 ≈ 20~30 元）
- 可以用 MicroPython 编程
- GPIO 引脚丰富，可以接各种传感器

### 17.3 你需要准备什么

| 物品 | 参考价格 | 用途 |
|------|---------|------|
| ESP32 开发板 | 20~30 元 | 核心硬件 |
| Micro-USB 数据线 | 约 10 元 | 连接电脑 |
| LED 灯珠 × 3 | 约 2 元 | 第19章用 |
| 220Ω 电阻 × 3 | 约 1 元 | 保护 LED |
| 按键开关 × 2 | 约 1 元 | 第20章用 |
| 面包板 + 杜邦线 | 约 10 元 | 免焊接连接 |
| DHT11 温湿度传感器 | 约 5 元 | 第22章用 |
| 0.96 寸 OLED 屏（SSD1306） | 约 15 元 | 第22章用 |

> 全部配件一套下来约 60~80 元。建议直接搜索 "ESP32 入门套件"，一般都会配齐上述基础元件。

### 17.4 ESP32 开发板引脚简介

拿到 ESP32 开发板后，你会看到两侧有很多金属针脚（引脚）。这些引脚可以：

- 输出高低电平（3.3V / 0V）
- 读取外部输入（按钮是否按下）
- 输出 PWM 信号（控制亮度、速度）
- 连接 I2C/SPI 设备（屏幕、传感器）

本章先认识，具体用到了再讲。

### 练习任务

**任务**：纯阅读任务，无需编程。仔细阅读本章内容，然后用自己的话回答两个问题：

1. 嵌入式系统和普通电脑的主要区别是什么？
2. ESP32 相比其他单片机的优势有哪些？

---

## 第18章 MicroPython 固件烧录 & Thonny 连接

### 18.1 什么是 MicroPython

MicroPython 是 Python 3 的精简版，专为微控制器设计。它保留了 Python 的核心语法（包括我们学的面向对象），去掉了一些在单片机上用不到的功能。

### 18.2 烧录固件——给 ESP32 "装系统"

第一次使用 ESP32 需要烧录 MicroPython 固件：

**步骤：**

1. 下载固件：访问 **https://micropython.org/download/ESP32_GENERIC/** ，下载最新的 `.bin` 文件
2. 下载烧录工具：访问 **https://www.espressif.com/en/support/download/other-tools** ，下载 **Flash Download Tool**（Windows）或用 `esptool`（macOS/Linux）
3. 用 USB 数据线将 ESP32 连上电脑
4. 打开 Thonny → 菜单栏 **运行** → **配置解释器**
5. 选择 **MicroPython (ESP32)**，端口选对应的串口（Windows 一般是 COM3/COM4，macOS 是 /dev/cu.usbserial-xxxx）
6. 点击 **Install or update MicroPython** 链接，按提示选择 `.bin` 文件烧录

> 如果 Thonny 不能自动烧录，可以用命令行：`esptool.py --port COM3 erase_flash` 先擦除，再 `esptool.py --port COM3 --baud 460800 write_flash -z 0x1000 firmware.bin`。

### 18.3 验证连接

烧录完成后，Thonny 的 Shell 区域应该出现 `>>>` 提示符。输入：

```python
import machine
print(machine.freq())  # 输出类似：240000000（240MHz）
```

如果能正确输出频率，说明连接成功！

### 练习任务

**任务**：按本章步骤完成 MicroPython 固件烧录，在 Thonny 的 Shell 中输入以下代码然后回车：

```python
import esp
esp.osdebug(None)
print("Hello from ESP32!")
```

拍一张 Thonny 界面截图，确保 Shell 中能看到 ESP32 的回复。

---

## 第19章 GPIO 点亮 LED——嵌入式版的 Hello World

### 19.1 什么是 GPIO

GPIO（General Purpose Input/Output）即**通用输入输出引脚**。你可以通过代码控制这些引脚输出高电平（3.3V）或低电平（0V）。

### 19.2 硬件连接

```
ESP32 引脚 D13(GPIO13) ──── 220Ω 电阻 ──── LED 正极（长脚）
                                            │
                                         LED 负极（短脚） ──── GND
```

> **关键**：LED 长脚接正极，短脚接 GND。电阻必须串接，否则 LED 会烧掉。

### 19.3 代码——点亮 LED

```python
from machine import Pin
import time

# GPIO13 设为输出模式
led = Pin(13, Pin.OUT)

# 点亮 LED
led.value(1)     # 1 = 高电平 = 亮
time.sleep(2)    # 保持 2 秒
led.value(0)     # 0 = 低电平 = 灭
```

### 19.4 LED 闪烁

```python
from machine import Pin
import time

led = Pin(13, Pin.OUT)

while True:
    led.value(1)     # 亮
    time.sleep(0.5)  # 等 0.5 秒
    led.value(0)     # 灭
    time.sleep(0.5)  # 等 0.5 秒
```

你会看到 LED 以每秒一次的频率闪烁。恭喜，你写的代码已经能影响物理世界了！

### 练习任务

**任务（简单部分）**：按上图连接好电路，让 LED 以 0.3 秒间隔快速闪烁 10 次，然后长亮 3 秒再熄灭。

**任务（挑战部分）**：接上 3 个 LED（分别接 GPIO13、GPIO12、GPIO14），实现**流水灯**效果：LED1 亮 → 灭 → LED2 亮 → 灭 → LED3 亮 → 灭 → LED1 亮 → …… 不断循环。

> 提示：可以定义一个列表 `leds = [led1, led2, led3]`，用 for 循环配合 `time.sleep()` 控制。

```
电路参考：
GPIO13 ──[220Ω]── LED1 ── GND
GPIO12 ──[220Ω]── LED2 ── GND
GPIO14 ──[220Ω]── LED3 ── GND
```

---

## 第20章 按键输入——ESP32 感知物理世界

### 20.1 数字输入

上一章我们用引脚输出信号（写），这一章用引脚读取信号（读）。

### 20.2 硬件连接

```
3.3V ──── 按键 ────┬──── GPIO25
                   │
                 10kΩ 下拉电阻
                   │
                  GND
```

简化的接法（利用 ESP32 内部上拉电阻）：

```
GND ──── 按键 ──── GPIO25
```

### 20.3 读取按键状态

```python
from machine import Pin
import time

# Pin.IN 表示输入模式，Pin.PULL_UP 启用内部上拉电阻
button = Pin(25, Pin.IN, Pin.PULL_UP)

while True:
    if button.value() == 0:   # 按下时值为 0（因为有上拉电阻）
        print("按键被按下了！")
    time.sleep(0.1)   # 短暂延时，防止输出刷屏
```

### 20.4 按键控制 LED

```python
from machine import Pin
import time

led = Pin(13, Pin.OUT)
button = Pin(25, Pin.IN, Pin.PULL_UP)

while True:
    if button.value() == 0:
        led.value(1)    # 按下亮
    else:
        led.value(0)    # 松开灭
    time.sleep(0.1)
```

### 练习任务

**任务（简单部分）**：用按键控制一个 LED 的开关。第一次按下 → LED 亮，第二次按下 → LED 灭，第三次按下 → LED 亮……如此循环（**切换模式**）。

> 提示：你需要一个变量 `led_state` 来记住当前状态，并在每次按下时翻转。

**任务（挑战部分）**：实现**单击 / 双击检测**。快速按一次（单击），LED 亮 1 秒后灭；快速连按两次（双击），LED 快闪 5 次。

> 提示：记录按键按下的时间 `time.ticks_ms()`，如果两次按键间隔小于 400 毫秒，判定为双击。

---

## 第21章 PWM 呼吸灯——让 LED 像呼吸一样渐变

### 21.1 什么是 PWM

PWM（脉冲宽度调制）通过快速开关来模拟不同的电压输出。在一个很短的时间周期里，如果 50% 时间高电平、50% 时间低电平，LED 看起来就是 50% 亮度。

### 21.2 MicroPython 的 PWM

```python
from machine import Pin, PWM
import time

led = PWM(Pin(13), freq=5000)   # 频率 5000Hz

# duty 范围 0~1023（10 位分辨率）
led.duty(0)      # 最暗（灭）
led.duty(512)    # 约 50% 亮度
led.duty(1023)   # 最亮
```

### 21.3 呼吸灯效果

```python
from machine import Pin, PWM
import time

led = PWM(Pin(13), freq=5000)

while True:
    # 亮度逐渐增加
    for duty in range(0, 1024, 4):
        led.duty(duty)
        time.sleep(0.005)

    # 亮度逐渐减小
    for duty in range(1023, -1, -4):
        led.duty(duty)
        time.sleep(0.005)
```

LED 会像呼吸一样，从暗到亮，再从亮到暗，不断循环。

### 练习任务

**任务（简单部分）**：接一个 LED，让它做一个呼吸周期（从暗到亮再到暗），但是速度是上面示例的两倍。

**任务（挑战部分）**：用第20章的按键来**切换模式**——按下按键在以下 3 种模式间循环切换：①呼吸灯 ②一直亮 ③闪烁模式。每个模式用不同的函数实现。

---

## 第22章 综合项目：温湿度计 + OLED 显示

> 🏆 **终章项目！** 结合前面学到的知识，做一个有实际用处的温湿度计。

### 22.1 DHT11 温湿度传感器

DHT11 是入门级温湿度传感器，精度一般但胜在便宜好用。

**硬件连接：**

```
DHT11       ESP32
VCC   ────  3.3V
DATA  ────  GPIO4
GND   ────  GND
```

在 Thonny → 工具 → 管理插件 中搜索安装 `dht` 库（通常内置，不需要额外安装）。

### 22.2 OLED 显示屏（SSD1306）

0.96 寸 OLED 屏幕，分辨率 128×64 像素，使用 I2C 通信。

**硬件连接：**

```
OLED        ESP32
VCC   ────  3.3V
GND   ────  GND
SCL   ────  GPIO22 (I2C 时钟)
SDA   ────  GPIO21 (I2C 数据)
```

在 Thonny → 工具 → 管理插件 中搜索安装 `ssd1306`。

### 22.3 完整代码

```python
from machine import Pin, SoftI2C
import dht
import ssd1306
import time

# ====== DHT11 初始化 ======
dht_sensor = dht.DHT11(Pin(4))

# ====== OLED 初始化 ======
i2c = SoftI2C(scl=Pin(22), sda=Pin(21))
oled = ssd1306.SSD1306_I2C(128, 64, i2c)

while True:
    try:
        # 读取温湿度
        dht_sensor.measure()
        temp = dht_sensor.temperature()   # 温度（℃）
        hum = dht_sensor.humidity()       # 湿度（%）

        # 清屏
        oled.fill(0)

        # 显示标题
        oled.text("Temp & Hum", 0, 0)

        # 显示温度
        oled.text(f"Temp: {temp} C", 0, 25)

        # 显示湿度
        oled.text(f"Hum : {hum} %", 0, 45)

        # 下方面一条提示线
        oled.text("Press Ctrl+C", 0, 55)

        # 刷新屏幕
        oled.show()

        time.sleep(2)

    except OSError:
        oled.fill(0)
        oled.text("Sensor Error!", 0, 25)
        oled.show()
        time.sleep(2)
```

### 22.4 运行效果

程序运行后，OLED 屏幕上会实时显示当前的温度和湿度，每 2 秒更新一次。对着 DHT11 哈一口气，你会看到湿度数值上升——物理世界的数据就这样被你的代码"读"了出来！

### 练习任务

**任务（简单部分）**：按上图连接好电路，运行上面的完整代码，确保屏幕上正确显示温湿度数据。

**任务（挑战部分 —— 毕业项目）**：在完整项目基础上增加以下功能：

1. **温湿度范围判断**：温度 > 30℃ 时显示 "Hot!"，< 15℃ 时显示 "Cold!"；湿度 > 70% 时显示 "Wet"，< 30% 时显示 "Dry"
2. **按键切换界面**：按一下按键，在"温度大字显示"和"温湿度同时显示"两个界面间切换
3. **LED 告警**：温度超过 32℃ 时，LED 闪烁警告（把第19章的 LED 接上）

> 这个综合任务考察了 **GPIO 输出（LED）、GPIO 输入（按键）、PWM（可选）、I2C 通信（OLED）、传感器读取（DHT11）、条件判断、循环、变量状态切换**……几乎涵盖了我们 22 章所学的全部内容。完成它就是真正的 ESP32 MicroPython 入门毕业了！🎓

---

## 附录A：常见问题排查

### Thonny 相关

| 问题 | 解决 |
|------|------|
| Thonny 打不开 | 重新安装，确保下载对应系统的版本 |
| 运行按钮灰色 | 先保存文件，或检查是否在上次运行中卡住了（重启 Thonny） |
| 中文显示乱码 | 文件 → 另存为，编码选 UTF-8 |

### ESP32 相关

| 问题 | 解决 |
|------|------|
| Thonny 连不上 ESP32 | ① 检查数据线是否支持数据传输（有些线只能充电）② 按住 BOOT 键再重新插拔 ③ 检查串口端口号选对没有 |
| 烧录失败 | 完全擦除后再烧录：`esptool.py erase_flash` |
| LED 不亮 | ① 检查正负极 ② 确认电阻串联 ③ 检查引脚号是否正确 |
| DHT11 读数总报错 | 尝试降低读取频率（time.sleep(3)） |

### Python 基础常见错误速查

| 错误信息 | 含义 | 常见原因 |
|----------|------|----------|
| `NameError: name 'xxx' is not defined` | 变量没定义 | 拼写错误或忘记赋值 |
| `SyntaxError: invalid syntax` | 语法错误 | 冒号忘了、括号没配对、中文标点 |
| `IndentationError` | 缩进错误 | 缩进不一致，有的用空格有的用 Tab |
| `TypeError` | 类型错误 | 字符串和数字混用 |
| `IndexError` | 索引越界 | 列表索引超出范围 |

---

## 附录B：学习路线图 & 后续方向

```
第1~2章        环境 + Hello World
第3~5章        变量、数字、字符串              ← 数据基础
第6~7章        输入 + 条件判断                 ← 交互入门
第8~11章       列表、循环、字典                ← 数据结构
第12~13章      函数 + 面向对象入门             ← 代码组织
第14~16章      文件、异常处理 + 面向对象进阶    ← 工程化 & 提高
    ═════════════════════════════════
第17~18章      嵌入式概念 + 环境搭建            ← 软硬结合
第19~21章      LED、按键、PWM                  ← 硬件交互
第22章         综合项目                        ← 实战检验
```

**完成本教程后，你可以继续学习：**

- **Python 进阶**：模块与包、正则表达式、requests 爬虫、迭代器与生成器
- **面向对象深入**：抽象类、设计模式、组合优于继承的实践
- **嵌入式进阶**：MQTT 物联网通信、ESP32 深度睡眠省电、FreeRTOS 任务调度
- **其他方向**：数据分析（Pandas）、可视化（Matplotlib）、Web 开发（Flask）
- **硬件扩展**：电机驱动、GPS 模块、蓝牙通信、摄像头（ESP32-CAM）

---

> **最后的话**：编程和嵌入式都不需要天赋，需要的是**好奇心**和**耐心**。遇到搞不定的问题，先搜再问，别自己闷上几个小时。Stack Overflow、CSDN、B站上面都有海量的教程。记住：每一个高级工程师都经历过 "hello world"——你已经出发了，剩下的只是时间问题。加油！🚀
