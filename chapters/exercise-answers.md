# 练习任务参考答案

> 对应 PR #1 三级难度体系（⭐容易 / ⭐⭐中等 / ⭐⭐⭐困难）
> 每道题只给出一种合理实现，不展示多种写法。

---

## 第1章 Python 是什么 & 安装 Thonny

**⭐ 容易**

在 Thonny Shell 中输入：

```python
print("我是张三，今天开始学Python！")
```

---

**⭐⭐ 中等**

在 Shell 中分别尝试以下三行，观察输出：

```python
print(3 + 5)
print("hello" + "world")
print("hello" * 3)
```

输出：
```
8
helloworld
hellohellohello
```

思考结论：`+` 对数字做加法，对字符串做拼接；`*` 对字符串做重复。

---

**⭐⭐⭐ 困难**

```python
print("*")
print("**")
print("***")
print("****")
print("*****")
```

或更简洁的写法：

```python
for i in range(1, 6):
    print("*" * i)
```

---

## 第2章 第一行代码：Hello, World!

**⭐ 容易**

```python
# about_me.py
print("大家好，我叫张三")
print("我是26级学生")
print("我喜欢编程、音乐、篮球")
```

---

**⭐⭐ 中等**

```python
print("=" * 20)
print("  姓名：张三")
print("  年龄：18")
print("  爱好：编程")
print("=" * 20)
```

---

**⭐⭐⭐ 困难**

```python
print("姓名：张三")
print("学校：阳光小学")
print("专业：计算机科学")
print()
# 名字首字母 Z
print("ZZZZZ")
print("    Z")
print("   Z")
print("  Z")
print("ZZZZZ")
```

---

## 第3章 变量——给数据取个名字

**⭐ 容易**

```python
name = "张三"
age = 12
city = "北京"
print(f"我叫{name}，今年{age}岁，来自{city}")
```

---

**⭐⭐ 中等**

```python
a = 30
b = 20

temp = a   # 临时盒子
a = b
b = temp

print(a)   # 20
print(b)   # 30
```

也可用 Python 特有的元组解包：`a, b = b, a`

---

**⭐⭐⭐ 困难**

```python
price = 15.5
quantity = 3
discount = 0.8

total = price * quantity * discount

print(f"单价：{price}")
print(f"数量：{quantity}")
print(f"折扣：{discount}")
print("-" * 11)
print(f"实付金额：{total}")
```

---

## 第4章 数字与运算符

**⭐ 容易**

```python
r = 5
area = 3.14 * r ** 2
print(f"半径为 {r} 的圆面积 = {area}")
```

---

**⭐⭐ 中等**

```python
num = 357
bai = num // 100
shi = (num // 10) % 10
ge = num % 10

print(f"百位：{bai}")
print(f"十位：{shi}")
print(f"个位：{ge}")
```

---

**⭐⭐⭐ 困难**

```python
distance = 3.6    # 公里
minutes = 45      # 分钟

hours = minutes / 60
speed = distance / hours

print(f"距离：{distance} 公里")
print(f"时间：{minutes} 分钟")
print(f"平均速度：{round(speed, 1)} 公里/小时")
```

---

## 第5章 字符串——文本处理的起点

**⭐ 容易**

```python
name = "张三"
age = 12
hobby = "编程"
print(f"大家好，我叫{name}，今年{age}岁，喜欢{hobby}")
```

---

**⭐⭐ 中等**

```python
full_name = " zhang san "
formatted = full_name.strip().title()
print(formatted)    # Zhang San
```

---

**⭐⭐⭐ 困难**

```python
sentence = "i love python and python loves me"

count = sentence.count("python")
print(f"'python' 出现了 {count} 次")

replaced = sentence.replace("python", "Java")
print(f"替换后：{replaced}")

uppered = replaced.upper()
print(f"转大写：{uppered}")

length = len(uppered)
print(f"最终句子长度：{length}")
```

---

## 第6章 input()——让程序和用户对话

**⭐ 容易**

```python
name = input("请输入你的姓名：")
age = int(input("请输入你的年龄："))
future_age = age + 10
print(f"{name}，你好！10年后你将是{future_age}岁。")
```

---

**⭐⭐ 中等**

```python
weight = float(input("请输入体重(kg)："))
height = float(input("请输入身高(m)："))

bmi = weight / (height ** 2)
print(f"你的 BMI 值为：{round(bmi, 2)}")
```

---

**⭐⭐⭐ 困难**

```python
temp = float(input("请输入温度值："))
unit = input("请输入单位（C/F）：")

if unit == "C" or unit == "c":
    f = temp * 9 / 5 + 32
    print(f"{temp}°C = {f}°F")
elif unit == "F" or unit == "f":
    c = (temp - 32) * 5 / 9
    print(f"{temp}°F = {c}°C")
else:
    print("单位输入错误，请输入 C 或 F")
```

