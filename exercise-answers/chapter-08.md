# 第8章 参考答案

## ⭐ 容易

```python
fruits = ["苹果", "香蕉", "橘子", "葡萄", "草莓"]
print(fruits[0])
print(fruits[-1])
print(len(fruits))
```

## ⭐⭐ 中等

```python
scores = [78, 95, 62, 88, 73, 91, 56]
print(f"最高分：{max(scores)}")
print(f"最低分：{min(scores)}")

pass_count = 0
for s in scores:
    if s >= 60:
        pass_count += 1
print(f"及格人数：{pass_count}")

# 删除不及格
new_scores = []
for s in scores:
    if s >= 60:
        new_scores.append(s)
print(f"修改后列表：{new_scores}")
```

## ⭐⭐⭐ 困难

```python
names = []
scores = []
for i in range(5):
    names.append(input(f"请输入第{i+1}个同学的名字："))
    scores.append(int(input(f"请输入{names[-1]}的成绩：")))

pairs = list(zip(scores, names))
pairs.sort(reverse=True)

for rank, (score, name) in enumerate(pairs, 1):
    print(f"第{rank}名：{name} {score}分")
```
