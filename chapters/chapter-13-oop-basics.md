# 第13章 面向对象入门——把数据和功能打包在一起

> **难度**：⭐⭐  
> **所属教程**：Python 零基础入门到 MicroPython 嵌入式实战  
> **前置章节**：第12章（函数）  
> **本章定位**：简单讲讲，建立面向对象的初步概念

---

### 13.1 之前的写法有什么问题？

到目前位置，你一直在用**变量存数据、函数处理数据**的方式写程序。比如要管理一个学生：

```python
# 用变量存数据
name = "小明"
age = 13
scores = [92, 88, 95]

# 用函数处理数据
def average(scores_list):
    return sum(scores_list) / len(scores_list)

def add_score(scores_list, new_score):
    scores_list.append(new_score)

add_score(scores, 100)
avg = average(scores)
print(f"{name} 的平均分是：{avg:.1f}")
```

这没问题——但如果有 3 个学生呢？

```python
# 3 个学生：数据翻三倍
name1, age1, scores1 = "小明", 13, [92, 88, 95]
name2, age2, scores2 = "小红", 14, [85, 90]
name3, age3, scores3 = "小刚", 13, [78, 95, 88]

# 传参时必须小心——不能把 name1 和 scores2 混在一起
print(average(scores1))   # 要记得传对参数
```

问题很明显：
1. 学生的信息**分散**在多个变量里，学生一多你就分不清哪几个变量属于同一个人
2. 函数和数据之间**没有绑定关系**——你随时可能把小明的年龄和小红的成绩传给同一个函数

**能不能把"一个学生的所有东西"打包在一起？** 这样每个学生都带着自己的数据，函数也知道该对谁操作。

### 13.2 类与对象——蓝图与实物

面向对象编程（OOP）就是把**数据**和**操作数据的功能**打包在一起。这个"打包"用**类**（class）来实现。

**类（class）= 蓝图**：描述一类事物长什么样、能做什么
**对象（object）= 按蓝图造的实物**：也叫**实例**

想象一个饼干模具——它就是"类"。用模具压出来的每一块饼干就是"对象"（实例）。模具本身可以重复使用，每块饼干有自己的实际状态。

现在用 Python 的 `class` 来定义一个"狗"的蓝图：

```python
class Dog:
    """狗——这是一个类的定义"""
    def __init__(self, name, age):
        self.name = name    # 属性：名字
        self.age = age      # 属性：年龄

    def bark(self):         # 行为：叫
        print(f"{self.name}：汪汪！")

    def sit(self):          # 行为：坐
        print(f"{self.name} 坐下了")
```

定义 `class Dog:` 只是在"设计模具"，还没有任何实际对象。要真的创建一只狗，需要**调用类名像调用函数**：

```python
# 根据蓝图创建两只狗（实例化）
my_dog = Dog("旺财", 3)
your_dog = Dog("小白", 1)

# 调用它们的方法
my_dog.bark()       # 旺财：汪汪！
your_dog.sit()      # 小白 坐下了
```

> `my_dog = Dog("旺财", 3)` 做了两件事：① 创建了一个新的对象（一块新饼干）② 把对象的引用存到变量 `my_dog` 里。

### 13.3 理解 `__init__` 和 `self`——这里会慢一点

刚接触 `__init__` 和 `self` 可能会有点绕，我们一步一步来。

**`__init__`：创建对象时的"初始化"**

`__init__` 是两个下划线 + init + 两个下划线，它是一个**特殊名字**。当你写 `Dog("旺财", 3)` 时，Python 会自动执行这个类里的 `__init__` 方法，把 `"旺财"` 和 `3` 传进去。

```python
class Dog:
    def __init__(self, name, age):  # ← 创建对象时自动运行
        self.name = name
        self.age = age
```

`__init__` 的任务只有一个：**把新创建的对象的属性设置好**。如果 `__init__` 里写了 `self.name = name`，那每个新狗对象一出生就带上了 `name` 属性。

**`self`：代表"这个对象自己"**

想象一下：你用同一个模具做了两块饼干，一块叫"旺财"，一块叫"小白"。当 Python 执行 `my_dog.bark()` 时，它需要知道——是让旺财叫，还是让小白叫？

`self` 就是帮它分辨的。`self` 是**当前对象本身的引用**：

```python
# Python 内部，my_dog.bark() 被翻译成了：
# Dog.bark(my_dog)，也就是 bark 里的 self = my_dog
```

所以 `self.name` 的意思是"这个对象的 name 属性"。`self.name = name` 的意思是"把我收到的 `name` 参数存进这个对象的 `name` 属性里"。

