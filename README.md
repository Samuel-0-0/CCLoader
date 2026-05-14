# 📁 XZG 多功能工具 - CC Loader 模块

本项目来自 [XZG 多功能工具仓库的 **cc_loader** 分支](https://github.com/xyzroe/XZG-MT/tree/cc_loader)！

本项目使用 Arduino/ESP8266/ESP32 开发板作为闪存编程器来烧录 TI CC2530 芯片的固件。所有二进制文件均通过 GitHub 工作流自动生成。

## 🗂 目录结构

- `README.md` - 本文件
- `task.json` - 构建/任务配置
- `Arduino/` - Arduino 实现
  - `CCLoader` - Arduino 草图文件夹
    - `CCLoader.ino` - 适用于 Arduino/ESP8266/ESP32 的 Arduino 草图
- `bins/` - 预编译固件二进制文件
  - `manifest.json` - 固件清单文件

## 🛠 如何使用

此分支中的所有固件文件主要用于搭配 [XZG 多功能工具](http://mt.xyzroe.cc/) 使用，但也可用于其他兼容软件。

现成的适用于不同 ESP 开发板的固件二进制文件可在 `bins` 目录中找到。请查看 `bins/manifest.json` 了解可用的配置。

## 📋 支持的硬件

- **Arduino**：Uno、Nano、Pro Mini 及兼容开发板
- **ESP8266**：D1 Mini、NodeMCU 及兼容开发板
- **ESP32**：ESP32 Dev、ESP32-C3、ESP32-C6、ESP32-S3

> [!IMPORTANT]
> 仅支持带有 **CH340** 或 **CP2102** USB-TTL 转换器的开发板。使用其他转换器或原生 USB 连接的开发板可能无法正常工作。

## 🔌 引脚配置

### CC2530 引脚

编程器通过 3 个调试接口引脚与 CC2530 芯片通信：

| 功能     | CC2530 引脚 | 描述             |
| -------- | ----------- | ---------------- |
| **DD**   | P2.1        | 调试数据（双向） |
| **DC**   | P2.2        | 调试时钟         |
| **RESET** | RST         | 复位线           |
| **VCC**  | VCC         | 电源（3.3V）     |
| **GND**  | GND         | 地               |

### ESP 引脚

ESP 开发板的 GPIO 引脚分配因构建版本而异，定义在 `bins/manifest.json` 中：

- **DD、DC、RESET** - 连接到 CC2530 调试接口
- **LED** - 状态指示灯

> [!IMPORTANT]
> 如果要自定义引脚，Fork 本项目，编辑 task.json 指定引脚，然后通过 Action 自动编译，编译完成后的固件在 bins 文件夹。

## 💡 致谢

- 感谢 RedBearLab 为 [CC Loader](https://github.com/RedBearLab/CCLoader) 所做的出色工作！
- 感谢 Timo Kokkonen 为 [CC Loader 分支](https://github.com/tjko/CCLoader) 添加了芯片 ID 检测和闪存转储功能！

## 🤝 贡献

欢迎贡献！如有任何更新、修复或改进，欢迎提交拉取请求或创建问题。

---

<div align="center"> 由 <a href="https://xyzroe.cc/">xyzroe</a> 用 &#x2764;&#xFE0F; 创建 © 2025</div>
