# Classes

AI training: class structure, ability effects, resource types, and progression patterns.

## Why Limit Class Count?

A simplified class roster—rather than replicating Classic's full set—offers several design advantages:

- **Reduced content scope**: Each class requires unique gear, abilities, and playstyle tuning. Fewer classes mean fewer variants to implement and balance.
- **Clearer progression path**: Players see distinct roles with non-overlapping gear and abilities, making leveling and gearing choices feel intentional rather than option-paralyzed.
- **Focused gameplay identity**: Gear restrictions (armor types, weapon proficiencies) naturally differentiate classes; a tight roster reinforces this identity rather than diluting it across many options.

Classic WoW manages 9 classes; most ports and variants reduce to 4–6 core roles (tank, healer, physical DPS, magic DPS, ranged DPS, utility).

### Classic's Implicit Limit: Race-Class Pairings

Classic itself limited choice via race-class restrictions. Each race offered only 4–6 playable classes, usually a mix of tank, melee DPS, ranged DPS, and healer roles. However, each individual class could fill 1–4 of those roles depending on talent/spec choices, meaning the role matrix wasn't a strict grid.

This suggests a design spectrum:
- **Extreme simplicity**: One classless character that can specialize into any role (tank → ranged → healer as playstyle shifts).
- **Moderate**: A few classes (4–6) with limited role overlap, each capable of 1–2 primary roles.
- **Full stratification**: Many classes (8–12), each specialized for specific roles with minimal flexibility.

You can build a port anywhere on this spectrum and scale it upward if design space opens up.

## Gear & Armor Class Restrictions

Classic restricts both armor types and weapon types by class:

**Armor types**: Cloth (fragile, caster-preferred), leather (rogue/shaman at start), mail (hunter/shaman at higher levels—hunters acquired mail partway through), plate (warrior/paladin). Low-level characters have access to fewer armor slots; a port might further reduce slot count for early-game simplicity.

**Weapon proficiencies**: Characters must train proficiency with a given weapon type by using it repeatedly. A unpracticed warrior swinging a mace has reduced damage output and miss chance until proficiency increases. This creates a meaningful early-game constraint—players cannot simply switch weapons and expect to be equally effective.

**Why this matters**: Gear restrictions anchor class identity and combat readiness. They create progression gates (can't equip heavy plate until level X; can't wield swords without training) that naturally encourage specialization and make loot drops feel rewarding.

### When NOT to Over-Restrict Gear

Tight armor/weapon restrictions can create friction early in the game:
- **Low-level loot scarcity**: If armor is heavily class-gated, a leather-only rogue may find few upgrades while a plate warrior swims in equipment. This creates perceived unfairness in progression.
- **Weapon training bottleneck**: Requiring proficiency training delays combat effectiveness. Players new to a weapon may feel underpowered until they train up, which can feel punishing rather than rewarding if the training cost is too high.
- **Playstyle experimentation tax**: Strict restrictions discourage trying new loadouts or roles mid-game. If a warrior wants to dual-wield daggers for fun, forced proficiency training makes it prohibitively expensive.

**Design consideration**: You might relax restrictions for:
- Early levels (first 10–15): Fewer gear options anyway; hard restrictions add busywork rather than choice.
- Low-impact slots (bracers, belt, off-hand): Fewer balance implications if a caster wears a plate bracer.
- Hybrid classes: Classes spanning multiple roles benefit from flexible armor access.

