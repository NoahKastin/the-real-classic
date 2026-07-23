# The Real Classic Taxonomy

This taxonomy defines the canonical vocabulary and structures for The Real Classic's AI-driven content generation. It is organized by builder prompt box and serves as the grounding corpus for the AI system (based on cry-with-me's retrieval pattern).

## Glossary: Common Shorthand

When designing abilities, mechanics, and progression, these abbreviated terms appear frequently:

- **1H** — One-handed; a weapon or shield that occupies one hand, allowing dual-wield or off-hand use
- **2H** — Two-handed; a weapon requiring both hands, preventing off-hand equips but typically dealing more damage per swing
- **AoE** — Area of Effect; an ability that damages or affects multiple targets in a zone rather than a single target
- **CC** — Crowd Control; any effect that restricts a target's movement or actions (stun, root, silence, slow)
- **CD** / **Cooldown** — Time required before an ability can be used again
- **DoT** — Damage over Time; an effect that deals damage to a target in increments over a duration (e.g., poison, burn)
- **DPS** — Damage Per Second; output rate or a player specializing in dealing damage
- **GCD** — Global Cooldown; a shared cooldown affecting most abilities, preventing instant ability chains
- **HoT** — Healing over Time; the inverse of DoT, restoring health in increments over a duration
- **Proc** — Probability of Occurrence; a passive chance for an effect to trigger (e.g., a weapon "procs" a bonus on hit)

## Structure

- **attributes.md** — Canonical attribute definitions, terminology, and how attributes interrelate
- **boss-mechanics.md** — Challenge types, enemy behaviors, element combinations, and difficulty scaling rules
- **classes.md** — Class structure, ability effects, resource types, progression patterns, and copyright-avoidance guidelines
- **index.md** — This file
- **races.md** — Appearance descriptors, starting stat bonuses, and copyrighted terms to avoid
- **story.md** — Quest types, NPC roles, narrative elements, questline/zone structure, and currency conventions

## How This Feeds the AI

The AI generation layer (cry-with-me's `build.js`, `modify.js`, `rebuild.js` verbs) uses this taxonomy as:
1. Grounding for structured outputs (typed entries matching the patterns here)
2. Training data for terminology and style (what language to use for attributes, abilities, lore, etc.)
3. A constraint model for generation (what combinations are valid, what ranges are reasonable)

Realm patches are generated as new ENTRY_TYPES entries conforming to these definitions, then frozen into the Realm fixture.
