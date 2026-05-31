# 第6章 参考答案

## ⭐ 容易

```python
name = input("请输入你的名字：")
age = int(input("请输入你的年龄："))
print(f"{name}，你好！10年后你将是{age + 10}岁。")
```

## ⭐⭐ 中等

```python
weight = float(input("请输入体重(kg)："))
height = float(input("请输入身高(m)："))
bmi = weight / height ** 2
print(f"BMI：{round(bmi, 2)}")
```

## ⭐⭐⭐ 困难

```python
temp = float(input("请输入温度值："))
unit = input("请输入单位（C/F）：")
if unit == "C":
    f = temp * 9 / 5 + 32
    print(f"{temp}°C = {f:.1f}°F")
elif unit == "F":
    c = (temp - 32) * 5 / 9
    print(f"{temp}°F = {c:.1f}°C")
```