---

## 第7章 条件判断——让程序学会做选择

**⭐ 容易**

```python
guess = int(input("请输入一个数字（1~10）："))

if guess == 7:
    print("猜对了！")
else:
    print("猜错了，答案是7")
```

---

**⭐⭐ 中等**

```python
year = int(input("请输入年份："))

if (year % 4 == 0 and year % 100 != 0) or (year % 400 == 0):
    print(f"{year} → 闰年")
else:
    print(f"{year} → 平年")
```

---

**⭐⭐⭐ 困难**

```python
score = int(input("请输入分数（0~100）："))

if score < 0 or score > 100:
    print("输入的分数无效！")
elif score >= 90:
    print("等级：A —— 优秀，继续保持！")
elif score >= 80:
    print("等级：B —— 良好，再加把劲！")
elif score >= 70:
    print("等级：C —— 中等，还有提升空间")
elif score >= 60:
    print("等级：D —— 及格，需要加油！")
else:
    print("等级：F —— 不及格，要努力了！")
```

---

## 第8章 列表——一个变量装多个数据

**⭐ 容易**

```python
fruits = ["苹果", "香蕉", "橘子", "葡萄", "草莓"]
print(f"第1个水果：{fruits[0]}")
print(f"最后一个：{fruits[-1]}")
print(f"总长度：{len(fruits)}")
```

---

**⭐⭐ 中等**

```python
scores = [78, 95, 62, 88, 73, 91, 56]

print(f"最高分：{max(scores)}")
print(f"最低分：{min(scores)}")

pass_count = 0
for s in scores:
    if s >= 60:
        pass_count += 1
print(f"及格人数：{pass_count}")

# 删除不及格
new_scores = []
for s in scores:
    if s >= 60:
        new_scores.append(s)
print(f"删除不及格后：{new_scores}")
```

---

**⭐⭐⭐ 困难**

```python
names = []
scores = []

for i in range(5):
    name = input(f"请输入第{i+1}个同学的姓名：")
    score = int(input(f"请输入{name}的成绩："))
    names.append(name)
    scores.append(score)

# 按成绩从高到低排序（冒泡排序）
for i in range(4):
    for j in range(4 - i):
        if scores[j] < scores[j + 1]:
            scores[j], scores[j + 1] = scores[j + 1], scores[j]
            names[j], names[j + 1] = names[j + 1], names[j]

print("\n=== 成绩排名 ===")
for i in range(5):
    print(f"第{i+1}名：{names[i]} {scores[i]}分")
```

---

## 第9章 for 循环——重复的事情交给机器

**⭐ 容易**

```python
n = 7
for i in range(1, 11):
    print(f"{n} × {i} = {n * i}")
```

---

**⭐⭐ 中等**

```python
for i in range(1, 10):
    for j in range(1, i + 1):
        print(f"{i}×{j}={i*j}", end="\t")
    print()
```

---

**⭐⭐⭐ 困难**

```python
for i in range(1, 10):
    for j in range(1, i + 1):
        if (i * j) % 2 == 0:
            print(f"{i}×{j}={i*j}", end="\t")
    print()
```

---

## 第10章 导入模块——借用别人的代码

**⭐ 容易**

```python
import math

print(f"π = {math.pi}")
print(f"√2 = {math.sqrt(2)}")
```

**⭐⭐ 中等**

```python
import random

counts = [0] * 6    # 索引 0~5 对应骰子 1~6

for i in range(10):
    result = random.randint(1, 6)
    print(f"第{i+1}次：{result}")
    counts[result - 1] += 1

print()
for i in range(6):
    print(f"{i+1} 出现了 {counts[i]} 次")
```

**⭐⭐⭐ 困难**

```python
import random

chars = "abcdefghijklmnopqrstuvwxyz0123456789!@#$%"
password = ""
for i in range(8):
    password += random.choice(chars)
print(f"生成的密码：{password}")
```

---

## 第11章 while 循环——不知道要循环多少次？

**⭐ 容易**

```python
total = 0
while True:
    num = int(input("请输入一个数字（输入0结束）："))
    if num == 0:
        break
    total += num
print(f"总和：{total}")
```

---

**⭐⭐ 中等**

```python
import random

target = random.randint(1, 100)
count = 0

while True:
    guess = int(input("猜一个数字（1~100）："))
    count += 1
    if guess > target:
        print("猜大了")
    elif guess < target:
        print("猜小了")
    else:
        print(f"猜对了！你猜了{count}次")
        break
```

---

**⭐⭐⭐ 困难**

