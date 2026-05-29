# 第18章 MicroPython 固件烧录 & Thonny 连接

> **难度**：⭐⭐  
> **所属教程**：Python 零基础入门到 MicroPython 嵌入式实战  
> **前置章节**：第17章（嵌入式是什么 & 认识 ESP32）

---

### 18.1 什么是 MicroPython

MicroPython 是 Python 3 的精简版，专为微控制器设计。它保留了 Python 的核心语法（包括我们学的面向对象），去掉了一些在单片机上用不到的功能。

### 18.2 烧录固件——给 ESP32 "装系统"

第一次使用 ESP32 需要烧录 MicroPython 固件：

**步骤：**

1. 下载固件：访问 **https://micropython.org/download/ESP32_GENERIC/** ，下载最新的 `.bin` 文件
2. 下载烧录工具：访问 **https://www.espressif.com/en/support/download/other-tools** ，下载 **Flash Download Tool**（Windows）或用 `esptool`（macOS/Linux）
3. 用 USB 数据线将 ESP32 连上电脑
4. 打开 Thonny → 菜单栏 **运行** → **配置解释器**
5. 选择 **MicroPython (ESP32)**，端口选对应的串口（Windows 一般是 COM3/COM4，macOS 是 /dev/cu.usbserial-xxxx）
6. 点击 **Install or update MicroPython** 链接，按提示选择 `.bin` 文件烧录

> 如果 Thonny 不能自动烧录，可以用命令行：`esptool.py --port COM3 erase_flash` 先擦除，再 `esptool.py --port COM3 --baud 460800 write_flash -z 0x1000 firmware.bin`。

### 18.3 验证连接

烧录完成后，Thonny 的 Shell 区域应该出现 `>>>` 提示符。输入：

```python
import machine
print(machine.freq())  # 输出类似：240000000（240MHz）
```

如果能正确输出频率，说明连接成功！

---

### 练习任务

**任务**：按本章步骤完成 MicroPython 固件烧录，在 Thonny 的 Shell 中输入以下代码然后回车：

```python
import esp
esp.osdebug(None)
print("Hello from ESP32!")
```

拍一张 Thonny 界面截图，确保 Shell 中能看到 ESP32 的回复。
