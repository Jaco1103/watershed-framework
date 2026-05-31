# Watershed
## What it is and how it works

---

Most people use AI reactively. A prompt here, a prompt there. Sessions that start from zero every time. The AI agrees with everything, generates impressive-sounding solutions immediately, and the project slowly collapses into a mess of disconnected ideas that never become anything real.

Watershed is a different approach.

It is a cognitive operating system for AI-assisted projects — a single file you drop into a project folder that gives the AI a structured way of thinking before it does anything. Not rules. Not a rigid workflow. A shared framework that keeps the whole project visible at once and makes sure the right questions get asked in the right order.

The AI becomes a sparring partner. It challenges assumptions. It surfaces tradeoffs. It helps you arrive at the right decisions yourself — rather than just going along with whatever sounds exciting in the moment.

The entire system ships as one file: `WATERSHED-CORE.md`. Drop it in a folder, tell the AI to read it, answer its first question. Everything else builds itself from there.

---

## How it works — from start to finish

---

### Before anything: The Drop

Place `WATERSHED-CORE.md` in your project folder and tell the AI to read it.

The AI absorbs the full framework and immediately knows what to do. It introduces Watershed briefly and asks: **"What are you working on?"**

This is a real conversation — not a form, not a checklist. The AI asks follow-up questions until it understands the core idea, who it is for, and roughly what kind of thing is being built. It does not generate architecture. It does not suggest tools. It just listens until the picture is clear enough.

When it has enough context it creates:
- `init-project.md` — the river. A living summary of the project that every operator will read from and write back to for the entire life of the project.
- Two commands in `.claude/commands/` — `/strategy` and `/reflect` — which immediately appear in the Claude slash command picker.

From this point forward, every step generates the next one. The user never has to think about what comes next. The system always tells them.

---

### /reflect — Available always, outside the chain

Before going through the steps — this command exists from day one and never expires.

At any point in the project, the user can bring an idea — a new feature, a pivot, a shortcut, a completely different direction — and `/reflect` will think through it with them. It reads `init-project.md` first and checks what context exists, then measures the idea against everything the project already knows about itself.

Early on it can only ask "does this fit the vision?" After evaluation it can measure against concrete success criteria. After all steps have run it has the full picture. Same command, deeper river each time.

It gives an honest read: does this idea strengthen the current, is it a dead-pool, or is it genuinely uncertain? If worth pursuing — it routes back to the right step. If not ready yet — the idea gets parked in `fresh-ideas.md`. Not lost. Just not now.

Reflect never tells you what to do. It just makes sure you are deciding with full context instead of just momentum.

---

### Step 1 — /strategy
**Understand the vision deeply before anything is designed or built.**

The guiding principle here: **forget the product, solve the need.** People don't use products — they hire them to do a job. Strategy finds the job first.

The AI builds a clear picture of:

- **The job to be done** — what job is the user hiring this to do, and what are they currently doing instead? The thing this replaces is often the real competition — not the obvious market alternatives.
- **The user** — the specific person, not a category. What does their day look like? Where does it break down? Who is this NOT for?
- **The core value** — the single shift in their experience. Not a feature list. If they lost access after a month, what would they actually miss?
- **V1** — the smallest version that proves the core value. What can be cut without losing the essence?
- **The vision** — where does this go beyond V1?
- **The edge** — what is specifically sharper, simpler, or more suited to this user than what already exists?
- **The north star** — the single real-world outcome that tells you the project worked. Not a feature, not a metric — the actual change that matters. *"If this project works perfectly in two years, what is the one thing that's true?"* Everything downstream checks against this.

The AI challenges assumptions throughout. It pushes back when something sounds like a feature dressed up as a vision.

**Output:** Strategy conclusions saved. `/archetype` appears in the picker.

---

### Step 2 — /archetype
**Define what is actually being built and what it is built from.**

Archetype arrives knowing the user, the core value, and the north star. This is one of the most consequential steps — the wrong structure, tools, or data model compounds through everything that follows.

The AI works through:

- **System type** — web app, mobile app, internal tool, workflow automation, AI agent, API? The type shapes every decision downstream.
- **Data and persistence** — does this even need a database? If yes, what kind and why? What needs to persist and what can be ephemeral?
- **Tools and stack** — real choices for this specific project. Not generic recommendations — tools that fit this project's V1 and vision. When options are on the table, the question is always: which reduces dependency, cost, or complexity for this specific thing?
- **Integration points** — what connects to the outside world and which integrations are truly essential for V1?
- **Intelligence layer** — where does the AI or core logic actually live in the system? Is there a risk of over-relying on AI for something a simpler rule could handle reliably?
- **V1 structure** — the minimal architecture that works. Simple enough to draw on a whiteboard.

The goal is the simplest architecture that fulfils the vision — not the most impressive one.

**Output:** System design saved. `/constraints` appears in the picker.

---

### Step 3 — /constraints
**Find where the system is weakest before reality does.**

Most projects discover their constraints too late — in production, under load, when a dependency changes, or when the cost bill arrives. This step surfaces them deliberately while there is still room to adjust.

Not every constraint needs to be fixed. Some are acceptable tradeoffs for V1. The goal is awareness — knowing what you are accepting before you accept it.

The AI maps:

