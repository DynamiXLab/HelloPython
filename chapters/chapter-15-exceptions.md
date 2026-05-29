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

### 练习任务

**任务（⭐ 容易）**：让用户输入两个整数并计算除法。用 `try...except` 处理以下情况：

- 输入非数字时提示"请输入数字"
- 除数为 0 时提示"除数不能为 0"

**任务（⭐⭐ 中等）**：改进第10章的猜数字游戏——给用户 `try...except` 保护，输入非数字时提示"请输入数字"，不计入猜测次数。

**任务（⭐⭐⭐ 困难）**：写一个"安全文件读取器"：

1. 提示用户输入文件名
2. 尝试读取并显示文件内容
3. 处理所有可能的异常：
   - 文件不存在（`FileNotFoundError`）→ 提示"文件不存在"
   - 权限不足（`PermissionError`）→ 提示"没有读取权限"
   - 编码错误（`UnicodeDecodeError`）→ 提示"文件编码不支持"
   - 其他异常 → 提示"未知错误"并显示错误信息
4. 用 `while True` 循环让用户反复尝试，输入 `quit` 退出

```python
while True:
    filename = input("请输入文件名（quit退出）：")
    if filename == "quit":
        break
    try:
        with open(filename, "r", encoding="utf-8") as f:
            print(f.read())
    except FileNotFoundError:
        print("文件不存在！")
    except PermissionError:
        print("没有读取权限！")
    except UnicodeDecodeError:
        print("文件编码不支持！")
    except Exception as e:
        print(f"未知错误：{e}")
```

> 综合运用：异常处理（第15章）+ 文件读写（第14章）+ while 循环（第10章）+ 条件判断（第7章）。
