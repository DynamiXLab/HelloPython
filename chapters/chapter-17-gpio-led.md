# 第17章 GPIO 点亮 LED——嵌入式版的 Hello World

> **难度**：⭐⭐⭐  
> **所属教程**：Python 零基础入门到 MicroPython 嵌入式实战  
> **前置章节**：第16章（MicroPython 固件烧录 & Thonny 连接）

---

### 17.1 什么是 GPIO

GPIO（General Purpose Input/Output）即**通用输入输出引脚**。你可以通过代码控制这些引脚输出高电平（3.3V）或低电平（0V）。

### 17.2 硬件连接

```
ESP32 引脚 D13(GPIO13) ──── 220Ω 电阻 ──── LED 正极（长脚）
                                            │
                                         LED 负极（短脚） ──── GND
```

> **关键**：LED 长脚接正极，短脚接 GND。电阻必须串接，否则 LED 会烧掉。

### 17.3 代码——点亮 LED

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

### 17.4 LED 闪烁

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

### 练习任务

**任务（⭐ 容易）**：连接一个 LED（GPIO13），让它以 0.3 秒间隔快速闪烁 10 次，然后长亮 3 秒再熄灭。

> 提示：用 `for i in range(10)` 循环 + `time.sleep(0.3)`。

**任务（⭐⭐ 中等）**：接上 3 个 LED（分别接 GPIO13、GPIO12、GPIO14），实现**流水灯**效果：LED1 亮 → 灭 → LED2 亮 → 灭 → LED3 亮 → 灭 → 循环往复。

```
电路参考：
GPIO13 ──[220Ω]── LED1 ── GND
GPIO12 ──[220Ω]── LED2 ── GND
GPIO14 ──[220Ω]── LED3 ── GND
```

> 提示：定义列表 `leds = [led1, led2, led3]`，用 for 循环控制。

**任务（⭐⭐⭐ 困难）**：用 3 个 LED 实现**倒计时灯**：

1. 开始时 3 个 LED 全亮
2. 每秒熄灭一个：3→2→1→0
3. 全灭后等 1 秒，然后 3 个 LED 同时快闪 3 次（模拟"发射"）
4. 最后全部长亮

> 综合运用：GPIO 输出（第17章）+ for 循环（第9章）+ 列表（第8章）+ `time.sleep()` 时间控制。

---

💡 **思考延续**

你刚点亮的这粒小小的 LED，是 1962 年由 **Nick Holonyak Jr.** 在通用电气实验室发明的——那是世界上第一颗可见光 LED。当时它只能发出微弱的红光，每颗要卖 200 美元。

经过 60 多年，LED 的亮度提升了上千倍，价格从几百美元降到了几分钱。当年 Holonyak 说："有一天 LED 会取代爱迪生的白炽灯泡。"当时没人信。而此时此刻，你正在用代码控制这束来自 1962 年的红光。
