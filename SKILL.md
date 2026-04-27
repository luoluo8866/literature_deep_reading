---
name: literature-deep-reading
description: 精读科研文献并转化为中文文献汇报稿和PPT逻辑。Use when the user says "Literature Deep Reading", "使用 Literature Deep Reading 精读这篇文献", "精读文献", "文献汇报", or when Codex needs to analyze a paper, PDF, Word reading notes, journal club draft, or slide deck; extract the user's reading logic; build a biomedical/mechanistic paper presentation; by default produce the full deep-reading package including deep-reading notes, figure-by-figure evidence chains, phenotype-to-mechanism logic chains, Q&A, professional terminology explanations/glossaries, critique, limitations, future directions, Thinking/课题迁移, report script, and PPT outline.
---

# Literature Deep Reading

## Overview

Use this skill to read a scientific paper like a journal-club mentor: extract the paper's central question, reconstruct the background logic, unpack each result as a question-experiment-evidence-inference chain, preserve the user's own questions, explain technical terms, and turn the analysis into a Chinese report script and PPT outline.

Default to the user's personal style when present: `logic`, `Q`, `潜在问题`, `补充`, `研究问题`, `结果说明`, `生物学意义`, `Limitation`, and `Thinking`.

Default invocation rule: if the user simply says `使用 Literature Deep Reading 精读这篇文献` or otherwise asks for broad literature deep reading without narrowing the scope, automatically produce the full package: 精读笔记、Background logic、逐图Result逻辑、表型到机制逻辑链、Q&A/补充、专业名词解释、Limitation/future directions、Thinking/课题迁移、中文汇报稿、PPT大纲. Only omit a section when the paper lacks that content or the user explicitly asks for a smaller output.

## Workflow

### 1. Gather Inputs

Collect all available artifacts before reasoning:

- Paper PDF or article text.
- User reading notes, especially Word documents with personal `Q` and `logic` comments.
- Existing report稿, PPT/PPTX, slide screenshots, or notes.
- User constraints: audience, duration, journal club vs group meeting, desired depth, and whether to create/edit PPT files.

If documents must be parsed, prefer local extraction tools and bundled document libraries. Do not upload private papers or notes to external services unless the user explicitly allows it.

### 2. Orientation Pass

Build a compact overview before deep reading:

- One-sentence central thesis.
- Known background -> unresolved gap -> paper's main question.
- Main methods and model systems.
- Core conclusion in causal-arrow form, e.g. `p53 loss -> L1 activation -> cis/trans R-loop accumulation -> DNA damage/inflammation`.
- Figure/result map: which figure answers which subquestion.

Use the three-pass habit from `references/method-checkpoints.md` when the paper is long or unfamiliar.

### 3. Background Logic

Reconstruct Background as a chain that forces the scientific question to appear:

1. Define the object and why it matters.
2. Explain the mechanism needed to understand the paper.
3. Move from phenomenon to mechanism, not encyclopedia detail.
4. Connect prior studies in this order when possible: correlation -> causality -> conservation/generalization -> remaining gap.
5. End with the exact unresolved problem the paper addresses.

For biomedical mechanism papers, explicitly distinguish:

- Phenomenon: what is observed in disease/cell models.
- Mechanism: what molecular process may explain it.
- Gap: what link is unproven.
- Hypothesis: what the authors are testing.
- Prediction: what result would support the hypothesis.

### 4. Result-by-Result Reading

For each result section or figure, create a "result card":

- **提出问题**: What question from Background does this figure answer?
- **实验设计**: What groups, perturbations, readouts, controls, and time points are used?
- **方法原理**: Why can this method answer the question?
- **结果**: What was observed, staying close to the figure.
- **说明了什么**: What inference is justified?
- **是否足够支持**: Missing controls, alternative explanations, technical caveats, model limitations.
- **承上启下**: Why the next experiment is needed.
- **可迁移点**: Can this design inspire the user's own project?

Do not flatten figures into a generic summary. Preserve figure numbers, panels, method names, and the logic connecting panels.

### 5. Evidence Chain

After result cards, merge them into a paper-level evidence chain:

- Background gap.
- Subquestion 1 -> evidence -> inference.
- Subquestion 2 -> evidence -> inference.
- Mechanistic model.
- Clinical/biological implication.

Use arrows for causal hypotheses and label confidence:

- `相关性`: association only.
- `因果性`: perturbation/rescue/intervention supports causality.
- `机制性`: molecular mediator or direct recruitment shown.
- `普适性`: multiple models, datasets, species, or clinical samples support generalization.

### 6. Phenotype-to-Mechanism Logic

When the paper has a strong mechanistic story, add a separate logic chain in the user's preferred style:

`表型观察 -> 提出问题 -> 猜机制/初筛线索 -> 找到候选 -> 验证候选定位/表达 -> 验证机制第一端 -> 验证机制第二端 -> 形成模型 -> 因果验证 -> 回到功能表型`

