# 课程报告 Skill

一个用于撰写或大幅修改课程报告的 Codex skill。它帮助 agent 根据课程题目和现有材料组织论证、核对证据、制作图表，并检查最终文档的页面效果。

## 适用范围

文献综述、实验报告、工程设计报告、项目实现报告和数据分析报告。仅需简单润色或论文审稿意见时，不必使用本 skill。

## 轻量结构

```text
course-report/
├── SKILL.md                         # Agent 默认读取的入口
├── agents/openai.yaml               # 技能展示与调用提示
├── references/
│   ├── report-shapes.md             # 按任务选择报告主线
│   ├── evidence-and-visuals.md      # 来源、计算与图表
│   └── document-and-qa.md           # 文档交付与逐页检查
├── assets/
│   ├── course-report-outline.md     # 可选的起草提纲
│   └── evidence-ledger.csv          # 资料较多时追踪关键结论
├── .gitignore                       # 排除课程材料与成品
└── README.md                        # 面向使用者的说明
```

`SKILL.md` 保留共同原则，参考文件只在相关任务中读取。提纲可以按题目改写，不是强制目录。仓库不附加脚本或运行依赖。

## 安装与调用

将本仓库放入 Codex 的 skills 目录，例如 `~/.codex/skills/course-report`。之后可以直接提出课程报告任务，或在提示中明确写 `$course-report`。

建议提供课程题目与评分要求、指定模板和格式、已有文献或数据、实验记录或旧稿，以及预期的交付文件类型。材料不全也可以先开始；skill 会要求区分已核实内容与待补信息。

示例：

> 使用 `$course-report`，根据附件中的课程要求、实验记录和数据，制作一份可提交的实验报告。请保留原始数据，标明计算假设，并检查导出的每一页。

## 设计原则

- 围绕课程问题组织报告，不机械套用固定目录。
- 区分资料事实、理论估算、仿真、实测和解释；不编造数据或文献。
- 图表和公式服务于论证，并标明来源、条件与单位。
- 交付前检查可编辑文件和实际渲染页面。

## 按需使用的材料

| 文件 | 适用情况 |
| --- | --- |
| [报告类型与主线](references/report-shapes.md) | 新写报告、题目没有指定目录，或需要重组旧稿 |
| [证据、计算与图表](references/evidence-and-visuals.md) | 来源较多、包含推导、实验记录或技术图表 |
| [成品与检查](references/document-and-qa.md) | 交付正式排版文件，尤其是 DOCX 或 PDF |
| [课程报告提纲](assets/course-report-outline.md) | 从零起草且没有指定模板 |
| [证据表](assets/evidence-ledger.csv) | 来源较多，需要追踪结论与依据 |

## 发布内容

仓库只包含通用写作方法，不包含具体课程材料、实验数据或私人文档。`.gitignore` 排除了常见工作目录和成品文件，公开发布前仍应核对实际文件清单。核心指令见 [SKILL.md](SKILL.md)。
