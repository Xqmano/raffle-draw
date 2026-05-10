# Game Design Document — Postapocalypse Now

Last updated: 2026-05-10

---

## Overview

**Postapocalypse Now** is a survival management game set in a near-future collapse scenario in Northern Europe or North America. The player is not a survivor — they are the camp leader's journal: an observer who watches, records, and occasionally influences the group's decisions through task assignment and resource policy.

The tone is grounded, bleak, and human. Survivors feel like real people, not stat-blocks. The player never sees numbers directly — they read the journal.

---

## Setting & Tone

- Northern Europe / North America post-collapse
- No supernatural elements; no zombies — just scarcity, weather, and other people
- English language throughout
- The player character is implied but never shown — the "you" of the journal
- Emphasis on the mundane: finding food, keeping people rested, avoiding mistakes that spiral

---

## Core Philosophy

- **Indirect control.** The player assigns tasks and sets policies; survivors do the rest. No direct control over survivors' moment-to-moment actions.
- **Hidden information.** Survivor traits, exact stat values, and probabilities are never shown. The player infers everything through journal entries and outcomes.
- **Narrative first.** All feedback comes through the camp leader's first-person journal. No stat bars. Ever.
- **Permanence.** Survivors who die are gone. Decisions have lasting weight.

---

## Survival Needs

Survivors have three hidden stats: **Hunger**, **Thirst**, and **Fatigue**. None are shown as numbers or bars — the player reads their state through journal entries.

### Hunger & Thirst

- Thirst depletes at roughly 1.2 units/hour (critical without water for ~72 hours)
- Hunger depletes at roughly 0.17 units/hour (critical without food for ~504 hours / 3 weeks)
- State transitions: Fine → Struggling → Distressed → Critical
- Each state transition triggers a first-person journal entry (e.g., "Thomas looks gaunt — he hasn't eaten properly in days")
- After 4 hours in the Critical state, a survivor enters crisis: they either leave the camp or die (currently 50/50)

### Ration Policy

The player sets a camp-wide ration policy that governs how much hunger and thirst is restored at each distribution (every 8 game hours):

| Policy  | Hunger restored | Thirst restored |
|---------|----------------|----------------|
| Full    | 4              | 15             |
| Half    | 2              | 7              |
| Quarter | 1              | 3              |

Survivors on Manual rations receive nothing until the policy is changed. Food and water are consumed from the shared camp inventory.

### Theft

If a survivor is Distressed or Critical and the inventory is empty, there is a small chance they will steal rations from a campmate. This is logged in the journal with the survivor's name.

### Fatigue

- Fatigue accumulates during active tasks (+0.4/hr)
- Fatigue recovers during the Rest task (-0.6/hr) and slowly while idle (-0.1/hr)
- States: Rested → Tired → Exhausted
- Fatigue state influences task performance (planned: higher fatigue → worse outcomes)

---

## Time

- 1 real-world second = 1 game hour
- 24-hour day/night cycle (visual/mechanical consequences planned for later)
- The clock advances continuously; all task timers, need depletion, and ration distribution are tied to it

---

## Survivors

### Structure

Each survivor is an entity with:
- Name (randomly assigned from a gendered name pool at game start)
- Gender
- Known recipe list (per-survivor; not shared)
- Task statistics (foraging success/fail counts, crafting count, rest count, guard duty count)
- Observations (earned journal entries unlocked by milestones)
- First impression (written at game start; visible in journal from day one)
- Hidden stats: Hunger, Thirst, Fatigue and their named states

### Names

Survivor names are randomly drawn at the start of each playthrough from gendered name pools. Starting pool size is small (10 per gender) and intended to grow. Names have a Northern European / North American feel.

### First Impressions

Each survivor has a handwritten first impression entry visible in the Survivors tab of the journal from the start of the game. These are fixed per survivor archetype and written in the camp leader's voice.

### Earned Observations

Observation entries unlock when a survivor hits a task milestone. Each key can only trigger once per survivor (no duplicates). Current triggers:

