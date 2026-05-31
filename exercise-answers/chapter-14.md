# 第14章 参考答案

## ⭐ 容易

```python
class Book:
    def __init__(self, title, author, pages):
        self.title = title
        self.author = author
        self.pages = pages

    def info(self):
        print(f"《{self.title}》作者：{self.author}，{self.pages}页")

book1 = Book("三体", "刘慈欣", 300)
book2 = Book("活着", "余华", 200)
book1.info()
book2.info()
```

## ⭐⭐ 中等

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

acc = BankAccount("张三")
acc.deposit(500)
acc.withdraw(200)
acc.withdraw(400)
acc.show()
```

## ⭐⭐⭐ 困难

```python
class Calculator:
    def __init__(self):
        self.history = []

    def add(self, a, b):
        result = a + b
        self.history.append(f"{a} + {b} = {result}")
        return result

    def sub(self, a, b):
        result = a - b
        self.history.append(f"{a} - {b} = {result}")
        return result

    def mul(self, a, b):
        result = a * b
        self.history.append(f"{a} × {b} = {result}")
        return result

    def div(self, a, b):
        if b == 0:
            print("错误：除数不能为 0")
            return None
        result = a / b
        self.history.append(f"{a} ÷ {b} = {result}")
        return result

    def show_history(self):
        for record in self.history:
            print(record)

calc = Calculator()
calc.add(10, 5)
calc.mul(3, 7)
calc.div(10, 0)
calc.show_history()
```
