# 附录：面向对象进阶——继承、多态与魔法方法

> **难度**：⭐⭐⭐⭐  
> **所属教程**：Python 零基础入门到 MicroPython 嵌入式实战  
> **前置章节**：第13章（面向对象入门）、第15章（异常处理）  
> **本章定位**：强化提高内容，帮你写出更优雅的代码  
> ⚠️ **本章已从主线教程移至附录**。建议先完成前 15 章+ESP32 实操项目，有一定代码量后再回来看。

> 如果感觉吃力，先理解概念，以后回头再看也不迟。

---

### 附1 一个场景：多个相似的类

假设你要做一个动物庄园程序。你需要猫（Cat）和狗（Dog），它们都有名字、都会发出声音，但叫声不同。

按第13章学到的，你会写两个独立的类：

```python
class Cat:
    def __init__(self, name):
        self.name = name

    def speak(self):
        print(f"{self.name}：喵喵喵~")

class Dog:
    def __init__(self, name):
        self.name = name

    def speak(self):
        print(f"{self.name}：汪汪！")
```

注意到了吗？**`__init__` 里的代码完全一样**——两个类都在做"存一个 `name`"。如果再增加一个 `Pig`、一个 `Duck`，你就得一遍又一遍地写同样的 `self.name = name`。

你能不能只写一次公共的部分，然后让猫和狗"继承"这部分，只写自己不同的地方？

### 附2 继承——子类共享父类的代码

**继承**就是干这个的：你定义一个**父类**（也叫基类）存放通用的代码，然后用子类继承它：

```python
# 父类：存放通用的东西
class Animal:
    def __init__(self, name):
        self.name = name

    def speak(self):
        print(f"{self.name} 发出了声音")

# 子类：继承 Animal，只写自己特有的
class Cat(Animal):
    def speak(self):
        print(f"{self.name}：喵喵喵~")

class Dog(Animal):
    def speak(self):
        print(f"{self.name}：汪汪！")
```

`class Cat(Animal):` 括号里的 `Animal` 就是**父类的名字**，意思是"Cat 继承 Animal"。Cat 会自动拥有 Animal 的所有属性和方法——包括 `__init__`——所以 Cat 不用再写一遍 `self.name = name`。

```python
cat = Cat("咪咪")          # __init__ 来自父类 Animal
dog = Dog("旺财")

cat.speak()                # 咪咪：喵喵喵~    ← 子类自己的版本
dog.speak()                # 旺财：汪汪！     ← 子类自己的版本
```

**重写（override）**：子类可以"覆盖"父类的同名方法，实现自己的行为。`Cat` 和 `Dog` 都重写了 `speak()`，所以叫声不同。如果子类没有重写，就会直接使用父类的方法：

```python
class Duck(Animal):
    pass    # 什么都不写，直接用父类的

duck = Duck("唐老鸭")
duck.speak()               # 唐老鸭 发出了声音  ← 用的是 Animal 的版本
```

### 附3 `super()`——调用父类的版本

有时候你不想完全重写父类的方法，而是想在父类的基础上**增加**一些内容。

比如你给 Animal 增加了一个 `age` 属性，而 Cat 额外还要存一个 `color` 属性。如果直接在 Cat 里重新写一遍 `__init__`，又会重复代码：

```python
class Animal:
    def __init__(self, name, age):
        self.name = name
        self.age = age

class Cat(Animal):
    # 想直接利用 Animal 的 __init__，再加一个 color
    def __init__(self, name, age, color):
        # 能不能先让父类帮我初始化 name 和 age？
        self.color = color
```

这时用 `super()`——它代表"父类的版本"：

```python
class Cat(Animal):
    def __init__(self, name, age, color):
        super().__init__(name, age)   # 调用父类的 __init__，设置 name 和 age
        self.color = color            # 子类额外的属性

    def info(self):
        print(f"{self.name}，{self.age}岁，{self.color}色")

cat = Cat("咪咪", 2, "白")
cat.info()   # 咪咪，2岁，白色
```

`super().__init__(name, age)` 的意思是"调用父类 Animal 的 `__init__` 方法，把 `name` 和 `age` 传给它"。这样就不用重复 `self.name = name`、`self.age = age` 了。

> 简单记：`super()` == "父类"，`.super().__init__(...)` == "让父类帮我把基础部分初始化好，我只管额外的属性"。

### 附4 多态——同一个接口，不同行为

继承带来的另一个好处是：你可以用一个列表把不同类型的子类对象放在一起，然后**用同样的方式调用它们的方法**——不需要区分谁是 Cat 谁是 Dog。

```python
# 不同的动物，但它只管调用 speak()
animals = [Cat("咪咪"), Dog("旺财"), Cat("花花"), Dog("大黄")]

for animal in animals:
    animal.speak()    # 同样的调用方式，各自产生不同的行为

# 输出：
# 咪咪：喵喵喵~
# 旺财：汪汪！
# 花花：喵喵喵~
# 大黄：汪汪！
```

注意循环里只有 `animal.speak()`，它不知道也**不需要知道**当前动物是猫还是狗。每个对象知道自己的类型，自己决定怎么叫。这就是**多态**（polymorphism）——同一句话（`.speak()`），不同对象给出不同反应。

如果你再增加一个新动物类（比如 `class Duck(Animal):`），**循环完全不需要改**。多态让你可以写出更通用的代码：写一次循环，对所有动物生效。

### 附5 魔法方法——让对象更"Pythonic"

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

### 附6 类属性 vs 实例属性

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

### 附7 @property——让方法像属性一样使用

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

> 综合运用：继承与多态（本章）+ 魔法方法（本章）+ 列表操作（第8章）+ 类基础（第14章）。


---

💡 **思考延续**

这一章你学到的继承、多态、魔法方法，其实是面向对象编程里最基础的模式。在软件工程中，"模式"（Pattern）这个概念本身有一段有趣的故事。

1994 年，四位软件工程师——Erich Gamma、Richard Helm、Ralph Johnson 和 John Vlissides——出版了一本名叫《设计模式：可复用面向对象软件的基础》的书。这四位后来被业内称为 **Gang of Four（四人帮，简称 GoF）**。书中归纳了 23 种最常见的面向对象设计问题及其成熟解法——包括工厂模式、单例模式、观察者模式等等。

有趣的是，GoF 并不是凭空创造了这些模式。他们的灵感来自一位建筑师——**Christopher Alexander**。Alexander 在 1977 年出版了《建筑模式语言》一书，提出好的建筑设计可以总结为一些可以复用的"模式"：门廊多高、窗户放在哪里、街道怎么转弯……把这些模式像乐高一样组合起来，就能可靠地建造出舒适的建筑。

GoF 的贡献就是把这种思想移植到了软件领域：你遇到的编程问题，几乎肯定有人遇到过，而且已经找到了比较好的解法。你不需要每次都从零发明一个方案——调用那些经过千锤百炼的模式就行。

你在本章学到的 `@property` 让方法像属性一样调用、魔法方法让自定义类支持 `len()` 和 `==`、子类重写父类方法实现多态……每一招都是从实战中提炼出来的通用套路。将来你看到"工厂模式"、"策略模式"这些词时，不要被吓住——它们只是给了那些模式一个名字，让你在团队里可以简单地说"这里用工厂模式"，而不必把整段设计思路重讲一遍。
