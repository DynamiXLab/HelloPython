# HelloPython — Python 零基础到 MicroPython 嵌入式实战

> 🎯 从零开始学 Python，后半段用 ESP32 做嵌入式项目。21 章主线 + 附录，每章末尾有三档难度练习。

## 📚 教程结构

| 阶段 | 章节 | 内容 |
|------|------|------|
| **Python 基础** | 第1~5章 | 环境搭建、变量与数据类型、数字运算、字符串（f-string / 转义 / 原始字符串） |
| **交互与逻辑** | 第6~10章 | 用户输入、条件判断、列表（索引 / 切片）、for/while 循环、导入模块 |
| **数据结构与函数** | 第11~13章 | 字典与元组（含列表/元组/字典对比）、函数（参数/返回值/作用域） |
| **面向对象** | 第14章 | OOP 入门（类、对象、self、\__init__） |
| **异常处理** | 第15章 | 常见错误类型、try/except、防御式编程 |
| **嵌入式实战** | 第16~21章 | ESP32 + MicroPython：认识ESP32、固件烧录、GPIO LED、按键输入、PWM呼吸灯、毕业项目（温湿度计+OLED） |

## 🧩 每章亮点

- **三级练习体系**：⭐容易（仅本章知识）/ ⭐⭐中等（逻辑推理）/ ⭐⭐⭐困难（融会贯通前面章节）
- **💡 思考延续**：每章末尾附编程历史故事或冷知识（Ada Lovelace、Grace Hopper 的飞蛾、阿波罗登月计算机等）
- **参考答案**：`chapters/exercise-answers.md` 包含全部练习的参考代码
- **附录**：文件读写、OOP 进阶（继承、多态、魔法方法）作为选学内容

## 🛠 所需工具

- **编辑器**：Thonny（https://thonny.org）— 自带 MicroPython 固件烧录功能，无需额外工具
- **硬件**（第16章起）：ESP32 开发板 + USB 数据线（约 30 元）；基础元件由实验室提供

## 📅 14天学习计划

| 天数 | 章节 | 内容 | 预计用时 |
|------|------|------|---------|
| Day 1 | 第1~2章 | 安装 Thonny、第一行 Hello World | 1h |
| Day 2 | 第3~4章 | 变量与类型转换、数字运算 | 1.5h |
| Day 3 | 第5章 | 字符串（f-string、转义、r''、方法速查） | 1.5h |
| Day 4 | 第6~7章 | input()、条件判断、缩进规则 | 1.5h |
| Day 5 | 第8章 | 列表（索引规则、切片全解） | 1.5h |
| Day 6 | 第9~10章 | for 循环、导入模块 | 1.5h |
| Day 7 | 第11章 | while 循环 | 1h |
| Day 8 | 第12~13章 | 字典与元组、函数 | 1.5h |
| Day 9 | 第14章 | 面向对象入门（类、对象、self） | 1.5h |
| Day 10 | 第15章 | 异常处理（try/except、防御式编程） | 1h |
| Day 11 | 第16~17章 | 认识 ESP32、MicroPython 固件烧录 | 1.5h |
| Day 12 | 第18章 | GPIO 点亮 LED（含限流电阻计算） | 1.5h |
| Day 13 | 第19~20章 | PWM 呼吸灯、按键输入 | 1.5h |
| Day 14 | 第21章 | 🏆 毕业项目：温湿度计 + OLED 显示 | 2h |

> 💡 每天 1~2 小时即可完成。第5、8 章内容较多，可酌情拆分到两天。每章练习先自己做，再看 `exercise-answers.md`。14天后可继续选读附录（文件读写、OOP进阶）。

## 🗂 目录

| 序号 | 章节 | 学习周期 |
|------|------|---------|
| 1 | [Python 是什么 & 安装 Thonny](chapters/chapter-01-python-intro.md) | Day 1 |
| 2 | [第一行代码：Hello, World!](chapters/chapter-02-hello-world.md) | Day 1 |
| 3 | [变量——给数据取个名字](chapters/chapter-03-variables.md) | Day 2 |
| 4 | [数字与运算符](chapters/chapter-04-numbers-and-operators.md) | Day 2 |
| 5 | [字符串——文本处理的起点](chapters/chapter-05-strings.md) | Day 3 |
| 6 | [input()——让程序和用户对话](chapters/chapter-06-input.md) | Day 4 |
| 7 | [条件判断——让程序学会做选择](chapters/chapter-07-conditionals.md) | Day 4 |
| 8 | [列表——一个变量装多个数据](chapters/chapter-08-lists.md) | Day 5 |
| 9 | [for 循环——重复的事情交给机器](chapters/chapter-09-for-loop.md) | Day 6 |
| 10 | [导入模块——借用别人的代码](chapters/chapter-10-modules-import.md) | Day 6 |
| 11 | [while 循环——不知道要循环多少次？](chapters/chapter-11-while-loop.md) | Day 7 |
| 12 | [字典与元组](chapters/chapter-12-dict-tuple.md) | Day 8 |
| 13 | [函数——把代码打包成积木](chapters/chapter-13-functions.md) | Day 8 |
| 14 | [面向对象入门——把数据和功能打包](chapters/chapter-14-oop-basics.md) | Day 9 |
| 15 | [异常处理——程序出错了怎么办](chapters/chapter-15-exceptions.md) | Day 10 |
| 16 | [嵌入式是什么 & 认识 ESP32](chapters/chapter-16-embedded-esp32.md) | Day 11 |
| 17 | [MicroPython 固件烧录 & Thonny 连接](chapters/chapter-17-micropython-setup.md) | Day 11 |
| 18 | [GPIO 点亮 LED](chapters/chapter-18-gpio-led.md) | Day 12 |
| 19 | [PWM 呼吸灯](chapters/chapter-19-pwm.md) | Day 13 |
| 20 | [按键输入——ESP32 感知物理世界](chapters/chapter-20-button-input.md) | Day 13 |
| 21 | [🏆 毕业项目：温湿度计 + OLED](chapters/chapter-21-final-project.md) | Day 14 |
| | |
| 附 | [OOP 进阶（继承、多态、魔法方法）](chapters/appendix-oop-advanced.md) | 选读 |
| 附 | [文件读写](chapters/appendix-file-io.md) | 选读 |
| 附 | [问题排查 & 学习路线](chapters/appendix-troubleshooting.md) | 参考 |
| | [参考答案](chapters/exercise-answers.md) | |
| | [完整合订本](chapters/python-esp32-tutorial.md) | |
