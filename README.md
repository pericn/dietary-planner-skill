# AI 膳食策划专家

> 面向中国家庭的老年人健康饮食规划助手 | Designed for 妈妈 👵

[![OpenClaw Skill](https://img.shields.io/badge/Platform-OpenClaw-blue)](https://github.com/openclaw)
[![Platform](https://img.shields.io/badge/Platform-Coze%20Bot-brightgreen)](https://www.coze.cn)

**让每一餐都充满爱与营养** 🍜

---

## 📖 项目简介

AI 膳食策划专家是一款基于大语言模型的智能膳食规划技能，专为中国家庭设计，尤其适合帮助不太熟悉复杂操作的**老年人（妈妈）** 轻松管理每日饮食。

核心能力：输入现有食材库存 → AI 自动生成每日食谱 → 输出营养分析 → 记录每日饮食情况。

---

## ✨ 核心功能

### 🥗 智能菜谱规划
根据现有食材库存，AI 自动生成符合家庭口味、时令节气、营养均衡的一周/每日菜谱推荐。

### 📊 营养分析
基于[中国居民膳食指南 2022](参考文件-中国居民膳食指南2022.md)和[卫健委成人肥胖食养指南 2024](参考文件-卫健委成人肥胖食养指南2024.md)等权威标准，自动计算每餐营养素摄入（热量、蛋白质、脂肪、碳水化合物、钠等）。

### 🏪 食材库存管理
录入家中现有食材，AI 帮你规划如何消耗、搭配，避免食材浪费。输入格式支持自然语言描述。

### 📝 每日饮食记录
按日期自动记录当日饮食内容，支持导入到 Excel 进行长期趋势分析。模板：[每日追踪模板](tracking/daily-YYYY-MM-DD.txt)

### 🖼️ 图片输出
生成精美的菜谱展示页面（HTML 模板：[meal-plan.html](templates/meal-plan.html)），支持截图保存或直接分享。

---

## 🛠️ 安装说明

### 方式一：导入为 OpenClaw Skill

1. 将本仓库克隆到本地：
   ```bash
   git clone https://github.com/laura-agent/dietary-planner-skill.git
   ```
2. 将 `SKILL.md` 内容配置到 OpenClaw 的 skill 管理中
3. 依赖文件结构：
   ```
   dietary-planner/
   ├── SKILL.md                    # 核心技能定义
   ├── data/inventory.txt         # 食材库存数据
   ├── tracking/daily-YYYY-MM-DD.txt  # 每日饮食记录
   ├── templates/meal-plan.html   # 菜谱展示模板
   ├── assets/capture.js          # 截图脚本
   ├── learnings/                 # 行为模式记录
   └── 参考文件/                   # 权威参考标准
   ```

### 方式二：导入为 Coze Bot 技能

1. 将 `SKILL.md` 完整内容复制到 Coze 平台的"技能配置"中
2. 上传 `data/inventory.txt` 作为知识库补充
3. 配置 Coze 工作流，将 `templates/meal-plan.html` 作为输出模板

---

## 📋 参考标准

本项目参考以下权威标准设计营养建议：

- [中国居民膳食指南 2022](参考文件-中国居民膳食指南2022.md) — 中国营养学会
- [卫健委成人肥胖食养指南 2024](参考文件-卫健委成人肥胖食养指南2024.md) — 国家卫生健康委员会
- [美国膳食指南 DGA 2025-2030](参考文件-美国膳食指南DGA2025-2030.md) — USDA/HHS

---

## 👥 目标用户

- **主要用户**：不太擅长使用 App 的中老年用户（妈妈）
- **家庭场景**：需要科学规划全家饮食的子女
- **特点**：自然语言交互、界面简洁、步骤少、容错率高

---

## 🤝 贡献指南

欢迎提交 Issue 和 Pull Request！

---

## 📄 License

MIT License