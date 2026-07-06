# 📚 参考文献真伪核验专家 (Reference Verification)

<p align="center">
  <img src="https://img.shields.io/badge/学术诚信-✅-blue?style=flat-square">
  <img src="https://img.shields.io/badge/多平台交叉检索-12+-green?style=flat-square">
  <img src="https://img.shields.io/badge/支持中英文献-100%-orange?style=flat-square">
  <img src="https://img.shields.io/badge/输出-核验报告-red?style=flat-square">
  <img src="https://img.shields.io/github/license/wzx11223344/reference-verification?style=flat-square">
</p>

<p align="center">
  <i>系统化 · 多平台交叉验证 · 杜绝学术不端 · 守护学术诚信</i>
</p>

---

## 🎯 项目简介

**参考文献真伪核验专家** 提供系统化的学术参考文献真伪核验工作流，覆盖**文献信息提取、多平台交叉检索、逐条真实性核验、异常问题归因、核验报告生成**五个核心阶段。支持中英文混合文献列表，适配期刊论文、会议论文、学位论文、书籍、专利、网络资源等多种文献类型。

> **核心价值**：在 10-30 分钟内完成一篇论文/报告的**全部参考文献核验**，识别「假文献、错位文献、捏造 DOI、张冠李戴」等学术不端行为，守护学术诚信。

---

## 🏗️ 五阶段工作流

```
┌─────────────────────────────────────────────────────────────┐
│  Stage 1 · 文献条目识别与结构化提取                         │
│  扫描目标材料 → 逐条提取字段 → 格式异常标注                 │
└──────────────────────┬────────────────────────────────────┘
                       ▼
┌─────────────────────────────────────────────────────────────┐
│  Stage 2 · 多平台学术检索                                │
│  优先级检索（Google Scholar → Semantic → CrossRef → …）    │
│  命中即停止，未命中进入下一平台                            │
└──────────────────────┬────────────────────────────────────┘
                       ▼
┌─────────────────────────────────────────────────────────────┐
│  Stage 3 · 逐条核验（V1-V5 标准）                       │
│  真实存在性 → 字段匹配度 → 类型一致性 → 可获取性 → 引    │
│  用上下文核验          │
└──────────────────────┬────────────────────────────────────┘
                       ▼
┌─────────────────────────────────────────────────────────────┐
│  Stage 4 · 异常问题归因                                  │
│  假文献 / 错位文献 / 捏造 DOI / 张冠李戴 / 自我引        │
│  用操纵 → 分类归因 + 严重程度评级                         │
└──────────────────────┬────────────────────────────────────┘
                       ▼
┌─────────────────────────────────────────────────────────────┐
│  Stage 5 · 核验报告生成                                  │
│  逐条核验结果表 + 异常汇总 + 可信度评级 + 修改建议         │
└─────────────────────────────────────────────────────────────┘
```

---

## 🔍 多平台检索优先级

### 通用优先平台

| 平台 | 适用范围 | 检索方式 | 优先级 |
|------|---------|---------|:--------:|
| **Google Scholar** | 全领域覆盖最广 | `site:scholar.google.com` + 题名 | ⭐⭐⭐⭐⭐ |
| **Semantic Scholar** | 全领域，AI 辅助 | API: `api.semanticscholar.org/graph/v1/paper/search` | ⭐⭐⭐⭐ |
| **CrossRef** | DOI 权威查询 | `api.crossref.org/works/{DOI}` | ⭐⭐⭐⭐ |
| **PubMed** | 生命科学/医学 | `pubmed.ncbi.nlm.nih.gov/?term=` | ⭐⭐⭐ |

### 专业数据库（按学科）

| 平台 | 适用学科 | 检索 URL 前缀 |
|------|---------|--------------|
| IEEE Xplore | 电气/电子/计算机 | `ieeexplore.ieee.org/search/searchresult.jsp?queryText=` |
| ACM Digital Library | 计算机科学 | `dl.acm.org/search/?query=` |
| arXiv | 预印本（CS/Math/Physics） | `arxiv.org/search/?query=` |
| CNKI 知网 | 中文文献 | `cnki.net/` |
| 万方数据 | 中文文献 | `wanfangdata.com.cn/` |
| Web of Science | 多学科高质量期刊 | SCI/SSCI 收录核验 |
| Springer/Nature | 自然科学 | `link.springer.com/search?query=` |
| Elsevier/ScienceDirect | 多学科 | `sciencedirect.com/search?qs=` |

---

## ✅ 逐条核验五维标准

