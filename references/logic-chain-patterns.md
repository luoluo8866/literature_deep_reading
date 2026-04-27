# Logic Chain Patterns

Use this reference when converting a biomedical mechanism paper into a clear presentation story.

## Core Pattern

```text
【表型 1：起始表型】
观察到某种细胞/分子/空间/疾病表型
        ↓
【提出问题】
什么机制导致这个表型？
        ↓
【猜机制】
扰动某类分子或过程后，表型改变
说明该分子类别/过程可能参与
        ↓
【找到候选】
通过筛选、测序、组学、成像或数据库分析找到候选因子
        ↓
【验证候选】
验证候选因子的表达、定位、富集、动态变化或相关性
        ↓
【验证机制第一端】
证明候选因子连接表型中的第一个对象
例如 DNA / RNA / chromatin / promoter / enhancer / active gene
        ↓
【验证机制第二端】
证明候选因子连接表型中的第二个对象
例如 protein complex / nuclear body / receptor / enzyme / pathway
        ↓
【形成模型】
候选因子把两端连接起来，解释原始表型
        ↓
【因果验证】
KD/KO/抑制剂/降解/突变 rescue/full-length rescue/结构域替换
证明该机制必要或充分
        ↓
【表型 2：功能表型】
回到细胞功能、分化、疾病、转录、代谢或生理表型
证明机制有生物学意义
```

## User Example: Alu RNA and Nuclear Speckles

Use this as a style exemplar, not as fixed biological content.

```text
【表型 1：核内空间表型】
红系分化中，活跃转录基因 / RNA Pol II / GATA1 / TAL1 / EKLF
靠近 SRRM2 标记的 nuclear speckles
        ↓

【提出问题】
是什么把活跃基因组织到 nuclear speckles 周围？
        ↓

【猜机制】
RNase A 降解 RNA 后，active gene-speckle association 下降
说明核内 RNA 参与这个空间组织过程
        ↓

【找到候选】
SRRM2 UV-RIP 筛选 nuclear speckle-enriched RNAs
发现一类富含 Alu repeat 的 RNA：
BGLT3、SNHG1、SNHG3、AC024267.1
        ↓

【验证候选定位】
RNA-FISH 证明这些 Alu RNAs 富集在 nuclear speckles
        ↓

【验证机制第一端：结合活跃基因 DNA】
ChIRP-seq 证明 Alu RNAs 结合 promoter / intron / exon 等基因区域
约三分之二结合基因被 RNA Pol II 占据
这些基因富集活性染色质标记，并靠近 speckles
        ↓

【解释 DNA 结合方式】
Alu RNA 结合区域富含 Alu DNA
BGLT3 的 Alu 区域可通过 RNA-DNA hybrid / R-loop 结合 DNA
EMSA、RNase H、DRIP-seq、S9.6 共同支持 R-loop 机制
        ↓

【验证机制第二端：结合 speckle 蛋白】
BGLT3 RNA pull-down + MS 发现其结合 RNA processing / speckle proteins
RIP / immunoblot 验证其与 SRRM2、SON、U2AF2 相互作用
        ↓

【形成桥接模型】
Alu RNA 一端通过 Alu/R-loop 结合活跃基因 DNA
另一端结合 nuclear speckle 蛋白
同时促进 SRRM2 相分离和 speckle 组装
        ↓

【因果验证】
KD BGLT3 / SNHG1：目标基因远离 speckles
full-length rescue：可以恢复目标基因靠近 speckles
ΔAlu / Alu replacement rescue：不能恢复
RNase H1 消除 R-loop：功能下降
        ↓

【表型 2：功能表型】
目标基因远离 speckles
RNA processing 和 nascent transcription 受损
红系基因表达下降
CD71+ / CD235a+ 红系细胞减少
HBA / HBG 表达下降
红系分化受阻
```

## How to Adapt

- Keep the first phenotype visible; do not start with a molecular detail.
- Separate "猜机制" from "找到候选"; an early perturbation suggests a molecular category, but does not identify the factor.
- Use "机制第一端" and "机制第二端" when the model is a bridge, scaffold, recruitment, localization, or phase-separation mechanism.
- Make rescue experiments explicit. Full-length rescue, mutant rescue, domain deletion, replacement, inhibitor rescue, and orthogonal rescue show different strengths of causality.
- End with a second phenotype or functional consequence so the audience knows why the mechanism matters.

## Term Glossary Pattern

When many English terms appear, add a glossary like:

| 英文术语 | 中文解释 | 本文中作用 | 怎么理解 |
| --- | --- | --- | --- |
| nuclear speckles | 核斑/核内剪接斑点 | 富集剪接和RNA加工因子的核内结构 | 像活跃转录基因附近的RNA加工中心 |
| SRRM2 | Serine/arginine repetitive matrix protein 2 | nuclear speckle 标记蛋白和结构支架 | 可当作 speckle 的定位标记 |
| ChIRP-seq | Chromatin Isolation by RNA Purification sequencing | 找 RNA 在基因组上结合的位置 | 用探针拉下某条 RNA 及其结合的 DNA |
| R-loop | RNA-DNA hybrid with displaced ssDNA | 解释 Alu RNA 如何结合 DNA | RNA 与 DNA 配对后挤出另一条 DNA 链 |
