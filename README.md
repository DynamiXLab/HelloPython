# HelloPython — Python 零基础到 MicroPython 嵌入式实战

> 🎯 从零开始学 Python，后半段用 ESP32 做嵌入式项目。20 章主线 + 附录，每章末尾有三档难度练习。

## 📚 教程结构

| 阶段 | 章节 | 内容 |
|------|------|------|
| **Python 基础** | 第1~5章 | 环境搭建、变量与数据类型、数字运算、字符串（f-string / 转义 / 原始字符串） |
| **交互与逻辑** | 第6~10章 | 用户输入、条件判断、列表（索引 / 切片）、for/while 循环 |
| **数据结构与函数** | 第11~12章 | 字典与元组（含列表/元组/字典对比）、函数（参数/返回值/作用域） |
| **面向对象** | 第13章 | OOP 入门（类、对象、self、\__init__） |
| **异常处理** | 第14章 | 常见错误类型、try/except、防御式编程 |
| **嵌入式实战** | 第15~20章 | ESP32 + MicroPython：认识ESP32、固件烧录、GPIO LED、按键输入、PWM呼吸灯、毕业项目（温湿度计+OLED） |

## 🧩 每章亮点

- **三级练习体系**：⭐容易（仅本章知识）/ ⭐⭐中等（逻辑推理）/ ⭐⭐⭐困难（融会贯通前面章节）
- **💡 思考延续**：每章末尾附编程历史故事或冷知识（Ada Lovelace、Grace Hopper 的飞蛾、阿波罗登月计算机等）
- **参考答案**：`chapters/exercise-answers.md` 包含全部练习的参考代码
- **附录**：文件读写、OOP 进阶（继承、多态、魔法方法）作为选学内容

## 🛠 所需工具

- **编辑器**：Thonny（https://thonny.org）— 自带 MicroPython 固件烧录功能，无需额外工具
- **硬件**（第15章起）：ESP32 开发板 + USB 数据线（约 30 元）；基础元件由实验室提供

## 📖 使用方式

从头按章节顺序阅读，每章末尾有练习任务。先自己尝试，再看 `exercise-answers.md` 参考答案。

## 🗂 文件说明

```
HelloPython/
├── README.md                              ← 本文件
└── chapters/
    ├── chapter-01-python-intro.md         第1章  Python 是什么 & 安装 Thonny
    ├── chapter-02-hello-world.md          第2章  第一行代码：Hello, World!
    ├── chapter-03-variables.md            第3章  变量（含类型转换）
    ├── chapter-04-numbers-and-operators.md 第4章 数字与运算符
    ├── chapter-05-strings.md              第5章  字符串（f-string、转义、r''）
    ├── chapter-06-input.md                第6章  input()
    ├── chapter-07-conditionals.md         第7章  条件判断（含缩进详解）
    ├── chapter-08-lists.md                第8章  列表（索引、切片全解）
    ├── chapter-09-for-loop.md             第9章  for 循环
    ├── chapter-10-while-loop.md           第10章 while 循环
    ├── chapter-11-dict-tuple.md           第11章 字典与元组（三种容器对比）
    ├── chapter-12-functions.md            第12章 函数
    ├── chapter-13-oop-basics.md           第13章 面向对象入门
    ├── chapter-14-exceptions.md           第14章 异常处理
    ├── chapter-15-embedded-esp32.md       第15章 嵌入式是什么 & 认识 ESP32
    ├── chapter-16-micropython-setup.md    第16章 MicroPython 固件烧录
    ├── chapter-17-gpio-led.md             第17章 GPIO 点亮 LED
    ├── chapter-18-button-input.md         第18章 按键输入
    ├── chapter-19-pwm.md                  第19章 PWM 呼吸灯
    ├── chapter-20-final-project.md        第20章 🏆 毕业项目：温湿度计 + OLED
    ├── appendix-oop-advanced.md           附录：OOP 进阶（继承、多态）
    ├── appendix-file-io.md                附录：文件读写
    ├── appendix-troubleshooting.md        附录：问题排查 & 学习路线
    ├── exercise-answers.md                参考答案
    └── python-esp32-tutorial.md           完整合订本
```

## 📄 许可

MIT License