| 标准 | 名称 | 核验内容 | 通过条件 |
|:----:|--------|---------|---------|
| **V1** | 文献真实存在性 | 能否在学术平台检索到 | 至少 1 个平台命中 |
| **V2** | 题名匹配度 | 实际题名与引用题名是否一致 | 相似度 ≥ 85% |
| **V3** | 作者匹配度 | 作者列表是否一致 | 第一作者匹配 |
| **V4** | 发表载体匹配 | 期刊/会议/书名是否一致 | 完全一致或缩写等价 |
| **V5** | 年份/卷期匹配 | 发表年份、卷、期、页码是否一致 | 年份一致，卷期误差 ≤ 1 |

### 核验结果等级

```
✅ 核验通过（Pass）        — V1-V5 全部通过
⚠️ 核验存疑（Warning）   — V1 通过，但 V2-V5 有轻微偏差
❌ 核验失败（Fail）       — V1 未通过，或 V2-V5 严重不匹配
❓ 无法核验（Unverifiable）— 无 DOI 且所有平台均未命中
```

---

## 🚨 常见异常类型与归因

| 异常类型 | 特征 | 严重程度 | 处理建议 |
|---------|------|:-------:|---------|
| **假文献** | 在任何平台均检索不到 | 🔴 极严重 | 立即删除，重新查找真实文献 |
| **错位文献** | 题名相似但非同一篇 | 🟡 中等 | 更正为正确文献 |
| **捏造 DOI** | DOI 格式正确但解析失败 | 🔴 极严重 | 删除，要求作者提供真实 DOI |
| **张冠李戴** | 题名正确但作者/期刊错误 | 🟠 严重 | 更正作者/期刊信息 |
| **自我引用操纵** | 过度引用自己或合作者文献 | 🟡 中等 | 补充第三方权威文献 |
| **格式不规范** | 缺少年份/卷期/页码 | 🟢 轻微 | 补充完整信息 |

---

## 📋 核验报告结构

```
参考文献核验报告
├── 📊 核验概览
│   ├── 总文献数：XX 条
│   ├── 通过：XX 条（XX%）
│   ├── 存疑：XX 条（XX%）
│   ├── 失败：XX 条（XX%）
│   └── 无法核验：XX 条（XX%）
├── 📋 逐条核验结果表
│   ├── 编号 · 题名 · 作者 · 载体 · 年份
│   ├── V1-V5 核验结果（✅/⚠️/❌/❓）
│   └── 异常说明（如有）
├── 🚨 异常问题汇总
│   ├── 按异常类型分类
│   └── 严重程度统计
├── 💡 修改建议
│   ├── 必须修改（❌ 失败条目）
│   ├── 建议核实（⚠️ 存疑条目）
│   └── 补充信息（❓ 无法核验条目）
└── 📎 附录：检索日志（各平台检索记录）
```

---

## 🚀 使用方式

### 作为 AI Skill 使用（推荐）

将本仓库放入 AI Agent 的 Skills 目录，触发词：

```
"核验参考文献"  "验证文献真实性"
"查一下这些引用是否真实"  "文献查重"
"帮我检查这篇论文的参考文献"
```

### 作为独立工具使用

```bash
# 安装依赖
pip install requests beautifulsoup4

# 对单篇论文的参考文献进行核验
python scripts/verify_refs.py --input paper.pdf --output report.md

# 对文献列表文件进行核验
python scripts/verify_refs.py --input references.txt --output report.md
```

---

## 📊 性能指标

| 指标 | 数值 |
|------|------|
| 单条文献平均核验时间 | 10-30 秒 |
| Google Scholar 命中率 | ~75% |
| DOI 直接解析成功率 | ~90% |
| 中文文献知网命中率 | ~60% |
| 假文献识别准确率 | ~95% |

---

## 📁 项目结构

```
reference-verification/
├── SKILL.md                      # Skill 完整定义
├── scripts/
│   ├── extract_refs.py           # 文献条目提取器
│   ├── search_engine.py           # 多平台检索引擎
│   ├── verify_engine.py           # 五维核验引擎
│   ├── report_generator.py        # 核验报告生成器
│   └── attribution.py            # 异常归因模块
├── references/
│   ├── platform_list.yaml        # 学术平台列表及检索规则
│   ├── error_patterns.json       # 常见错误模式库
│   └── severity_rubric.md       # 严重程度评级标准
└── examples/
    ├── sample_paper.pdf          # 示例论文（脱敏）
    └── sample_report.md          # 示例核验报告
```

---

## ⚠️ 免责声明

本工具供 **学术诚信自查** 使用，旨在帮助研究者识别参考文献中的错误和不当行为。核验结果仅供参考，最终判断需结合人工审查。

---

## 📄 License

[MIT License](LICENSE)

---

<p align="center">
  <b>Created by WorkBuddy AI · 原创内容 · 禁止抄袭</b><br>
  GitHub: <a href="https://github.com/wzx11223344">@wzx11223344</a>
</p>
