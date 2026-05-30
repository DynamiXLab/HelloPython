# 第20章 按键输入——ESP32 感知物理世界

> **难度**：⭐⭐⭐  
> **所属教程**：Python 零基础入门到 MicroPython 嵌入式实战  
> **前置章节**：第19章（PWM 呼吸灯）

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

### 练习任务

**任务（⭐ 容易）**：用按键控制一个 LED 的开关。第一次按下 → LED 亮，第二次按下 → LED 亮……松开 → LED 灭（按住亮，松开灭）。

**任务（⭐⭐ 中等）**：用按键实现**模式切换**。第一次按下 → LED 亮，第二次按下 → LED 灭，第三次按下 → LED 亮……如此循环（切换模式）。

> 提示：用一个变量 `led_state = False` 记住当前状态，每次按下时 `led_state = not led_state` 翻转。注意要加"消抖"——按下后等 0.2 秒再检测。

**任务（⭐⭐⭐ 困难）**：实现**单击 / 双击检测**：

- 快速按一次（单击）→ LED 亮 1 秒后灭
- 快速连按两次（双击）→ LED 快闪 5 次
- 用 `time.ticks_ms()` 记录两次按键的时间间隔，小于 400ms 判定为双击

```python
# 参考思路
last_press = 0
while True:
    if button.value() == 0:
        now = time.ticks_ms()
        interval = time.ticks_diff(now, last_press)
        last_press = now
        if interval < 400:
            # 双击处理
        else:
            # 等一会儿看看有没有第二次按下
```

> 综合运用：GPIO 输入/输出（第18、19章）+ 条件判断（第7章）+ 变量状态管理（第3章）。

---

💡 **思考延续**

你有没有注意到这段代码里的 `time.sleep(0.2)`？它的名字叫**消抖**（debounce），是嵌入式开发中的经典问题。物理按键的金属触点不是瞬间闭合——它会在极短时间内弹跳（bounce）数次，产生一连串的快速开/关信号。如果不消抖，程序可能会把一次按下误判为好几次。

软件消抖（延时再检测）是最简单有效的方式。将来你在任何设备上按下按钮时，心里都会默认：背后有消抖代码。
