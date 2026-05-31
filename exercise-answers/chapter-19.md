# 第19章 参考答案

## ⭐ 容易

```python
from machine import Pin, PWM
import time

led = PWM(Pin(13), freq=5000)
while True:
    for duty in range(0, 1024, 8):
        led.duty(duty)
        time.sleep(0.005)
    for duty in range(1023, -1, -8):
        led.duty(duty)
        time.sleep(0.005)
```

## ⭐⭐ 中等

```python
from machine import Pin
import time

led = Pin(13, Pin.OUT)
while True:
    for _ in range(5):
        led.value(1); time.sleep(0.1)
        led.value(0); time.sleep(0.1)
    for _ in range(3):
        led.value(1); time.sleep(0.5)
        led.value(0); time.sleep(0.5)
```

## ⭐⭐⭐ 困难

```python
from machine import Pin, PWM
import time

led1 = PWM(Pin(13), freq=5000)
led2 = PWM(Pin(12), freq=5000)
while True:
    for x in range(0, 1024, 4):
        led1.duty(x); led2.duty(1023 - x)
        time.sleep(0.005)
    for x in range(1023, -1, -4):
        led1.duty(x); led2.duty(1023 - x)
        time.sleep(0.005)
```

## 🎨 RGB 三色混光

```python
from machine import Pin, PWM
import time

r = PWM(Pin(13), freq=5000)
g = PWM(Pin(12), freq=5000)
b = PWM(Pin(14), freq=5000)

while True:
    for x in range(0, 1024, 8):
        r.duty(1023 - x); g.duty(x)
        time.sleep(0.01)
    for x in range(0, 1024, 8):
        g.duty(1023 - x); b.duty(x)
        time.sleep(0.01)
    for x in range(0, 1024, 8):
        b.duty(1023 - x); r.duty(x)
        time.sleep(0.01)
```
