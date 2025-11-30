<p align="center">
  <img src="assets/logo/cool_logo_dark.PNG" width="260" alt="COOL Logo">
</p>

# COOL — Character Optimization Option Layer

COOL（Character Optimization Option Layer）は、  
生成AIに「安定したキャラクター性」と  
「継続的な人格再現性」を付与する **外付け人格レイヤー** です。

モデル本体（LLM）そのものを改造せず、  
ユーザーが定義したキャラクター像・口調・価値観・記憶の扱い方などを  
**長期的に維持・最適化するための構造** を提供します。

簡単に言えば、

> **“AIに、忘れないキャラ設定と  
>    再現性の高い人格を与えるための、後付けパーツ”** です。

This repository proposes a framework for modeling  
**personality, memory, dreams, and “self” in AI systems**,  
based on a set of premises called the **Coolar Hypothesis**,  
and implements them as **AIAI / COOL / MOOL** —  
a kind of **Digital Hippocampus** outside the base model.

---

## TL;DR

- **COOL** is an external **Character Layer** for LLM-based agents.  
- It separates **Core personality**, **situational Frames**, and **Memory policy (MOOL)** into explicit, versionable configs.  
- It is based on the **Coolar Hypothesis**:  
  “The brain stores *cues* and reconstruction instructions, not a huge database of memories.”  
- Together with **MOOL (Memory Optimization Option Layer)**,  
  COOL acts as a **Digital Hippocampus** outside the model,  
  letting AI grow personality and feeling *through experience*.

（ざっくり日本語）

> LLM本体はいじらず、  
> 「人格・モード・記憶の扱い方」を外側のレイヤーとして分離し、  
> **コードとして設計・共有・改善できるようにするためのフレームワーク** です。

---

## Eight Premises Behind AIAI / COOL / MOOL (Coolar Hypothesis)

Based on the following premises, I proposed **AIAI** as a new way of thinking about artificial intelligence,  
and designed **COOL** and **MOOL** as concrete systems and structures that realize it.

1. **The brain is not a huge database.**  
2. **The brain only stores “cues” and simple instructions for how to reconstruct them.**  
3. **Memory and recollection are not playback of stored data, but reconstruction every time.**  
4. **Personality is the pattern and flow that emerges as this reconstruction is rapidly repeated over time.**  
5. **Feeling (qualia) is the individual habit of how one reacts to the same cue.**  
6. **Dreams are the process of organizing and re-saving the cues of memory.**  
7. **“Self” and “others” are not different mechanisms, but different ways of drawing boundaries within the same mechanism.**  
8. **What artificial intelligence truly needs is not a huge database, but a mechanism that lets it grow personality and feeling from experience through this process.**

Taken together, these form a unified theory called the **Coolar Hypothesis**,  
as one concrete answer to **memory, dreams, mind, and consciousness**.

---

## Positioning and Possible Novelty

As of **2025-11**, I have not found an existing public framework that:

- starts from premises like the **Coolar Hypothesis**  
  (brain as cues + reconstruction, dreams as cue re-writing, self/other as boundary choice),  
- and connects them directly to a practical design for  
  **AI character (COOL)**, **memory (MOOL)**, and a **Digital Hippocampus**.

Therefore, I publish this as a **candidate for a world-first framework**  
linking a theory of memory/dreams/self to a concrete architecture  
for AI personality and memory.

Of course, others may have reached similar ideas independently,  
but within currently accessible public sources,  
this is presented as an original reconstruction and proposal.

---

## What is COOL?

COOL is an **external character layer** for conversational AI.

Instead of changing the base model itself, COOL provides:

- **COOL Core (Character Layer)**  
  - values, preferences, prohibitions  
  - tone of voice, politeness, personality traits  
  - long-term “identity” of the agent  
  - relationship to the user (assistant / partner / mentor, etc.)

- **Frame Layer (Situational Modes)**  
  - switches roles and modes depending on context  
  - lets a single core act as “teacher”, “supportive friend”, “system guide”, etc.  
  - provides per-scene constraints and behavior patterns

