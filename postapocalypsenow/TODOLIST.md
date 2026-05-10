# Postapocalypse Now — Development Roadmap

Last updated: 2026-05-10

---

## Tier 1 — Foundation
*The game doesn't work without these.*

- [ ] **Win/lose conditions** — starvation and group wipe are handled; define a survival goal
- [x] **Hunger & thirst system** — hidden stats, deplete over time, ration policy, journal feedback
- [x] **Fatigue system** — accumulates from tasks, recovers from rest and idle time
- [x] **Rest task mechanics** — restores fatigue
- [ ] **New game screen** — name your camp, start fresh; currently launches straight into the scene

---

## Tier 2 — Core Loop Depth
*Makes the game worth playing.*

- [ ] **Survivor traits** — hidden attributes (Perception, Endurance, etc.) that skew task outcomes; never shown as numbers
- [ ] **Guard duty mechanics** — something to protect against (raids, wildlife, theft); without a threat, guard duty is meaningless
- [ ] **Random events** — ambushes, strangers at camp edge, found caches, illness; drive the narrative
- [ ] **Day/night cycle consequences** — night should feel more dangerous than day
- [ ] **Improvise crafting** — chance-based recipe discovery; main way to unlock new recipes mid-game

---

## Tier 3 — Survivor Systems
*Makes survivors feel like people.*

- [ ] **Survivor backgrounds** — scout, medic, labourer, etc.; each grants starting recipe bonuses and trait skews; Campfire recipe unlocks here
- [ ] **Morale system** — affects task performance and disobedience; tied to food, rest, events, social dynamics
- [ ] **Teaching recipes** — survivors can spend time passing a known recipe to another survivor
- [ ] **Survivor death & departure** — permanent; currently stubbed as 50/50 leave/die; tie to personality later
- [ ] **Permanent jobs** — assign survivors standing roles rather than one-off tasks *(pinned for discussion after more testing)*
- [ ] **More observation triggers** — richer journal entries over time; currently only 5 triggers exist
- [ ] **Personality & disposition system** — drives theft chance, leave vs. die decision, morale reactions

---

## Tier 4 — World & Crafting Depth

- [ ] **Item quality system** — makeshift / standard / high quality output based on materials and survivor experience; recipe "optional" fields are already structured for this
- [ ] **Experience system** — survivors improve at tasks they repeat; feeds into quality and trait expression
- [ ] **Weather effects** — impacts foraging yield, fatigue rate, mood
- [ ] **Building & shelter** — basic camp structures that improve conditions or unlock new tasks
- [ ] **Water filter** — craftable; reduces infection risk from unfiltered water
- [ ] **Campfire crafting project** — boiling water lowers infection chance; Campfire recipe already in catalog, background-gated
- [ ] **Expanded loot tables** — more biome variety, seasonal shifts, urban vs. wilderness zones
- [ ] **Expanded recipe catalog** — tools, medicine, traps, food preparation
- [ ] **Backpacks & carrying implements** — increase max items found per forage trip (currently capped at 3)
- [ ] **Infections / illness** — from unfiltered water, wounds, or exposure; treatable with medicine

---

## Tier 5 — Polish & Shippable Product

- [ ] **Save/load system** — persist a playthrough across sessions
- [ ] **Graphical journal overhaul** — handwritten notebook look, as discussed
- [ ] **Survivor portrait system** — move away from placeholder images; support more visual variety
- [ ] **Sound design** — ambient camp sounds, task feedback, event stings
- [ ] **Music**
- [ ] **Main menu & settings** — volume, keybinds, new game / continue
- [ ] **Try Again on game over screen** — currently only has Quit; needs main menu first
- [ ] **Expanded name lists** — currently 10 per gender; target 50+
- [ ] **Balance pass** — loot weights, hunger/thirst rates, crafting durations, event frequency
- [ ] **Remove or toggle debug stat labels** — currently always visible; should be dev-only

---

## Design Decisions Locked In

- Traits are always hidden — never shown as numbers or percentages
- Journal is the camp leader's first-person notebook — no stat bars, ever
- Recipes are per-survivor; teaching = copying recipe keys from one survivor to another
- Quality system: base materials → makeshift; optional materials + experienced survivor → better tiers
- Campfire is background-gated (not a universal starter recipe)
- Survivor names drawn randomly per playthrough from gendered name pools
- Game setting: Northern Europe / North America post-apocalyptic, English language
- Backpacks and carrying gear will increase the foraging multi-roll cap (currently 3 items max)
- Water filter and campfire boiling are the planned infection-prevention crafting projects
