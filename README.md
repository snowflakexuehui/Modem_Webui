# Modem Manager WebUI

一个基于 Ant Design Pro 的 5G 模组管理 Web 界面，提供网络状态监控、配置管理、短信收发等功能。

![Dashboard](https://raw.githubusercontent.com/snowflakexuehui/Modem_Webui/master/images/1.png)

## 📋 目录

- [功能特性](#功能特性)
- [技术栈](#技术栈)
- [快速开始](#快速开始)
- [项目结构](#项目结构)
- [功能展示](#功能展示)
- [开发说明](#开发说明)
- [许可证](#许可证)

## ✨ 功能特性

### 🎯 仪表盘 (Dashboard)
- **信号质量监控**: 实时显示 RSRP（参考信号接收功率）、SINR（信号与干扰加噪声比）、RSRQ（参考信号接收质量）等信号参数，支持信号强度等级评估（4级）
- **实时速率监控**: 实时监控上行/下行网络速率，支持 Kbps 单位显示
- **流量统计**: 显示累计上传/下载流量数据，支持 MB 单位显示
- **温度监控**: 监控模组各功能模块温度状态，支持温度异常告警
- **网络状态**: 显示运营商（中国移动/中国联通/中国电信）、网络类型（NR5G）、注册状态（已注册、归属网络）等信息
- **速率趋势图**: 面积图实时展示上行/下行速率变化趋势，支持时间轴显示
- **流量分布图**: 饼图展示上传/下载流量占比
- **信号趋势图**: 堆叠图展示 RSRP、SINR、RSRQ 等信号参数的变化趋势
- **自动刷新**: 支持定时自动刷新数据，可自定义刷新间隔

![Network Status](https://raw.githubusercontent.com/snowflakexuehui/Modem_Webui/master/images/2.png)

### 🌐 网络管理 (Network)

#### 网络状态 (Network Status)
- **信号板**: 显示信号质量百分比、RSRP（dBm）、SINR（dB）、RSRQ（dB）等关键指标
- **网络参数**: 显示 PCI（物理小区标识）、频率、MCC-MNC（移动国家码-移动网络码）、LAC（位置区码）、Cell ID（小区ID）
- **载波聚合信息**: 显示载波数量、总带宽（下行/上行）、主载波详细信息（PCI、频率、带宽、MIMO 层数、调制方式如 QPSK、64QAM）
- **基本信息**: 显示 SIM 卡号、IMEI（国际移动设备识别码）、ICCID（集成电路卡标识符）、模块电压
- **网络速度信息**: 支持实时速度监控开关，显示网络速度相关信息
- **流量统计**: 显示上次连接的连接时长、上传流量、下载流量

#### 网络配置 (Network Config)
- **小区锁定配置**: 支持强制 UE 注册到特定小区（单小区锁定），可设置配置、查询当前配置、关闭小区锁定、查询参数范围
- **频段锁定配置**: 
  - **4G 频段**: 支持 B1, B2, B3, B4, B5, B7, B8, B12, B13, B14, B17, B18, B19, B20, B25, B26, B28, B29, B30, B32, B34, B38, B39, B40, B41, B42, B43, B46, B48, B66, B71 等频段选择
  - **5G 频段**: 支持 N1, N2, N3, N5, N7, N8, N20, N25, N28, N30, N38, N40, N41, N48, N66, N71, N77, N78, N79 等频段选择
  - 支持恢复出厂设置和设置配置
- **邻区扫描**: 扫描邻近小区，显示小区信息（锁定状态、PCI、频率、RSRP、RSRQ），支持质量评估（Excellent/Good/Normal/Poor），支持锁定特定小区

![Network Config](https://raw.githubusercontent.com/snowflakexuehui/Modem_Webui/master/images/3.png)

#### 拨号设置 (Dial Settings)
- **自动拨号**: 
  - 支持自动拨号开关
  - 协议类型: 支持 IPv4/IPv6 双栈
  - APN 配置: 可设置 APN（如 CMNET）、用户名、密码
  - 认证类型: 支持无认证等多种认证方式
  - 显示拨号状态（已开启/已关闭）
- **拨号模式设置**: 
  - 拨号方式: 支持 USB 和 PCIE 模式
  - USB 端口模式: 支持 RNDIS 拨号模式-41 等模式
- **PDP 上下文管理**: 
  - 显示 PDP 上下文列表（CID、协议类型、APN、状态）
  - 支持编辑、删除、激活/去激活 PDP 上下文
  - 支持刷新状态

![Dial Settings](https://raw.githubusercontent.com/snowflakexuehui/Modem_Webui/master/images/4.png)

### 📱 短信中心 (SMS)

#### 短信管理 (SMS Management)
- **存储状态**: 显示短信存储使用情况（已用/总容量，如 0/50）
- **短信收发**: 支持发送新短信，显示发送按钮和刷新按钮
- **短信列表**: 显示短信列表，支持查看、删除、标记短信
- **空状态提示**: 当没有短信时，显示友好的空状态提示

![SMS Management](https://raw.githubusercontent.com/snowflakexuehui/Modem_Webui/master/images/5.png)

#### 短信设置 (SMS Settings)
- **短信功能开关**: 支持启用/禁用短信功能
- **短信中心设置**: 
  - 可配置短信中心号码（如 8613800290500）
  - 需先启用短信功能才能保存设置
- **存储设置**: 
  - 存储位置: 支持 SIM 卡或模块存储
  - 读取存储: 显示已用容量和百分比（如 25/100，25%）
  - 写入存储: 显示已用容量和百分比
  - 接收存储: 显示已用容量和百分比
  - 支持保存存储设置

![SMS Settings](https://raw.githubusercontent.com/snowflakexuehui/Modem_Webui/master/images/6.png)

### ⚙️ 系统设置 (System - Modem Settings)

#### AT 服务器配置
- **服务模式**: 显示当前服务模式（Serial AT）
- **服务器地址**: 可配置 AT 服务器 IP 地址和端口（如 192.168.88.1:8765）
- **上传/下载交换**: 支持交换上传/下载功能
- **配置锁定**: 支持通过 config.json 锁定配置

#### SIM 卡配置
- **SIM 卡切换**: 支持外部 SIM 卡和内部 SIM 卡切换（切换需要设备重启）
- **热插拔**: 支持外部 SIM 卡热插拔功能（设备运行时插入/移除）
- **PIN 码管理**: 支持启用/禁用 PIN 码验证，显示 PIN 码状态
- **飞行模式**: 支持启用/禁用飞行模式（启用后将断开所有网络）

#### 系统信息
- **制造商**: 显示制造商信息（如 Fibocom Wireless Inc.）
- **设备型号**: 显示设备型号（如 FM350-GL）
- **固件版本**: 显示固件版本（如 81600.0000.00.29.23.24-F31）
- **IMEI**: 显示国际移动设备识别码

#### 设备控制
- **以太网速度**: 可配置以太网驱动和速度（更改需要设备重启）
- **性能模式**: 支持启用/禁用性能模式
- **恢复出厂设置**: 支持恢复出厂设置功能
- **重启设备**: 支持重启设备功能

#### 网络系统配置
- **RAT 优先级**: 支持设置无线接入技术优先级（如 5G -> 4G -> 3G）
- **服务类型**: 支持选择服务类型（如语音和数据）

#### 漫游设置
- **漫游模式**: 支持设置漫游模式（如仅限本地网络）

![Modem Settings](https://raw.githubusercontent.com/snowflakexuehui/Modem_Webui/master/images/7.png)

### 🔧 调试工具 (AT Debug)
- **AT 命令终端**: 提供 AT 命令输入和输出显示区域
- **命令发送**: 支持输入 AT 命令并发送，支持回车键快速发送
- **命令历史**: 显示命令执行历史和结果
- **常用命令**: 提供常用 AT 命令快捷按钮：
  - 查询信号强度
  - 查询 IMEI
  - 查询版本
  - 查询 SIM 卡状态
  - 查询网络注册
  - 查询网络时间
  - 查询小区信息
- **命令保存**: 支持保存常用命令
- **清除功能**: 支持清除输入或日志
- **多模组支持**: 支持 Quectel、Fibocom 等多种模组

![AT Debug Terminal](https://raw.githubusercontent.com/snowflakexuehui/Modem_Webui/master/images/8.png)

### 📊 图表功能
- **信号趋势图**: 堆叠图/折线图实时显示 RSRP、SINR、RSRQ 等信号参数的变化趋势，支持时间轴显示
- **网速趋势图**: 面积图实时展示上行/下行速率变化，支持 Kbps 单位，显示实时速率峰值和变化曲线
- **流量分布图**: 饼图直观展示上传/下载流量占比，显示总流量和各项流量数据
- **温度柱状图**: 柱状图显示各模块温度状态，支持温度范围显示（0-50°C），显示温度状态（正常/异常）

> 注：图表功能集成在仪表盘页面中，详见上方仪表盘功能介绍。

## 🛠 技术栈

- **前端框架**: React 19 + TypeScript
- **UI 组件库**: Ant Design 5.x
- **图表库**: Ant Design Charts
- **构建工具**: UmiJS 4.x
- **包管理器**: pnpm
- **通信协议**: WebSocket

## 🚀 快速开始

### 环境要求

- Node.js >= 20.0.0
- pnpm >= 8.0.0

### 安装依赖

```bash
pnpm install
```

### 启动开发服务器

```bash
pnpm start
```

访问 http://localhost:8000

### 构建生产版本

```bash
pnpm build
```

构建产物将输出到 `dist` 目录。

### 配置说明

在 `public/config.json` 中配置 WebSocket 服务器地址：

```json
{
  "status": "true",
  "at": {
    "host": "192.168.88.1",
    "port": 8765
  }
}
```

## 📁 项目结构

```
modem_manager_webui/
├── src/
│   ├── pages/
│   │   ├── dashboard/          # 仪表盘页面
│   │   ├── network/           # 网络相关页面
│   │   │   ├── status.tsx     # 网络状态
│   │   │   ├── config.tsx     # 网络配置
│   │   │   └── dial.tsx       # 拨号管理
│   │   ├── system/            # 系统设置页面
│   │   │   └── ModemSetting.tsx
│   │   ├── sms/               # 短信中心页面
│   │   │   ├── sms.tsx        # 短信管理
│   │   │   └── setting.tsx    # 短信设置
│   │   └── atdebug/           # 调试工具页面
│   │       └── atdebug.tsx
│   ├── utils/
│   │   ├── atModule.ts        # AT 命令模块
│   │   ├── atQueue.ts         # AT 命令队列
│   │   └── formatUtils.ts     # 格式化工具
│   ├── services/
│   │   └── websocket.ts       # WebSocket 服务
│   └── contexts/
│       └── WebSocketConfigContext.tsx  # WebSocket 配置上下文
├── config/
│   ├── config.ts              # UmiJS 配置
│   └── routes.ts              # 路由配置
├── public/
│   ├── config.json            # 配置文件
│   └── icons/                 # 图标资源
└── project/
    └── images/                # 项目截图
```

## 🎨 功能展示

### 实时数据监控
- 通过 WebSocket 连接实时获取模组数据
- 支持多种 5G 模组型号（如 Fibocom FM350-GL、Quectel 等）
- 自动识别命令族，适配不同模组
- 支持自动刷新和手动刷新数据
- 实时显示信号质量、网络速率、流量统计、温度等关键指标

### 美观的图表展示
- 使用 Ant Design Charts 提供专业的图表展示
- 响应式设计，支持移动端和桌面端
- 实时数据更新，动态图表效果
- 支持多种图表类型：面积图、饼图、柱状图、堆叠图
- 图表支持时间轴显示，可查看历史趋势

### 智能状态管理
- 网络连接状态实时监控（已注册、归属网络等）
- 信号质量等级自动评估（Excellent/Good/Normal/Poor）
- 温度异常自动告警
- 支持载波聚合信息显示（载波数量、带宽、MIMO 层数、调制方式）
- 支持 PDP 上下文管理（激活/去激活、编辑、删除）

### 高级网络配置
- 支持小区锁定配置，可强制注册到特定小区
- 支持 4G/5G 频段锁定，可选择支持的频段
- 支持邻区扫描，显示邻近小区的详细信息
- 支持自动拨号配置（APN、认证类型等）
- 支持拨号模式设置（USB/PCIE 模式）

### 完善的设备管理
- 支持 SIM 卡切换（外部/内部 SIM 卡）
- 支持 SIM 卡热插拔
- 支持 PIN 码管理
- 支持飞行模式
- 支持设备重启和恢复出厂设置
- 支持性能模式配置
- 支持以太网速度配置

## 💻 开发说明

### 添加新的图表
1. 在 `src/pages/dashboard/dashboard.tsx` 中添加新的数据获取函数
2. 配置图表参数和样式
3. 在页面布局中添加图表组件

### 扩展 AT 命令支持
1. 在 `src/utils/atModule.ts` 中添加新的命令族配置
2. 实现命令解析函数
3. 在相应页面中使用新的命令

### 添加新的页面
1. 在 `src/pages` 目录下创建新的页面组件
2. 在 `config/routes.ts` 中添加路由配置
3. 在 `src/locales` 中添加国际化文本

## 📝 许可证

MIT License

## 🔗 相关链接

- [项目地址](https://github.com/snowflakexuehui/Modem_Webui)
- [Ant Design Pro](https://pro.ant.design/)
- [UmiJS](https://umijs.org/)

## 🤝 贡献

欢迎提交 Issue 和 Pull Request！

---

**注意**: 本项目需要配合后端 WebSocket 服务器使用，请确保后端服务正常运行。