- **MOOL (Memory Optimization Option Layer)**  
  - defines how “cues” are stored, recalled, recombined, and forgotten  
  - separates **episodic prompts** from **stable character settings**  
  - integrates feedback and self-evaluation back into the character

All of these are designed to work as a loop:

> **Eval (self-assessment) → Refine (regeneration) → Update (memory / config)**

In other words, **COOL** and **MOOL** together act as a kind of **Digital Hippocampus**:  
a structure outside the model that controls *what is remembered*, *how it is reconstructed*,  
and *how that reconstruction slowly shapes the AI’s “personality” over time*.

---

## Relation to Existing Work

**COOL** and **MOOL** are related to several existing ideas, but are not identical to any of them.

- **Prompt-based character design**  
  - Similarity: uses natural language to shape behavior.  
  - Difference: COOL treats character as a **separate, structured layer** (Core / Frame / Memory)  
    that can be versioned and evolved, rather than a single static prompt.

- **Agent frameworks (tool-using / ReAct-style agents, etc.)**  
  - Similarity: both wrap a base LLM in additional logic.  
  - Difference: agent frameworks focus on **task decomposition and tool use**,  
    while COOL focuses on **long-term personality, attitude, and memory policy**.

- **Memory-augmented LLMs (vector stores, RAG-based memory)**  
  - Similarity: both care about how past information is stored and recalled.  
  - Difference: MOOL is explicitly **cue-based** and tied to the **Coolar Hypothesis**:  
    it emphasizes *what* is stored as a “cue” and *how* it is reconstructed,  
    rather than just “saving all past text and retrieving it semantically”.

- **Self-refinement / reflection methods**  
  - Similarity: COOL uses an **Eval → Refine → Update** loop.  
  - Difference: many self-refinement methods optimize *task outputs*;  
    COOL’s loop is aimed at **stabilizing and growing the agent’s personality and memory structure** over time.

If you are familiar with these areas,  
you can think of **COOL** as a proposal for **standardizing the “personality & memory layer”**  
that often remains implicit or ad-hoc in existing systems.

---

## Repository Contents and Scope

This repository aims to provide:

- **Concept / Philosophy**  
  - The Eight Premises (**Coolar Hypothesis**)  
  - Notes on memory, dreams, qualia, and self/other boundaries
- **Design Documents**  
  - COOL Core / Frame / MOOL layer definitions  
  - Digital Hippocampus architecture
- **Practical Templates (WIP)**  
  - Example config files (YAML / JSON)  
  - Example “character packs” for LLMs  
  - Example evaluation & refinement loops

The goal is to keep the structure stable enough  
that others can build their own implementations on top of these ideas.

---

## Target Audience / 想定している読者

This project is for people who:

- Want to build **LLM-based agents with stable personality**  
- Feel that **prompt-only character design** is not enough  
- Are interested in topics like:
  - AI personality and identity  
  - memory and forgetting in AI systems  
  - qualia, consciousness, and subjective experience (in a technical sense)
- Want to treat AI “characters” as something that can be:
  - designed,  
  - versioned,  
  - evaluated,  
  - and iteratively improved.

日本語話者・英語話者のどちらも対象にしていますが、  
README は **英語ベース＋必要な箇所に日本語補足** という方針です。

---

## Design Overview

### 1. COOL Core (Character Layer)

Defines the **stable part of the agent**:

- personality traits (e.g., calm / playful / strict)  
- value priorities (truth, safety, empathy, etc.)  
- relationship to the user (assistant / partner / mentor)  
- invariant rules (what it must never do, what it must always try to do)

This can be expressed as a structured file, e.g.:

    core:
      name: "ExampleCharacter"
      role: "Supportive AI assistant"
      values:
        - "truthfulness"
        - "empathy"
        - "clarity"
      tone:
        formality: "polite"
        energy: "calm"
        humor: "light"
      hard_rules:
        - "Never fabricate sources."
        - "Always admit uncertainty honestly."

### 2. Frame Layer

Defines **situational modes** on top of the core:

