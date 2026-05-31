# 第7章 参考答案

## ⭐ 容易

```python
guess = int(input("猜一个数字（1~10）："))
if guess == 7:
    print("猜对了！")
else:
    print("猜错了，答案是7")
```

## ⭐⭐ 中等

```python
year = int(input("请输入年份："))
if (year % 4 == 0 and year % 100 != 0) or (year % 400 == 0):
    print(f"{year} → 闰年")
else:
    print(f"{year} → 平年")
```

## ⭐⭐⭐ 困难

```python
score = int(input("请输入分数（0~100）："))
if score < 0 or score > 100:
    print("输入的分数无效！")
elif score >= 90:
    print("A — 优秀，继续保持！")
elif score >= 80:
    print("B — 良好，再加把劲！")
elif score >= 70:
    print("C — 中等，还有提升空间")
elif score >= 60:
    print("D — 及格，需要加油！")
else:
    print("F — 不及格，要努力了！")
```