| Trigger Key        | Condition                          |
|--------------------|------------------------------------|
| forage_success_3   | 3 successful foraging trips        |
| forage_success_5   | 5 successful foraging trips        |
| forage_fail_3      | 3 failed foraging trips            |
| craft_3            | 3 completed crafting tasks         |
| rest_3             | 3 completed rest tasks             |

### Survivor Backgrounds (Planned)

Survivors will have backgrounds (scout, medic, labourer, etc.) that:
- Grant starting recipe bonuses (e.g., scouts start knowing Campfire)
- Skew hidden trait values
- Influence personality and morale reactions

### Traits (Planned)

Survivors have hidden attributes (e.g., Perception, Endurance) that influence task outcome probabilities. Traits are **never shown as numbers or labels** — the player infers them over time from journal observations and patterns in task outcomes.

### Personality & Disposition (Planned)

Drives: theft likelihood, the leave-vs-die decision during crisis, morale reactions to events.

### Death & Departure

When a survivor enters crisis (4 hours at Critical need with no resolution):
- They leave or die permanently (currently 50/50)
- The outcome is logged in the journal
- The survivor node becomes invisible; they are gone from the playthrough
- Future: tie the leave/die decision to personality and morale

---

## Task System

The player clicks a survivor, picks a task, and sets a duration. The task runs in real time; the journal logs the result when it completes.

### Available Tasks

| Task        | Effect                                           |
|-------------|--------------------------------------------------|
| Forage      | Rolls the loot table; adds items to inventory    |
| Craft       | Consumes materials; produces a recipe output     |
| Rest        | Reduces fatigue over time                        |
| Guard Duty  | Placeholder; requires a threat system to matter  |
| Improvise   | Attempts to discover a new recipe (stubbed)      |

---

## Foraging

### Multi-Roll System

Each foraging trip makes up to three loot table rolls:

1. **First roll** — always made; full table including "Nothing Found"
2. **Second roll** — 65% chance; fails entry excluded (always finds something)
3. **Third roll** — 35% chance; fails entry excluded

This means foragers reliably find at least one item most of the time, with a meaningful chance of a good haul.

### Loot Table (Current)

| Item          | Type     | Weight | Amount Range |
|---------------|----------|--------|--------------|
| Berries       | Food     | 15     | 1–13         |
| Mushrooms     | Food     | 15     | 1–5          |
| Canned Fruit  | Food     | 10     | 1–2          |
| Scrap Metal   | Material | 10     | 1–2          |
| Glass Shard   | Material | 10     | 1–5          |
| Sharp Stone   | Material | 15     | 1–3          |
| Long Stick    | Material | 10     | 1–2          |
| Short Stick   | Material | 12     | 1–3          |
| Heavy Branch  | Material | 8      | 1–2          |
| Torn Cloth    | Material | 8      | 1–3          |
| Rock          | Material | 12     | 1–4          |
| Clean Water   | Water    | 80     | 1–4          |
| Nothing Found | Fail     | 25     | —            |

### Carrying Capacity (Planned)

Multi-roll foraging is currently capped at 3 items per trip. Crafting backpacks and carrying implements will increase this cap in a future update.

---

## Crafting

### Per-Survivor Recipe Lists

Each survivor has their own `known_recipes` array. Survivors start with a set of universal starter recipes and can learn more through backgrounds, improvisation, or teaching (future systems).

**Starter recipes (all survivors):** Spear, Club, Bandage, Crude Hammer

Campfire is in the recipe catalog but is **not** a starter recipe — it is reserved for background-gated survivors (e.g., scouts).

### Recipe Format

Each recipe defines:
- Required ingredients (consumed at task start)
- Optional ingredients (planned: influence output quality)
- Output item and quantity

### Ingredient Consumption

Ingredients are checked and consumed at **task start**, not on completion. If materials are missing when the task fires, the craft fails.

### Quality System (Planned)

Output quality will depend on the materials used and the survivor's experience with that task type:

