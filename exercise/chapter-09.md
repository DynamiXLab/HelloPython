# 第9章 参考答案

## ⭐ 容易

```python
n = 7
for i in range(1, 11):
    print(f"{n} × {i} = {n * i}")
```

## ⭐⭐ 中等

```python
for i in range(1, 10):
    for j in range(1, i + 1):
        print(f"{i}×{j}={i*j}", end="\t")
    print()
```

## ⭐⭐⭐ 困难

```python
for i in range(1, 10):
    for j in range(1, i + 1):
        if (i * j) % 2 == 0:
            print(f"{i}×{j}={i*j}", end="\t")
        else:
            print(" " * 6, end="\t")
    print()
```
