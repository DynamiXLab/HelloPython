# 第10章 参考答案

## ⭐ 容易

```python
import math
print(f"π = {math.pi}")
print(f"√2 = {math.sqrt(2)}")
```

## ⭐⭐ 中等

```python
import random
counts = [0] * 6
for i in range(10):
    result = random.randint(1, 6)
    print(f"第{i+1}次：{result}")
    counts[result - 1] += 1
print()
for i in range(6):
    print(f"{i+1} 出现了 {counts[i]} 次")
```

## ⭐⭐⭐ 困难

```python
import random
chars = "abcdefghijklmnopqrstuvwxyz0123456789!@#$%"
password = ""
for i in range(8):
    password += random.choice(chars)
print(f"生成的密码：{password}")
```
