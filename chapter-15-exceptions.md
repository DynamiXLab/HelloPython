# 第15章 异常处理——程序出错了怎么办

> **难度**：⭐⭐  
> **所属教程**：Python 零基础入门到 MicroPython 嵌入式实战  
> **前置章节**：第14章（文件读写）

---

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

---

### 练习任务

**任务（简单部分）**：让用户输入两个整数并计算除法。用 `try...except` 处理用户输入非数字和除数为 0 的情况。

**任务（挑战部分）**：改进第10章的猜数字游戏——给用户 `try...except` 保护，输入非数字时提示"请输入数字"，不计入猜测次数。