| Condition                              | Output tier   |
|----------------------------------------|---------------|
| Required materials only, low experience | Makeshift     |
| Required + optional materials          | Standard      |
| Optional materials + experienced survivor | High Quality |

The recipe data structure already includes optional ingredient fields in preparation for this system.

### Improvise Crafting (Planned)

When a survivor attempts to Improvise, they spend time and possibly consume materials in an attempt to discover a new recipe. This is the primary mid-game mechanism for expanding a survivor's recipe list without a teacher. Currently stubbed — logs a journal entry, no mechanics yet.

### Teaching (Planned)

A survivor can spend an action slot to teach a known recipe to another survivor. Mechanically this copies a recipe key from one survivor's `known_recipes` to another's.

---

## Inventory & Journal

### Inventory

All items go into a shared camp inventory (Dictionary, item name → count). There is no per-survivor inventory.

### Journal

The journal (opened with J) is the player's only interface to the game state beyond the scene itself. It is written in the camp leader's first-person voice.

**Tabs:**

- **Log** — full chronological event history; timestamped entries in bold
- **Survivors** — first impression + earned observations per survivor
- **Inventory** — current item counts; consumed/depleted items shown with strikethrough

**Design rules:**
- No stat bars. No numbers for survivor needs. Ever.
- All feedback is narrative — the player reads, they do not observe UI meters
- Future: graphical overhaul to a handwritten notebook look (Tier 5 polish)

---

## Win & Lose Conditions

### Lose

- All survivors are dead or have left camp
- Game over screen shows days and hours survived, then Quit

### Win (Planned)

A survival goal has not yet been defined. Candidate options:
- Survive X days
- Reach a specific location or milestone
- Establish a self-sufficient camp (building/shelter threshold)

This remains an open design question.

---

## Current Recipe Catalog

| Recipe       | Required             | Optional          | Output            | Notes                        |
|--------------|----------------------|-------------------|-------------------|------------------------------|
| Spear        | Long Stick           | Sharp Stone       | Spear ×1          | Optional improves quality    |
| Club         | Short Stick or Heavy Branch | —         | Club ×1           | Either ingredient works      |
| Bandage      | Torn Cloth           | —                 | Bandage ×1        |                              |
| Crude Hammer | Rock                 | Short Stick       | Crude Hammer ×1   | Optional improves quality    |
| Campfire     | Heavy Branch ×3, Rock ×2 | —            | Campfire ×1       | Background-gated; not starter |

---

## Planned Systems (Summary)

See TODOLIST.md for the full tiered roadmap. Key upcoming systems:

- **Survivor traits** — hidden, inferred from journal
- **Random events** — ambushes, strangers, illness, found caches
- **Guard duty threats** — raids, wildlife; without a threat, guard duty is meaningless
- **Morale** — affects performance and crisis decisions
- **Survivor backgrounds** — starting bonuses and trait skews
- **Weather** — affects fatigue rate, foraging yield, mood
- **Building & shelter** — structures that improve conditions or unlock tasks
- **Water filter & campfire boiling** — craftable infection-prevention projects
- **Infections / illness** — from unfiltered water, wounds, exposure
- **Experience system** — survivors improve at repeated tasks
- **Save / load** — persist a playthrough across sessions
- **Main menu** — new game, continue, settings
- **Sound & music**
- **Graphical journal** — handwritten notebook look

---

## Locked Design Decisions

- Traits are always hidden — never shown as numbers or labels
- Journal is the camp leader's first-person notebook — no stat bars, ever
- Recipes are per-survivor; teaching = copying recipe keys from one survivor to another
- Quality system: base materials → makeshift; optional materials + experienced survivor → better tiers
- Campfire is background-gated (not a universal starter recipe)
- Survivor names are randomly drawn per playthrough from gendered name pools
- Game setting: Northern Europe / North America post-apocalyptic, English language
- Backpacks and carrying gear will increase the foraging multi-roll cap (currently 3 items max)
- Water filter and campfire boiling are the planned infection-prevention crafting projects
- Ingredients are consumed at task start, not completion