```python
import random

while True:
    target = random.randint(1, 100)
    count = 0

    while True:
        user_input = input("猜一个数字（1~100）：")

        try:
            guess = int(user_input)
        except ValueError:
            print("请输入数字！")
            continue

        count += 1

        if guess > target:
            print("猜大了")
        elif guess < target:
            print("猜小了")
        else:
            if count <= 3:
                rank = "天才！"
            elif count <= 7:
                rank = "不错！"
            else:
                rank = "继续加油！"
            print(f"猜对了！共猜了{count}次，评价：{rank}")
            break

    again = input("是否再玩一次？(y/n)：")
    if again != "y":
        print("游戏结束，再见！")
        break
```

---

## 第12章 字典与元组

**⭐ 容易**

```python
song = {
    "title": "晴天",
    "artist": "周杰伦",
    "year": 2003
}
print(f"歌名：{song['title']}")
print(f"歌手：{song['artist']}")
print(f"年份：{song['year']}")
```

---

**⭐⭐ 中等**

```python
contacts = {}

while True:
    print("\n--- 通讯录 ---")
    print("1. 添加联系人")
    print("2. 查询电话")
    print("3. 显示全部")
    print("输入 quit 退出")
    choice = input("请选择：")

    if choice == "1":
        name = input("请输入姓名：")
        phone = input("请输入电话：")
        contacts[name] = phone
        print("添加成功！")
    elif choice == "2":
        name = input("请输入要查询的姓名：")
        if name in contacts:
            print(f"{name} 的电话：{contacts[name]}")
        else:
            print("未找到该联系人")
    elif choice == "3":
        for name, phone in contacts.items():
            print(f"{name}: {phone}")
    elif choice == "quit":
        break
    else:
        print("无效选项，请重新选择")
```

---

**⭐⭐⭐ 困难**

```python
students = {
    "小明": {"math": 95, "chinese": 88, "english": 92},
    "小红": {"math": 78, "chinese": 85, "english": 80},
    "小刚": {"math": 92, "chinese": 90, "english": 85}
}

while True:
    print("\n=== 成绩管理系统 ===")
    print("1. 查看所有学生成绩")
    print("2. 计算某学生平均分")
    print("3. 显示各科最高分")
    print("输入 quit 退出")

    choice = input("请选择：")

    if choice == "1":
        for name, scores in students.items():
            print(f"\n{name}:")
            for subject, score in scores.items():
                print(f"  {subject}: {score}")
    elif choice == "2":
        name = input("请输入学生姓名：")
        if name in students:
            scores = students[name].values()
            avg = sum(scores) / len(scores)
            print(f"{name} 的平均分：{round(avg, 1)}")
        else:
            print("未找到该学生")
    elif choice == "3":
        subjects = ["math", "chinese", "english"]
        for subject in subjects:
            best_student = max(students, key=lambda s: students[s][subject])
            best_score = students[best_student][subject]
            print(f"{subject} 最高分：{best_student} {best_score}分")
    elif choice == "quit":
        break
```

---

## 第13章 函数——把代码打包成积木

**⭐ 容易**

```python
def is_even(num):
    return num % 2 == 0

for i in range(1, 11):
    if is_even(i):
        print(f"{i} 是偶数")
    else:
        print(f"{i} 是奇数")
```

---

**⭐⭐ 中等**

```python
def is_prime(n):
    if n < 2:
        return False
    for i in range(2, n):
        if n % i == 0:
            return False
    return True

print("2~100之间的质数：")
for num in range(2, 101):
    if is_prime(num):
        print(num, end=" ")
```

---

**⭐⭐⭐ 困难**

```python
def check_password_strength(pwd):
    if len(pwd) < 6:
        return "弱：密码太短（至少6位）"

    has_upper = False
    has_lower = False
    has_digit = False

    for ch in pwd:
        if ch.isupper():
            has_upper = True
        elif ch.islower():
            has_lower = True
        elif ch.isdigit():
            has_digit = True

    if has_upper and has_lower and has_digit:
        return "强：包含大写、小写和数字"
    elif has_upper or has_digit:
        return "中：建议同时包含大小写字母和数字"
    else:
        return "弱：请混合大小写字母和数字"

# 测试
print(check_password_strength("abc"))
print(check_password_strength("Abc123"))
print(check_password_strength("Hello999"))
print(check_password_strength("PythonRocks"))
```

---

## 第14章 面向对象入门——把数据和功能打包在一起

**⭐ 容易**

```python
class Book:
    def __init__(self, title, author, pages):
        self.title = title
        self.author = author
        self.pages = pages

    def info(self):
        print(f"《{self.title}》- {self.author}（{self.pages}页）")

book1 = Book("三体", "刘慈欣", 300)
book2 = Book("活着", "余华", 200)
book1.info()
book2.info()
```

