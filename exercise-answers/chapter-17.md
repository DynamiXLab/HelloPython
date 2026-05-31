# 第17章 参考答案

## ⭐ 容易

烧录完成后在 Shell 中输入验证代码，截图保存。

## ⭐⭐ 中等

在 Shell 依次执行后大致结果：
- 频率：240000000（240MHz）
- 可用内存：约 100~200KB
- 文件列表：`['boot.py']`（可能为空）

## ⭐⭐⭐ 困难

在 Thonny 中创建 `boot.py`：

```python
import esp
esp.osdebug(None)
print("=== DYnamix Lab ESP32 ===")
print("System Ready!")
```

保存到 MicroPython 设备，按 RST 重启观察启动信息。
