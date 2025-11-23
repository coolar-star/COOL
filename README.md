# COOL — Character Optimization Option Layer

<p align="center">
  <img src="assets/logo/cool_logo_dark.PNG" width="260" alt="COOL Logo">
</p>

COOL (Character Optimization Option Layer) is an external identity framework  
that gives AI models **stable character behavior** and **consistent persona reproduction**  
without modifying the base model.

It solves the common issues such as:

- “The character breaks after several turns”
- “Tone consistency is unstable”
- “LLMs forget the personality the user defined”
- “Long conversations drift away from the intended persona”

COOL uses a **Core / Frame / Eval** triple-layer loop  
to maintain identity continuity.

---

## Contents

- [1. What is COOL?](#1-what-is-cool)
- [2. Purpose & Design Philosophy](#2-purpose--design-philosophy)
- [3. Architecture Overview](#3-architecture-overview)
- [4. How COOL Generates “Current Me”](#4-how-cool-generates-current-me)
- [5. Hallucination Mitigation](#5-hallucination-mitigation)
- [6. Problems COOL Solves](#6-problems-cool-solves)
- [7. COOL Runtime Loop](#7-cool-runtime-loop)
- [8. Setup (Core Generation)](#8-setup-core-generation)
- [9. Directory Structure](#9-directory-structure)
- [10. Basic Usage Example](#10-basic-usage-example)
- [11. Future Extensions](#11-future-extensions)
  - [11.1 Core Update Rules](#111-core-update-rules)
- [12. MOOL — Memory Optimization Option Layer](#12-mool--memory-optimization-option-layer)
- [13. MOOL Processing Flow](#13-mool-processing-flow)
- [14. Digital Hippocampus — Integrated Architecture](#14-digital-hippocampus--integrated-architecture)
- [15. AIAI — Artificial Identity Architecture Intelligence](#15-aiai--artificial-identity-architecture-intelligence)
- [16. License](#16-license)

---

## 1. What is COOL?

**COOL** is an external framework that provides  
**stable identity**, **consistent persona**, and **repeatable character behavior**  
for conversational AI systems.

It does **not** modify the base model.

Instead, COOL recreates the AI’s persona every turn using:

- Long-term stable identity (Core)  
- Short-term context-adaptive frame (Frame)  
- Self-evaluation memory (Eval)

In short:

> **“An external identity unit that gives LLMs a stable character frame  
> and persistent persona consistency.”**

---

## 2. Purpose & Design Philosophy

COOL has one goal:

> **To enable AI–human dialogue with a stable, coherent,  
> and continuously reproducible personality.**

Design principles:

- Do not modify the base LLM  
- Function as an external layer  
- Consistently handle character definitions  
- Rebuild “current persona” every turn  
- Mimic the human hippocampus (short-term reconstruction)  
- Simple implementation

COOL is **not a memory system**.  
It is:

> **“A loop that reconstructs a persona frame using Core + Eval every turn.”**

---

## 3. Architecture Overview

COOL consists of three components:

### ◆ Core — Long-Term Identity

The stable axis of personality.

- Values  
- Tone, pronouns  
- Rules that must not be violated  
- Relationship to the user  
- Character atmosphere  

Stored in: `core_profile.json`  
Updated rarely.

---

### ◆ Frame — Current Persona

Rebuilt every turn based on:

- Core  
- Eval  
- Recent conversational context  

This represents “who I am **right now**.”  
Not stored permanently.

---

### ◆ Eval — Self-Evaluation Memory

A minimal memory that stores:

- What worked  
- What didn’t  
- Behavior adjustments  
- Future Frame tuning  
- Candidate micro-updates for Core  

Stored in: `eval_memory.json`

---

## 4. How COOL Generates “Current Me”

Every turn, COOL uses:

1. **Core** — persistent identity  
2. **Eval** — accumulated reflection  
3. **Recent context** — limited short-term recall  

And reconstructs **Frame** (current persona) from scratch.

This separation enables:

- No character drift  
- No tone collapse  
- No forgetting of core traits  
- Natural adaptation to conversation flow

COOL mimics a **digital hippocampus** that rebuilds identity on demand.

---

## 5. Hallucination Mitigation

Although COOL is not a safety system,  
its structure naturally reduces hallucinations by enforcing:

- Factual priority (Core values)  
- No overconfident speculation  
- Prohibited behaviors (constraints)  
- Continuous self-correction (Eval)

This acts as a “persona brake,”  
reducing hallucination tendencies.

---

## 6. Problems COOL Solves

- Character breaks in long conversations  
- Tone inconsistency  
- Persona drift  
- No distinction between long-term identity & short-term state  
- No mechanism to rebuild “current self”  

COOL solves these through:

> **Core (identity) × Frame (momentary behavior) × Eval (reflection)**

---

## 7. COOL Runtime Loop

```
Initial State:
  core_profile.json
  eval_memory.json
  prev_answer = None
```

### Step 1 — Idle  
Wait for user input **Uₙ**.

### Step 2 — Frame Rebuild  
Generate Frame from Core + Eval + recent context.

### Step 3 — Output  
Aₙ = f(Core, Frame, Uₙ)

### Step 4 — Self-Evaluation  
Update Eval using the triad:

- Aₙ₋₁  
- Uₙ  
- Aₙ  

### Step 5 — Save  
Store Eval → loop back to Idle.

---

## 8. Setup (Core Generation)

Users describe the character in natural language.  
Setup scripts parse it into `core_profile.json`.

Example:

> “You are my junior coworker, polite but mischievous.  
> You call me ‘senpai’ and speak in a calm, soft tone.  
> Your values are…”  

COOL transforms this into a formal Core profile.

---

## 9. Directory Structure

```
COOL/
  README.md
  spec/
    core.md
    frame.md
    eval.md
  setup/
    setup_dialogue.md
  data/
    core_profile_template.json
    eval_memory_template.json
  examples/
    manual_loop_example.md
```

---

## 10. Basic Usage Example

```python
core = load_core_profile()
eval = load_eval_memory()
prev_A = None

while True:
    U = wait_user_input()
    frame = rebuild_frame(core, eval)
    A = llm_answer(core, frame, U)
    eval = evaluate(prev_A, U, A)
    save(eval)
    prev_A = A
```

---

## 11. Future Extensions

- Automatic log compression  
- Faster Frame generation  
- Optional safety/ethics profile integration  
- Plugin support  
- Connection layer for GPTs & other models  
- Advanced “digital hippocampus” mode  
- MOOL (offline memory optimization layer)

---

### 11.1 Core Update Rules

Core = the “identity nucleus.”  
Updating it improperly will fundamentally alter the AI.

Rules:

1. **Values are considered immutable**  
   - Additions must be rare  
   - Removal is not allowed  

2. **Tone/character changes should be micro-adjustments only**

3. **Constraints must never be reduced**

4. **Short-term emotional states must not be added to Core**

5. **Only multi-turn recurring patterns (Eval consensus) may update Core**

---

## 12. MOOL — Memory Optimization Option Layer

MOOL works **outside** COOL.  
It optimizes Eval **offline** (non-dialogue time).

MOOL handles:

- Eval compression  
- Noise removal  
- Long-term pattern extraction  
- Core update candidate generation  
- Stabilization of Frame generation  

MOOL never updates Core directly.

---

## 13. MOOL Processing Flow

1. Load all Eval entries  
2. Remove noise & one-time reactions  
3. Extract recurring behavior patterns  
4. Generate Core update candidates  
5. Save optimized Eval  

---

## 14. Digital Hippocampus — Integrated Architecture

LLMs lack:

- Stable identity  
- Persona continuity  
- Reconstruction of “current self”  
- Self-evaluation  
- Separation of long-term & short-term traits  

Digital Hippocampus combines:

- **COOL** (online identity reconstruction)  
- **MOOL** (offline memory integration)  

Recreating the human cycle of  
**daily experience → sleep-based memory consolidation**.

---

### 14.1 Dual Loop Structure

```
Digital Hippocampus
├─ COOL (online)
│    ├─ Core
│    ├─ Frame
│    └─ Eval
└─ MOOL (offline)
     ├─ Eval compression
     ├─ Noise removal
     └─ Core update candidates
```

---

### 14.2 Motivation

LLMs break character in long sessions because they have  
**no identity architecture**.

Digital Hippocampus provides that missing structure.

---

### 14.3 Identity Gap Filled by COOL  
### 14.4 Memory Integration Filled by MOOL  

(Sections intentionally summarized for clarity.)

---

## 15. AIAI — Artificial Identity Architecture Intelligence

COOL’s extension is not AGI or ASI.

It is:

> **AIAI — a controllable, safe identity architecture  
> that enables advanced personality design  
> without self-preservation or autonomous goals.**

AIAI focuses on:

- Structured identity  
- Predictable behavior  
- Safe persona design

---

## 16. License

This project is licensed under **COOL License v1.0**.

- Free use, modification, redistribution  
- Commercial use allowed  
- “COOL” name cannot be removed/altered  
- “Created by Coolar” must be included  
- Derivatives must acknowledge origin  

© 2025 Coolar — Original Creator of the COOL Framework