---

**⭐⭐ 中等**

```python
class BankAccount:
    def __init__(self, owner):
        self.owner = owner
        self.balance = 0

    def deposit(self, amount):
        self.balance += amount
        print(f"存入 {amount} 元，余额 {self.balance}")

    def withdraw(self, amount):
        if amount > self.balance:
            print(f"余额不足！当前余额 {self.balance}")
        else:
            self.balance -= amount
            print(f"取出 {amount} 元，余额 {self.balance}")

    def show(self):
        print(f"当前余额：{self.balance} 元")

account = BankAccount("张三")
account.deposit(500)
account.withdraw(200)
account.withdraw(400)
account.show()
```

---

**⭐⭐⭐ 困难**

```python
class Student:
    def __init__(self, name):
        self.name = name
        self.scores = {}

    def add_score(self, subject, score):
        self.scores[subject] = score

    def average(self):
        if not self.scores:
            return 0
        return sum(self.scores.values()) / len(self.scores)

    def report(self):
        print(f"\n=== {self.name} 的成绩单 ===")
        for subject, score in self.scores.items():
            print(f"  {subject}: {score}")
        print(f"  平均分: {round(self.average(), 1)}")

# 创建多个学生
students = [
    Student("小明"),
    Student("小红"),
    Student("小刚")
]

# 添加成绩
students[0].add_score("语文", 92)
students[0].add_score("数学", 88)
students[0].add_score("英语", 95)

students[1].add_score("语文", 85)
students[1].add_score("数学", 90)
students[1].add_score("英语", 82)

students[2].add_score("语文", 78)
students[2].add_score("数学", 95)
students[2].add_score("英语", 88)

# 输出所有成绩单
for s in students:
    s.report()

# 找出平均分最高的学生
best = max(students, key=lambda s: s.average())
print(f"\n🏆 平均分最高的学生：{best.name} ({round(best.average(), 1)}分)")
```

---

## 附录：文件读写——让数据"留下来"

**⭐ 容易**

```python
# 写入 3 句话
with open("notes.txt", "w", encoding="utf-8") as f:
    for i in range(3):
        line = input(f"请输入第{i+1}句话：")
        f.write(line + "\n")

# 读出来打印
print("\n你写的内容：")
with open("notes.txt", "r", encoding="utf-8") as f:
    print(f.read())
```

---

**⭐⭐ 中等**

```python
# 持久化通讯录
import os

def load_contacts():
    contacts = {}
    if os.path.exists("contacts.txt"):
        with open("contacts.txt", "r", encoding="utf-8") as f:
            for line in f:
                name, phone = line.strip().split(":")
                contacts[name] = phone
    return contacts

def save_contacts(contacts):
    with open("contacts.txt", "w", encoding="utf-8") as f:
        for name, phone in contacts.items():
            f.write(f"{name}:{phone}\n")

contacts = load_contacts()

while True:
    print("\n--- 通讯录 ---")
    print("1. 添加联系人")
    print("2. 查询电话")
    print("3. 显示全部")
    print("输入 quit 退出")
    choice = input("请选择：")

    if choice == "1":
        name = input("请输入姓名：")
        phone = input("请输入电话：")
        contacts[name] = phone
        save_contacts(contacts)
        print("添加成功！")
    elif choice == "2":
        name = input("请输入姓名：")
        if name in contacts:
            print(f"{name}: {contacts[name]}")
        else:
            print("未找到")
    elif choice == "3":
        for name, phone in contacts.items():
            print(f"{name}: {phone}")
    elif choice == "quit":
        print("再见！")
        break
```

---

**⭐⭐⭐ 困难**

```python
import os

def write_diary():
    date = input("请输入日期（如 2026-06-01）：")
    content = input(f"请输入{date}的日记内容：")
    with open("diary.txt", "a", encoding="utf-8") as f:
        f.write(f"[{date}]\n{content}\n")
    print("日记已保存！")

def read_diary():
    if not os.path.exists("diary.txt"):
        print("还没有日记内容。")
        return
    keyword = input("请输入要搜索的关键词（直接回车显示全部）：")
    with open("diary.txt", "r", encoding="utf-8") as f:
        content = f.read()
    if keyword:
        lines = content.split("\n")
        found = False
        for line in lines:
            if keyword in line:
                print(line)
                found = True
        if not found:
            print("未找到包含该关键词的内容。")
    else:
        print(content)

while True:
    print("\n=== 日记本 ===")
    print("1. 写日记")
    print("2. 读日记")
    print("输入 quit 退出")
    choice = input("请选择：")

    if choice == "1":
        write_diary()
    elif choice == "2":
        read_diary()
    elif choice == "quit":
        break
```