> **两个容易忽略的规则**：
> 1. `self` 必须写在每个方法的**第一个参数位置**——这是 Python 的硬性规定，多一个不行，少一个也不行
> 2. 调用方法时（比如 `my_dog.bark()`），你**不需要传 `self`**——Python 会自动帮你把 `my_dog` 传进去

### 13.4 一个实用的例子——Student 类

把最开始的学生问题用类来重写：

```python
class Student:
    def __init__(self, name, age, grade):
        self.name = name      # 学生的名字
        self.age = age        # 学生的年龄
        self.grade = grade    # 学生的年级
        self.scores = []      # 学生的成绩列表，初始为空

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

# 创建两个学生对象
xiaoming = Student("小明", 13, 7)
xiaohong = Student("小红", 14, 8)

# 各自添加成绩——不用操心"这是谁的成绩"
xiaoming.add_score(92)
xiaoming.add_score(88)
xiaohong.add_score(85)
xiaohong.add_score(90)

# 各自自我介绍
xiaoming.introduce()
xiaohong.introduce()
```

对比最开始的写法：现在每个学生的数据和操作**绑定在一起**了。`xiaoming.average()` 一定算的是小明的平均分，不可能搞混。

### 13.5 什么时候用面向对象？

并不是所有问题都适合面向对象。回到我们之前的知识做对比：

| 场景 | 用什么 | 原因 |
|------|--------|------|
| 存 5 个水果的名字 | 列表 | 只有数据，没有行为 |
| 存一个学生信息、成绩、平均分 | **类（Student）** | 数据和操作数据的方法绑在一起 |
| 写一个计算器 | 函数（第12章） | 只是一组计算逻辑，不需要状态管理 |

一个简单的判断标准：**如果你发现一组数据和操作这组数据的函数被反复一起使用，把它们放进一个类里。** 学完本章你不需要强迫自己全用 OOP——能理解这个概念、能读懂用 OOP 写的代码，就已经达到目标了。

---

### 练习任务

### 练习任务

**任务（⭐ 容易）**：定义一个 `Book` 类，包含属性：书名（title）、作者（author）、页数（pages）。再写一个 `info()` 方法，打印书籍信息。创建 2 本不同的书并分别调用 `info()`。

**任务（⭐⭐ 中等）**：定义一个 `BankAccount` 类，包含：

- 属性：`owner`（账户名）、`balance`（余额，初始为 0）
- 方法：`deposit(amount)` 存钱、`withdraw(amount)` 取钱（余额不足时提示）、`show()` 显示余额

创建账户后，存入 500，取出 200，再取出 400（应该提示余额不足），最后显示余额。

**任务（⭐⭐⭐ 困难）**：用类实现一个**简易计算器** `Calculator`：

- 属性：`history`（列表，记录所有计算历史）
- 方法：`add(a, b)`、`sub(a, b)`、`mul(a, b)`、`div(a, b)`（除法要处理除以 0 的情况）
- 每次计算后，把表达式和结果存入 `history`
- 方法：`show_history()` 打印所有计算历史

```python
calc = Calculator()
calc.add(10, 5)      # 10 + 5 = 15
calc.mul(3, 7)       # 3 × 7 = 21
calc.div(10, 0)      # 错误：除数不能为 0
calc.show_history()
# 输出：
# 10 + 5 = 15
# 3 × 7 = 21
```

> 综合运用：类与方法（第13章）+ 列表（第8章）+ 条件判断（第7章）+ 字符串格式化（第5章）。

---

💡 **思考延续**

你可能以为面向对象编程是硅谷那些大公司发明的。不是。它的故乡是挪威，一个维京海盗的后代聚居的北欧国家。

1960 年代初，挪威计算机中心的 **Ole-Johan Dahl** 和 **Kristen Nygaard** 接到了一个实际任务：模拟港口拥堵。他们需要写一个程序，描述不同大小、不同装载量的船只在港口进进出出，每个船有自己的属性（长度、吃水深度、停泊时间）、自己的行为（进港、停靠、离港），而且彼此之间还会互相影响（一艘船堵住后，后面的船要等待）。

他们尝试了当时所有的编程语言来实现这个模拟器，发现都不合适——因为传统语言是"面向过程"的，数据和操作数据的过程分开存放。但现实世界的船不是这样的：船是一个整体，它有属性也同时有行为。

于是他们从头设计了一门新语言——**Simula**（Simulation Language 的缩写），并在 1967 年正式发布。Simula 第一个提出了"类"（class）和"对象"（object）的概念，以及"继承"的机制。

你今天的 `class Dog:` 和 `class Cat(Animal):`，本质上在用半个多世纪前两个挪威人为解决港口拥堵而想出来的办法。这件事放在人类思想史上也算相当有意思的一笔。