The restriction creates identity when it *solves a problem* (tank needs heavy armor to survive), not when it *creates one* (player can't use the only upgrade they found).

### Sidebar: Armor Appearance

Like racial appearance, armor appearance can make or break player interest in the game. It's important to both:
- Make armor that looks appealing to the user, drawing from the user's tone prompt.
- Allow that armor to be used by the characters who its appeal is central to.
Making armor that does not appeal to the user or where appealing armor cannot be used by the characters whose appeal it contributes to foils the purpose of having armor visually render.

## Leveling Progression: Grinding & XP Scaling

Classic assumes **grinding (killing monsters) as the primary leveling mechanism**, with quests secondary. This shapes pacing and content design fundamentally:

- **Monster experience decays**: Monsters too low-level relative to the player stop giving meaningful XP; players are naturally pushed toward higher-level content as they progress.
- **Exponential time investment**: Early levels are fast (Level 1→2 might take 20 min); later levels take exponentially longer. Players at level 50+ may grind for hours between level-ups, reinforcing the grind-heavy feel.
- **High-level content is gatekept**: Only high-level monsters (or quests) provide XP approximating what high-level players need. This funnels players into appropriate zones and encounters.

### XP Formula

Classic's original XP requirement per level:
- Level 1 → 400 XP
- Level 2 → 400 + 500 = 900 XP cumulative
- Level 3 → 900 + 600 = 1500 XP cumulative
- (Each level adds 100 more XP than the previous step)

Level 1 monsters gave ~50 XP (as of 2010 patch). Dividing the formula by 50 yields cleaner numbers:
- Level 1 → 8 XP
- Level 2 → 18 XP
- Level 3 → 30 XP

(Original numbers on [warcraft.wiki.gg/wiki/Experience_to_level](https://warcraft.wiki.gg/wiki/Experience_to_level) are less tidy and were smoothed over time.)

**Why this matters**: The grind-heavy model and exponential scaling make leveling feel like a long-term commitment, encouraging playstyle specialization and creating natural breakpoints where players refresh their gear.

## Spell Mechanics & Ability Design

AI training: spell structure, casting rules, cost systems, effects, and how spells scale over time.

### Spell Effects: Categories and Behavior

Spells fall into several distinct effect categories. Understanding each helps builders reason about ability costs and balance:

**Damage and Healing**
- Deal or restore health
- May scale with attributes (Intellect for spell damage, Spirit for healing)
- Can be instant or cast-time dependent
- Higher-damage spells typically require longer cast times or larger resource costs

**Buffs (temporary attribute adjustments)**
- Increase a target's attributes or capabilities for a fixed duration (usually seconds to minutes)
- Stack additively: two buffs granting +2 Strength each grant +4 total
- Typically small-scale but long-term within a single encounter
- End when duration expires or are manually dispelled

**Debuffs (temporary reductions or status effects)**
- Reduce a target's stats or apply crowd control (stun, root, silence, slow, etc.)
- Mechanics vary by type (stun blocks all actions; root blocks movement but not casting; silence blocks spells but not attacks)
- Player typically wants to remove these; enemies apply them defensively
- Duration and intensity should reflect the spell's other costs

**Item Creation**
- Some spells create consumables or equipment that didn't already exist in the game
- Saves player gold and inventory space vs. vendor purchases
- Often restricted by profession or class (e.g., only enchanters or alchemists can create specific items)
- Reagent cost is the primary balance lever

**Reagent Consumption**
- Ranged weapons and some spells consume consumable resources (arrows, reagent components, runes, etc.)
- Acts as a soft resource sink, encouraging players to manage inventory and plan longer engagements
- Runecasters and certain buff spells (especially support abilities) commonly consume reagents
- Reagent cost scales with spell rank/power

### Resources: Mana and Class-Specific Alternatives

**Mana** is the primary resource for casters:
- Regenerates slowly in and out of combat (in Classic, Spirit drives mana regen out of combat; out-of-combat regen is significantly faster)
- Depletes on spell casts
- Higher-power spells cost more mana
- Mana pool scales with Intellect
- Running out of mana is a meaningful limitation; players must manage it or wait for regen

**Class-specific resources** vary widely and are often class-defining:
- Warrior Rage: starts at 0, builds up on taking damage or dealing damage, decays slowly out of combat
- Rogue Energy: fast natural regen, but limited pool (similar to Mana but regenerates faster and at higher frequency)
- Paladin Holy Power (if included): builds from specific spells, spent on finishing moves
- Druid Combo Points (if included): build from basic attacks, spent on finishing moves

Class-specific resources typically are **not** directly supported by gear (e.g., gear doesn't grant +Rage or +Energy directly), though talents and certain effects may affect their generation. These resources are often the main constraint on a class's damage output or role flexibility.

**Design consideration**: Out-of-combat healing and regen speed should differ from in-combat. Classic typically allowed eating (healing) out of combat but blocked it during active combat. If your port includes this, it creates natural pacing between encounters.

### Casting Mechanics

**Cast Time**
- Most damaging spells require a cast time of 1–3 seconds (faster spells are weaker or more costly)
- Instant-cast spells are rare and typically have longer cooldowns or higher costs
- Cast time is a primary balance lever: longer casts mean more vulnerability and opportunity cost
- Healing spells often have longer cast times than damage spells of equivalent power

**Movement While Casting**
- In Classic, very few spells allow movement during cast time
- Most casts are interrupted or cancelled if the caster moves
- This is intentional: it forces positioning choices and makes kiting (ranged classes moving while attacking) riskier
- Decide at the class level whether spell-while-moving is allowed; if permitted for specific spells, note it explicitly

**Interrupts and Silences**
- **Interrupt** (or "kick"): stops a target's current spell cast, typically causing the spell to fail and the caster to lose the resource they spent
- **Silence**: blocks all spell casting for a duration, but doesn't interrupt current casts in progress
- Both are core tactical tools for combat
- Interrupt windows are usually tight (melee-range attacks or specific abilities only)
- Silence duration typically 2–5 seconds

**Channeled Abilities**
- Some spells channel (continue casting for several seconds) rather than casting once
- Channeled spells can be interrupted by damage or effects; some require active channeling concentration to maintain
- In Classic, this is less common than in Retail; most Classic abilities are instant-cast or fixed-duration casts that complete once
- If included, channeled spells should have clear visual/audio feedback so players know they're active

**Global Cooldown (GCD)**
- Classic did not have a formal global cooldown; abilities could chain instantly
- Many player-made ports add a small GCD (0.5–1.5 seconds) for pacing and to reduce button-mashing feel
- If included, decide whether all abilities share one GCD or if certain instant-cast spells bypass it
- This is a user/project-specific design choice; document it in your port's spec once decided

### Spell Ranks and Scaling

**Spell Ranks**
- Most spells have multiple ranks tied to max level (e.g., level-60 game = ~10 ranks; level-80 game = ~16 ranks)
- Higher ranks deal more damage, heal more, or grant larger buffs
- Higher ranks require higher level to train
- Each rank requires separate training from a trainer (costs money and sometimes components)
- Players can knowingly cast lower ranks if it suits their strategy (e.g., lower mana cost for the same effect at reduced power)
- **Spacing**: Rank availability typically gates out every 6 levels (level 1, 6, 12, 18, 24, 30, 36, 42, 48, 54, 60 for a level-60 game); scale the interval based on max level so that the last rank is trainable at or near max level

**Why ranks matter for progression**: As monsters scale in toughness with player level, players need higher-rank spells to keep pace. Leveling a character involves not just learning new spells, but constantly re-training higher ranks of existing spells. This is a major gold sink and quest/vendor engagement point.

**Cost Scaling by Rank**
- Mana cost typically increases with spell rank (higher power = higher cost)
- This means higher-level characters can't spam high-rank spells endlessly; they must manage mana carefully
- Many players deliberately use lower ranks in extended fights to preserve mana
- Reagent costs similarly scale with rank

**Level Gates**
- You must reach a minimum level to train a spell or rank
- Typical gates: new spell at levels 6, 12, 18, 24, etc. (every 6 levels)
- New ranks of existing spells come at similar intervals
- This creates natural breakpoints where players visit trainers and refresh their loadouts

### Status Effects & Crowd Control

Crowd control effects change how the target behaves:

**Stun**: Target cannot act (move, cast, attack) for the duration. Powerful but short-duration (1–3 seconds typical). Stuns break on damage in some systems.

**Root**: Target cannot move but can still cast and attack. Lasts longer than stuns (up to 10+ seconds). Broken by certain damage types or movement-related buffs.

**Silence**: Target cannot cast spells but can move and melee attack. Duration typically 2–5 seconds. Useful against casters.

**Slow**: Reduces target's movement speed. Can stack with itself (multiple slows = cumulative reduction). Often tied to specific debuffs (e.g., frost spells apply slow).

**Displacement**: Forces target to move (knockback, teleport, etc.). Rare in Classic but worth knowing. Can trigger fall damage or reposition an enemy away from allies.

Each effect should have clear counterplay: removable buffs, duration limits, or conditional breaks. Avoid applying crowd control effects that the target has no way to remove or prevent entirely.

### Ability Progression & Training

- **Trainable abilities**: Purchased from NPCs (trainers) at the cost of gold and, sometimes, reagents
- **Quest-reward abilities**: Earned through questlines; often unique to a class
- **Talent tree abilities**: Unlocked by spending talent points (deeper class customization; typically Retail and later, but may be in your port)

All trainable spells have level gates. Players cannot train a spell above their current level; they must level up to access it. This prevents over-powered early progression and creates natural encounter gates.

### Ability Cost Structure: The Design Pattern

The relationship between power and cost is fundamental to Classic balance:

> The more powerful, ranged, or conclusive a spell is, the more it should cost in terms of:
> - Cast time (longer casts = more vulnerability)
> - Mana or resource (higher sustained cost = limits spam)
> - Cooldown (longer waits between uses)
> - Reagent consumption (direct resource investment)
> - All of the above

This pattern ensures that powerful spells are not free. A player choosing to cast a high-damage spell is sacrificing positioning safety, mana availability, or time. Weaker, faster, or cheaper spells should feel like reasonable alternatives for specific situations, not trap picks.

**Design consideration**: If a spell feels too strong relative to its cost, adding any of the above (slightly longer cast time, higher mana, small cooldown) typically fixes it without needing to nerf its raw power. Conversely, a spell that feels weak can be buffed by reducing cost before increasing raw effect.

### Integrating Spell Effects into Ability Design

When designing a spell, describe it using this framework:

1. **Effect type** (damage, heal, buff, debuff, etc.)
2. **Resource cost** (mana, Rage, combo points, etc.)
3. **Casting mechanic** (instant, cast time, channeled; whether it allows movement)
4. **Rank/scaling** (if any; how it scales with attributes or spell power)
5. **Duration** (for buffs/debuffs) or **cooldown** (for high-impact abilities)
6. **Availability** (level gate, talent requirement, cooldown between uses)
7. **Any special interactions** (interrupts it, items it consumes, status effects it applies, dispellable vs. permanent)

This structure ensures consistency with Classic mechanics and makes abilities easier for builders to reason about and balance.