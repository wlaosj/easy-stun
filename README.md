# Easy-Stun

<div align="center">

**🚀 智能 NAT 穿透工具 + Cloudflare 深度集成**

*让你的内网服务像云服务一样被访问*

[![Go](https://img.shields.io/badge/Go-1.20+-00ADD8?style=flat&logo=go)](https://go.dev/)
[![Telegram](https://img.shields.io/badge/Telegram-交流群-0088cc?style=flat&logo=telegram)](https://t.me/+7jcTMePlNVwwZjg1)

</div>

---

> **⚠️ Beta 测试版本**
> 
> 当前版本为 Beta 测试阶段，功能持续优化中。使用过程中如遇到 Bug 或问题属于正常现象，欢迎加入 Telegram 群反馈，也可关注B站反馈，帮助我们改进！

---

## 📺 视频教程

> 🎬 **不知道如何配置？看视频教程更直观！**
> 
> 👉 **[【完整教程】Easy-Stun 安装配置指南 - Bilibili](https://space.bilibili.com/416291500)**
> 
> 涵盖：安装部署、Cloudflare 配置、隧道创建、HTTPS 设置等完整流程

---

## ✨ 核心特色

### 🌟 **为什么选择 Easy-Stun？**

传统的 NAT 穿透工具只能让你访问 `http://ip:随机端口`，而 **Easy-Stun** 通过深度集成 Cloudflare，让你的内网服务可以像云服务一样被访问：

```
传统方案：http://123.456.789.012:18234  ❌ 难记、不安全、端口会变
Easy-Stun：https://your-service.com      ✅ 简洁、安全、永远不变
```

### 🎯 **核心优势**

| 特性 | 传统工具 | Easy-Stun |
|------|---------|-----------|
| 访问方式 | `http://ip:port` | `https://domain.com` |
| 端口变化 | 需要重新告知 | **自动更新规则** |
| SSL 证书 | 手动申请 | **Cloudflare 自动** |
| 用户体验 | 需要记住端口 | **标准 HTTPS 访问** |
| 安全性 | 明文传输 | **强制 HTTPS** |

---

## 🚀 快速开始

### Unraid 用户（推荐）

**安装步骤：**

1. **安装插件**：
   - 打开 Unraid 管理界面 → `插件` → `安装插件`
   - 在 URL 输入框中粘贴：
     ```
     https://raw.githubusercontent.com/wlaosj/easy-stun/refs/heads/main/easy-stun.plg
     ```
   - 点击 `安装` 等待完成

2. **配置 Cloudflare**：输入 API Token 和域名

3. **创建隧道**：添加内网服务（如 Jellyfin、qBittorrent）配置https相关设置

4. **一键启动**：自动完成 NAT 穿透 + DNS + HTTPS

🎉 **完成！** 现在可以通过 `https://jellyfin.yourdomain.com` 访问内网服务了！

### 飞牛 OS (FNasOS)

**手动安装方式：**

1. **下载安装包**：
   - 下载最新版本：[easy-stun-2025.11.05.fpk](https://github.com/wlaosj/easy-stun/blob/main/easy-stun-2025.11.05.fpk)
   - 或直接下载：[直接下载链接](https://raw.githubusercontent.com/wlaosj/easy-stun/main/easy-stun-2025.11.05.fpk)
   
2. **安装应用**：
   - 打开飞牛OS应用中心
   - 点击右上角"手动安装"
   - 选择下载的 `.fpk` 文件
   - 等待安装完成

3. **启动配置**：
   - 在已安装应用中找到 Easy-Stun
   - 点击打开 WebUI
   - 按照 Unraid 相同的步骤配置即可

### 其他平台

🚧 **待适配中...**

---

## 📦 功能特性

### ☁️ Cloudflare 深度集成

- **自动 DNS 管理**：动态更新 A 记录指向公网 IP
- **智能页面规则**：自动重定向到正确的端口
- **零配置 SSL**：利用 Cloudflare 自动获取证书
- **域名池管理**：统一管理多个域名和服务
- **实时同步**：端口变化后 3 秒内完成所有更新

### 🌐 NAT 穿透

- **STUN 协议**（RFC 5389）：获取公网映射地址
- **端口复用技术**：SO_REUSEADDR/SO_REUSEPORT
- **TCP/UDP 支持**：同时支持两种协议
- **多服务器轮询**：提高成功率和稳定性
- **WAN 有效性检测**：自动验证端口可达性
- **智能重连**：网络异常自动重试

### 🔒 HTTPS 反向代理

- **SSL/TLS 终止**：外部 HTTPS → 内网 HTTP
- **证书自动管理**：集成 acme.sh / certmagic / lego
- **自动续签**：证书到期前自动续签
- **SNI 支持**：一个端口服务多个域名

### 🎛️ Web 管理界面

- **可视化管理**：完整的 Web UI
- **多隧道支持**：统一管理多个内网服务
- **实时监控**：SSE 推送隧道状态
- **配置导入导出**：JSON 格式配置
- **日志查看**：实时日志和历史记录

---

## 🎬 使用场景

### 场景 1：家庭媒体服务器
```
内网：Jellyfin 运行在 192.168.1.100:8096
外网：访问 https://jellyfin.yourdomain.com
效果：和 Netflix 一样的访问体验！
```

### 场景 2：远程下载管理
```
内网：qBittorrent 运行在 192.168.1.100:8080
外网：访问 https://bt.yourdomain.com
效果：在任何地方管理下载任务
```

### 场景 3：家庭云存储
```
内网：Nextcloud 运行在 192.168.1.100:8000
外网：访问 https://cloud.yourdomain.com
效果：自己的 Google Drive
```

---

## 📋 系统要求

- **操作系统**：Linux / Windows / macOS / Unraid
- **网络环境**：具有公网 IP 的网络（NAT 环境）
- **Cloudflare**：托管的域名（免费版即可）
- **Go 版本**：1.20+ （仅编译时需要）

---

## 🤝 支持与交流

- **Telegram 交流群**：[点击加入](https://t.me/+7jcTMePlNVwwZjg1)
- **Bilibili 主页**：[@隔壁小王](https://space.bilibili.com/416291500)
- **问题反馈**：欢迎在 Telegram 群内讨论
- **使用帮助**：可自行观看B站视频
---

## 📄 版权声明

本项目为闭源软件，版权归作者所有。依赖标准库与公开 STUN 服务，仅供个人学习和非商业使用。未经授权，禁止用于商业目的或二次分发。

---

<div align="center">

**💬 遇到问题？加入 Telegram 群一起交流！**

Made with ❤️ by bigv

</div>