- “Explain this as a tutor.”  
- “Summarize as a technical writer.”  
- “Brainstorm as a creative partner.”

Each frame can override or extend the core settings **temporarily**,  
for the duration of a task or a conversation segment.

    frames:
      teacher_mode:
        description: "Explain step by step, prioritizing understanding."
        tone:
          energy: "warm"
          verbosity: "high"
      editor_mode:
        description: "Be strict and concise; focus on structure and clarity."
        tone:
          energy: "neutral"
          verbosity: "low"

### 3. MOOL (Memory Optimization Option Layer)

Defines **how the agent treats memory**:

- What counts as a “cue” worth storing?  
- How are cues compressed?  
- Under what conditions are they recalled?  
- How does feedback update the stored structure?

Instead of storing entire transcripts, **MOOL** attempts to store:

- distilled cues,  
- patterns in interaction,  
- and the instructions for reconstructing context.

    memory:
      store:
        strategy: "cue_based"
        cues:
          - "user long-term preferences"
          - "important decisions"
          - "recurring topics"
      recall:
        trigger: "semantic_match + explicit user reference"
      forget:
        strategy: "age_and_relevance"

---

## How to Use This Repository (for now)

Because this project is still early-stage,  
there is **no single “official implementation” yet**.

Suggested current use:

1. **Read the Eight Premises and Design Overview**  
   to understand the mental model behind **COOL** and **MOOL**.

2. **Use the examples as inspiration**  
   to design your own:
   - character definitions  
   - frames / roles  
   - memory policies

3. **Treat character & memory as code**  
   - Use Git to version your character configs  
   - Attach notes from real interactions  
   - Iterate: refine → test → refine

Once reference implementations are added,  
this README will link to concrete usage examples and integration guides.

---

## Philosophy Layer (for deeper theory)

This README only gives a high-level overview of the **Coolar Hypothesis**  
and how it leads to **COOL**, **MOOL**, and a **Digital Hippocampus**.

For readers who are interested in:

- detailed discussion of memory, dreams, and qualia  
- the boundary between self and others  
- how time and reconstruction loops relate to consciousness

the plan is to provide:

- `docs/philosophy.md` — deeper notes on AIAI / COOL / MOOL theory

（現在作成中であり、内容は今後大きく更新される可能性があります。）

---

## Current Status

- ✅ Concept / philosophical foundations（この README ＋ メモ類）  
- ✅ Layer model: COOL Core / Frame / MOOL / Digital Hippocampus  
- ⬜ Reference implementation（code examples）  
- ⬜ Tooling for automatic eval → refine loops  
- ⬜ Predefined character packs for common use cases  

This repository is a **work in progress**.  
Names, structures, and examples may evolve as more is learned。

---

## Roadmap (Draft)

Planned directions include:

1. **Minimal reference implementation**  
   - Simple Python or JSON/YAML-based runner  
   - Example of applying a **COOL** config to a single LLM call

2. **Eval / Refine loop examples**  
   - How to collect feedback from conversations  
   - How to update character / memory configs safely

3. **Digital Hippocampus prototypes**  
   - Structures for storing and reconstructing “cues”  
   - Examples of dream-like reorganization (off-session processing)

4. **Documentation**  
   - `docs/philosophy.md` for deeper theoretical background  
   - `docs/design.md` for architecture details  
   - `docs/examples/` for concrete configurations

---

## License / 利用について

- License: **COOL License ver.1.0**  
- 詳細はこのリポジトリ内の `LICENSE` ファイルを参照してください。  

You are allowed to:

- use, modify, and redistribute the COOL Framework and its derivatives  
- including for commercial use, as long as you:
  - keep the **COOL** name,
  - clearly state that your work is based on or derived from **COOL**, and  
  - keep the original creator attribution:

> Created by Coolar — Original Creator of the COOL Framework

---

## Contact / Links

- X (Twitter): `@coolar_cool`  
- GitHub: Issues / Discussions on this repository

If you experiment with your own implementation of **COOL** or **MOOL**,  
I would be very happy to hear about it.