---

## 第15章 异常处理——程序出错了怎么办

**⭐ 容易**

```python
try:
    a = int(input("请输入第一个整数："))
    b = int(input("请输入第二个整数："))
    result = a / b
    print(f"{a} ÷ {b} = {result}")
except ValueError:
    print("输入的不是数字，请重新运行程序")
except ZeroDivisionError:
    print("除数不能为0！")
```

---

**⭐⭐ 中等**

```python
import random

target = random.randint(1, 100)
count = 0

while True:
    user_input = input("猜一个数字（1~100）：")
    try:
        guess = int(user_input)
    except ValueError:
        print("请输入数字！")
        continue

    count += 1
    if guess > target:
        print("猜大了")
    elif guess < target:
        print("猜小了")
    else:
        print(f"猜对了！你一共猜了{count}次")
        break
```

---

**⭐⭐⭐ 困难**

```python
def safe_read_file():
    filename = input("请输入要读取的文件名：")

    try:
        with open(filename, "r", encoding="utf-8") as f:
            content = f.read()
            print(f"文件内容（共{len(content)}字符）：")
            print(content)

    except FileNotFoundError:
        print(f"错误：文件'{filename}'不存在，请检查文件名")
    except PermissionError:
        print(f"错误：没有权限读取文件'{filename}'")
    except UnicodeDecodeError:
        print(f"错误：文件'{filename}'不是文本文件，无法读取")
    except Exception as e:
        print(f"发生未知错误：{e}")

safe_read_file()
```

---

## 附录：面向对象进阶——继承、多态与魔法方法

> ⚠️ 本章为进阶内容，从主教程移至附录。建议学完前 15 章并有 2~3 个小项目经验后再来阅读。

**⭐ 容易**

```python
class Shape:
    def __init__(self, name):
        self.name = name

    def area(self):
        return 0

class Rectangle(Shape):
    def __init__(self, width, height):
        super().__init__("矩形")
        self.width = width
        self.height = height

    def area(self):
        return self.width * self.height

class Circle(Shape):
    def __init__(self, radius):
        super().__init__("圆形")
        self.radius = radius

    def area(self):
        return 3.14 * self.radius ** 2

shapes = [Rectangle(10, 5), Circle(7), Rectangle(3, 4)]
for s in shapes:
    print(f"{s.name}的面积：{s.area()}")
```

---

**⭐⭐ 中等**

```python
class Book:
    def __init__(self, title, author):
        self.title = title
        self.author = author

    def __str__(self):
        return f"《{self.title}》- {self.author}"

class Library:
    def __init__(self):
        self.books = []

    def add_book(self, book):
        self.books.append(book)
        print(f"添加成功：{book}")

    def remove_book(self, title):
        for book in self.books:
            if book.title == title:
                self.books.remove(book)
                print(f"已删除：{title}")
                return
        print(f"未找到：《{title}》")

    def find_by_author(self, author):
        return [b for b in self.books if b.author == author]

    def list_all(self):
        print("\n--- 图书馆藏书 ---")
        for book in self.books:
            print(book)

lib = Library()
lib.add_book(Book("三体", "刘慈欣"))
lib.add_book(Book("流浪地球", "刘慈欣"))
lib.add_book(Book("活着", "余华"))
lib.add_book(Book("许三观卖血记", "余华"))
lib.add_book(Book("三毛流浪记", "张乐平"))

lib.list_all()

print("\n--- 搜索：刘慈欣 ---")
for book in lib.find_by_author("刘慈欣"):
    print(book)
```

---

**⭐⭐⭐ 困难**

```python
class Employee:
    def __init__(self, name, base_salary):
        self.name = name
        self.base_salary = base_salary

    def calculate_salary(self):
        return self.base_salary

    def __str__(self):
        return f"{self.name}：{self.calculate_salary()}元"

class Manager(Employee):
    def __init__(self, name, base_salary, bonus):
        super().__init__(name, base_salary)
        self.bonus = bonus

    def calculate_salary(self):
        return self.base_salary + self.bonus

class Intern(Employee):
    def __init__(self, name, daily_wage, days):
        super().__init__(name, 0)
        self.daily_wage = daily_wage
        self.days = days

    def calculate_salary(self):
        return self.daily_wage * self.days

    def __str__(self):
        return f"{self.name}（实习）：{self.calculate_salary()}元"

class Salesperson(Employee):
    def __init__(self, name, base_salary, sales, commission_rate):
        super().__init__(name, base_salary)
        self.sales = sales
        self.commission_rate = commission_rate

    def calculate_salary(self):
        return self.base_salary + self.sales * self.commission_rate

employees = [
    Manager("张三", 8000, 5000),
    Intern("李四", 200, 22),
    Salesperson("王五", 3000, 50000, 0.05),
    Employee("赵六", 6000)
]

print("=== 员工薪资报表 ===")
total = 0
for emp in employees:
    print(emp)
    total += emp.calculate_salary()

print(f"\n本月总薪资：{total}元")
print(f"平均薪资：{round(total / len(employees), 1)}元")
```

