# CopyHuman ✍️👤

> **Remove the structural fingerprint that makes narrative writing read as AI-generated.**  

[![Skills Ecosystem](https://img.shields.io/badge/skills.sh-copyhuman-blue.svg)](https://skills.sh)
[![Compatible with](https://img.shields.io/badge/agents-Claude%20%7C%20Codex%20%7C%20Antigravity%20%7C%20Cursor%20%7C%20Cline-purple.svg)](#installation)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

---

## The Core Insight

**Style edits do not work.**

Researchers at the University of Maryland and Google DeepMind (*Russell et al., COLM 2026*) ran AI stories through professional-grade humanizing and prose-polishing tools that removed clichés, purple prose, and redundant exposition. **Detection fell by only 1.6 points (from 95.5% to 93.9%).**

When they removed all stylistic markers (word choice, cadence, grammar) and tested **narrative structure alone**, the classifier still identified AI writing at **93.2% macro-F1**.

> **The fingerprint is not in the words. It is in the shape of the story.**

CopyHuman forces AI coding agents and narrative assistants to operate on **narrative architecture** before drafting, preventing the structural tells that flag text as machine-generated.

---

## 🚀 Installation

CopyHuman is compatible with **all major AI coding agents and assistants** through the universal Skills specification (`npx skills`) or direct folder installation.

### 1. Universal Installation (Recommended)

Install globally across all supported AI agents on your machine:

```bash
npx skills add hallogroup-hq/copyhuman -g -y
```

Or install for specific agents:

```bash
npx skills add hallogroup-hq/copyhuman -g --agent claude-code codex cursor
```

---

### 2. Claude Code

**Global (all projects):**
```bash
npx skills add hallogroup-hq/copyhuman -g --agent claude-code
```

**Project-only:**
```bash
mkdir -p .claude/skills
git clone https://github.com/hallogroup-hq/copyhuman.git .claude/skills/copyhuman
```

---

### 3. OpenAI Codex / Agent Workspaces

**Global:**
```bash
npx skills add hallogroup-hq/copyhuman -g --agent codex
```

**Project-only (`.agents/skills`):**
```bash
mkdir -p .agents/skills
git clone https://github.com/hallogroup-hq/copyhuman.git .agents/skills/copyhuman
```

---

### 4. Google Antigravity / Gemini CLI

**Global installation:**
```bash
git clone https://github.com/hallogroup-hq/copyhuman.git ~/.gemini/config/skills/copyhuman
```

---

### 5. Cursor, Cline, Windsurf, Roo Code & Aider

Install directly with the Skills CLI:
```bash
npx skills add hallogroup-hq/copyhuman -g
```

Or copy `SKILL.md` directly into your workspace rules (`.cursorrules`, `.clinerules`, or system instructions).

---

## ⚡ How It Works

CopyHuman operates in two distinct modes:

### Mode A: Structure First (Pre-Drafting)
*Trigger when writing a new story, screenplay, scene, video script, or essay.*

The agent pauses before drafting prose to fill out a **10-Decision Structure Sheet** based on measured human vs. AI distribution baselines:

| # | Narrative Axis | AI Default | Measured Human Rate |
|---|---|---|---|
| 1 | **Timeline** | Mostly linear (2.12 / 5) | More flashbacks/jumps (2.40 / 5) |
| 2 | **Subplots** | No subplots (79%) | Parallel / contrasting subplots (43%) |
| 3 | **Ending Cause** | Protagonist choice alone (69%) | Mixed or outside forces (54%) |
| 4 | **Resolution** | Internal understanding (47%) | Concrete external events (73%) |
| 5 | **The Moral** | States moral in closing (77%) | Leaves unstated (48%) |
| 6 | **Emotion Delivery** | Somatic / body sensations (81%) | Stated plain or behavioral (62%) |
| 7 | **Lead Introduction**| Exterior description (52%) | In dialogue or mid-action (70%) |
| 8 | **References** | Vague generic echoes (72%) | Specific named real entities (47%) |
| 9 | **Reader Address** | Strictly fourth-wall (93%) | Direct or permeable address (28%) |
| 10| **Lead Morality** | Morally clean (62%) | Ambivalent / flawed (59%) |

> **The Budget Rule:** Do not invert all ten. Pick **3 to 4 deliberate deviations** that serve the story. Inverting everything creates an artificial, difficult read.

### Mode B: Narrative Audit (Existing Drafts)
*Trigger on: `"Audit this draft"`, `"Does this read like AI?"`, `"Why does my script feel generic?"`*

1. **30-Feature Audit**: Evaluates the piece against the 30 structural markers from StoryScope Table 16.
2. **Separates Structural vs. Cosmetic Issues**:
   - **Structural** (*moves the needle*): Ending causes, unearned revelations, moralizing conclusions, sensory distribution.
   - **Cosmetic** (*does not move detection*): Synonyms, rhythm, adjective trimming.
3. **Restructures, Not Rewords**: Delivers actionable scene changes and structural fixes.

---

## 💡 Practical Rules & Real-World AI Tells

Through real-world application across digital marketing, screenwriting, and social media, two additional rules have been established:

### 1. The Punctuation Tell: Banning the Em-Dash (`—`)
In English literary journals, the em-dash (`—`) is considered an elegant pause. However, in digital copy, social media captions, and localized languages (like Indonesian), **the em-dash is an instant dead giveaway for AI-generated text**. 
* **The Reality:** Real humans typing on mobile or desktop keyboards rarely go out of their way to input `—`. 
* **The Rule:** Replace em-dashes with commas, colons, parentheses, or clean, natural sentence splits (`.`).

### 2. The Somatic Proportion Rule: Earned, Not Absent
* **The Misconception:** If AI overuses physical body sensations (81% of AI stories feature tight chests, cold sweat, or held breath), should we ban somatic descriptions completely?
* **The Data:** Human authors still use somatic descriptions in **38% of stories**. Complete elimination makes writing sterile and robotic.
* **The Rule:** Apply physical sensations only when **earned** at peak crisis or genuine physical strain, and draw from diverse, grounded physical reality (e.g., cramped fingers from writing, dry eyes from screens) rather than the generic AI triad of chest/throat/breath.

---

## 🎯 Prompts & Trigger Phrases

You can invoke CopyHuman naturally in your prompts:

* *"Draft a short film scene using copyhuman. Plan the structure sheet first."*
* *"Does this essay read like AI? Audit it with copyhuman."*
* *"Why does this narrative feel flat and machine-generated? Fix the structural tells."*
* *"Make this narrative sound human, don't just change the words."*

> [!TIP]
> **If your AI agent skips the Structure Sheet (Mode A):**  
> Some AI agents occasionally guess how to write "human" text without reading the skill file. If your agent drafts text immediately without presenting the 10-decision table, explicitly prompt:  
> `👉 "Read the copyhuman SKILL.md file and output the Mode A Structure Sheet before writing any prose."`

---

## 📁 Repository Structure

```
copyhuman/
├── SKILL.md                          # Main skill instructions & execution protocol
├── references/
│   ├── core-features.md              # 30 narrative features & statistical benchmarks
│   └── model-fingerprints.md         # Characteristic habits of Claude, GPT, Gemini, etc.
├── README.md                         # Documentation & installation guide
├── LICENSE                           # MIT License
└── .gitignore
```

---

## 📚 Attribution & Research

This skill is designed based on the methodology and empirical datasets published in:

> Russell, Rajendhran, Pham, Iyyer, & Wieting.  
> **"StoryScope: Structural Separation of Human and Machine Fiction"**  
> *University of Maryland and Google DeepMind*, COLM 2026.

---

## 📄 License

MIT License. Free to use, modify, and distribute across all agents and toolchains.
