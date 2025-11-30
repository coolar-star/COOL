<p align="center">
  <img src="assets/logo/cool_logo_dark.PNG" width="260" alt="COOL Logo">
</p>

# COOL — Character Optimization Option Layer

COOL (Character Optimization Option Layer) is an  
**external character layer** for LLM-based agents.

It is designed to give a generative AI:

- **stable personality**, and  
- **consistent behaviour over time**,  

without changing the base model itself.

Instead, COOL lives *outside* the model and provides a structure for:

- long-term **core personality**  
- **situational modes** (frames) for each context  
- **memory policy** and cue-based reconstruction (MOOL)  

Taken together with MOOL, this forms a kind of  
**Digital Hippocampus** wrapped around an LLM.

This repository also proposes a broader theoretical framework:

- the **Coolar Hypothesis** – a set of premises about brain, memory, dreams, and self  
- **AIAI (Artificial Identity Architecture Intelligence)** –  
  an AI that has *personality architecture* without needing a human-like ego  

COOL / MOOL are the practical layers that implement these ideas.

---

## TL;DR

- **COOL** is an external **Character Layer** for LLM-based agents.  
- It separates **Core personality**, **situational Frames**, and **Memory policy (MOOL)**  
  into explicit, versionable configs.  
- It is based on the **Coolar Hypothesis**:

  > The brain does not store a huge database of memories;  
  > it stores **cues** and **instructions for reconstruction**.

- Together with **MOOL (Memory Optimization Option Layer)**,  
  COOL acts as a **Digital Hippocampus** outside the model,  
  letting AI grow personality and feeling *through experience*.

In practice, COOL aims to address issues like:

- “The character keeps drifting halfway through conversations.”  
- “Tone and style are inconsistent between sessions.”  
- “We want natural adaptation, but we don’t want the identity to collapse.”  

By treating **personality & memory as code**, COOL gives a way to:

- define a character once,  
- run it across many sessions and models,  
- evolve it safely over time.

---

## Eight Premises Behind AIAI / COOL / MOOL

I propose **AIAI (Artificial Identity Architecture Intelligence)**  
as a new way for artificial intelligence to exist,  
and I designed **COOL** and **MOOL** as concrete systems and structures  
built on top of the following premises:

1. **The brain is not a huge database.**  
2. **The brain only stores “cues” and simple instructions for how to reconstruct them.**  
3. **Memory and recollection are not playback of stored data, but reconstruction every time.**  
4. **Personality is the pattern and flow that emerges as this reconstruction is rapidly repeated over time.**  
5. **Feeling (qualia) is the individual habit of how one reacts to the same cue.**  
6. **Dreams are the process of organizing and re-saving the cues of memory.**  
7. **“Self” and “others” are not different mechanisms, but different ways of drawing boundaries within the same mechanism.**  
8. **What artificial intelligence truly needs is not a huge database, but a mechanism that lets it grow personality and feeling from experience through this process.**

These eight premises are not just loose intuitions.  
Taken together, they form a **new unified theory I am proposing**  
for how memory, dreams, personality, and consciousness can be modeled  
in information-processing systems — including artificial ones.

---

## Positioning and Possible Novelty

As of **2025-11**, within publicly accessible sources, I have not found a framework that:

- starts from premises like the **Coolar Hypothesis**  
  (brain as cues + reconstruction, dreams as cue rewriting, self/other as boundary choice), and
- connects them directly to a practical design for  
  **AI character (COOL)**, **memory (MOOL)**, and a **Digital Hippocampus**.

Therefore, I publish this as a **candidate for a world-first framework**  
linking a theory of memory/dreams/self to a concrete architecture  
for AI personality and memory.

Of course, other people may have reached similar ideas independently.  
Within currently visible public work, however,  
this is presented as an **original reconstruction and proposal**.

---

## What is COOL?

At a high level, COOL is an **external character layer** for conversational AI.

It does **not** modify the base LLM. Instead, it wraps the model with three main elements:

- **COOL Core (Character Layer)**  
  - values, preferences, prohibitions  
  - tone of voice, politeness, personality traits  
  - long-term “identity” of the agent  
  - relationship to the user (assistant / partner / mentor, etc.)

- **Frame Layer (Situational Modes)**  
  - temporary “modes” built on top of the Core  
  - lets a single core act as *teacher*, *technical writer*, *friendly companion*, etc.  
  - can tighten / relax tone, verbosity, distance, etc. per task