---

## 第16章 嵌入式是什么 & 认识 ESP32

**⭐ 容易**

嵌入式系统和普通电脑的主要区别：

1. **专用性**：嵌入式系统通常只做一件事（如微波炉控制），而普通电脑通用
2. **资源限制**：嵌入式系统 RAM/ROM 很小（KB/MB 级），普通电脑大（GB 级）
3. **功耗**：嵌入式系统功耗低（mW），普通电脑功耗高（几十瓦）
4. **交互方式**：嵌入式系统通常没有屏幕键盘，通过传感器/引脚与外界交互

ESP32 相比其他单片机的优势：
- 双核处理器 240MHz，性能较强
- 内置 Wi-Fi + 蓝牙，通信能力强
- 价格便宜（20~30 元）
- 支持 MicroPython，编程友好

---

**⭐⭐ 中等**

1. 查阅 ESP32 的数据手册，列出它支持的外设接口（UART、I2C、SPI、I2S、CAN 等）
2. ESP32 的 GPIO 引脚大部分是功能复用的（如某些引脚同时支持 ADC/DAC/Touch 等）

---

**⭐⭐⭐ 困难**

查阅 MicroPython 官方文档，列举 ESP32 上可用的 machine 模块的核心类：

```
Pin      — GPIO 输入输出
PWM      — 脉冲宽度调制
ADC      — 模拟信号读取
DAC      — 模拟信号输出（部分引脚）
I2C      — I2C 总线通信
SPI      — SPI 总线通信
UART     — 串口通信
Timer    — 定时器
RTC      — 实时时钟
WDT      — 看门狗定时器
```

---

## 第17章 MicroPython 固件烧录 & Thonny 连接

**⭐ 容易**

按本章步骤完成固件烧录后，在 Thonny Shell 中运行：

```python
import esp
esp.osdebug(None)
print("Hello from ESP32!")
```

预期输出：
```
Hello from ESP32!
```

---

**⭐⭐ 中等**

在 Thonny Shell 中依次测试：

```python
import machine
print(machine.freq())   # 查看 CPU 频率

import gc
print(gc.mem_free())    # 查看剩余内存

import sys
print(sys.version)      # 查看 MicroPython 版本
```

---

**⭐⭐⭐ 困难**

查阅 MicroPython 和 ESP-IDF 官方文档，比较两种开发方式：

| 对比维度 | MicroPython | ESP-IDF (C) |
|---------|------------|-------------|
| 上手难度 | 简单，Python 语法 | 较难，需 C 语言 |
| 运行速度 | 较慢（解释执行） | 快（编译执行） |
| 内存占用 | 较大（运行时约 150KB） | 小 |
| 库生态 | 有限，但够用 | 丰富，官方支持 |
| 适合场景 | 快速原型、教学 | 正式产品、性能要求高 |

---

## 第18章 GPIO 点亮 LED——嵌入式版的 Hello World

**⭐ 容易**

```python
from machine import Pin
import time

led = Pin(13, Pin.OUT)

# 快速闪烁 10 次
for _ in range(10):
    led.value(1)
    time.sleep(0.3)
    led.value(0)
    time.sleep(0.3)

# 长亮 3 秒
led.value(1)
time.sleep(3)
led.value(0)
```

---

**⭐⭐ 中等**

```python
from machine import Pin
import time

led1 = Pin(13, Pin.OUT)
led2 = Pin(12, Pin.OUT)
led3 = Pin(14, Pin.OUT)

leds = [led1, led2, led3]

while True:
    for led in leds:
        led.value(1)
        time.sleep(0.3)
        led.value(0)
        time.sleep(0.3)
```

---

**⭐⭐⭐ 困难**

```python
from machine import Pin
import time

# 红灯 GPIO13，黄灯 GPIO12，绿灯 GPIO14
red = Pin(13, Pin.OUT)
yellow = Pin(12, Pin.OUT)
green = Pin(14, Pin.OUT)

while True:
    # 红灯 5 秒
    red.value(1)
    time.sleep(5)
    red.value(0)

    # 黄灯闪烁 3 次
    for _ in range(3):
        yellow.value(1)
        time.sleep(0.5)
        yellow.value(0)
        time.sleep(0.5)

    # 绿灯 4 秒
    green.value(1)
    time.sleep(4)
    green.value(0)
```

