# Literature Deep Reading Skill

This repository contains a Codex skill for deep scientific literature reading, Chinese journal-club reporting, phenotype-to-mechanism logic chains, and professional terminology explanations.

## Repository Layout

```text
literature_deep_reading/
  SKILL.md
  agents/openai.yaml
  references/logic-chain-patterns.md
  references/method-checkpoints.md
```

## Install From GitHub

After pushing this folder to GitHub, install it with the Codex skill installer:

```bash
scripts/install-skill-from-github.py --repo <owner>/<repo> --path literature-deep-reading
```

Or, if installing from a GitHub URL:

```bash
scripts/install-skill-from-github.py --url https://github.com/<owner>/<repo>/tree/main/literature-deep-reading
```

Restart Codex after installation.

## Default Use

```text
使用 Literature Deep Reading 精读这篇文献
```

The skill defaults to a complete deep-reading package:

- 科学问题
- Background logic
- 逐图 Result 逻辑
- 表型到机制逻辑链
- Q&A / 补充
- 专业名词解释
- Limitation / future directions
- Thinking / 课题迁移
- 中文汇报稿
- PPT 大纲
