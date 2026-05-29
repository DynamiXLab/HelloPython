# 第21章 PWM 呼吸灯——让 LED 像呼吸一样渐变

> **难度**：⭐⭐⭐  
> **所属教程**：Python 零基础入门到 MicroPython 嵌入式实战  
> **前置章节**：第20章（按键输入）

---

### 21.1 什么是 PWM

PWM（脉冲宽度调制）通过快速开关来模拟不同的电压输出。在一个很短的时间周期里，如果 50% 时间高电平、50% 时间低电平，LED 看起来就是 50% 亮度。

### 21.2 MicroPython 的 PWM

```python
from machine import Pin, PWM
import time

led = PWM(Pin(13), freq=5000)   # 频率 5000Hz

# duty 范围 0~1023（10 位分辨率）
led.duty(0)      # 最暗（灭）
led.duty(512)    # 约 50% 亮度
led.duty(1023)   # 最亮
```

### 21.3 呼吸灯效果

```python
from machine import Pin, PWM
import time

led = PWM(Pin(13), freq=5000)

while True:
    # 亮度逐渐增加
    for duty in range(0, 1024, 4):
        led.duty(duty)
        time.sleep(0.005)

    # 亮度逐渐减小
    for duty in range(1023, -1, -4):
        led.duty(duty)
        time.sleep(0.005)
```

LED 会像呼吸一样，从暗到亮，再从亮到暗，不断循环。

---

### 练习任务

**任务（简单部分）**：接一个 LED，让它做一个呼吸周期（从暗到亮再到暗），但是速度是上面示例的两倍。

**任务（挑战部分）**：用第20章的按键来**切换模式**——按下按键在以下 3 种模式间循环切换：①呼吸灯 ②一直亮 ③闪烁模式。每个模式用不同的函数实现。