---

## 第19章 按键输入——ESP32 感知物理世界

**⭐ 容易**

```python
from machine import Pin
import time

led = Pin(13, Pin.OUT)
button = Pin(25, Pin.IN, Pin.PULL_UP)

led_state = False

while True:
    if button.value() == 0:          # 按键按下
        time.sleep(0.2)              # 消抖
        if button.value() == 0:      # 确认按下
            led_state = not led_state
            led.value(led_state)
            while button.value() == 0:  # 等待松开
                time.sleep(0.1)
```

---

**⭐⭐ 中等**

```python
from machine import Pin
import time

led = Pin(13, Pin.OUT)
button = Pin(25, Pin.IN, Pin.PULL_UP)

last_press_time = 0

while True:
    if button.value() == 0:
        time.sleep(0.05)
        if button.value() == 0:
            now = time.ticks_ms()
            interval = time.ticks_diff(now, last_press_time)

            if interval < 400:   # 双击
                for _ in range(5):
                    led.value(1)
                    time.sleep(0.1)
                    led.value(0)
                    time.sleep(0.1)
                last_press_time = 0
            else:                # 单击
                led.value(1)
                time.sleep(1)
                led.value(0)
                last_press_time = now

            while button.value() == 0:
                time.sleep(0.05)
```

---

**⭐⭐⭐ 困难**

```python
from machine import Pin, PWM
import time

led = PWM(Pin(13), freq=5000)
led.duty(0)

button = Pin(25, Pin.IN, Pin.PULL_UP)

mode = 0  # 0=呼吸, 1=常亮, 2=闪烁

def breathe():
    for d in range(0, 1024, 8):
        led.duty(d)
        time.sleep(0.003)
    for d in range(1023, -1, -8):
        led.duty(d)
        time.sleep(0.003)

def steady():
    led.duty(1023)

def blink():
    for _ in range(3):
        led.duty(1023)
        time.sleep(0.2)
        led.duty(0)
        time.sleep(0.2)

while True:
    # 检查按键
    if button.value() == 0:
        time.sleep(0.2)
        if button.value() == 0:
            mode = (mode + 1) % 3
            print(f"切换到模式 {mode}")
            while button.value() == 0:
                time.sleep(0.1)

    # 执行当前模式
    if mode == 0:
        breathe()
    elif mode == 1:
        steady()
    else:
        blink()
```

---

## 第20章 PWM 呼吸灯——让 LED 像呼吸一样渐变

**⭐ 容易**

```python
from machine import Pin, PWM
import time

led = PWM(Pin(13), freq=5000)

while True:
    for duty in range(0, 1024, 8):
        led.duty(duty)
        time.sleep(0.003)
    for duty in range(1023, -1, -8):
        led.duty(duty)
        time.sleep(0.003)
```

---

**⭐⭐ 中等**

```python
from machine import Pin, PWM
import time

led = PWM(Pin(13), freq=5000)
led.duty(1023)   # 初始常亮

button = Pin(25, Pin.IN, Pin.PULL_UP)

mode = 0  # 0=呼吸, 1=常亮, 2=闪烁

def breathe():
    for d in range(0, 1024, 4):
        led.duty(d)
        time.sleep(0.005)
    for d in range(1023, -1, -4):
        led.duty(d)
        time.sleep(0.005)
    return False  # 不是短时模式

def steady():
    led.duty(1023)
    return False

def blink():
    led.duty(1023)
    time.sleep(0.3)
    led.duty(0)
    time.sleep(0.3)
    return False

modes = [breathe, steady, blink]

while True:
    if button.value() == 0:
        time.sleep(0.2)
        if button.value() == 0:
            mode = (mode + 1) % 3
            while button.value() == 0:
                time.sleep(0.05)

    modes[mode]()
```

---

**⭐⭐⭐ 困难**

```python
from machine import Pin, PWM
import time

# RGB LED 三色引脚
red = PWM(Pin(13), freq=5000)
green = PWM(Pin(12), freq=5000)
blue = PWM(Pin(14), freq=5000)

def set_color(r, g, b):
    red.duty(1023 - r)
    green.duty(1023 - g)
    blue.duty(1023 - b)

def fade_in_out(pwm, steps=1024, delay=0.003):
    for d in range(0, steps, 8):
        pwm.duty(d)
        time.sleep(delay)
    for d in range(steps - 1, -1, -8):
        pwm.duty(d)
        time.sleep(delay)

while True:
    # 红色渐变
    fade_in_out(red)
    # 绿色渐变
    fade_in_out(green)
    # 蓝色渐变
    fade_in_out(blue)
```