Use this chain to connect spatial, molecular, and functional phenotypes. Keep each node short and concrete:

- **表型**: What biological or cellular pattern starts the story?
- **提出问题**: What mechanism is missing?
- **猜机制**: What perturbation suggests a molecular class, such as RNA, chromatin, protein complex, metabolite, or signaling pathway?
- **找到候选**: What screen, sequencing, proteomics, or imaging result nominates candidates?
- **机制第一端/第二端**: What does the candidate bind or affect on each side of the proposed bridge?
- **模型**: What physical or causal model integrates both ends?
- **因果验证**: Which knockdown, rescue, mutant rescue, inhibitor, degradation, or overexpression experiment proves necessity/sufficiency?
- **表型验证**: Does the mechanism explain the original phenotype and downstream biological function?

Read `references/logic-chain-patterns.md` when the user asks for `逻辑梳理`, when a paper moves from phenotype to mechanism, or when the presentation needs a clear causal story.

### 7. User Questions, Method Notes, and Terms

Treat the user's `Q:` lines as first-class output. For each question:

- Answer from the paper if possible.
- Add method background only as much as needed.
- Mark uncertain points as `需查证` or `文章未充分说明`.
- Suggest one validation experiment when useful.

For common method-heavy papers, explain why each control exists: knockout validation, antibody specificity, RNase H control, rescue/inhibitor treatment, reporter validation, input normalization, positive/negative loci, orthogonal detection systems, and cross-cell-line validation.

Add a professional terminology section when the output contains many English terms. For each term, include:

- English term and common abbreviation.
- Chinese translation.
- Plain-language meaning.
- Why it matters in this paper.
- Related method/marker/pathway if useful.

Prefer short, study-specific explanations over dictionary definitions.

### 8. Critical Reading

Critique with care and specificity:

- **Validity**: Does the design answer the question? Are controls adequate?
- **Result strength**: Are effects quantified, replicated, and supported by orthogonal methods?
- **Causality**: Does the paper distinguish cause from consequence?
- **Mechanism**: Does it show direct recruitment/interaction or only correlation?
- **Generalizability**: cell lines vs primary cells, animal models, clinical data, disease context.
- **Alternative explanations**: technical artifacts, off-target effects, antibody specificity, normalization, selection bias.
- **Future work**: experiments that directly repair the weakness.

Prefer concrete critique over broad complaints.

### 9. Outputs

For a default broad invocation, produce the complete deep-reading package below. Do not require the user to separately request `表型到机制逻辑链` or `专业名词解释`; include both automatically when applicable.

1. **精读笔记**
   - Abstract主线
   - Background logic
   - 研究问题
   - Result logic/result cards
   - 表型到机制逻辑链 when applicable
   - Q&A/补充
   - 专业名词解释
   - 总结模型
   - Limitation/future directions

2. **汇报稿**
   - Page-by-page or section-by-section Chinese oral script.
   - Use transitional sentences: `由此引出...`, `为了验证...`, `结果显示...`, `这说明...`, `但这里仍有一个问题...`.

3. **PPT大纲**
   - Title
   - Background
   - Question
   - 研究思路
   - Result 1-N
   - Conclusion
   - Limitation
   - Thinking

4. **Thinking/课题迁移**
   - Which methods, controls, data integration strategies, or conceptual distinctions can be borrowed for the user's project.
   - Include concrete experimental or analysis ideas, not only general inspiration.

5. **专业名词解释**
   - Table format is preferred: `英文术语 | 中文解释 | 本文中作用 | 怎么理解/记忆`.
   - Include methods, cell markers, proteins, genomic elements, sequencing assays, inhibitors, and conceptual terms.
   - Group terms by topic if there are many: `分子/结构`, `实验方法`, `细胞表型`, `数据分析`, `疾病/功能`.

If the user asks to create or edit an actual `.pptx`, use the PowerPoint skill after the logic is approved.

## Style Rules

- Write primarily in Chinese for the user's literature notes and report content.
- Keep English technical terms when they are standard or useful for searching: `DRIP-seq`, `GRO-seq`, `R-loop`, `ChIP-qPCR`, `HDACi`, `SETDB1`.
- Preserve the user's causal arrows and shorthand when they clarify logic.
- Prefer arrow chains for mechanism stories, especially `表型 -> 问题 -> 候选 -> 机制两端 -> 桥接模型 -> 因果验证 -> 表型验证`.
- Separate author claims from your interpretation.
- If using web research, prefer the original paper, official method resources, primary literature, or authoritative reviews; cite sources briefly.

## Reference

Read `references/method-checkpoints.md` when designing a new deep-reading workflow, when the user asks to improve the skill, or when a paper needs especially rigorous critique.

Read `references/logic-chain-patterns.md` when the user asks for phenotype-to-mechanism logic, mechanism storytelling, or a concise presentation flow from initial phenotype to functional validation.
