<div align="center">

# 🛡️ LXD Central Control Panel

**轻量级 · 高安全 · 集中化**
<br>
专为 LXD 打造的多节点管理控制台，基于 FastAPI + Vue 构建。

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue?style=flat-square&logo=python)](https://www.python.org/)
[![FastAPI](https://img.shields.io/badge/Backend-FastAPI-009688?style=flat-square&logo=fastapi)](https://fastapi.tiangolo.com/)
[![Vue](https://img.shields.io/badge/Frontend-Vue.js-4FC08D?style=flat-square&logo=vue.js)](https://vuejs.org/)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg?style=flat-square)](LICENSE)

[功能特性](#-功能特性) • [一键安装](#-一键安装) • [添加节点](#-添加节点-agent) • [截图预览](#-截图预览)

</div>

---

## 📖 项目简介

**LXD Panel** 是一个现代化的中央控制台，旨在解决多台 LXD 宿主机的管理难题。它不依赖复杂的数据库或重量级组件，仅需一条命令即可部署。

与传统的 SSH 管理不同，本系统采用 **mTLS (双向 TLS 认证)** 技术与宿主机 Agent 通信，确保只有经过授权的面板才能控制您的服务器，极大提升了安全性。

## 🛡️ 核心架构

```mermaid
graph LR
    User["管理员/用户"] -->|HTTPS| Panel["LXD Panel (本控制台)"]
    Panel -->|mTLS 加密通道| Node1["宿主机 A (Agent)"]
    Panel -->|mTLS 加密通道| Node2["宿主机 B (Agent)"]
    Panel -->|mTLS 加密通道| Node3["宿主机 C (Agent)"]
    
    subgraph "安全层 (Security)"
    Node1 --- Cert["客户端证书校验"]
    end