---

## 第21章 🏆 毕业项目：温湿度计 + OLED 显示

**⭐ 容易**

按硬件连接图接好 DHT11 和 OLED，运行章节中的完整代码，验证 OLED 屏幕正确显示温湿度数据即可。

参考代码（即章节完整代码）：

```python
from machine import Pin, SoftI2C
import dht
import ssd1306
import time

dht_sensor = dht.DHT11(Pin(4))

i2c = SoftI2C(scl=Pin(22), sda=Pin(21))
oled = ssd1306.SSD1306_I2C(128, 64, i2c)

while True:
    try:
        dht_sensor.measure()
        temp = dht_sensor.temperature()
        hum = dht_sensor.humidity()

        oled.fill(0)
        oled.text("Temp & Hum", 0, 0)
        oled.text(f"Temp: {temp} C", 0, 25)
        oled.text(f"Hume: {hum} %", 0, 45)
        oled.text("Press Ctrl+C", 0, 55)
        oled.show()
        time.sleep(2)

    except OSError:
        oled.fill(0)
        oled.text("Sensor Error!", 0, 25)
        oled.show()
        time.sleep(2)
```

---

**⭐⭐ 中等**

```python
from machine import Pin, SoftI2C
import dht
import ssd1306
import time

dht_sensor = dht.DHT11(Pin(4))
led = Pin(13, Pin.OUT)

i2c = SoftI2C(scl=Pin(22), sda=Pin(21))
oled = ssd1306.SSD1306_I2C(128, 64, i2c)

while True:
    try:
        dht_sensor.measure()
        temp = dht_sensor.temperature()
        hum = dht_sensor.humidity()

        oled.fill(0)
        oled.text(f"Temp: {temp} C", 0, 0)
        oled.text(f"Hume: {hum} %", 0, 20)

        # 温湿度判断
        if temp > 30:
            oled.text("Hot!", 0, 40)
        elif temp < 15:
            oled.text("Cold!", 0, 40)
        else:
            oled.text("Comfort", 0, 40)

        if hum > 70:
            oled.text("Wet!", 0, 50)
        elif hum < 30:
            oled.text("Dry!", 0, 50)

        oled.show()

        # 温度超32℃ LED告警
        if temp > 32:
            led.value(1)
            time.sleep(0.3)
            led.value(0)
            time.sleep(0.3)
        else:
            led.value(0)
            time.sleep(2)

    except OSError:
        oled.fill(0)
        oled.text("Sensor Error!", 0, 25)
        oled.show()
        time.sleep(2)
```

---

**⭐⭐⭐ 困难 —— 毕业项目**

```python
from machine import Pin, SoftI2C, PWM
import dht
import ssd1306
import time

# ====== 硬件初始化 ======
dht_sensor = dht.DHT11(Pin(4))
led = PWM(Pin(13), freq=5000)
led.duty(0)

button = Pin(25, Pin.IN, Pin.PULL_UP)

i2c = SoftI2C(scl=Pin(22), sda=Pin(21))
oled = ssd1306.SSD1306_I2C(128, 64, i2c)

# ====== 状态变量 ======
display_mode = 0   # 0=双行显示, 1=大字温度
led_alert_active = False

def led_alert():
    """LED 闪烁告警"""
    for _ in range(3):
        led.duty(1023)
        time.sleep(0.1)
        led.duty(0)
        time.sleep(0.1)

while True:
    try:
        dht_sensor.measure()
        temp = dht_sensor.temperature()
        hum = dht_sensor.humidity()

        # 温度超32℃触发告警
        if temp > 32:
            led_alert_active = True
        else:
            led_alert_active = False

        # 按键检测（切换显示模式）
        if button.value() == 0:
            time.sleep(0.2)
            if button.value() == 0:
                display_mode = 1 - display_mode
                while button.value() == 0:
                    time.sleep(0.05)

        oled.fill(0)

        if display_mode == 0:
            # 双行显示
            oled.text(f"Temp: {temp} C", 0, 10)
            oled.text(f"Hume: {hum} %", 0, 30)
            if temp > 30:
                oled.text("Hot!", 80, 10)
            elif temp < 15:
                oled.text("Cold!", 80, 10)
            if hum > 70:
                oled.text("Wet!", 80, 30)
            elif hum < 30:
                oled.text("Dry!", 80, 30)
        else:
            # 大字温度
            oled.text(f"{temp}C", 20, 20)

        oled.show()

        if led_alert_active:
            led_alert()
        else:
            led.duty(0)
            time.sleep(2)

    except OSError:
        oled.fill(0)
        oled.text("Sensor Error!", 0, 25)
        oled.show()
        time.sleep(1)
```
