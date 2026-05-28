# 🍽️ dietary-planner-skill

**AI 膳食规划系统** — 针对不同健康目标（减脂、慢病管理）生成精准营养方案，含食谱设计、营养分析、库存管理、可视化输出。

专为不同健康目标（减脂、慢病管理等）设计，支持 OpenClaw / Coze 等 AI Agent 平台。

---

## ✨ 核心功能

| 功能 | 说明 |
|------|------|
| 🏋️ **减脂方案** | 基于卫健委《成人肥胖食养指南》，能量控制 1200-1800 千卡/日 |
| 🩺 **慢病管理** | 高血压/糖尿病/痛风等专项膳食方案，营养指标精确跟踪 |
| 📦 **库存管理** | 记录冰箱食材，自动生成采购清单，追踪每日消耗 |
| ✅ **执行追踪** | 记录每餐执行状态（已执行/待执行/已跳过），积累行为频率 |
| 🖼️ **可视化输出** | 调用 orca-insta 生成杂志风格长图（1080px 宽） |
| 🔄 **自进化机制** | 学习用户反馈，棘轮固化，同类问题第三次出现时有预防机制 |

---

## 📁 项目结构

```
dietary-planner/
├── SKILL.md                              # 主技能文件（含完整说明）
├── orca-insta/                           # 图片生成 submodule
│   ├── SKILL.md                         # orca-insta 视觉卡片生成
│   ├── SPEC/                            # 设计规格文档
│   ├── templates/magazine-long.html     # 杂志长图模板
│   └── capture.js                       # Playwright 截图引擎
├── data/
│   └── inventory.txt                     # 库存 + 人员档案（空模板）
├── tracking/
│   └── daily-YYYY-MM-DD.txt              # 每日追踪日志（空模板）
├── learnings/
│   └── behavior-frequency.md             # 行为频率记录（空模板）
└── 参考文件/
    ├── 参考文件-中国居民膳食指南2022.md
    ├── 参考文件-卫健委成人肥胖食养指南2024.md
    └── 参考文件-美国膳食指南DGA2025-2030.md
```

---

## 🚀 安装

### 安装依赖

本技能通过 **orca-insta** submodule 生成可视化图片。安装时自动包含：

```bash
# 克隆主仓库（含 submodule）
git clone --recurse-submodules https://github.com/pericn/dietary-planner-skill.git

# 进入目录
cd dietary-planner-skill

# 初始化 submodules（首次克隆后如需手动拉取）
git submodule update --init --recursive

# 安装 Playwright 截图依赖
cd orca-insta && npm install && npx playwright install chromium
```

### 使用方式一：作为 OpenClaw Skill 使用

将整个目录放入 workspace skills 目录：

```bash
cp -r dietary-planner ~/.openclaw/workspace-laura/skills/
```

### 使用方式二：作为 Coze 智能体 Skill 使用

1. 将 `SKILL.md` 内容导入到 Coze 的 Skill 配置中
2. 配置知识库：关联 `参考文件/` 下的三个参考文档
3. 配置变量/知识库：`data/inventory.txt` 作为人员档案知识库
4. 启用文件写入支持（或使用对话快照模式）

---

## 🔄 工作流程

```
用户请求制定食谱
    ↓
dietary-planner 生成 Markdown 方案
    ↓
调用 orca-insta（magzine-long 模式）
    ↓
生成 PNG 长图（1080px 宽）
    ↓
发送图片给用户（文字版 + 图片版）
```

---

## 🎯 支持的目标场景

- **减脂**：能量控制、宏量营养素比例优化、食物交换份
- **高血压管理**：限钠（<5克/日）、富钾食材、高钙推荐
- **糖尿病管理**：低GI碳水、碳水均匀分布、血糖稳定技巧
- **痛风管理**：限嘌呤、多饮水、酒精控制
- **骨质疏松管理**：高钙食材、维生素D补充、优质蛋白

- **家庭用户**：为家人定制健康饮食
- **AI 开发者**：集成到 AI Agent / 聊天机器人中提供膳食规划能力

---

## 🏷️ 触发关键词

仅以下关键词触发本技能：

- 「制定【某人/某餐】食谱」— 如「制定晚餐食谱」「制定三人食谱」
- 「吃什么」— 如「今晚吃什么」「中午吃什么」
- 「做什么菜」— 如「晚上做什么菜」「做点什么好」
- 「采购/冰箱」— 如「冰箱里还有啥」「采购清单」

---

## 📋 输出内容

生成的方案包含以下五个核心板块：

1. **标题区** — 日期、人员、健康主题标签
2. **人员档案卡** — 禁忌（×）/ 医嘱 / 软性偏好 / 饮食目标
3. **膳食目标** — 热量/蛋白质/脂肪/碳水/钠/钙/纤维/钾，关键指标高亮
4. **菜谱详情** — 主料/辅料/调味/步骤/长者提示/替换方案/营养分析
5. **健康提示** — 根据档案自动生成的专项健康建议（3-5条）

---

## 📚 参考来源

- [中国居民膳食指南（2022）](http://dg.cnsoc.org/) — 中国营养学会
- [成人肥胖食养指南（2024年版）](http://www.nhc.gov.cn/) — 国家卫生健康委办公厅
- [Dietary Guidelines for Americans 2025-2030](https://www.dietaryguidelines.gov/) — USDA & HHS

---

## ⚠️ 免责声明

本技能生成的食谱方案仅供参考，不能替代专业医疗建议。
如有特殊疾病（糖尿病、高血压、痛风、肾功能不全等），请在使用前咨询医生或营养师。

---

## 📄 License

MIT License — 可自由使用、修改、分发。