# 第20章 按键输入——ESP32 感知物理世界

> **难度**：⭐⭐⭐  
> **所属教程**：Python 零基础入门到 MicroPython 嵌入式实战  
> **前置章节**：第19章（GPIO 点亮 LED）

---

### 20.1 数字输入

上一章我们用引脚输出信号（写），这一章用引脚读取信号（读）。

### 20.2 硬件连接

```
3.3V ──── 按键 ────┬──── GPIO25
                   │
                 10kΩ 下拉电阻
                   │
                  GND
```

简化的接法（利用 ESP32 内部上拉电阻）：

```
GND ──── 按键 ──── GPIO25
```

### 20.3 读取按键状态

```python
from machine import Pin
import time

# Pin.IN 表示输入模式，Pin.PULL_UP 启用内部上拉电阻
button = Pin(25, Pin.IN, Pin.PULL_UP)

while True:
    if button.value() == 0:   # 按下时值为 0（因为有上拉电阻）
        print("按键被按下了！")
    time.sleep(0.1)   # 短暂延时，防止输出刷屏
```

### 20.4 按键控制 LED

```python
from machine import Pin
import time

led = Pin(13, Pin.OUT)
button = Pin(25, Pin.IN, Pin.PULL_UP)

while True:
    if button.value() == 0:
        led.value(1)    # 按下亮
    else:
        led.value(0)    # 松开灭
    time.sleep(0.1)
```

---

### 练习任务

**任务（简单部分）**：用按键控制一个 LED 的开关。第一次按下 → LED 亮，第二次按下 → LED 灭，第三次按下 → LED 亮……如此循环（**切换模式**）。

> 提示：你需要一个变量 `led_state` 来记住当前状态，并在每次按下时翻转。

**任务（挑战部分）**：实现**单击 / 双击检测**。快速按一次（单击），LED 亮 1 秒后灭；快速连按两次（双击），LED 快闪 5 次。

> 提示：记录按键按下的时间 `time.ticks_ms()`，如果两次按键间隔小于 400 毫秒，判定为双击。
