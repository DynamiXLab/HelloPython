# 第20章 参考答案

## ⭐ 容易

```python
from machine import Pin
import time

led = Pin(13, Pin.OUT)
button = Pin(25, Pin.IN, Pin.PULL_UP)
led_state = False

while True:
    if button.value() == 0:
        time.sleep(0.2)
        if button.value() == 0:
            led_state = not led_state
            led.value(led_state)
            while button.value() == 0:
                time.sleep(0.05)
```

## ⭐⭐ 中等

```python
from machine import Pin
import time

led = Pin(13, Pin.OUT)
button = Pin(25, Pin.IN, Pin.PULL_UP)
last_press = 0

while True:
    if button.value() == 0:
        time.sleep(0.05)
        if button.value() == 0:
            now = time.ticks_ms()
            interval = time.ticks_diff(now, last_press)
            if interval < 400:
                for _ in range(5):
                    led.value(1); time.sleep(0.1)
                    led.value(0); time.sleep(0.1)
            else:
                last_press = now
                time.sleep(0.2)
                if button.value() == 1:
                    led.value(1)
                    time.sleep(1)
                    led.value(0)
            while button.value() == 0:
                time.sleep(0.05)
```

## ⭐⭐⭐ 困难

```python
from machine import Pin, PWM
import time

led = PWM(Pin(13), freq=5000)
button = Pin(25, Pin.IN, Pin.PULL_UP)
brightness = [0, 256, 512, 768, 1023]
level = 0
led.duty(brightness[level])

while True:
    if button.value() == 0:
        time.sleep(0.2)
        if button.value() == 0:
            level = (level + 1) % 5
            led.duty(brightness[level])
            print(f"亮度档位：{level + 1}/5")
            while button.value() == 0:
                time.sleep(0.05)
```
