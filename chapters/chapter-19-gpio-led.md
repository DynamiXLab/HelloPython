# 第19章 GPIO 点亮 LED——嵌入式版的 Hello World

> **难度**：⭐⭐⭐  
> **所属教程**：Python 零基础入门到 MicroPython 嵌入式实战  
> **前置章节**：第18章（MicroPython 固件烧录 & Thonny 连接）

---

### 19.1 什么是 GPIO

GPIO（General Purpose Input/Output）即**通用输入输出引脚**。你可以通过代码控制这些引脚输出高电平（3.3V）或低电平（0V）。

### 19.2 硬件连接

```
ESP32 引脚 D13(GPIO13) ──── 220Ω 电阻 ──── LED 正极（长脚）
                                            │
                                         LED 负极（短脚） ──── GND
```

> **关键**：LED 长脚接正极，短脚接 GND。电阻必须串接，否则 LED 会烧掉。

### 19.3 代码——点亮 LED

```python
from machine import Pin
import time

# GPIO13 设为输出模式
led = Pin(13, Pin.OUT)

# 点亮 LED
led.value(1)     # 1 = 高电平 = 亮
time.sleep(2)    # 保持 2 秒
led.value(0)     # 0 = 低电平 = 灭
```

### 19.4 LED 闪烁

```python
from machine import Pin
import time

led = Pin(13, Pin.OUT)

while True:
    led.value(1)     # 亮
    time.sleep(0.5)  # 等 0.5 秒
    led.value(0)     # 灭
    time.sleep(0.5)  # 等 0.5 秒
```

你会看到 LED 以每秒一次的频率闪烁。恭喜，你写的代码已经能影响物理世界了！

---

### 练习任务

**任务（简单部分）**：按上图连接好电路，让 LED 以 0.3 秒间隔快速闪烁 10 次，然后长亮 3 秒再熄灭。

**任务（挑战部分）**：接上 3 个 LED（分别接 GPIO13、GPIO12、GPIO14），实现**流水灯**效果：LED1 亮 → 灭 → LED2 亮 → 灭 → LED3 亮 → 灭 → LED1 亮 → …… 不断循环。

> 提示：可以定义一个列表 `leds = [led1, led2, led3]`，用 for 循环配合 `time.sleep()` 控制。

```
电路参考：
GPIO13 ──[220Ω]── LED1 ── GND
GPIO12 ──[220Ω]── LED2 ── GND
GPIO14 ──[220Ω]── LED3 ── GND
```
