# Journal Review · 期刊审稿技能

A configurable, evidence-grounded journal peer-review skill for Codex.

一套可配置的期刊审稿工作流：阅读稿件与图表、核对证据，生成兼顾整体判断与具体细节的英文审稿意见，支持大修、拒稿及使用者指定的其他结论。

## 特点

- 同时覆盖综评、宏观问题与具体细节，避免只有笼统评价或格式纠错。
- 所有意见按稿件出现顺序排列，少量长重点搭配简短意见，不固定总条数。
- 根据证据区分真实缺陷、描述不足与尚待核实的问题，不编造事实、定位或引文。
- 可核查使用者提供的候选文献；相关性优先，不因论文属于审稿者而要求引用。
- 默认中文交互、英文正式意见，可按要求调整语言、语气与格式。
- 请求 Word 时，按 Times New Roman、10.5 pt、单倍行距等默认样式交付。

## 安装

在 Codex 中使用内置技能安装器，并提供本仓库地址：

```text
$skill-installer 请从 https://github.com/Franlivia/journal-review 安装技能。技能位于仓库根目录（路径 .），安装名称为 journal-review。
```

也可以下载本仓库，将包含 `SKILL.md` 的整个 `journal-review` 文件夹放到当前版本 Codex 支持的技能目录，例如个人目录 `~/.agents/skills/journal-review/`，或项目目录 `.agents/skills/journal-review/`。技能未出现时可重启 Codex；不同版本的目录约定请参阅 [OpenAI Docs](https://learn.chatgpt.com/docs/build-skills)。

## 使用

上传或指定稿件后，调用：

```text
请使用 $journal-review 审阅这篇稿件。
```

默认先确认期望的审稿结论，再询问是否需要建议补引己方论文。你可以回答“请依据证据判断”，也可以明确指定 Major Revision、Reject、Minor Revision 或 Accept。预设结论不构成学术缺陷的证据。

需要核查候选论文时，默认请提供两篇论文的 PDF、题名与 DOI 或可访问链接；数量可调整。不需要时回答“不需要”即可。候选论文只有在相关性与信息均已核实后，才会进入正式意见。

也可一次说明全部要求：

```text
请使用 $journal-review 审阅附件。请依据证据判断结论，不需要补引己方论文，正式意见用英文，并交付 Word 文件。
```

## 输出与自定义

默认输出为一行 `Recommendation ...`、一个综评段落，以及按稿件顺序排列的连续编号意见。通常有2–3条展开充分的重点，其余问题按实际影响决定长短。事实不足时，不为凑数量或支持预设结论而制造批评。

可直接在当次请求中覆盖默认交互顺序、候选文献数量、意见语言、语气和 Word 排版。只有你明确授权持久化偏好后，助手才应更新本地技能文件。

## 运行条件与适用范围

这是供 Codex 读取的 Agent Skill，不是独立运行的软件，不附带模型或 API 服务。基础包只有 Markdown 和 YAML，无需要单独安装的 Python 或 Node 依赖，也不要求本技能专用的 API 密钥。

读取 PDF 图表、Word 内容及生成 `.docx` 需要当前环境具备相应文档工具；本仓库不附带文档转换器或字体。外部文献与 DOI 核验需要网络和可访问的原始来源；材料缺失时应说明审阅范围。

技能用于辅助人工审稿，不自动提交期刊系统或对外发送意见。处理保密稿件前，请遵守适用的期刊及机构关于 AI 工具的规定。

## 文件结构

```text
journal-review/
├── SKILL.md
├── agents/openai.yaml
├── references/review-style.md
├── README.md
└── LICENSE
```

`SKILL.md` 是技能入口，`references/review-style.md` 提供详细写法和 Word 样式，`agents/openai.yaml` 提供展示信息。本仓库只包含技能规则与说明。

## 反馈与贡献

欢迎通过 Issues 提交问题或通过 Pull Requests 改进工作流。反馈请使用虚构或已获公开授权的示例，避免附带保密稿件和审稿记录。

## 许可证

[MIT License](LICENSE)。Copyright (c) 2026 Franlivia.
