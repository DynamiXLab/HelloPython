# HelloPython — Python 零基础到 MicroPython 嵌入式实战

> 🎯 贺州学院 **机动不已实验室** 新人培养教程。从 Python 入门到 ESP32 嵌入式实战，20 章主线 + 附录。

## 📖 关于本教程

本教程由机动不已实验室编写，面向**零编程基础**的新队员。目标是让你快速掌握 Python 基础，并能用 ESP32 做一些简单的嵌入式项目。

学完本教程后，Python 可以直接用于实验室参加的 **自主巡航** 等现有比赛项目。如果你想在嵌入式方向走得更远，后面还有**绘制 PCB、设计原理图、C/C++ 裸机编程**等更深入的内容——嵌入式远不止点个灯，但这本教程是一个扎实的起点。

> 💪 实验室喜欢**积极主动**的人。前几个高质量完成全部练习的队员，可以借用实验室资源继续往下做更复杂的项目。实验室资源有限，为了可持续发展，我们会优先支持投入度高、进度快的同学——这不是筛选，是让最想学的人不被耽误。

## 🛒 前提准备

| 物品 | 参考价格 | 说明 |
|------|---------|------|
| 一台电脑（Windows / macOS 均可） | — | 前半部分纯 Python 只用电脑 |
| ESP32 开发板（Type-C 接口） | 约 20 元 | 第16章起需要 |
| Type-C 数据线 | 约 10 元 | 连接 ESP32 |
| 面包板 + 杜邦线 | 约 10 元 | 免焊接连接 |
| I2C OLED 屏幕（SSD1306） | 约 10 元 | 第21章用 |
| LED 灯珠 ×3（红、绿、蓝） | 实验室提供 | 第18/19章用 |
| 1kΩ 电阻 ×3 | 实验室提供 | 限流保护 |
| 按键开关 ×2 | 实验室提供 | 第20章用 |
| AHT20 温湿度传感器 | 实验室提供 | 第21章用 |

> 🚚 嵌入式硬件快递一般 **2~3 天**就到。建议**先学前半部分（第1~14章纯 Python），学到第14章时提前 5 天左右下单**。一来不耽误进度，二来如果你学了几天发现不感兴趣，也不会浪费钱。

## 📚 教程结构

| 阶段 | 章节 | 内容 |
|------|------|------|
| **Python 基础** | 第1~5章 | 环境搭建 (Thonny/VS Code)、变量与类型、数字运算、字符串 (f-string/转义/r'') |
| **交互与逻辑** | 第6~10章 | input()、条件判断 (缩进详解)、列表 (索引/切片)、for/while 循环、导入模块 |
| **数据结构与函数** | 第11~13章 | 字典与元组 (三容器对比)、函数 (参数/返回值)、OOP 入门 (类/对象/self) |
| **工程化** | 第14~15章 | 异常处理 (try/except/防御式编程) |
| **嵌入式实战** | 第16~21章 | ESP32 认识、固件烧录、GPIO LED (限流电阻/推挽开漏/上下拉)、PWM 呼吸灯 (RGB 混光)、按键输入 (消抖)、毕业项目 (I2C 温湿度+OLED)、通讯协议 (I2C/SPI/UART/CAN) |
| **附录** | — | 文件读写、OOP 进阶 (继承/多态/魔法方法)、问题排查 |

## 🗂 目录 & 14天学习计划

| 序号 | 章节 | 学习周期 | 预计用时 |
|------|------|---------|---------|
| 1 | [Python 是什么 & 安装 Thonny](chapters/chapter-01-python-intro.md) | Day 1 | 1h |
| 2 | [第一行代码：Hello, World!](chapters/chapter-02-hello-world.md) | Day 1 | |
| 3 | [变量——给数据取个名字](chapters/chapter-03-variables.md) | Day 2 | 1.5h |
| 4 | [数字与运算符](chapters/chapter-04-numbers-and-operators.md) | Day 2 | |
| 5 | [字符串——文本处理的起点](chapters/chapter-05-strings.md) | Day 3 | 1.5h |
| 6 | [input()——让程序和用户对话](chapters/chapter-06-input.md) | Day 4 | 1.5h |
| 7 | [条件判断——让程序学会做选择](chapters/chapter-07-conditionals.md) | Day 4 | |
| 8 | [列表——一个变量装多个数据](chapters/chapter-08-lists.md) | Day 5 | 1.5h |
| 9 | [for 循环——重复的事情交给机器](chapters/chapter-09-for-loop.md) | Day 6 | 1.5h |
| 10 | [导入模块——借用别人的代码](chapters/chapter-10-modules-import.md) | Day 6 | |
| 11 | [while 循环——不知道要循环多少次？](chapters/chapter-11-while-loop.md) | Day 7 | 1h |
| 12 | [字典与元组](chapters/chapter-12-dict-tuple.md) | Day 8 | 1.5h |
| 13 | [函数——把代码打包成积木](chapters/chapter-13-functions.md) | Day 8 | |
| 14 | [面向对象入门——把数据和功能打包](chapters/chapter-14-oop-basics.md) | Day 9 | 1.5h |
| 15 | [异常处理——程序出错了怎么办](chapters/chapter-15-exceptions.md) | Day 10 | 1h |
| 16 | [嵌入式是什么 & 认识 ESP32](chapters/chapter-16-embedded-esp32.md) | Day 11 | 1.5h |
| 17 | [MicroPython 固件烧录 & Thonny 连接](chapters/chapter-17-micropython-setup.md) | Day 11 | |
| 18 | [GPIO 点亮 LED](chapters/chapter-18-gpio-led.md) | Day 12 | 1.5h |
| 19 | [PWM 呼吸灯](chapters/chapter-19-pwm.md) | Day 13 | 1.5h |
| 20 | [按键输入——ESP32 感知物理世界](chapters/chapter-20-button-input.md) | Day 13 | |
| 21 | [🏆 毕业项目：温湿度计 + OLED](chapters/chapter-21-final-project.md) | Day 14 | 2h |
| | |
| 附 | [OOP 进阶（继承、多态、魔法方法）](chapters/appendix-oop-advanced.md) | 选读 | |
| 附 | [文件读写](chapters/appendix-file-io.md) | 选读 | |
| 附 | [问题排查 & 学习路线](chapters/appendix-troubleshooting.md) | 参考 | |

> 💡 每章末尾有三级难度练习（⭐容易 / ⭐⭐中等 / ⭐⭐⭐困难），先自己尝试再看参考答案。第3、5、8 章内容较多，可酌情拆分。14天后可继续选读附录。

## 📝 修订记录

| 日期 | 版本 | 说明 |
|------|------|------|
| 2026-05-29 | v1.0 | 初始版本，22章 Python 零基础到 MicroPython |
| 2026-05-30 | v2.0 | 练习升级为三级难度体系；新增导入模块章节；文件读写/OOP进阶移入附录；第14章新增通讯协议 (I2C/SPI/UART/CAN)；传感器改用 I2C-AHT20；新增 GPIO 推挽/开漏/上下拉详解；每章末尾新增思考延续故事；全面优化零基础教学体验 |

## 📄 许可

MIT License
