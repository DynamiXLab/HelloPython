# 第22章 综合项目：温湿度计 + OLED 显示

> **难度**：⭐⭐⭐⭐  
> **所属教程**：Python 零基础入门到 MicroPython 嵌入式实战  
> **前置章节**：第19~21章（LED、按键、PWM）  
> **本章定位**：🏆 终章毕业项目

---

### 22.1 DHT11 温湿度传感器

DHT11 是入门级温湿度传感器，精度一般但胜在便宜好用。

**硬件连接：**

```
DHT11       ESP32
VCC   ────  3.3V
DATA  ────  GPIO4
GND   ────  GND
```

在 Thonny → 工具 → 管理插件 中搜索安装 `dht` 库（通常内置，不需要额外安装）。

### 22.2 OLED 显示屏（SSD1306）

0.96 寸 OLED 屏幕，分辨率 128×64 像素，使用 I2C 通信。

**硬件连接：**

```
OLED        ESP32
VCC   ────  3.3V
GND   ────  GND
SCL   ────  GPIO22 (I2C 时钟)
SDA   ────  GPIO21 (I2C 数据)
```

在 Thonny → 工具 → 管理插件 中搜索安装 `ssd1306`。

### 22.3 完整代码

```python
from machine import Pin, SoftI2C
import dht
import ssd1306
import time

# ====== DHT11 初始化 ======
dht_sensor = dht.DHT11(Pin(4))

# ====== OLED 初始化 ======
i2c = SoftI2C(scl=Pin(22), sda=Pin(21))
oled = ssd1306.SSD1306_I2C(128, 64, i2c)

while True:
    try:
        # 读取温湿度
        dht_sensor.measure()
        temp = dht_sensor.temperature()   # 温度（℃）
        hum = dht_sensor.humidity()       # 湿度（%）

        # 清屏
        oled.fill(0)

        # 显示标题
        oled.text("Temp & Hum", 0, 0)

        # 显示温度
        oled.text(f"Temp: {temp} C", 0, 25)

        # 显示湿度
        oled.text(f"Hum : {hum} %", 0, 45)

        # 下方面一条提示线
        oled.text("Press Ctrl+C", 0, 55)

        # 刷新屏幕
        oled.show()

        time.sleep(2)

    except OSError:
        oled.fill(0)
        oled.text("Sensor Error!", 0, 25)
        oled.show()
        time.sleep(2)
```

### 22.4 运行效果

程序运行后，OLED 屏幕上会实时显示当前的温度和湿度，每 2 秒更新一次。对着 DHT11 哈一口气，你会看到湿度数值上升——物理世界的数据就这样被你的代码"读"了出来！

---

### 练习任务

**任务（简单部分）**：按上图连接好电路，运行上面的完整代码，确保屏幕上正确显示温湿度数据。

**任务（挑战部分 —— 毕业项目）**：在完整项目基础上增加以下功能：

1. **温湿度范围判断**：温度 > 30℃ 时显示 "Hot!"，< 15℃ 时显示 "Cold!"；湿度 > 70% 时显示 "Wet"，< 30% 时显示 "Dry"
2. **按键切换界面**：按一下按键，在"温度大字显示"和"温湿度同时显示"两个界面间切换
3. **LED 告警**：温度超过 32℃ 时，LED 闪烁警告（把第19章的 LED 接上）

> 这个综合任务考察了 **GPIO 输出（LED）、GPIO 输入（按键）、PWM（可选）、I2C 通信（OLED）、传感器读取（DHT11）、条件判断、循环、变量状态切换**……几乎涵盖了我们 22 章所学的全部内容。完成它就是真正的 ESP32 MicroPython 入门毕业了！🎓
