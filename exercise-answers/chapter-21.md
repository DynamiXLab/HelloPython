# 第21章 参考答案

## ⭐ 容易

接好 AHT20 + OLED（共享 I2C 总线），运行完整代码。

```python
from machine import Pin, SoftI2C
import ahtx0
import ssd1306
import time

i2c = SoftI2C(scl=Pin(22), sda=Pin(21))
sensor = ahtx0.AHT20(i2c)
oled = ssd1306.SSD1306_I2C(128, 64, i2c)

while True:
    try:
        temp = sensor.temperature
        hum = sensor.relative_humidity
        oled.fill(0)
        oled.text("Temp & Hum", 0, 0)
        oled.text(f"Temp: {temp:.1f} C", 0, 25)
        oled.text(f"Hum : {hum:.1f} %", 0, 45)
        oled.text("Press Ctrl+C", 0, 55)
        oled.show()
        time.sleep(2)
    except OSError:
        oled.fill(0)
        oled.text("Sensor Error!", 0, 25)
        oled.show()
        time.sleep(2)
```

## ⭐⭐ 中等

```python
from machine import Pin, SoftI2C
import ahtx0
import ssd1306
import time

i2c = SoftI2C(scl=Pin(22), sda=Pin(21))
sensor = ahtx0.AHT20(i2c)
led = Pin(13, Pin.OUT)
oled = ssd1306.SSD1306_I2C(128, 64, i2c)

while True:
    try:
        temp = sensor.temperature
        hum = sensor.relative_humidity
        oled.fill(0)
        oled.text(f"Temp: {temp:.1f} C", 0, 0)
        oled.text(f"Hum: {hum:.1f} %", 0, 20)
        if temp > 30:
            oled.text("Hot!", 0, 40)
        elif temp < 15:
            oled.text("Cold!", 0, 40)
        else:
            oled.text("Comfortable", 0, 40)
        if hum > 70:
            oled.text("Wet!", 0, 50)
        elif hum < 30:
            oled.text("Dry!", 0, 50)
        oled.show()
        if temp > 32:
            led.value(1); time.sleep(0.1)
            led.value(0); time.sleep(0.1)
        else:
            led.value(0)
            time.sleep(2)
    except OSError:
        oled.fill(0)
        oled.text("Sensor Error!", 0, 25)
        oled.show()
        time.sleep(2)
```

## ⭐⭐⭐ 困难（毕业项目）

```python
from machine import Pin, SoftI2C, PWM
import ahtx0
import ssd1306
import time

i2c = SoftI2C(scl=Pin(22), sda=Pin(21))
sensor = ahtx0.AHT20(i2c)
led = PWM(Pin(13), freq=5000); led.duty(0)
button = Pin(25, Pin.IN, Pin.PULL_UP)
oled = ssd1306.SSD1306_I2C(128, 64, i2c)

display_mode = 0
while True:
    try:
        temp = sensor.temperature
        hum = sensor.relative_humidity
        if button.value() == 0:
            time.sleep(0.2)
            if button.value() == 0:
                display_mode = 1 - display_mode
                while button.value() == 0:
                    time.sleep(0.05)
        oled.fill(0)
        if display_mode == 0:
            oled.text(f"Temp: {temp:.1f} C", 0, 10)
            oled.text(f"Hum : {hum:.1f} %", 0, 30)
        else:
            oled.text(f"{temp:.1f}C", 20, 20)
        if temp > 32:
            for _ in range(3):
                led.duty(1023); time.sleep(0.1)
                led.duty(0); time.sleep(0.1)
        elif 25 <= temp <= 32:
            for d in range(0, 1024, 16):
                led.duty(d); time.sleep(0.002)
            for d in range(1023, -1, -16):
                led.duty(d); time.sleep(0.002)
        else:
            led.duty(0)
            time.sleep(2)
        oled.show()
    except OSError:
        oled.fill(0)
        oled.text("Sensor Error!", 0, 25)
        oled.show()
        time.sleep(1)
```
