# 第16章 MicroPython 固件烧录 & Thonny 连接

> **难度**：⭐⭐  
> **所属教程**：Python 零基础入门到 MicroPython 嵌入式实战  
> **前置章节**：第15章（嵌入式是什么 & 认识 ESP32）

---

### 16.1 什么是 MicroPython

MicroPython 是 Python 3 的精简版，专为微控制器设计。它保留了 Python 的核心语法（包括我们学的面向对象），去掉了一些在单片机上用不到的功能。

### 16.2 烧录固件——给 ESP32 "装系统"

第一次使用 ESP32 需要烧录 MicroPython 固件。好消息是——**Thonny 自带烧录功能**，不需要任何额外工具。

**步骤：**

1. 用 USB 数据线将 ESP32 连上电脑
2. 打开 Thonny → 菜单栏 **运行** → **配置解释器**
3. 在弹出的窗口中选择 **MicroPython (ESP32)**，端口选对应的串口
   - Windows 一般是 `COM3` 或 `COM4`
   - macOS 是 `/dev/cu.usbserial-xxxx` 或 `/dev/ttyUSB0`
4. 点击窗口右下角的 **Install or update MicroPython** 链接
5. 在弹出的烧录窗口中：
   - 确认端口已选对
   - 在 **MicroPython family** 中选择 **ESP32**（或 Generic ESP32）
   - 在 **Variant** 中选择适合你开发板的版本（通常选带 SPIRAM 或不带的标准版）
   - 点击 **Install** 开始烧录
6. 等待进度条跑完，提示安装成功后关闭窗口

> **如果烧录失败**：先按住 ESP32 板上的 **BOOT/IO0 按键**不放，再点击 Install，等烧录开始后再松开 BOOT 键。

### 16.3 验证连接

烧录完成后，Thonny 的 Shell 区域应该出现 `>>>` 提示符。输入：

```python
import machine
print(machine.freq())  # 输出类似：240000000（240MHz）
```

如果能正确输出频率，说明连接成功！

---

### 练习任务

**任务（⭐ 容易）**：按本章步骤完成 MicroPython 固件烧录，在 Thonny 的 Shell 中输入：

```python
import esp
esp.osdebug(None)
print("Hello from ESP32!")
```

拍一张 Thonny 界面截图，确保 Shell 中能看到 ESP32 的回复。

**任务（⭐⭐ 中等）**：在 Thonny Shell 中依次执行以下命令，记录每条的输出：

```python
import machine
print(machine.freq())        # CPU 频率
import gc
gc.collect()                 # 垃圾回收
print(gc.mem_free())         # 可用内存（字节）
import os
print(os.listdir())          # 列出 ESP32 上的文件
```

> 思考：ESP32 的可用内存和你电脑的内存差多少个数量级？

**任务（⭐⭐⭐ 困难）**：在 ESP32 上创建一个文件 `boot.py`，写入以下内容：

```python
import esp
esp.osdebug(None)
print("=== DynamiXLab ESP32 ===")
print("System Ready!")
```

然后重启 ESP32（按 RST 键），观察是否在启动时自动打印了欢迎信息。

> 提示：`boot.py` 是 ESP32 的启动脚本，每次上电都会自动执行。可以用 Thonny 的"文件→另存为→保存到 MicroPython 设备"来保存。

---

💡 **思考延续**

在 MicroPython 出现之前，给单片机写程序几乎是 C 语言工程师的专利。你要考虑内存分配、指针、寄存器操作、编译链配置……对于一个只想"让 LED 闪一下"的硬件爱好者来说，门槛高得离谱。

2013 年，一位名叫 **Damien George** 的英国物理学家决定改变这个局面。他当时正在剑桥大学做物理学博士后的研究，业余时间捣鼓微控制器，深深体会到对初学者来说 C 语言太不友好了。于是他在 Kickstarter 上发起了一个众筹项目——"MicroPython：把 Python 带到微控制器上"。目标筹款 £15,000。

Kickstarter 的众筹页面里有一句很有感染力的话："想象一下，如果 Arduino 可以用 Python 来编程。"这个愿景击中了很多人的心——最终他筹到了将近 £100,000，是目标的 6 倍多。

接下来的一年里，George 几乎是一个人写出了 MicroPython 的核心——包括 Python 3 的编译器、运行时内核、以及针对 ARM 架构硬件的底层接口代码。2014 年，他带着 MicroPython 在 PyCon 上做了首次公开演示：用一块饼干大小的开发板执行了 `for i in range(10): print(i)`，全场掌声雷动。

你说你现在在 ESP32 上敲 `print("Hello from ESP32!")`——这个看似理所当然的操作，它的每一行都经过了层层打磨：从 Guido 的 Python 解释器，到 Damien 的 MicroPython 移植，再到乐鑫科技的 ESP32 硬件。
