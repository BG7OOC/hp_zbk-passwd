# hp_zbk‑passwd
> 惠普增霸卡（HP ZBK）管理员密码解密工具

[![GitHub stars](https://img.shields.io/github/stars/BG7OOC/hp_zbk-passwd.svg)](https://github.com/BG7OOC/hp_zbk-passwd)
[![license](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)

## 简介
**hp_zbk‑passwd** 是针对惠普商用机预装的**增霸卡（ZBK）**的密码解密小工具。
增霸卡提供硬盘保护、系统还原、机房多系统部署功能；管理员密码保存在硬盘特定扇区，遗忘密码将无法进入 `LocalSet.exe` 管理界面修改保护参数、卸载增霸卡组件。

本项目基于对增霸卡密码存储逻辑逆向分析实现，读取硬盘原始扇区数据，解析并还原增霸卡管理员明文密码，帮助运维人员处理机房批量惠普机器密码遗忘场景。

> ⚠️ **仅用于你拥有所有权、合法授权的设备，禁止用于未授权设备。**

## 功能特性
- 直接读取物理硬盘扇区，解析增霸卡存储的加密密码数据
- 输出解密后的管理员明文密码
- 支持常见版本惠普增霸卡固件
- 需要系统管理员权限访问磁盘底层

## 环境要求
- Windows（需要访问物理磁盘，仅支持Windows平台）
- **必须以管理员身份运行**
- 目标机器硬盘上已安装惠普增霸卡，存在增霸卡分区/扇区标记
- 编译器：MinGW‑w64 / MSVC(Visual Studio)，C/C++编译环境

## 编译
### MinGW‑w64
```bash
gcc main.c -o hp_zbk-passwd.exe -luser32
