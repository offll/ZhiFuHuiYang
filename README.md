# 👁️ 智辅慧眼 (Smart Assistive Eyes) 
**基于微信小程序与端云协同的视障群体视觉语音辅助系统**

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Spring Boot](https://img.shields.io/badge/Spring%20Boot-2.7+-brightgreen.svg)]()
[![YOLOv9](https://img.shields.io/badge/YOLO-v9--s-orange.svg)]()
[![WeChat MiniProgram](https://img.shields.io/badge/WeChat-MiniProgram-07C160.svg)]()

## 📖 项目简介
本项目是一款专为视障群体设计的智能辅助出行系统。系统秉持“Bring Your Own Device (BYOD)”理念，无需购买昂贵的激光雷达盲杖或导盲犬，视障人士仅需使用普通智能手机即可实现环境感知与安全出行。

系统采用端云协同的三层架构：
*   **前端**：基于微信小程序，提供极简的双模态盲操交互（全屏长按说话、双击急停）。
*   **后端**：基于 Spring Boot，负责并发处理、空间测距解算以及防冲突调度。
*   **AI 边缘端**：基于 YOLOv9-s 构建的本地微服务，提供低延迟、高精度的特定障碍物识别。

## ✨ 核心特性
*   **🎯 极简盲操交互**：彻底抛弃传统 GUI 细小按钮，采用全屏长按唤醒 ASR（语音识别）、全屏双击触发紧急熔断，结合多级震动马达反馈，实现无视觉障碍的流畅操作。
*   **📐 单目物理测距**：不依赖深度摄像头，基于小孔成像透视原理，独创单目测距算法。在 2 米核心危险区内的物理测距误差控制在 10% 以内。
*   **🚦 “智能分诊台”防冲突调度**：独创基于优先级的状态机调度引擎，彻底解决“步行导航语音”与“紧急避障警报”并发重叠的痛点。当 1.8 米极危区出现障碍物时，系统强制抢占音频通道，优先触发震动与停步警报。
*   **⚡ 快闪抽帧节流**：前端根据导航与守护状态动态调整抽帧频率（3s/5s），全链路平均响应时延仅为 345ms，兼顾了高实时性与移动端续航。

## 🏗️ 系统架构与目录结构

```text
Smart-Assistive-Eyes/
├── frontend-miniprogram/      # 微信小程序前端源码
├── backend-springboot/        # Spring Boot 后端核心业务与空间决策引擎
├── vision-microservice/       # 基于 YOLOv9-s 与 Flask 的视觉推理微服务
├── dataset/                   # 特定导盲场景数据集说明及预处理脚本 (COCO to YOLO)
├── docs/                      # 系统架构图、数据库 E-R 图及答辩相关材料
└── README.md                  # 项目说明文档
