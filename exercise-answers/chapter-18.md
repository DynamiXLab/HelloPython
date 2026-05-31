# 第18章 参考答案

## ⭐ 容易

```python
from machine import Pin
import time

led = Pin(13, Pin.OUT)
for i in range(10):
    led.value(1)
    time.sleep(0.3)
    led.value(0)
    time.sleep(0.3)
led.value(1)
time.sleep(3)
led.value(0)
```

## ⭐⭐ 中等

```python
from machine import Pin
import time

leds = [Pin(13, Pin.OUT), Pin(12, Pin.OUT), Pin(14, Pin.OUT)]
while True:
    for led in leds:
        led.value(1)
        time.sleep(0.2)
        led.value(0)
```

## ⭐⭐⭐ 困难

```python
from machine import Pin
import time

leds = [Pin(13, Pin.OUT), Pin(12, Pin.OUT), Pin(14, Pin.OUT)]
while True:
    for led in leds:
        led.value(1)
    for i in range(3):
        time.sleep(1)
        leds[-i-1].value(0)
    time.sleep(1)
    for _ in range(3):
        for led in leds:
            led.value(1)
        time.sleep(0.1)
        for led in leds:
            led.value(0)
        time.sleep(0.1)
    for led in leds:
        led.value(1)
```
