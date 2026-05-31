# 第5章 参考答案

## ⭐ 容易

```python
name = "张三"
age = 18
hobby = "编程"
print(f"我叫{name}，今年{age}岁，喜欢{hobby}")
```

## ⭐⭐ 中等

```python
full_name = " zhang san "
formatted = full_name.strip().title()
print(formatted)  # "Zhang San"
```

## ⭐⭐⭐ 困难

```python
sentence = "i love python and python loves me"

count = sentence.count("python")
print(f"'python' 出现了 {count} 次")

new_sentence = sentence.replace("python", "Java")
print(new_sentence)

upper_sentence = new_sentence.upper()
print(upper_sentence)

length = len(upper_sentence)
print(f"最终句子长度：{length}")
```
