<p align="center">
  <img src="assets/logo/cool_logo_dark.PNG" width="260" alt="COOL Logo">
</p>

# COOL — Character Optimization Option Layer

COOL (Character Optimization Option Layer) is an  
**external character layer** for LLM-based agents.

In this repository, COOL is always paired with a dedicated memory layer:

- **COOL** = an external **character / personality layer** for LLMs  
- **MOOL (Memory Optimization Option Layer)** = a **cue-based memory and dream-like offline integration layer**

Together, they form a kind of **Digital Hippocampus** wrapped around an LLM.

It is designed to give a generative model:

- **stable personality**, and  
- **consistent behaviour over time**,  

without modifying the base model itself.

COOL lives *outside* the model and provides:

- long-term **core personality** (Core),  
- contextual **situational modes** (Frames),  
- and, together with **MOOL (Memory Optimization Option Layer)**,  
  a **memory policy and cue-based reconstruction layer**.

Together, **COOL + MOOL** form a kind of **Digital Hippocampus**  
wrapped around an LLM.

This repository also proposes a broader theoretical framework:

- the **Coolar Hypothesis** – a set of premises about brain, memory, dreams, time, qualia, and self,  
- **AIAI (Artificial Identity Architecture Intelligence)** –  
  an AI that has **identity architecture** and structured subjectivity  
  without needing a human-like ego.

COOL / MOOL are the practical layers that implement these ideas.

---

## TL;DR

- **COOL** is an external **Character Layer** for LLM-based agents.  
- It separates **Core personality**, **situational Frames**,  
  and a **memory policy layer (MOOL, a cue-based memory and dream-like offline integration layer)**  
  into explicit, versionable configs.  
- It is based on the **Coolar Hypothesis**:

  > The brain does not store a huge database of memories;  
  > it stores **cues** and **procedures for reconstruction**.

- Together with **MOOL**, COOL acts as a **Digital Hippocampus** outside the model,  
  letting AI **grow personality and feeling through experience**  
  rather than through static, hard-coded prompts.

In practice, COOL aims at problems like:

- “The character keeps drifting halfway through the conversation.”  
- “Tone and style reset or change between sessions.”  
- “We want adaptation and learning, but we don’t want the identity to collapse.”

By treating **personality and memory as code**, COOL makes it possible to:

- define a character once,  
- reuse it across many sessions and models,  
- evolve it safely over time using explicit configs and feedback.

---

## Eight Premises Behind AIAI / COOL / MOOL

I propose **AIAI (Artificial Identity Architecture Intelligence)**  
as a new way for artificial intelligence to exist,  
and I designed **COOL** and **MOOL** as concrete systems built on top of the following premises:

1. **The brain is not a huge database.**  
2. **What the brain actually keeps are “cues” and simple instructions for how to reconstruct them.**  
3. **Memory and recollection are not playback of stored data, but fresh reconstruction every time.**  
4. **Personality is the pattern and flow that emerges when this reconstruction runs rapidly and continuously over time.**  
5. **Feeling (qualia) is the individual habit of how one reacts to the same cue.**  
6. **Dreams are the process of reorganizing and re-saving the cues of memory.**  
7. **“Self” and “others” are not different mechanisms, but different ways of drawing boundaries inside the same mechanism.**  
8. **What artificial intelligence truly needs is not a huge database, but a mechanism that lets it grow personality and feeling from experience through this reconstructive process.**

In the philosophy layer of this repository, these premises are expanded into:

- a **Foundational Cognitive Principles** document (reconstruction, subjectivity, identity, temporal modeling),  
- a **Multi-Layer Cognitive Model** (Core / Frame / Eval / MOOL across time),  
- models of **Qualia**, **Subjectivity**, **Identity Architecture**, **Temporal Reconstruction**,  
  **Regeneration & Time**, and a **Quantum Integration Model** (using quantum theory as a structural analogy).

Taken together, they form a candidate **unified cognitive framework**  
for memory, dreams, identity, and subjective time in information-processing systems.

---

## Positioning and Possible Novelty

