# 第12章 参考答案

## ⭐ 容易

```python
song = {"title": "七里香", "artist": "周杰伦", "year": 2004}
print(f"歌名：{song['title']}，歌手：{song['artist']}，年份：{song['year']}")
```

## ⭐⭐ 中等

```python
contacts = {}
while True:
    print("--- 通讯录 ---")
    print("1. 添加联系人")
    print("2. 查询电话")
    print("3. 显示全部")
    choice = input("请选择（quit退出）：")
    if choice == "quit":
        break
    elif choice == "1":
        name = input("姓名：")
        phone = input("电话：")
        contacts[name] = phone
    elif choice == "2":
        name = input("请输入姓名：")
        print(contacts.get(name, "未找到"))
    elif choice == "3":
        for name, phone in contacts.items():
            print(f"{name}: {phone}")
```

## ⭐⭐⭐ 困难

```python
students = {}
while True:
    print("1.添加学生 2.录入成绩 3.查询 4.显示全部 quit退出")
    choice = input("请选择：")
    if choice == "quit":
        break
    elif choice == "1":
        name = input("姓名：")
        students[name] = {}
    elif choice == "2":
        name = input("姓名：")
        subject = input("科目：")
        score = int(input("成绩："))
        if name in students:
            students[name][subject] = score
    elif choice == "3":
        name = input("姓名：")
        if name in students:
            scores = students[name].values()
            avg = sum(scores) / len(scores) if scores else 0
            print(f"{name}：{students[name]}，平均分{avg:.1f}")
    elif choice == "4":
        for name, subjects in students.items():
            scores = subjects.values()
            avg = sum(scores) / len(scores) if scores else 0
            print(f"{name}：平均分{avg:.1f}")
```
