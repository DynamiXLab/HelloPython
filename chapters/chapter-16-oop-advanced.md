# 第16章 面向对象进阶——继承、多态与魔法方法

> **难度**：⭐⭐⭐⭐  
> **所属教程**：Python 零基础入门到 MicroPython 嵌入式实战  
> **前置章节**：第13章（面向对象入门）、第15章（异常处理）  
> **本章定位**：强化提高内容，帮你写出更优雅的代码

> 如果感觉吃力，先理解概念，以后回头再看也不迟。

---

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

---

### 练习任务

### 练习任务

**任务（⭐ 容易）**：定义一个 `Shape` 父类，包含 `name` 属性和 `area()` 方法（返回 0）。再定义两个子类 `Rectangle`（矩形）和 `Circle`（圆），分别重写 `area()` 方法。创建几个对象并调用 `area()` 计算面积。

**任务（⭐⭐ 中等）**：设计一个**简易图书馆管理系统**：

1. 定义 `Book` 类：属性 `title`、`author`，魔法方法 `__str__` 返回格式化的书名信息
2. 定义 `Library` 类：属性 `books`（列表），方法 `add_book(book)`、`remove_book(title)`、`find_by_author(author)`（返回该作者所有书）、`list_all()`
3. 创建 Library 对象，添加至少 5 本书，测试所有功能

**任务（⭐⭐⭐ 困难）**：设计一个**员工薪资管理系统**：

1. 定义 `Employee` 父类：属性 `name`、`base_salary`，方法 `get_salary()` 返回基本工资
2. 定义子类 `FullTimeEmployee`（全职）：额外属性 `bonus`（奖金），`get_salary()` 返回基本工资 + 奖金
3. 定义子类 `PartTimeEmployee`（兼职）：额外属性 `hourly_rate`（时薪）、`hours`（工时），`get_salary()` 返回时薪 × 工时
4. 定义 `Company` 类：
   - 属性：`name`、`employees`（列表）
   - 方法：`add_employee(emp)`、`total_salary()`（计算总薪资）、`highest_paid()`（返回薪资最高的员工）、`__len__`（返回员工数量）
5. 创建公司，添加全职和兼职员工各 2 名，测试所有功能

```python
公司名称：科技有限公司
员工总数：4
总薪资：31000.0
薪资最高：张三 (15000.0)
```

> 综合运用：继承与多态（第16章）+ 魔法方法（第16章）+ 列表操作（第8章）+ 类基础（第13章）。
