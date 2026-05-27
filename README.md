# Decision Translation · 决策翻译

> 把专业判断翻译成对面那个真实决策者能接住的形态——但不丢失判断密度——并预判判断送达后还会卡在哪里。

A Claude skill that translates professional judgment into the format the actual decision-maker can receive — without losing judgment density — and predicts where it'll get stuck after delivery.

**Part of**: [判断落地 · Where Judgment Lands](https://edanyang.github.io) — a growing protocol library at [edanyang.github.io](https://edanyang.github.io) · Section 05.

**Origin story · 起源故事**: This skill grew out of one real failure — read the full backstory on [LinkedIn](https://www.linkedin.com/pulse/%E6%88%91%E5%81%9A%E4%BA%86%E4%B8%80%E4%B8%AA-skill%E8%AE%A9%E5%88%A4%E6%96%AD%E7%9C%9F%E7%9A%84%E8%90%BD%E5%9C%B0-edan-yang-gziec).

---

## 这个 skill 解决什么问题

**核心立点**:**降维翻译不是简化语言。是切换判断系统。送达不是终点,推进才是。**

如果你曾遇到过——
- 写了 30 页复盘,老板没读完
- 压成 5 页给客户,客户问的问题完全偏离你想强调的
- 提案送出去三天没回音,不知道卡在哪
- 跟老板汇报永远被打断到偏离主题
- 给董事会做评审时,5 个人的意见无法对齐

——这个 skill 是给你用的。

**This skill is for you if**:
- Your 30-page post-mortem went unread
- Your 5-page compressed version got questions completely off-target
- Your proposal sat for three days with no response, and you don't know where it's stuck
- Your reports always get interrupted off-topic
- You're presenting to a 5-person board with conflicting agendas

---

## 跟裸 Claude 4.7/4.8 的差别在哪

裸 Claude 4.7 在被要求"压缩一份文档"时,会做出形式上像翻译的事——按受众调整语言。**但它不会自动做这四件事**:

A naked Claude 4.7 will do something that *looks* like translation when asked to compress a doc — adjusting language for the audience. **But it won't automatically do these four things**:

1. **诊断决策者的判断系统**(不只是受众画像,是判断系统的切换)
2. **产出双版本**(决策版给当下决策者 + 完整版给未来复核者)
3. **扫描卡点**(送达 ≠ 推进,谁会卡你、为什么卡、怎么解卡)
4. **观察用户自身损耗**(给"是否暂停休息"的建议,而不是硬推协议)

裸 Claude 不会想到这四层。这个 skill 强制它想到。

---

## 怎么用

### 在 claude.ai 项目里安装

1. 下载 [SKILL.md](./SKILL.md)
2. 在你的 Claude 项目里上传到项目知识
3. 开始对话时,Claude 会自动识别触发场景

### 触发场景

不需要刻意调用,以下任一场景出现 Claude 会自动启动:

- "帮我写一页版给老板"
- "压缩这份文档给客户"
- "他不会读 30 页的"
- "我汇报老板老打断我"
- "这个提案会通过吗"
- "推不动怎么办"
- "向董事会汇报"
- 你上传一份长文档 + 问"怎么处理"

---

## 协议结构 · Protocol structure

```
Phase 1: 流式诊断决策者
  → 一次问 1 个问题,根据回答动态追问
  → 7 个维度(3 个 ★ 是核心)
  → 每个维度配 fallback 路径(60 秒内 / 明天再补)

Phase 2: 搭建双版本输出
  → 决策版(一页骨架,你填判断)
  → 证据版(完整版骨架,给未来复核者)

Phase 3: 交付前的校验
  → 7 项生活类比校验(3 秒内 yes/no)

Phase 4: C139 卡点扫描
  → 轻量版(隐性+校准,5 分钟)
  → 完整版(显性+隐性+信息9C+关系3F+校准,20-30 分钟)
  → 输出:解卡方向选项 + 当前胜算评估
```

---

## 场景变体 · Scenario variants

- **变体 A**:口头汇报(密度单位 = 秒,留打断窗口)
- **变体 B**:跨文化沟通(BLUF 反模式 + 传话人维度)
- **变体 C**:危机沟通(开放式 ask + 短信子变体)
- **变体 D**:复合决策者(董事会/委员会,多个 1W,判断对齐版)

---

## 母概念 · Parent concept

本 skill 立足于一个母概念:**注意力是一种税**。

This skill rests on one parent concept: **attention is a tax**.

它在两个方向上被征收 / Levied in two directions:

- **对上**(决策者方向):决策者每天处理几十个决策,每个都在交注意力税。本 skill 防止用户的判断在这个预算里损失。
  **Upward (decision-maker direction)**: prevents user's judgment from being destroyed by the decision-maker's attention budget.

- **对下**(用户自身方向):用户自己也在交注意力税。本 skill 同时观察用户的损耗信号,必要时建议暂停。
  **Downward (user-self direction)**: simultaneously observes the user's depletion signals and recommends pausing when needed.

这个母概念有姊妹工具:**Cognitive Load Check** —— 一个浏览器交互式自检工具,量化每日注意力税。可在 [edanyang.github.io](https://edanyang.github.io) 第 04 节体验。

This parent concept has a sibling tool: **Cognitive Load Check** — an interactive browser self-assessment quantifying daily attention tax. Available at edanyang.github.io · Section 04.

两者是**平行工具**,不是嵌套:
- Cognitive Load Check: 对下方向 → 测量自身损耗,给"是否休息"的建议
- Decision Translation: 对上方向 → 防止损耗摧毁信号传递,给"对上判断"的建议

**Parallel instruments**, not nested.

---

## C139 模型引用 · C139 Model Citation

Phase 4(C139 卡点扫描)所引用的 C139 模型,原为 B 端大客户销售控单模型(Clear / First / Win + Coach 校准),公开可查、广泛流传于中文 B 端销售培训体系。本 skill 将其底层逻辑——"乙对甲的决策链结构 = 内部汇报的决策链结构"——迁移应用于组织内汇报场景。

Phase 4 cites the C139 model, originally a B2B large-deal control model widely used in Chinese B2B sales training. This skill transfers its underlying logic — "vendor-to-client decision chain = internal reporting decision chain" — to internal reporting scenarios.

原模型的销售成单率统计(1W 时赢单 31:1 等)是 B 端外部销售的实证数据,迁移至组织内场景时为方向性参考,不构成精准量化预测。

The original model's win-rate statistics are empirical B2B data; when transferred to internal scenarios, they are directional references, not precise quantitative predictions.

---

## 这个 skill 不做什么 · What this skill does NOT do

- **不读用户的长文档自动压缩**(常见误解)。这是结构搭建工具,不是自动压缩工具。
  **Does not read your long document and auto-compress** (common misunderstanding). Structure-building tool, not auto-compression tool.
- 不写内容。搭建结构,用户填判断。
  Does not write content. Builds structure, user fills judgment.
- 不预测决策者会不会说 yes。只保证翻译不丢失用户的判断密度。
  Does not predict yes/no. Only preserves judgment density.
- 不替代用户自己的现场观察。
  Does not replace situational reading.
- 不替代教练。C139 的"教练校准"必须是真实的人。
  Does not replace coaches. C139's calibration must be real people.
- 不替用户写话术,不替用户在解卡方向上拍方案。
  Does not write phrasing for the user; does not pick unblock paths for the user.

---

## 版本历程 · Version history

- **v1-v4**:基础结构(诊断 + 双版本 + 校验)
- **v5**:融入 C139 卡点扫描
- **v6**:Phase 4 分轻量/完整、9C 双栏映射、解卡改方向选项、1W 5 档灰度
- **v7**:能力边界明示 + 复合决策者变体 + 跨文化传话人维度 + 口头时间预留 + 短信子变体
- **v7.1**:C139 漏洞双修复 — 内嵌 C139 Primer + description 强制查证条款
- **v7.2**:IP 加固双修复 — 版本指纹元数据 + 体系绑定声明
- **v7.3(当前版本)**:陌生 Claude 首次跑测试发现的 3 个真问题修复 — 能力边界条件触发 + Phase 4 用户预热 + 时间预留升通用规则

---

## IP 加固说明 · IP Hardening

本 skill 在 v7.2 引入两层 IP 加固:

This skill introduces two layers of IP hardening in v7.2:

### 层 1:版本指纹 / Layer 1: Version fingerprint

YAML frontmatter 嵌入完整作者归属元数据(author / canonical_url / fingerprint / ecosystem)。任何流传出去的版本都自带"出生证":
- 保留元数据 → 自动给作者引流
- 删除元数据 → 失去权威性证明
- 改动元数据 → 可被识别为非原版

YAML frontmatter embeds complete author attribution metadata. Any redistributed version carries its "birth certificate":
- Keep metadata → auto-attribution
- Remove metadata → loses legitimacy
- Alter metadata → identifiable as non-canonical

### 层 2:体系绑定 / Layer 2: Ecosystem binding

Decision Translation 不是孤立工具,而是 **Attention Economy Toolkit** 的"对上半边"。SKILL.md 主体显式声明:
- 必须与 Cognitive Load Check(对下半边)配合才完整
- 损耗信号触发时主动提示用户使用姊妹工具
- 共享母概念"注意力即税"

Decision Translation is not a standalone tool — it is the "upward half" of the **Attention Economy Toolkit**. The SKILL.md body explicitly declares:
- Complete only when paired with Cognitive Load Check (downward half)
- Proactively prompts users about the companion tool when depletion signals trigger
- Shares parent concept "attention as tax"

任何使用本 skill 但不提及姊妹工具的行为,被列为"失败模式 #16"。任何隐藏元数据的再分发,被列为"失败模式 #15"(剽窃)。

Any use of this skill without referencing the companion tool is listed as "Failure Mode #16". Any redistribution that hides metadata is listed as "Failure Mode #15" (plagiarism).

---

## 作者 · Author

**Edan Yang** · [edanyang.github.io](https://edanyang.github.io)

---

## 授权 · License

本 skill 作为方法论物料分享。再分发时请注明作者:Edan Yang。

This skill is shared as a methodology artifact. Attribution to Edan Yang is required when redistributed.