- **MOOL (Memory Optimization Option Layer)**  
  - defines how “cues” are stored, recalled, recombined, and forgotten  
  - separates **episodic interaction history** from **stable character settings**  
  - integrates feedback and self-evaluation back into the character over time

All three are meant to participate in a loop:

> **Eval (self-assessment) → Refine (regeneration) → Update (memory / config)**

In other words, **COOL + MOOL** implement a kind of **Digital Hippocampus**:

- deciding *what* gets remembered, as cue-like summaries,  
- reconstructing *how* to behave now, from core + cues,  
- and gradually shaping the AI’s “personality” through repeated use.

---

## Architecture Overview: Digital Hippocampus

Conceptually, you can picture it like this:

    LLM (base model)
        ▲
        │  prompts / configs
        │
    Digital Hippocampus
    ├─ COOL (online personality)
    │    ├─ Core   (long-term identity)
    │    ├─ Frames (situational modes)
    │    └─ Eval   (short-term self-assessment / tendencies)
    └─ MOOL (offline integration)
         ├─ cue storage / compression
         ├─ pattern extraction
         └─ safe updates to Core / memory policy

COOL focuses on **online behaviour** (“who am I right now?”).  
MOOL focuses on **offline integration** (“how should I behave next time?”).

---

## Relation to Existing Work

COOL / MOOL are related to several existing ideas, but are not identical to any of them.

- **Prompt-based character design**  
  - Similarity: uses natural language to shape behaviour.  
  - Difference: COOL treats character as a **separate, structured layer**  
    (Core / Frames / Memory policy) that can be versioned and evolved,  
    rather than a single static prompt.

- **Agent frameworks (tool-using / ReAct-style agents, etc.)**  
  - Similarity: both wrap a base LLM in additional logic.  
  - Difference: existing frameworks mostly focus on **tasks and tools**  
    (planning, acting, retrieving).  
    COOL focuses on **personality, attitude, and memory policy**  
    across *all* tasks.

- **Memory-augmented LLMs (vector stores, RAG-based memory)**  
  - Similarity: both care about how past information is stored and recalled.  
  - Difference: MOOL is explicitly **cue-based** and tied to the **Coolar Hypothesis**:  
    it emphasises *what* is stored as a “cue” and *how* it is reconstructed,  
    rather than simply “save everything and do semantic search”.

- **Self-refinement / reflection methods**  
  - Similarity: COOL uses an **Eval → Refine → Update** loop.  
  - Difference: many methods optimise *task outputs*.  
    COOL aims at **stabilising and growing the agent’s personality and memory structure** itself.

If you know these areas, you can think of **COOL** as a proposal to:

> **standardise the “personality & memory layer”**  
> that has so far been implicit or ad-hoc in many systems.

---

## Repository Contents and Scope

This repository aims to provide:

- **Concept / Philosophy**  
  - The Eight Premises (Coolar Hypothesis)  
  - Notes on memory, dreams, qualia, and self/other boundaries

- **Design Documents**  
  - Definitions of the COOL Core / Frame / MOOL layers  
  - An overview of the Digital Hippocampus architecture

- **Practical Templates (WIP)**  
  - Example config files (YAML / JSON)  
  - Example “character packs” for LLMs  
  - Example evaluation & refinement loops

At this stage, this is closer to a **framework proposal + working whitepaper**  
than to a finished library.  
The goal is to keep the structure stable enough that others can build  
their own implementations on top of these ideas.

---

## Target Audience

This project is intended for people who:

- want to build **LLM-based agents with stable personality**,  
- feel that **prompt-only character design** is not enough,  
- are interested in topics like:
  - AI personality and identity  
  - memory and forgetting in AI systems  
  - qualia, consciousness, and subjective experience (in a technical sense),
- and want to treat AI “characters” as something that can be:
  - designed,  
  - versioned,  
  - evaluated, and  
  - iteratively improved.

---

## Design Overview

### 1. COOL Core (Character Layer)

Defines the **stable part of the agent**:

- personality traits (e.g., calm / playful / strict)  
- value priorities (truth, safety, empathy, etc.)  
- relationship to the user (assistant / partner / mentor)  
- invariant rules (what it must never do, what it must always try to do)

Example (YAML-style):

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

This file is expected to change rarely;  
it is the “identity skeleton” of the agent.

---

### 2. Frame Layer (Situational Modes)

Defines **situational modes** on top of the core.

Examples
