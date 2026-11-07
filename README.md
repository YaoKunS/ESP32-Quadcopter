<div align="center">

# 🚁 ESP32 开源四轴无人机 · 耀坤项目集

**一块 ¥80 的 PCB，四套飞控固件通吃 —— 教学、仿真、竞技、定高悬停，按需切换**

![MCU](https://img.shields.io/badge/MCU-ESP32%20%7C%20ESP32--S3-purple)
![Cost](https://img.shields.io/badge/%E5%A4%8D%E5%88%BB%E6%88%90%E6%9C%AC-%C2%A580-brightgreen)
![Firmware](https://img.shields.io/badge/Firmware-4%20%E5%A5%97%E9%A3%9E%E6%8E%A7-blue)
![RC](https://img.shields.io/badge/Remote-6%20%E7%A7%8D%E4%BF%A1%E5%8F%B7%E6%BA%90-orange)
![Platform](https://img.shields.io/badge/Platform-%E7%AB%8B%E5%88%9B%E5%BC%80%E6%BA%90%E7%A1%AC%E4%BB%B6%E5%B9%B3%E5%8F%B0-ff6b35)
![License](https://img.shields.io/badge/License-Mixed--GPL3%20%7C%20MIT%20%7C%20CC--BY--NC--SA4.0-lightgrey)

[![立创开源 · 星火计划2026](https://img.shields.io/badge/%E7%AB%8B%E5%88%9B%E5%BC%80%E6%BA%90-%E6%98%9F%E7%81%AB%E8%AE%A1%E5%88%922026-ff6b35)](https://oshwhub.com/lindahe/project_sulkgarf)
[![B站 · 耀坤智联](https://img.shields.io/badge/B%E7%AB%99-%E8%80%80%E5%9D%A4%E6%99%BA%E8%81%94-ff69b4)](https://space.bilibili.com/3707011699050767)

</div>

---

## 这是什么

一套**完整的 ESP32-S3 四轴无人机开源方案**，包含硬件 PCB、固件仓库、技术文档与教程视频。

**核心差异：同一块 PCB 可以刷 4 套成熟的开源飞控固件**，换固件不用改硬件、不用改线。

| | |
|---|---|
| 🛠 **硬件** | [立创开源工程页](https://oshwhub.com/lindahe/project_sulkgarf) —— 原理图 / PCB / BOM / 3D 模型 / 预编译固件下载 |
| 💰 **复刻成本** | 约 **￥80**（含立创 ESP32-S3R8N8 开发板 19.9 元、1S 电池、空心杯马达） |
| 🔥 **飞控固件** | **4 套通吃**：YaoKun_Drone（自研）/ Flix / ESP-FC / 乐鑫 ESP-Drone |
| 🎮 **遥控方式** | **6 种**：ESP-NOW / 手机浏览器 Web / QGC / LiteWing APP / SBUS / ELRS(CRSF) |
| 🧭 **IMU** | MPU6050（I2C）或 MPU6500（SPI），**固件自动识别**，无需改代码 |
| 📏 **拓展接口** | 预留 SPI（PMW3901 光流）、第二组 I2C（VL53L1X 激光）、UART（ELRS）、SBUS |
| 🎥 **视频教程** | [B站 · 耀坤智联](https://space.bilibili.com/3707011699050767) |

---

## 4 套固件怎么选

| 固件 | 协议栈 | 上位机 | 定高 / 悬停 | 适合谁 |
|---|---|---|---|---|
| [**YaoKun_Drone**](https://github.com/YaoKunS/ESP32-Drone) | WebSocket + HTTP | 手机浏览器 | ❌ 未实现 | 嵌入式教学、科创竞赛、算法验证 |
| [**Flix**](https://github.com/YaoKunS/flix) | MAVLink | QGroundControl | ❌ 未实现 | 地面站、Gazebo 仿真、MAVLink 教学 |
| [**ESP-FC**](https://github.com/YaoKunS/esp-fc) | MSP + CLI | Betaflight Configurator | ❌ 未实现 | 穿越机手感、黑匣子分析、空中调参 |
| [**ESP-Drone**](https://github.com/YaoKunS/ESP-Drone) | CRTP | ESP-Drone APP | **✅ 激光定高 + 光流悬停** | 想要**开箱即用的定高悬停** |

> 💡 **刷乐鑫 ESP-Drone 固件 + 接上 PMW3901 光流与 VL53L1X 激光 TOF，即可获得定高与悬停能力**（本板已预留接口，即插即用）。

---

## 四套固件仓库

| 仓库 | 说明 | 协议 |
|---|---|---|
| **[ESP32-Drone](https://github.com/YaoKunS/ESP32-Drone)** | ✨ 耀坤自研飞控。Arduino 模块化 12 文件，三种姿态解算（Madgwick / Mahony / 互补滤波）可热切换，串级 PID，浏览器直连遥控 + 全参数在线可调 | GPL-3.0 |
| **[flix](https://github.com/YaoKunS/flix)** | 🚁 Flix 中文整理版 + 双板硬件适配（耀坤 S3 / 微辣火龙果 2.0）。固件 <2000 行 Arduino，MAVLink + ESP-NOW + Web 三路通信并存 | 上游无 LICENSE，版权保留原作者 |
| **[esp-fc](https://github.com/YaoKunS/esp-fc)** | 🛩️ ESP-FC 中文整理版 + 耀坤 S3 板级适配。Betaflight Configurator 直接调参，多电调协议（Oneshot / Dshot / Brushed） | MIT |
| **[ESP-Drone](https://github.com/YaoKunS/ESP-Drone)** | 🚁 乐鑫官方中文整理版。ESP-IDF v5.0，飞控内核移植自 Crazyflie | GPL-3.0 |

---

## 一分钟了解这个项目的技术含量

**① 引脚方案是三版 PCB 打样才定下来的**

立创 ESP32S3R8N8 用的是**开发板**形态，排针分布在两侧、跨区布线困难，
**无法直接沿用**乐鑫 ESP-Drone / Ardupilot / ESP-FC / Flix 的引脚定义。

第 1 版把电机放在 `GPIO14 / 1 / 42 / 40`，静态评估全绿、实测功能全正常，
**但烧录固件时 GPIO1 对应的电机会转**。第 2 版起改为 `GPIO16 / 6 / 5 / 15`，
避开下载模式与 strapping 相关引脚，实测刷 4 套固件均正常。

**② 关键引脚速查**

| 功能 | 引脚 |
|---|---|
| 电机 1/2/3/4 | `GPIO16 / 6 / 5 / 15` |
| I2C（陀螺仪） | `SDA 9 / SCL 8` |
| SPI（MPU6500） | `MOSI 18 / CLK 38 / MISO 21 / CS 17` |
| 拓展 I2C（VL53L1X 激光） | `SCL 4 / SDA 3` |
| UART（ELRS） | `TX 12 / RX 11` |
| SBUS | `GPIO1` |
| 电池电压 | `GPIO2`（100K+100K 分压，比值 2.0） |

**③ 一块板子的完整 BOM 只要 ￥80**，全部采用淘宝通用成熟件，无定制专用模块。

---

## 📚 技术文档

- **飞控技术说明书（18 章）** —— 每个仓库的 `Docs/` 与 `README` 内，含架构、控制主流程、算法详解、故障排查
- **硬件工程页** —— [oshwhub.com/lindahe/project_sulkgarf](https://oshwhub.com/lindahe/project_sulkgarf)
  含完整 BOM（33 项）、物料清单实物图、焊接组装步骤、6 步复刻 checklist、飞控兼容矩阵
- **视频教程** —— [B站 · 耀坤智联](https://space.bilibili.com/3707011699050767)

---

## 📄 协议

| 对象 | 协议 |
|---|---|
| 硬件（原理图 / PCB / BOM / 文档） | **CC BY-NC-SA 4.0** —— 禁止商业使用，衍生作品须同协议 |
| YaoKun_Drone / ESP-Drone 固件 | GPL-3.0 |
| esp-fc 固件 | MIT |
| flix 固件 | 上游 okalachev/flix 未附带 LICENSE，版权默认保留原作者（本整理版不擅自代为选择协议） |

> ⚠️ 各仓库保留上游原作者署名（GPL 义务）。使用、修改、分发时请注明出处。

---

## 🔗 相关链接

- **立创开源工程页** → [oshwhub.com/lindahe/project_sulkgarf](https://oshwhub.com/lindahe/project_sulkgarf)
- **作者主页** → [oshwhub.com/lindahe](https://oshwhub.com/lindahe)
- **B站** → [space.bilibili.com/3707011699050767](https://space.bilibili.com/3707011699050767)
- **淘宝元件套件** → [shop35432590.taobao.com](https://shop35432590.taobao.com/)

---

<div align="center">

**如果这个项目对你有帮助，请给仓库点一个 ⭐ Star，并到立创开源给工程点个 👍 + 收藏 ——**
**立创的点赞与收藏是星火计划「项目影响力」评奖的硬性指标，也决定了这个项目能否被更多工程师看到。**

*耀坤智联 YaoKunSmart · 硬件与固件全开源 · 星火计划 2026*

</div>
