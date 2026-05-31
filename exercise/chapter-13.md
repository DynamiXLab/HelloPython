# 第13章 参考答案

## ⭐ 容易

```python
def is_even(num):
    return num % 2 == 0

for i in range(1, 11):
    if is_even(i):
        print(f"{i} 是偶数")
    else:
        print(f"{i} 是奇数")
```

## ⭐⭐ 中等

```python
def is_prime(n):
    if n < 2:
        return False
    for i in range(2, int(n ** 0.5) + 1):
        if n % i == 0:
            return False
    return True

primes = [n for n in range(2, 101) if is_prime(n)]
print(primes)
```

## ⭐⭐⭐ 困难

```python
def factorial(n):
    result = 1
    for i in range(1, n + 1):
        result *= i
    return result

def fibonacci(n):
    result = [1, 1]
    for i in range(2, n):
        result.append(result[-1] + result[-2])
    return result[:n]

def gcd(a, b):
    while b:
        a, b = b, a % b
    return a

print(factorial(5))       # 120
print(fibonacci(8))       # [1, 1, 2, 3, 5, 8, 13, 21]
print(gcd(12, 8))         # 4
```