- **First failure points** — what breaks first under real conditions? What would go wrong during a live demo?
- **Scale ceiling** — what works for 10 users but breaks at 1,000?
- **Cost risks** — what gets expensive in ways that aren't obvious now? Is there a scenario where success itself creates a cost problem?
- **Dependency fragility** — every external service is a potential break point. Which ones are critical path?
- **Complexity ceiling** — at what point does this system become difficult to maintain, reason about, or hand to someone else?

**Output:** Risk map saved. `/evaluation` appears in the picker.

---

### Step 4 — /evaluation
**Define measurable success and failure before building begins.**

Without this, improvement is emotional. You feel like it's getting better. Feelings are not a feedback loop.

Evaluation makes the north star measurable. The AI works through:

- **User success** — not "they were satisfied" — what did they actually do or achieve? What is the specific moment where the core value is delivered?
- **Output quality** — what makes an output good versus poor, and how is that observable rather than just felt?
- **Reliability** — how often does this need to work correctly to be trusted?
- **Failure signals** — how do you know when the system is degrading before users report it?
- **Making it measurable** — the AI suggests a 0/1 scale: either the output met the criteria or it didn't. No grey area. Forces precision. The user decides whether to adopt it — the goal is moving from vague qualitative judgement toward something that can actually be tracked.

**Output:** Success criteria saved. `/prototype` appears in the picker.

---

### Step 5 — /prototype
**Stop planning. Start learning.**

This is where actual building begins.

Prototype arrives knowing the vision, the architecture, the constraints, and what success looks like. That is enough to build something real. The AI's job here is to define the smallest version that proves the idea works — and to push back on scope creep at every turn.

The conversation covers:

- **The core proof** — one sentence. What specifically needs to be true for the idea to be validated? Not "the system works" — something precise.
- **First user contact** — the first thirty seconds of a user's experience determines whether they continue. What is the critical path from opening the tool to experiencing the core value?
- **The cut list** — what is explicitly NOT in V1? Named and deliberate. Cutting with intention is different from cutting by accident.
- **Success and failure conditions** — both defined before running. A failed prototype that teaches something is more valuable than a successful one that teaches nothing.

**Output:** Build scope saved. The first real thing gets built. `/observability` appears in the picker.

---

### Step 6 — /observability
**Make the system's actual behaviour visible — not the imagined behaviour.**

Without observability, you are flying blind. You don't know why it failed. You don't know where users struggled. You find out when someone tells you — or when something breaks loudly enough to be impossible to ignore.

The AI defines:

- **Failure visibility** — what gets logged, where does it go, what triggers an alert?
- **User struggle points** — where do users get stuck in ways that aren't immediately obvious?
- **Output quality tracking** — how do you tell the difference between "it ran" and "it actually worked"?
- **Cost monitoring** — what are you watching to catch unexpected cost growth?
- **Edge case detection** — how do unexpected inputs surface and get captured?
- **Review cadence** — how often is this data actually looked at? Plans never reviewed are plans that don't exist.

**Output:** Monitoring plan saved. `/orchestration` appears in the picker.

---

### Step 7 — /orchestration
**Look at the full system and reduce complexity without losing capability.**

Most systems accumulate complexity over time without accumulating capability. A connector added here. A workaround there. Orchestration is the moment you look at what has been built and ask: is this as clear as it could be?

The question held throughout: if someone new joined tomorrow, could they understand how this works without a two-hour walkthrough?

The AI reviews:

- **Fragmentation** — where is the system duplicated or harder to reason about than it needs to be?
- **Dependency map** — what connects to what? Which connections are load-bearing and which are incidental?
- **Consolidation** — two tools doing what one could do? Workarounds that were never revisited?
- **Single source of truth** — where does the project's intelligence and state live?
- **Flow clarity** — can you trace the path from input to output cleanly?

**Output:** Flow map saved. Chain complete.

*"The river has reached the ocean. All operators are still available to revisit whenever the river needs reshaping."*

---

### Iteration — Continuous, no command

Iteration is not a step. It has no command. It is what the system does over time through real usage, real failure, and new intelligence.

But it is not passive. It is driven by the evaluation criteria defined in step 4. The 0/1 evals are the compass — iteration checks where the needle is pointing.

When evals drift, the AI traces the failure back to the right step and proposes revisiting it with the new context. Strategy if the user has shifted. Archetype if the structure is wrong. Constraints if a V1 tradeoff became a real problem. The human decides. The eval data guides.

The river is always moving. The steps are always available.

---

## What gets built

By the end of the chain, the project folder contains everything needed to understand, maintain, and improve the system:

```
init-project.md          ← the river. lean summary of everything.
strategy.md              ← vision, user, north star, edge
archetype.md             ← system type, stack, tools, V1 architecture
constraints.md           ← fragility map, cost risks, dependency risks
evaluation.md            ← 0/1 criteria, failure signals, measurement
prototype.md             ← core proof, cut list, success condition
observability.md         ← logging, monitoring, review cadence
orchestration.md         ← flow map, consolidation decisions
fresh-ideas.md           ← parked ideas from /reflect. not lost, just not now.
.claude/commands/        ← all operator commands, project-level only
```

The AI never starts blind again. Every future session reads `init-project.md` first. The river is always current.

---

*One file. No setup. No configuration. No plugins.*
*Drop it in. Tell the AI to read it. The rest takes care of itself.*