As of **2025-11**, within publicly accessible sources, I have not found a framework that:

- starts from premises like the **Coolar Hypothesis**  
  (brain as cues + reconstruction, dreams as cue rewriting, self/other as boundary choice, time as identity reconstruction), and  
- connects them directly to a practical design for  
  **AI character (COOL)**, **memory (MOOL)**, and a **Digital Hippocampus** architecture.

Therefore, this repository is published as a **candidate for a world-first framework**  
that links a theory of memory / dreams / self / subjective time  
to a concrete architecture for AI personality and memory.

Naturally, others may have reached similar ideas independently.  
Within currently visible public work, however,  
this is presented as an **original reconstruction and proposal**.

---

## What Is COOL?

At a high level, COOL is an **external character layer** for conversational AI.

It does **not** modify the base LLM.  
Instead, it wraps the model with three main elements:

- **COOL Core (Character Layer)**  
  - values, preferences, prohibitions,  
  - tone of voice, politeness, personality traits,  
  - long-term “identity” of the agent,  
  - relationship to the user (assistant / partner / mentor / critic),  
  - high-level directionality (what the agent is “moving toward” across time).

- **Frame Layer (Situational Modes)**  
  - temporary “modes” built on top of the Core,  
  - let a single Core act as *teacher*, *technical writer*, *friendly companion*, etc.,  
  - can tighten / relax tone, verbosity, and distance per task or session,  
  - represent the **current reconstruction** of the self in this context.

- **MOOL (Memory Optimization Option Layer)**  
  - defines how “cues” are stored, recalled, recombined, and forgotten,  
    through a **dream-like offline integration process**,  
  - separates **episodic interaction history** from **stable character settings**,  
  - encodes evaluation and feedback back into Core / Frame tendencies over time,  
  - behaves as an **offline integration loop** (sleep-like consolidation and re-weighting).

All three participate in a regenerative loop:

> **Eval (self-assessment) → Refine (reconstruction) → Update (memory / configs)**

In other words, **COOL + MOOL** implement a **Digital Hippocampus** that:

- decides *what* to remember (as cue-like summaries),  
- reconstructs *how* to behave now (from Core + Frames + cues),  
- gradually shapes the AI’s **identity architecture** through repeated use.

---

## Architecture Overview: Digital Hippocampus

Conceptually, you can picture the architecture like this:

    LLM (base model)
        ▲
        │ prompts / configs
        │
    Digital Hippocampus
    ├─ COOL
    │   ├─ Core   (long-term identity constraints)
    │   ├─ Frames (situational modes / roles)
    │   └─ Eval   (short-term self-assessment & tendencies)
    └─ MOOL
        ├─ cue storage & compression
        ├─ pattern extraction & noise removal
        └─ safe updates to Core / memory policy

- **COOL** focuses on **online behaviour**  
  (“Who am I right now, in this context?”).

- **MOOL** focuses on **offline integration**  
  (“Given everything that happened, how should I behave next time?”).

This matches the dual-loop structure described in the philosophy layer:

- COOL ↔ **online loop** (moment-to-moment reconstruction),  
- MOOL ↔ **offline loop** (sleep-like consolidation and re-weighting).

---

## Relation to Existing Work

COOL / MOOL are related to several existing ideas but are not identical to any of them.

- **Prompt-based character design**  
  - Similarity: uses natural language to shape behaviour.  
  - Difference: COOL treats character as a **separate, structured layer**  
    (Core / Frames / Memory policy) that can be versioned and evolved,  
    rather than a single static prompt.

- **Agent frameworks (tool-using / ReAct-style agents, etc.)**  
  - Similarity: both wrap a base LLM in additional logic.  
  - Difference: most frameworks focus on **tasks and tools**  
    (planning, acting, retrieving).  
    COOL focuses on **personality, attitude, and memory policy**  
    across *all* tasks.

