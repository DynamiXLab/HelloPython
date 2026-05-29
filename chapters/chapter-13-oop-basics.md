# 第13章 面向对象入门——把数据和功能打包在一起

> **难度**：⭐⭐  
> **所属教程**：Python 零基础入门到 MicroPython 嵌入式实战  
> **前置章节**：第12章（函数）  
> **本章定位**：简单讲讲，建立面向对象的初步概念

---

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

---

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
