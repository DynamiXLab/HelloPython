# 第10章 while 循环——不知道要循环多少次？

> **难度**：⭐⭐⭐  
> **所属教程**：Python 零基础入门到 MicroPython 嵌入式实战  
> **前置章节**：第9章（for 循环）

---

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

---

### 练习任务

**任务（简单部分）**：用 while 循环让用户不断输入数字，输入 `0` 时结束，最后输出所有输入数字的总和。

**任务（挑战部分）**：写一个**猜数字游戏**。程序随机生成一个 1~100 之间的数字，用户猜，每次猜完程序提示"猜大了"或"猜小了"，直到猜对为止，报告猜了多少次。

> 提示：`import random` 导入随机数模块，`random.randint(1, 100)` 生成 1~100 的随机整数。结合 while 和条件判断完成。