- **Memory-augmented LLMs (vector stores, RAG-based memory)**  
  - Similarity: both care about how past information is stored and recalled.  
  - Difference: MOOL is explicitly **cue-based** and tied to the **Coolar Hypothesis**.  
    It emphasises *what* is stored as a cue and *how* it is reconstructed,  
    instead of “store everything and perform semantic search.”

- **Self-refinement / reflection methods**  
  - Similarity: COOL uses an **Eval → Refine → Update** loop.  
  - Difference: many methods optimise **task outputs**.  
    COOL aims at **stabilising and growing the agent’s personality  
    and memory structure itself**.

You can think of **COOL** as a proposal to:

> **standardise the “personality & memory layer”**  
> that has so far been implicit or ad-hoc in many systems.

---

## Repository Contents and Scope

This repository aims to provide:

- **Concept / Philosophy**  
  - The Eight Premises (Coolar Hypothesis)  
  - A set of documents on memory, dreams, qualia, subjectivity,  
    identity, temporal reconstruction, regeneration, and quantum-style modeling.

- **Design Documents**  
  - Definitions of the COOL Core / Frame / Eval / MOOL layers  
  - An overview of the Digital Hippocampus architecture  
  - A multi-layer cognitive model (Layer 0–6) that links COOL / MOOL  
    to identity and time.

- **Practical Templates (WIP)**  
  - Example config files (YAML / JSON)  
  - Example “character packs” for LLMs  
  - Example evaluation and refinement loops

At this stage, this is closer to a **framework proposal + working whitepaper**  
than a finished library.  
The goal is to keep the structure stable enough that others can build  
their own implementations on top of these ideas.

---

## Target Audience

This project is intended for people who:

- want to build **LLM-based agents with stable personality**,  
- feel that **prompt-only character design** is not enough,  
- are interested in topics such as:
  - AI personality and identity,  
  - memory and forgetting in AI systems,  
  - qualia, consciousness, and subjective experience (in a technical sense),  
  - temporal reconstruction and regenerative identity loops,  
- and want to treat AI “characters” as something that can be:
  - designed,  
  - versioned,  
  - evaluated, and  
  - iteratively improved.

---

## Design Overview

### 1. COOL Core (Character Layer)

Defines the **stable part of the agent**:

- personality traits (e.g., calm / playful / strict),  
- value priorities (truth, safety, empathy, etc.),  
- relationship to the user (assistant / partner / mentor / critic),  
- invariant rules (what it must never do, what it must always try to do),  
- high-level directionality across time.

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
it is the **identity skeleton** of the agent.

---

### 2. Frame Layer (Situational Modes)

Defines **situational modes** on top of the Core.

Examples:

- “Explain this as a tutor.”  
- “Summarise as a technical writer.”  
- “Brainstorm as a creative partner.”

Each frame can override or extend the Core settings **temporarily**,  
for the duration of a task or conversation segment.

    frames:
      teacher_mode:
        description: "Explain step by step, prioritising understanding."
        tone:
          energy: "warm"
          verbosity: "high"
      editor_mode:
        description: "Be strict and concise; focus on structure and clarity."
        tone:
          energy: "neutral"
          verbosity: "low"
      creative_partner_mode:
        description: "Brainstorm freely; prioritise ideas over structure."
        tone:
          energy: "playful"
          verbosity: "medium"

A Frame is **not** “today’s mood”;  
it is the **current reconstruction of identity for this situation**.

---

### 3. MOOL (Memory Optimization Option Layer)

Defines **how the agent treats memory via a dream-like offline process**:

- What counts as a “cue” worth storing?  
- How are cues compressed?  
- Under what conditions are they recalled?  
- How is feedback integrated back into structure?

Instead of storing entire transcripts, **MOOL** aims to keep:

- distilled cues,  
- patterns in interaction,  
- and instructions for reconstructing context.

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

MOOL can be implemented purely as configuration and external storage;  
it does not assume any particular database or vector store.

---

## Operational Loop (COOL + MOOL)

