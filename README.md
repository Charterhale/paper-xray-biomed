# Paper X-Ray Biomed · 医学与生命科学论文 X 光机

把一篇医学、基础医学或生命科学论文讲到读者能解释实验为何这样设计、图表证明了什么，以及结论在哪一步需要停下来。

基于 [Wang-auspicious/paper-xray](https://github.com/Wang-auspicious/paper-xray) 改写，保留深入讲解、具体推演、审慎审读以及 Markdown/HTML 两种交付方式。医学版重写研究设计、测量原理、机制链条、统计单位与外推边界，不只是把“计算机科学家”换成“医学研究者”。

## 能做什么

- 串起“科学问题 → 实验与对照 → 直接结果 → 作者解释 → 尚未排除的解释”。
- 按关键 Figure/面板讲解坐标、单位、分母、误差、统计和来源。
- 分别处理临床试验、观察性研究、动物/细胞机制、组学/图谱、诊断/预测、结构/方法和综述。
- 分清患者、供者、动物、组织样本、切片、细胞及技术重复。
- 解释干预、必要性、充分性、救援、直接作用与人体外推各需要什么证据。
- 用小例子讲清方法和统计；教学构造与论文真实数据明确区分。
- 默认自然中文，可按要求用英语；深度按用户目标调整。

## 安装

需要支持 `SKILL.md` 的 Agent。将**整个仓库目录**复制到对应 skills 目录，保留 `references/`、`agents/`、`LICENSE` 和 `UPSTREAM.md`。

Codex 默认位置：`~/.codex/skills/paper-xray-biomed/`；如配置了 `CODEX_HOME`，使用其 `skills/` 子目录。Claude Code 可放在 `~/.claude/skills/paper-xray-biomed/`。目标已存在时先查看，不覆盖已有版本。

也可以在目标不存在时克隆完整仓库：

```bash
# Codex 默认位置
git clone https://github.com/Charterhale/paper-xray-biomed.git ~/.codex/skills/paper-xray-biomed

# Claude Code：按实际使用的 Agent 选择一条
git clone https://github.com/Charterhale/paper-xray-biomed.git ~/.claude/skills/paper-xray-biomed
```

安装后在新的对话中调用。实际自动发现与界面行为由宿主 Agent 决定；仓库发布不等于已经安装到你的本机。

## 用法

Codex 可用 `$paper-xray-biomed`，支持斜杠命令的 Agent 可用 `/paper-xray-biomed`。也可以直接说明要用这个 skill。

```text
用 $paper-xray-biomed 精读这篇 PDF。用中文逐图讲解，尤其解释实验为什么这样设计。

用 $paper-xray-biomed 只讲这篇论文的 Figure 3，区分直接结果和作者的机制解释。

用 $paper-xray-biomed 分析 PMID: <实际 PMID>，先核对正文与补充材料是否可得。

用 $paper-xray-biomed 讲清这项临床试验的主要结局、绝对效应、失访与适用人群。

用 $paper-xray-biomed 做 HTML 精读文档，加入供者与细胞层级图，以及可点击的实验证据链。
```

支持 PDF 路径、PMID、DOI、链接、标题、粘贴正文或指定图。全文不可得时提供有边界的摘要级/局部解读，不编造缺失图表和方法。

## 与原版相比

| 原版重点 | 医学版调整 |
|---|---|
| 数学、网络架构与机器学习基线 | 测量原理、研究设计、干预与对照、统计和证据链 |
| 推演作者思考过程 | 解释有证据的研究逻辑，教学推演不冒充研究历史 |
| 公开代码优先 | 正文、补充材料、方案、数据与代码按作用核对，冲突并列记录 |
| 方法/理论/系统等类型 | 临床、流行病学、机制、组学、诊断预测、结构方法与综述 |
| 参数、张量和消融 | 独立 N、剂量/时间、读出、救援/互作和替代解释 |
| 固定架构图与视觉尺寸 | 保留科学坐标、图例、单位和不确定性，交互按疑问选择 |
| 自动偏好校准 | 不自动写长期偏好或修改 skill；按用户明确要求更新 |

## 文件

```text
paper-xray-biomed/
├── SKILL.md
├── agents/openai.yaml
├── references/
│   ├── study-designs.md
│   ├── evidence-and-statistics.md
│   ├── worked-examples.md
│   └── html-delivery.md
├── README.md
├── UPSTREAM.md
└── LICENSE
```

`SKILL.md` 是入口，其余参考只在相关任务中读取。无需额外安装分析包；PDF、检索、文件输出及网页预览使用宿主可用工具。论文代码不会因为存在而自动运行，skill 不自动对外上传或发布结果。

## 验证与范围

初版为 `0.1.0`。本次检查包括 skill 格式、内部引用、界面元数据、15 个针对性场景的指令审查和教学风险计算。场景审查用于检查规则覆盖，不等于模型执行评测。

尚未以真实论文完成独立行为测试，未生成或运行 HTML 成品，也未验证 Claude Code 的运行行为。实际解读质量依赖论文材料与宿主能力；不将候选机制、动物结果或计算预测升级成人体已确证结论。

## 来源与许可

MIT。保留原作者版权声明；依据的具体版本和改写说明见 [UPSTREAM.md](UPSTREAM.md)。研究设计指南路由参考 [EQUATOR 指南库](https://www.equator-network.org/library/)；使用具体规范时应核对当前版本。
