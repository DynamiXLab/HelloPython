# 第5章 字符串——文本处理的起点

> **难度**：⭐⭐  
> **所属教程**：Python 零基础入门到 MicroPython 嵌入式实战  
> **前置章节**：第4章（数字与运算符）  
> **本章新知识点**：f-string、字符串方法（strip / upper / lower / replace）

---

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

---

### 练习任务

**任务（⭐ 容易）**：用 f-string 创建一个自我介绍模板，至少包含姓名、年龄、爱好三个变量，打印出一段完整的话。

**任务（⭐⭐ 中等）**：给定一个姓名变量 `full_name = " zhang san "`（注意前后有空格，且是小写），请用字符串方法把它格式化成 `"Zhang San"`（首字母大写，去掉两端空格）并输出。

> 提示：可以试试 `title()` 方法和 `strip()` 方法。

**任务（⭐⭐⭐ 困难）**：给定一个字符串 `sentence = "i love python and python loves me"`，完成以下操作并输出每一步的结果：

1. 统计 `python` 出现了几次（提示：用 `count()`）
2. 把所有的 `python` 替换成 `Java`
3. 把最终结果全部转成大写
4. 输出最终句子的总长度（提示：用 `len()`）

```python
sentence = "i love python and python loves me"
```

> 这道题综合运用了 `count()`、`replace()`、`upper()`、`len()` 和变量。