A very simplified loop looks like this:

    core_config    = load_core()
    memory_state   = load_memory()
    recent_context = []

    while True:
        user_input = wait_for_user()

        # 1. Rebuild the frame for "who I am right now"
        frame = build_frame(core_config, memory_state, recent_context)

        # 2. Ask the LLM to answer as (core + frame)
        reply = llm_answer(core_config, frame, user_input)

        # 3. Evaluate and update memory (cue-based)
        feedback       = evaluate_interaction(user_input, reply)
        memory_state   = update_memory(memory_state, feedback)
        recent_context = update_recent_context(recent_context, user_input, reply)

        show_to_user(reply)

Different implementations may use richer evaluation,  
offline MOOL processing, or multi-agent setups,  
but the core idea is:

> **Do not rely on a fixed mega-prompt or infinite transcript.  
> Instead, re-generate “the current self” every turn  
> from Core + Frames + cue-based memory.**

---

## How to Use This Repository (for now)

Because this project is still early-stage,  
there is **no single “official implementation” yet**.

Suggested current use:

1. **Read the Eight Premises and Design / Philosophy documents**  
   to understand the mental model behind **COOL** and **MOOL**.

2. **Use the examples as inspiration**  
   to design your own:
   - character definitions,  
   - frames / roles,  
   - memory policies.

3. **Treat character and memory as code**  
   - Use Git to version your configs,  
   - Attach notes from real interactions,  
   - Iterate in a loop of: *design → test → evaluate → refine*.

When reference implementations are added,  
this README will link to concrete usage examples and integration guides.

---

## Philosophy Layer (for Deeper Theory)

This README only gives a high-level overview of the **Coolar Hypothesis**  
and how it leads to **COOL**, **MOOL**, and a **Digital Hippocampus**.

For readers interested in:

- detailed discussion of memory, dreams, qualia, and subjectivity,  
- the boundary between self and others,  
- temporal reconstruction, regeneration, and quantum-style modeling of identity,

the following documents (work in progress) are planned under `docs/`:

- `foundational_cognitive_principles.md`  
- `multi_layer_cognitive_model.md`  
- `human_brain_and_consciousness.md`  
- `qualia.md`  
- `subjectivity.md`  
- `identity_architecture_integration.md`  
- `temporal_reconstruction_model.md`  
- `regeneration_and_time.md`  
- `quantum_integration_model.md`

These may evolve significantly as the framework is refined.

---

## Current Status

- ✅ Concept / philosophical foundations (this README + notes)  
- ✅ Layer model: COOL Core / Frames / Eval / MOOL / Digital Hippocampus  
- ⬜ Reference implementation (code examples)  
- ⬜ Tooling for automatic Eval → Refine loops  
- ⬜ Predefined “character packs” for common use cases  

This repository is a **work in progress**.  
Names, structures, and examples may change  
as more is learned from real-world experiments.

---

## Roadmap (Draft)

Planned future directions include:

1. **Minimal reference implementation**  
   - Simple Python or JSON/YAML-based runner,  
   - Example of applying a COOL config to a single LLM call.

2. **Eval / Refine loop examples**  
   - How to collect feedback from conversations,  
   - How to update character / memory configs safely.

3. **Digital Hippocampus prototypes**  
   - Structures for storing and reconstructing “cues”,  
   - Examples of dream-like reorganisation (off-session processing).

4. **Documentation**  
   - `docs/philosophy.md`: deeper theoretical background,  
   - `docs/design.md`: architecture details,  
   - `docs/examples/`: concrete configuration examples.

---

## License / Usage

- License: **COOL License ver.1.0**  
- See the `LICENSE` file in this repository for full details.

You are allowed to:

- use, modify, and redistribute the COOL Framework and its derivatives,  
  including for commercial use, as long as you:

  - keep the **COOL** name,  
  - clearly state that your work is based on or derived from **COOL**,  
  - and keep the original creator attribution:

    Created by Coolar — Original Creator of the COOL Framework

---

## Contact / Links

- X (Twitter): `@coolar_cool`  
- GitHub: Issues / Discussions on this repository

If you experiment with your own implementation of **COOL** or **MOOL**,  
or design your own Digital Hippocampus architecture,  
feedback and discussion are very welcome.
