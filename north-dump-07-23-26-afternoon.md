Hey North. I'd like you to help me outline the language stack for an application called The Real Classic, reusing as much as possible from previous applications while also being as simple as possible language-wise (not using too many languages).

# The Real Classic: Spec

## What is this?
It's like the Club Penguin Builder (https://github.com/NoahKastin/club-penguin-builder), but for World of Warcraft Classic, which everyone argues over the "real", "authentic" feel for, causing so many spinoffs that they're basically their own genre that has nothing to do with Microsoft's copyrighted IP, much like Club Penguin. It shouldn't be too hard to get an AI to build this given the precedent in other devs' knockoffs and given that the main additional coding layer beyond the Club Penguin Builder is adding real-time rendered NPCs (mostly for combat, technically also for quests). The **tagline** is: ***You know the Real Classic. Why play someone else's?***

## Branding
The favicon for The Real Classic is an **R in a C**. This is **inspired** by World of Warcraft's iconic **W in an O *but is not intended to be so similar as to infringe on copyright***; it's **just inspiration**, a hat-tip if you will.

## Builder Interface
To create or modify ("patch") a game ("Realm") of The Real Classic, players are presented with a builder interface much like the Club Penguin Builder's Edit interface for Club Penguins (or like https://github.com/NoahKastin/cry-with-me).
Instead of focusing on how many rooms there are and what items exist within them, there's instead a set of prompt boxes to deploy an AI to patch the game, as follows:
- **Name:** A text field specifying the Realm's name (appears when creating or modifying a Realm). This name is shown in the Realm picker.
- **New zone?:** This box has to be ticked on when creating a Realm. Creating a new zone shapes the feel of Realm creation; the prompt is now what's in the starting zone for the first characters, not what's in the whole game, so future patches can add more progression (which often, but does not have to, include a new zone per patch) or new starting experiences for alts or new players. A follow-up prompt asks how far the patch's changes extend — from just part of the zone, to the whole zone, up to the entire existing world (e.g., a new monster level range might be scoped to a single zone or apply everywhere).
- **Tone:** A catch-all box that impacts everything else, such as artstyle/zone look, story feel, and difficulty. This also defines player-facing mechanics like death systems and resurrection rules. (The AI model interprets this and spits back a suggested response, as with all else here. See https://github.com/NoahKastin/cry-with-me/docs/MODEL-LOG.md for how this can go right or wrong.)
- **Attributes:** Many other AI outputs—including race, class, and gear—rely on an authoritative, canonical set of attributes. The AI will be trained on typical terminology used in attribute definitions. See https://github.com/NoahKastin/cry-with-me/docs/FOUNDING.md for how this was previously done elsewhere.
- **Races:** Number of races added in the patch, with a prompt box for each defining its (probably stock fantasy) appearance and any starting statistics endowed by being a member of that race. The AI should be trained to avoid copyrighted language, such as using "minotaur" instead of "tauren". Heavily suggested to be only 1 race for creating a Realm in order to make the first zone be a standard racial starting zone for authenticity and initial party cohesion. **Note on starting zones:** New races often get new starting zones, but not always; design choice depends on Realm scope. High-level zones should not be used as starting zones.
- **Classes:** Number of classes added in the patch ("1" for classless), number of levels added (heavily suggested to be 10 or fewer per patch), when/if Talents are unlocked, anything class-restricted (armor, weapons, resource types, starting attributes, etc.), and any specifics on individual class flavor/abilities/ranks/tree structures. (The AI would be trained on typical World of Warcraft ability effects for grounding, but prepared to accept atypical ones according to the user's whim — and the §Races rule applies here too: ground on mechanical patterns, never reproduce Blizzard proper nouns or lore names. See https://github.com/NoahKastin/cry-with-me/docs/MODEL-LOG.md again.)
- **Boss mechanics:** If there are any bosses in the zone, they'll likely have unconventional, perhaps grueling boss mechanics defining what the user sees as the "authentic" experience.
- **Story:** The overarching lore of this patch, which can tie into previous Story prompts.
- **Factions/reputation:** Suggested not to be used for Realm creation, but helpful to have eventually for PvP and long-term progression.
- **Professions:** A yes/no toggle, heavily suggested to be turned to "no" for Realm creation. If toggled to "yes", there's then a box for what the Professions make to facilitate "true" long-term progression.

Finishing with a patch publishes the Realm to a Realm picker like World of Warcraft's own.

## Default Game Systems

The following systems are assumed to exist in The Real Classic by default and need not be toggled or prompted for during Realm creation:

### Hearthstones (to be renamed; "Hearthstone" is a registered, actively-used trademark)
All characters can bind to an inn or home location (the "Hearthstone" bind point) and teleport back to it after a cooldown (30 minutes by default, out of combat). This is a convenience system allowing characters to return to safe towns or bases without requiring a long run, and serves as a soft reset point for raid/dungeon runs. Hearthstones may be configured per-Realm (cooldown, bind points, whether they can be cast in combat, etc.), but the basic mechanic is assumed.

### Mail and Trade Systems
Characters can mail items and currency to other characters on the same Realm (with a small delivery delay). Trade also allows direct peer-to-peer item and currency exchange via an interface where both players confirm. These systems facilitate gearing, economy, and inter-character progression without requiring the same player to run items across zones manually. Both are assumed to exist unless explicitly disabled for a Realm.

### Death Mechanics
Death in The Real Classic is defined by the Realm's Tone box. Players should specify resurrection mechanics, drawing from these historical designs (see [WoW evolution guide](https://warcraft.wiki.gg/wiki/World_of_Warcraft_evolution_guide)):

- **Bind stone** — Blizzard's original concept: characters bind to a stone/location (one at a time) and automatically resurrect there on death. No corpse run required; instant resurrection.
- **Altar resurrection** — A Warcraft legacy feature originally planned for WoW (altars of kings appeared in alpha): characters bind to a specific altar and resurrect there instantly on death. Was removed before WoW beta, but remains conceptually close to bind stones and represents an earlier design pass.
- **Graveyard with corpse run** — What Classic actually shipped with: characters respawn at the nearest graveyard, then must run to their corpse to resurrect (with durability penalties and resurrection sickness). Encourages risky resurrection-sickness shortcuts vs. corpse runs.
- **Emerald Dream (to be renamed; "Emerald Dream" is Microsoft IP)** — Alternative design: death sends characters to the Emerald Dream realm where they can quest to earn their resurrection instead of instant revival.
- **Hardcore permadeath** — Later variant: death is permanent; character is deleted.

Players should also specify:
- **Durability penalties** — Do armor/weapons take durability damage on death? How severe?
- **Resurrection sickness** — Debuff duration and intensity for rapid consecutive deaths to discourage corpse-running abuse.
- **Corpse visibility** — Can other players loot a corpse's items, or is the corpse private?

Classic's original design (graveyard + corpse run) created meaningful choices between risky instant resurrection at the graveyard vs. a long run back to the corpse. Variant Realms may choose simpler (bind stones, permadeath) or alternative (Emerald Dream) systems depending on intended feel.

## Design Milestones: Key Patches That Shaped the Game

While Classic WoW lasted from 2004-2006, several patches in later expansions introduced features that fundamentally shifted the game's design, often without explicit fanfare. Understanding these can inform Realm design choices:

- **Patch 2.3.0 (The Burning Crusade era)** — Guild banking (shared inventory storage for guilds), leveling speed adjustments, and visible enemy debuffs on nameplates. Guild banking especially changed how players managed inventory and coordinated as a unit.
- **Patch 3.0.2 (Wrath of the Lich King pre-patch)** — Talent system overhaul/squish (abilities reorganized and consolidated), achievements (optional progression goals), and barber shops (cosmetic character customization). These made character progression feel less rigid and more personalized.

These patches often flew under the radar as "QoL improvements" but were actually game-design inflection points—they made the game feel less grindy, more social, and more customizable. When designing a Realm, consider whether you want the pre-2.3 experience, or whether features like guild banking and achievement tracking should be included from the start.

## Subscriptions
Like World of Warcraft before it, all this real-time server usage would cost something for the host (namely me via fly.io), not to mention any (hopefully minor) LLM costs for Patching (including any heavy art generation). Fortunately, there's already a precedented payment model: Subscriptions for hosting a server (probably at different tiers for different numbers of concurrent players, e.g. 5-man, 10-man, 20-man, 40-man, etc.). Server hosts could then share costs or pass on subscriptions to players. See https://github.com/NoahKastin/cry-with-me/docs/ECONOMY.md and https://github.com/NoahKastin/cry-with-me/docs/MODEL-EVAL.md for previous ideas on this topic.

## Source Repos (Port Map)

The Real Classic is assembled from Noah's existing projects. Standing directive (2026-07-13): **base the generative AI on cry-with-me — not just its docs, its implementation.**

- **JS/Vite/Express/fly.io stack:** `club-penguin-builder` — the platform skeleton: accounts, Socket.IO multiplayer presence, SQLite persistence, Stripe payments, Phaser+React client, fly.io deploy with auto-stop. Feature-complete and deployed.
- **JS/Vite/Express/fly.io stack:** `cry-with-me` — the AI layer: `server/build.js`/`modify.js`/`rebuild.js` generation verbs, `shared/types.js` ENTRY_TYPES taxonomy format + `shared/schema.js` structured outputs, `server/providers/` model abstraction, `server/meter.js` token/$ metering, and retrieval grounding (retrieval-only won the A/B; the curated pack is opt-in). Author the Realm patch schema as a new ENTRY_TYPES vocabulary in this format so the whole pipeline carries over.
- **GDScript:** `take-a-stab` (Godot 4) — shipped real-time melee combat, with aggro radius, pathing, respawn, and XP design: enemy chase/attack loop (`zombie.gd` `_physics_process`/`_bite`/`die`), hit geometry, difficulty ramp.

**Taxonomy source of truth:** the docs in `taxonomy/` are canonical — statistics + entry types, this project's analogue of the Master 4E source that cry-with-me's `types.js` encoded rather than invented. ENTRY_TYPES gets encoded *from* those docs, and the same docs feed the runtime retrieval corpus (cry-with-me's `corpus/` + `retrieval.js` pattern). Realm Zero is a test fixture (generate-then-freeze; hand-write as fallback), not the taxonomy-defining act.

**Original planned build order (may be deprecated):** scaffold + port cry-with-me plumbing → ENTRY_TYPES from the taxonomy docs → taxonomy docs into the corpus → generate Realm Zero, freeze as fixture → JS combat sim from the design ports → wire the generation verbs.

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

## How This Feeds the AI

The AI generation layer (cry-with-me's `build.js`, `modify.js`, `rebuild.js` verbs) uses this taxonomy as:
1. Grounding for structured outputs (typed entries matching the patterns here)
2. Training data for terminology and style (what language to use for attributes, abilities, lore, etc.)
3. A constraint model for generation (what combinations are valid, what ranges are reasonable)

Realm patches are generated as new ENTRY_TYPES entries conforming to these definitions, then frozen into the Realm fixture.

# Attributes

AI training: canonical attribute definitions, terminology, and simplification guidance.

Attributes here are **reference material and precedent**, not a mandatory schema — the Attributes prompt box lets a Realm creator define their own canonical set from scratch. This document exists so the AI has a full menu of familiar terms to draw from, deliberately riff on, or ignore. Nothing below has to be used, and the lists aren't exhaustive.

**Simplification is the common case, not the exception.** Realms typically have far fewer races/classes than WoW itself (spec.md suggests as few as 1 race and a handful of classes for Realm creation), so most Realms will want *fewer* attributes than either list below, not more. Common patterns: use fewer primary stats than either historical list, skip secondary/tertiary stats entirely until the class roster is large enough to justify differentiating them, and introduce complexity gradually across patches rather than all at once. A reasonable total-attribute range, unless Tone specifies otherwise, is **3-8**, with 5-6 as a natural middle: 5 matches WoW Classic's own primary-stat count, 6 matches classic D&D's ability-score count (itself often simplified down to 3 in derivative systems), and 8 approximates the number of distinct values a typical WoW retail player actually tracks in practice — Stamina, Armor, weapon damage, whichever single primary stat their class cares about, and the 4 secondary stats — even though the game formally itemizes differently. Beyond 8 starts trending toward stats that matter only to specific builds (e.g. Block, relevant only to shield-users) — the same pattern already noted in Version History: narrow, situational stats don't have staying power.

**New attributes are expected too.** Tone or Classes prompts may call for attributes with no Classic precedent at all (e.g. a resource like "Corruption," or a flavor stat like "Luck"). Treat the lists below as vocabulary and precedent, not a ceiling.

## Classic-Era Attributes (pre-6.0 style)

The sprawling, granular era — five primary stats and a long tail of secondary combat ratings. Most "authentic Classic" recreations draw primarily from this list.

**Primary:**
- **Strength** — melee attack power; parry chance for plate wearers
- **Agility** — ranged/melee attack power for some classes; critical strike chance; dodge chance
- **Stamina** — health pool; scales harder at higher values
- **Intellect** — spell power; spell critical strike chance
- **Spirit** — health regeneration for every class, plus mana regeneration (especially out of combat, and for healers); spell hit for a few caster specs. Health regen from Spirit was removed in Patch 4.0.1 (Cataclysm) — outside the Classic era — so within Classic proper, Spirit is universally relevant, not just to casters/healers.

**Secondary** (extensive, and only partly consolidated even within this era — see Spell Damage/Healing and Resistance below):
- **Attack Power** — derived from Strength/Agility; drives weapon damage
- **Ranged Attack Power** — derived mostly from Agility; drives bow/gun/crossbow damage
- **Attack Speed / Haste** — time between attacks; Haste also reduces cast time
- **Hit Rating** — accuracy; melee/ranged and spell calculated separately
- **Critical Strike Rating** — chance for bonus-damage hits, physical and spell
- **Expertise** — reduces enemy dodge/parry chance; also aids spell hit
- **Spell Damage** — damage scaling for damaging spells only, sometimes itemized further per school (Fire/Frost/Nature/Shadow/Arcane/Holy); merged with Healing into a unified **Spell Power** stat in Patch 3.0.2
- **Healing** — scaling for healing spells; itemized entirely separately from Spell Damage until the same Patch 3.0.2 merge
- **Spell Haste / Spell Hit / Spell Critical Strike** — spell-specific analogs of the above
- **Armor** — reduces physical damage taken
- **Dodge / Parry / Block** — avoidance mechanics; Parry and Block require a weapon or shield
- **Resistance** — reduces magical damage taken, itemized per school: Fire, Frost, Nature, Shadow, and Arcane (Holy Resistance existed only briefly pre-release before folding into Arcane). The defensive counterpart to Spell Damage/Healing above — specific encounters were famous for demanding it (Ragnaros and Fire Resistance gear; Sapphiron and Frost Resistance gear), making resistance itemization its own gearing minigame. Removed from player itemization in Mists of Pandaria (Patch 5.0.4).
- **Mastery** — unique effect per class/spec (a later addition — see Version History below)
- **PvP Power / PvP Resilience** — separate scaling for player-vs-player damage and mitigation

**Retired outright in later eras** (present in Classic, worth knowing existed, but folded away): **Defense**, **Block Value**, **Armor Penetration**, **Mana Regen (MP5)**, and **Spell Power on armor**.

## Streamlined Attributes (modern era)

Later expansions consolidated the above into a tighter set. Worth keeping as an alternate reference point — a request for something "simpler but still authentic-feeling" is often unconsciously asking for something closer to this shape rather than the full Classic list.

**Primary:** Stamina, Strength, Agility, Intellect

**Secondary:** Critical Strike, Haste, Mastery, Versatility (damage/healing up and damage taken down — replaced several narrower stats)

**Tertiary** (rarer, found on a minority of gear): Avoidance (reduces AoE damage taken), Leech (converts damage/healing dealt into self-healing), Speed (movement), Indestructible (gear ignores durability loss)

**Derived combat stats** (not itemized directly — calculated from the above): weapon damage and attack speed (physical), spell power and cast speed (magic), armor/dodge/parry/block (defense)

## Version History: Consolidation Over Time

The throughline across every version change is consolidation — narrow, situational stats kept getting merged or cut into broader ones:
- **Patch 0.9** (pre-release) replaced Holy Resistance with Arcane Resistance, settling on the five-school resistance split (Fire/Frost/Nature/Shadow/Arcane) that lasted through Classic
- **Patch 2.0.1** introduced Resilience and the combat rating system (ratings convert via level-scaled tables rather than flat percentages)
- **Patch 3.0.2** merged the separate Spell Damage and Healing stats into a single itemized Spell Power
- **Patch 4.0.1** added Mastery, reworked Resilience into flat damage reduction, steepened Stamina's scaling, and removed Spirit's health-regeneration function — the point where Spirit stopped mattering to non-casters
- **Patch 4.2.0** removed Dodge-from-Agility for some plate classes and increased Parry-from-Strength
- **Patch 5.0.4** (Mists) removed Resistance from player itemization entirely, ending the era of encounter-specific resistance gearing
- **Patch 6.0.2** (Warlords) removed Hit and Expertise entirely, and dropped Dodge/Parry itemization
- **Patch 7.0.3** (Legion) removed Spirit and Bonus Armor, retired the short-lived Multistrike, and introduced Versatility in its place
- **Patch 8.3.0** (Battle for Azeroth) removed PvP Power and PvP Resilience from itemization

For a Realm creator, this is a useful signal: **if an attribute only matters to one class or one edge case, that's usually the first kind of stat real Classic eventually cut.** Attributes that scale broadly (a damage stat, a survivability stat, a pacing stat) have more staying power than narrow situational ones. It also means the "Classic-era" list above is itself a snapshot mid-consolidation — Spirit's health regen and the offense/defense spell-stat split were already on their way out before Classic's own successor expansions shipped.

## How Attributes Interrelate

A consistent pattern across both eras: a small number of **primary** stats (usually class-defining — a Strength-class vs. an Intellect-class) feed a larger number of **derived/secondary** stats (Attack Power, Spell Power, Health), which in turn determine actual combat outcomes (damage per turn, survivability). When defining a new attribute, decide early which tier it occupies: a primary stat should differentiate races/classes, while a secondary stat is closer to itemization — something found on gear, not granted by race or class alone.

# Boss Mechanics & Challenge Types

Boss mechanics in The Real Classic are not individual prescriptive encounters, but rather **patterns and building blocks** that combine to create unique challenges. This document defines those patterns so encounters can be generated systematically while remaining fresh and varied.

## Challenge Types

Each challenge type represents a distinct mechanic pattern. Encounters may blend types or feature one as the primary hook.

### Combat
Pure hostile engagement. Enemies attack; player must defeat them before time/resources run out.
- Core mechanic: damage output vs. enemy HP
- Scaling: enemy count, enemy HP, enemy damage, enemy variety
- Common combinations: multiple enemies of different behaviors (aggressive + healer), ranged threats, summoner spawning adds

### Survival
Extended pressure—enemies attack continuously, resources deplete, player must sustain.
- Core mechanic: healing output must match incoming damage over many turns
- Scaling: enemy count, wave timing, hazard presence
- Common combinations: damage threats + environmental hazards (persistent damage zones), adds that multiply (summoner)

### Obstacle
Navigation challenge—barriers block the path, player must destroy or navigate around them.
- Core mechanic: clearing/bypassing destructible or impassable terrain
- Scaling: barrier HP/destructibility, path complexity, distance
- Constraints: player must have damage capability or mobility to proceed

### Puzzle
Knowledge/mechanism challenge—activate or interact with non-hostile game state.
- Core mechanic: finding/activating triggers, dispelling illusions/darkness, revealing hidden paths
- Scaling: number of triggers, darkness radius, visual complexity
- Constraints: player must have illumination or information-gathering capability

### Stealth
Avoidance challenge—powerful guardians are too strong to fight; player must bypass them.
- Core mechanic: reach goal without triggering guards' aggression
- Scaling: guard count, guard strength, available paths (crowd control can create/widen paths)
- Constraints: requires either crowd control, mobility, or ranged distance to circumvent

### Rescue
Protection challenge—defend/aid an NPC while under pressure.
- Core mechanic: heal injured ally or reach trapped ally while managing hostile interference
- Scaling: NPC health deficit, enemy interference, distance-to-NPC
- Constraints: player must have healing (for injured) or damage capability (for enemy interference)

### Timed
Race against clock—reach multiple targets before deadline.
- Core mechanic: movement efficiency under time pressure
- Scaling: target count, target spread, time budget
- Constraints: player must have range or mobility to reach spread targets within time

## Enemy Behaviors

Enemies exhibit distinct behavioral patterns that define how they engage:

### Aggressive
Charges player, deals damage in melee. Predictable and direct.
- Positioning: moves toward player
- Threat range: 1 hex (melee)
- Usage: frontline threat, basic opposition

### Defensive
Holds position, only attacks if player approaches. Protects territory/allies.
- Positioning: maintains stance
- Threat range: 1 hex (melee if provoked)
- Usage: guard patterns, patrol enemies, "too strong to rush" stealth targets

### Ranged
Maintains distance, attacks from afar. Threatens from safe position.
- Positioning: moves to max attack distance, maintains range
- Threat range: variable (typically 2+ hex)
- Usage: adds pressure to overcome range, forces player range-matching decision

### Healer
Restores ally health. Support role, low damage.
- Positioning: maintains distance from player
- Actions: heals nearby allies instead of attacking
- Threat range: 1 hex (melee if forced)
- Usage: extends fight duration, teaches resource prioritization (kill healer first vs. tank damage)

### Summoner
Spawns additional enemies each turn. Escalates threat.
- Positioning: maintains distance, spawns minions nearby
- Actions: generates new enemies
- Threat range: spawning radius (typically 2-3 hex)
- Usage: waves/adds mechanic, tests AoE and crowd control

## Challenge Elements

Atomic building blocks that populate an encounter:

### Enemy
- Properties: hp, damage per turn, behavior (aggressive/defensive/ranged/healer/summoner), level/rank (see Enemy Rank & Level Progression)
- Interaction: player must reduce HP to 0
- Grounding: varied combinations define encounter difficulty

### Invisible Enemy
- Properties: hp, damage, initially hidden from sight
- Interaction: player must detect (requires illumination or information capability) before engagement
- Grounding: information-denial challenge, teaches scouting

### Hazard
- Properties: damage per turn, radius (affects hex grid area), duration
- Interaction: player takes damage each turn in affected area; may be avoidable
- Grounding: environmental pressure, teaches positioning/avoidance

### Darkness
- Properties: radius (2-3 hex typical), position
- Interaction: blocks line of sight; player cannot see through it
- Interaction (with illumination): player can dispel it
- Grounding: vision denial, information gate, puzzle element

### Obstacle
- Properties: blocking (yes/no), destructible (yes/no), hp (if destructible)
- Interaction: if blocking, path is impassable; if destructible, player can remove it
- Grounding: forces path decision (destroy vs. navigate around if possible)

### Target
- Properties: required (yes/no), position
- Interaction: player must reach/interact with it (typically by moving to it)
- Grounding: objective marker for obstacles, puzzles, timed challenges

### NPC
- Properties: needs healing (yes/no), needs rescue (yes/no), position, hp (if healable)
- Interaction: if healable, player must restore HP to max; if trapped, player must reach and "rescue"
- Grounding: ally protection mechanic, teaches split-focus (protect while fighting)

### Trigger
- Properties: activation condition, position
- Interaction: player must interact (typically by proximity or specific action) to activate
- Grounding: puzzle mechanism, gate, mechanic enabler

## Enemy Rank & Level Progression

Enemy Behaviors (above) describe how an enemy fights; **Rank** describes how strong it is relative to its zone. Rank is a second, independent axis layered on the Enemy element — any behavior can appear at any rank.

### Level Curve Within a Zone
Monster levels climb across a zone as the player progresses through it, from a floor near the zone's minimum level up to its maximum:
- **Floor:** one level below the zone's minimum, clamped so it never drops below 1. Level 1 is the absolute floor of the system — there is no level 0. (A starting zone spanning levels 1-5 has a floor of 1, not 0, since 1 minus 1 gets clamped back up.)
- **Ceiling:** the zone's stated maximum level, reached by monsters near the end of the zone's progression.

### Rank Tiers (Beyond Zone Maximum)
Beyond a zone's ceiling, three further levels are reserved for progressively rarer, more dangerous monsters:
- **+1 — Rare/Powerful:** a notable step up; still fought solo or in small numbers.
- **+2 — Extremely Powerful:** a serious difficulty spike; often the anchor of a zone's own finale.
- **+3 — Boss (major questline completion):** the scariest tier, and genuinely rare — fewer than one per zone on average. Reserved for the climactic encounter of a **major questline** (the kind running into the double digits of quests, often spanning multiple zones per story.md's Zone & Questline Shape) — not tied to any single zone's own finale. Pegged to the level of whichever zone hosts that climactic encounter, +3; most zones resolve their own story at +1 or +2.

No separate Elite/Rare *designation* sits on top of rank. In practice those tags only ever showed up on monsters already above a zone's normal level range anyway, so the rank tier itself already carries that signal — a separate tag would be redundant complexity.

### Zone Finales
An individual zone's own climax is commonly one of:
- A single powerful monster (+1 or +2)
- A **boss gauntlet** — a sequence of weaker bosses fought back to back
- A **multi-phase fight** — one boss, multiple mechanical phases within a single encounter

The rare +3 tier is reserved for the climactic encounter of a major questline, which (per story.md's Zone & Questline Shape) often spans multiple zones. Earlier zones/quests in that arc end on a lesser beat (per the tiers above) that hands off rather than fully resolving; the +3 encounter itself lives in whichever zone the questline is heading toward at its conclusion.

### Rank Does Not Gate Challenge/Quest Types
Any Challenge Type or Quest Type can involve an enemy of any rank — a Rescue, Stealth, or Timed challenge works the same regardless of the rank of the enemy involved. Rank only affects the enemy's underlying hp/damage.

## Difficulty Scaling

Encounters scale by **composition** rather than stat inflation:

### By Player Capability
- **Has damage:** enemies can be spawned with proportional HP; obstacles can be more destructible/harder
- **Has healing:** survival encounters can sustain longer; rescue encounters can require more healing
- **Has AoE:** enemy count can increase (AoE handles swarms); summon encounters become more viable
- **Has range:** enemies can spawn at distance; stealth/timed can space targets further
- **Has crowd control:** stealth encounters can open up (CC creates paths); summoners can be CC'd to prevent spawning
- **Has illumination/info:** darkness/invisible enemies become viable encounter elements

### By Enemy Composition
- **Single strong enemy:** tests focused damage output
- **Multiple weak enemies:** tests AoE/multi-target capability or crowd control
- **Mixed behaviors:** forces adaptation (healer + aggressive = kill priority decision)
- **Summoner present:** escalates turn-by-turn (adds spawn each round)
- **Higher rank:** a single +1/+2/+3 enemy substitutes for a group of weaker ones — tests sustained single-target output rather than AoE/crowd control

### By Element Combinations
- **Enemy + Hazard:** adds positioning challenge to combat
- **Obstacle + Range limitation:** forces navigation or crowd control
- **Darkness + Puzzle:** information-denial puzzle
- **NPC + Enemies:** split-focus challenge (heal/save while fighting)
- **Multiple element types:** complexity bonus (teaches ability switching, resource management)

## Design Notes

**Uniqueness:** Encounters are unique because of **element combinations** and **positioning**. Rather than 100 hand-scripted "boss" encounters, the system generates fresh encounters by varying challenge type, enemy behavior mix, element presence, and difficulty tuning. This keeps the game feel fresh without prescribing individual boss designs.

**Balancing:** Constraint Satisfaction Problem (CSP) approach: before spawning an encounter, verify it's solvable given the player's loadout (damage output vs. enemy HP, healing output vs. damage taken, range vs. distance, etc.).

**Progression:** Early Realm zones use simple challenge types (Combat, Obstacle); later zones blend types and add element variety (Survival + Hazard, Stealth + Invisible, Rescue + Summoner).

**Open world, not instanced:** Classic's original design intent was fully open-world content, but in practice the toughest encounters ended up gated behind instanced dungeons and raids — a workaround for population and technical limits on how many players could safely share one high-stakes fight at once. The Real Classic deliberately skips instancing and keeps every encounter, including the rarest and toughest, in the open world: Realms are unlikely to reach the population scale that made instancing necessary in the first place, the technical constraints that motivated it have largely evaporated, high-level monsters roaming the open world are themselves a beloved part of the classic fantasy, and instanced content historically only becomes relevant at levels beyond a single Realm-creation prompt's default scope anyway.

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

# Races

AI training: appearance descriptors, starting attribute bonuses (bearing in mind that players may not want to have the attributes' baseline be 20 if that seems like too large a number for balancing purposes), and copyrighted terms to avoid (from World of Warcraft, from the universe that it largely derives content from (namely that of Dungeons and Dragons), and from the universe that players flock to if they leave World of Warcraft (namely that of Final Fantasy 14, also known as Final Fantasy XIV, also known as FF14 or FFXIV, which contains copyrighted terms including Hydaelyn, Zodiark, Etheirys, and Ascians that don't fit elsewhere here).

**A note on the Attribute Deltas below:** every number in this file is a modifier against the canonical attribute baseline set by the Attributes prompt box — this file doesn't own that baseline, just consumes it (see wherever that system ends up documented). The delta is the authoritative part; the absolute ranges printed alongside each one (e.g., "22–25") assume the baseline currently sits at 20–23, as stated for Humans below. If the baseline ever moves, recompute the absolutes from the deltas — don't trust the printed numbers as a substitute.

## Design Notes and AI Generation Guidelines

### Visual Race Design

Race design is the visual foundation of the player experience. A player commits to looking at the player's chosen race for potentially dozens of hours of gameplay; aesthetic appeal and visual distinctiveness matter more than lore consistency or mechanical balance alone.

Prioritize creating races that players *want to see*. When a race resonates visually—when it looks the way players imagine or hope—they're far more likely to commit to the game itself. This is why Blood Elves spiked Horde participation in The Burning Crusade: suddenly there was a race that looked the way a significant player demographic wanted to look.

As a subset of this, keep an eye out for what level of customization users want to have over each race. For example, in the latest Diablo games, while character customization exists, a handful of presets are shown to make it easy for players to easily begin play, thus showing keeping only a handful of options open may be desired by some players. On the other hand, Final Fantasy XIV's lavish character customization, with about 20 appearance sliders or pickers per race and 100 or so options per slider or picker, serves a different audience that cares far more about character design and consequent roleplay than starting play post-haste. Pay attention to what depth of customization users want in a given race; it's vital to the entry experience.

### Racial Design Philosophy

Core racial design philosophy: **Let lore and mechanics serve aesthetic appeal, not the reverse.** If a compelling visual design requires lore adjustments or cross-cutting mechanics (a race that doesn't fit the traditional faction split, or one with hybrid capabilities), make those changes. The race players want to play is the race that will keep them engaged.

**Dual purpose—playable and NPC**: Races serve both as playable character options and as templates for AI-generated NPC races to populate the world. Generation requests should treat races as archetypes that can spawn variants, not one-to-one character blueprints.

### Deferred or Modification-Only

Races can start with **pre-set reputation** standing toward various factions — this is the actual mechanism tying Race to Faction/PvP alignment in the original Classic, rather than factions being a free-floating system. Relevant once Reputation/Factions and PvP-kill quests (deferred — see story.md's Quest Types, "Deferred or Out of Scope") eventually get built out.

**Duplicate race handling**: When a user requests multiple instances of the same race, the AI should confirm whether they want a variant of the existing version (same subrace/culture) or a distinct alternate version with different lore and appearance. This prevents accidental duplicates while respecting intentional racial diversity.

### Player Cohesion: Why Start with One Race?

In Classic WoW, early-game groups naturally cohered around a single race. Players created characters of the same race, progressed through that race's themed starting zones together, and only branched into other races' zones if additional quests were needed for leveling. This created a strong visual and narrative unity—the group *looked* like a unit and shared the same introductory world.

Starting a Realm with **one playable race** preserves this cohesion. Players don't spread across different starting zones; they all begin in the same place, meet at the same NPCs, and face the same early content together. This is especially valuable for integral groups—a few players who will level together before finding a larger guild for endgame content.

This isn't a hard requirement; Realms targeting immediate PvP play or maximum player choice may prefer multiple starting races. But most Realms benefit from the shared starting experience, and it significantly reduces the complexity of the first-zone design.

**On starting zones specifically:** new races often get new starting zones, but not always — it depends on Realm scope — and high-level zones should never be used as starting zones. The full rule lives in the Builder Interface spec's Races prompt box (see `../spec.md`, one level up from this file).

## Races

**None of these descriptions are hard requirements; they are simply ideas to mine from, as many players may expect these descriptions if certain aspects of them are left unspecified.**

### Humans
- **Appearance:** No special appearance of note; everything else in this file is weighted against Humans, who get average appearances.
- **Attribute Deltas:** Average across the board, usually 20–23 — the implicit baseline everything else shifts against.
- **Classes:** Assumed pious, with a vaguely Christian-coded pantheistic religion; favor martial, holy, or magical classes over nature-heavy ones, though some dark or otherwise unsavory paths are available to Humans who stray. This is the shakiest lore assumption of the bunch — Humans get wildly inconsistent depiction across franchises because that's who all the developers and writers are.
- **Avoid:** Any of the WoW human kingdoms — Stormwind, Gilneas, Kul Tiras, Dalaran, Lordaeron, Arathor (demonym Arathi), Stromgarde, Alterac; the FF14 term Hyur; the D&D term Genasi.

### Orcs
- **Appearance:** Strapping, sometimes hunched, often with porcine features or protruding canines (fangs/tusks); read above all as a fearsome sight to enemies.
- **Attribute Deltas:** Strength or Spirit +2–3 (23–25/26), Stamina +1–2 (22–24), Agility and Intellect −3 (17–20).
- **Classes:** Highly aggressive combat, often imbued by religion or allegiance to alien powers — anywhere from benevolent animism or elemental worship to aberrations beyond comprehension to outright evil deities.
- **Avoid:** Gith, Githyanki, Githzerai, Jhorguun-taal, Mag'har, Quilboar.

### Elves
- **Appearance:** Slender, usually tall, pointy-eared (sometimes with very long ears on the sides or top of the head), almost always long-lived or outright immortal, with features reflecting an ancient yet still supernaturally beautiful bearing.
- **Attribute Deltas:** Agility +2 to +5 (22–25 up to 25–28), with how high depending partly on whether Intellect is also raised (up to +4, to 24–27). Strength and Stamina both drop, Strength more (17–20 to 19–21); if attributes beyond Agility drop too, Spirit goes down 1 (19–22).
- **Classes:** Extreme emphasis on ranged combat.
- **Variants:** Trolls (the WoW/D&D sense — folklore trolls don't fit this entry; see Ogres below) follow the same profile but tusked, sometimes hunched, and usually less beautiful, with every non-Agility attribute +1 except Intellect, which lands at 16–19 instead. Shivarra, if requested, get six arms.
- **Avoid:** Names/demonyms ending in "-'dorei"; Eladrin, Elezen, Khoravar, Shivarra, Vedalken, Viera; the languages/demonyms Darnassian, Shalassian, Thalassian.

### Dwarves
- **Appearance:** Short, broad, muscular, usually bearded — whether females share the beard is an open subject of fan debate. Ensure that users' requests are warranted as to whether female dwarves have beards or no beards; not listening to this request may well alienate the users.
- **Attribute Deltas:** Strength and Stamina +2 (22–25), Intellect and Spirit −1 (19–22), Agility −4 (16–19).
- **Classes:** The base game's classes don't reflect any of this and are the most average of the lot, largely because dwarven culture/religion is highly fractious; other Warcraft media instead lean hard into ranged, elemental-magic, gryphon-riding, and firearm-heavy classes (fitting a setting roughly on the cusp of an Industrial Revolution). Worth deciding deliberately which version a given Realm follows.
- **Avoid:** Ironforge, Khaz Modan, Grim Batol, Shadowforge City; being considered Bronzebeard, Wildhammer, Dark Iron, Earthen, or especially Duergar or Baugsmidr.

### Gnomes/goblins/halflings/imps/pygmies
- **Appearance:** Diminutive, sometimes earth spirits, frequently long-armed with few digits, almost always exaggerated (large heads, large and sometimes pointed ears). Split by tone: played childlike and cute, or adult and hideous (grins, sometimes horns) — read which the user is going for (gnomes skew cute, imps skew hideous/horned).
- **Attribute Deltas:** Roughly the reverse of Dwarves: Agility and Intellect +2–3 (22–25 or 23–26), Strength and Stamina −1–3 (17–20 to 19–21) depending on what else moves. Spirit and Stamina trade off rather than both dropping hard — anywhere from Stamina −5 (15–18) with Spirit untouched (20–23), to Spirit −2 (18–21) with Stamina untouched (20–23), depending on balance needs and the exact racial fantasy.
- **Classes:** Usually engineering-flavored, built around advantages from diminutive stature or high intellect; some incarnations prioritize spirit-communion instead, in which case the class set follows that — diminutive stature still shapes classes either way.
- **Variants:** Mechanical prosthetics are fine for customization — the issue is only the name Mechagnomes, not the concept. Watch for fully artificial, golem-like tiny beings if Wechselkind are requested; the line between the two is thin and not worth stressing over.
- **Avoid:** Grell, Grummles, Hobbits, Kender, Lalafell; being from Gnomeregan; Mechagnomes; Wechselkind.

### Vampires/dhampir
- **Appearance:** Blood-sucking, usually undead, batlike features and/or bat transformation — a very common trope, fuzzily defined in WoW itself, where vampires read as either undead elves or elf/troll progenitors.
- **Attribute Deltas:** None — playable variants were added decades into WoW's history, long after starting attribute bonuses were removed as a system, so there's no precedent to draw a delta from.
- **Classes:** Dark, disturbing magics, even for versions of the race not otherwise intended to read as dark or dead.
- **Avoid:** San'layn, Haranir, Venthyr.

### Other undead
- **Appearance:** Almost-universally hunched and gruesome; the spectrum runs from fleshy abominations to lean, hirsute ghouls to fleshless skeletons to fleshless-and-shimmery liches to transparent ghosts and banshees, distinguished mainly by hair/skin/transparency. Zombies sit in the middle of that spectrum (except transparency) and sometimes are missing an arm — though player characters wouldn't be.
- **Attribute Deltas:** Spirit +up to 5 (25–28), Stamina +0–1 (21–23 — a deliberate paradox alongside everything else dropping), everything else −1–3 (18–20 at minimum, 19–22 at maximum).
- **Classes:** Dark magics.
- **Avoid:** Shadar-kai, Kalashtar.

### Satyrs
- **Appearance:** Widely varying amounts of hair; a prominent set of races in the original universe.
- **Attribute Deltas:** Strength, Intellect, and Spirit +1–2 (21–22, or 22–23 for Spirit); Agility and Stamina −1–3 (19–21 for Agility, 17–20 for Stamina) — emphasizing a strong, old race over an agile or tough one.
- **Classes:** Martial prowess or old religions of any variety, over stealth or succumbing to new and tempting ideologies.
- **Variants:** Wings, if a demonic archetype is requested (Ered'ruin, Incubi, Nathrezim, Sayaads, Succubi, Terrorguards — the link is Pan's association with Satan). Facial tentacles only if specified, or if Draenei/Eredar are requested.
- **Avoid:** Draenei, Eredar, Ered'ruin, Incubi, Man'ari, Nathrezim, Sayaads, Succubi, Sylvar, Terrorguards.

### Naga/siren/undine
- **Appearance:** Graceful but deadly, aquatic, sometimes draconic and serpentine — rooted in Indian folklore but blurring heavily into Western mermaids visually: scales, head protrusions that could read as fins or snake-hoods, long tails instead of legs.
- **Attribute Deltas:** Entirely absent.
- **Classes:** Even martial builds keep their distance — polearms or tridents rather than closing in — with most classes leaning toward magic or other ranged tactics, fitting their inhumanly slight build.
- **Avoid:** Yuan-ti, Sahuagin, Kalamer, Laneshi, Limukin, Satarre, Sethrak, Saurok.

### Frogmen/fishmen
- **Appearance:** Little distinction between frogmen and fishmen as a category, especially since WoW's Murlocs blend both. Often (not always) small, hunched, large-headed and grotesque, with fins or other head protrusions and eyes on the side or top of the head.
- **Attribute Deltas:** Entirely absent.
- **Classes:** Dark, aquatic, or both at once.
- **Avoid:** Murlocs, Gorlocs, Grippli, Kuo-toa, Locathah, Nakudama, Jinyu, Ankoans, Grungs.

### Ogres/half-giants/hobgoblins/ettins
- **Appearance:** Like humans, but much bigger and usually far more muscular; sometimes multiple heads, sometimes one eye per head. Weight-to-height varies widely — ogres and hobgoblins run heavyset, other types in the category run slenderer.
- **Attribute Deltas:** Entirely absent.
- **Classes:** A surprisingly wide and potent variety of unusual magics.
- **Variants:** One-eyed, if Magnaron, Gronn, or Ogron are requested. Made of stone, if a stone variant is requested (Mogu or Magnaron). Folklore trolls (the bridge-dwelling sort) conform to this entry — unlike WoW/D&D trolls, which fit the Elves entry instead.
- **Avoid:** Roegadyn, Vrykul, Gronn, Ogron, Drust, Drogbar, Djaradin, Mogu, Mo'arg, Magnaron, Ankylier, Giff.

### Harpies
- **Appearance:** Winged, feathered, taloned, often hunched — unless meant to read as angelic, which WoW folds into this same category quite often. Size varies widely.
- **Attribute Deltas:** Entirely absent.
- **Classes:** Twisted versions of other races' classes, whether the twist reads as noble, ignoble, or simply scholarly.
- **Avoid:** Aasimar, Kyrians, Val'kyr (all skew larger and more angelic); Arakkoa, or the D&D progenitor Aarakocra (skews small and hunched instead).

### Foxmen/raccoonmen/squirrelmen/rabbitmen/mousemen
- **Appearance:** Short, furry, scrappy, with prominent ears corresponding to the specific animal.
- **Attribute Deltas:** None on record — added too late in the game's history to have starting bonuses — but the concept implies a gnome-like profile: low Strength/Stamina, high Agility/Intellect, possibly high Spirit too.
- **Classes:** Survival at any cost.
- **Variants:** Distinguished from Catmen (below) by an emphasis on scavenging rather than deception, and by being exclusively diminutive — Catmen aren't always small and lean crafty/tricky instead. If Viera are requested, that's the Elves entry, not this one.
- **Avoid:** Harengon, Jerbeen, Mapach, Ratatosk, Virmen, Vulpera.

### Catmen
- **Appearance:** A common fantasy race, ranging from lithe, sometimes diminutive housecat-like humanoids to more leonine and physically imposing variants.
- **Attribute Deltas:** Not given directly, but inferable: smaller, savvier, and less physically aggressive than Other large animal-men (below) suggests a gnome-like profile.
- **Classes:** Old magics, often crafty or tricky ones.
- **Variants:** Six-limbed, if Tol'vir or six limbs are requested — WoW's own version of this race.
- **Avoid:** Tabaxi, Tol'vir, Saberon, Leonin, Miqo'te, Hrothgar — though Hrothgar, being the name of a legendary Scandinavian king predating FF14 by a millennium, is probably not something FF14 can defend as its own; avoid it anyway for safety.

### Other large animal-men (werewolves/minotaurs/centaurs/dryads/tarands)
- **Appearance:** Heads and/or bodies of wolves, horses, cows, bears, monkeys, or other animals — moose, deer, reindeer, hyenas, even something as different as elephants.
- **Attribute Deltas:** Spirit and Stamina +0–2 (21–23, usually 22–24) — modest next to Strength, which can rise as much as +5 (25–28) if not left untouched, paid for with Agility and Intellect penalties of −2–6 (never higher than 19–21, never lower than 15–17).
- **Classes:** Communion with spirits.
- **Variants:** Werewolves/wolfmen are the exception to the attribute pattern above: Agility +2 (22–25), Spirit and Stamina −0–1 (19/20–22), with Strength and Intellect still following the general rule.
- **Avoid:** Yaungol (moose), Worgen/Wolvar (werewolf), Tuskarr (walrus), Tortollan (turtle), Tauren (cow — "minotaur" is a safe generic substitute), Pandaren (panda), Hozen/Hadozee (monkey), Gnoll (hyena), Furbolg/Firbolg (bear — though Fir Bolg itself is an uncopyrightable Irish legend unrelated to the bear-men sense, avoid the term anyway given the overlap), Owlbear, Loxodon (elephant, via the genus Loxodonta).

### Dragonkin
- **Appearance:** Dragons themselves usually run too large to be playable, but their humanoid ilk often are — wings, horns, usually scales, sometimes other draconic features like reptilian snouts, but roughly the size of other playable races, if more innately magical than most.
- **Attribute Deltas:** Extremely poorly defined.
- **Classes:** Extremely poorly defined, though likely to include some form of draconic magical breath.
- **Avoid:** Au Ra, Dracthyr, Jeholrak, Pluvenn, Refti.

### Epiphagi
- **Appearance:** Headless. May have floating headgear (masks and the like) or simply no head at all. If corporeal, facial features may relocate elsewhere on the body (eyes in the shoulders or nipples, mouths in the neck or stomach); otherwise the features are just missing, with only any headgear hinting at them.
- **Attribute Deltas:** Entirely absent.
- **Classes:** Entirely absent.
- **Avoid:** Ethereals, Brokers.

### Insectmen
- **Appearance:** Wide variety across the WoW universe, often cast as servants of evil races, corrupted by evil magic, or both — no more specific visual description given.
- **Attribute Deltas:** Entirely absent.
- **Classes:** Entirely absent.
- **Avoid:** Makrura (crab-like rather than strictly insectile — lean into a crabby look if this one's requested), Mantid, Nerubians, Aqir, Qiraji, Fal'dorei, Aranasi, Thri-keen.

### Plantmen/spriggans/treants
- **Appearance:** Woody skin, leaves or branches for hair or limbs. Size is inconsistent across the category — spriggans usually tiny, treants usually enormous, plain plantmen somewhere in between (tall and slender, or merely large).
- **Attribute Deltas:** Entirely absent.
- **Classes:** Entirely absent.
- **Avoid:** Botani, Ents, Hederan, Podlings, Tirnenn.

# Story

AI training: quest types, NPC roles, narrative elements, questline/zone structure, and currency conventions.

Story content in The Real Classic is not a fixed plot to reproduce, but a set of **patterns and building blocks** — quest types, NPC roles, and narrative elements — that combine to generate fresh questlines. This document defines those patterns, plus how they compose into zones and questlines, so generated content feels authentically Classic rather than retail-standardized.

## Narrative Beats

Problems often start local, with a particular NPC, town, or other small group suffering from an issue that must be solved by the player slaying monsters, gathering items, talking to other NPCs, or the like. As the narrative progresses, the problems often increase in scope and/or severity, usually culminating in a boss fight and/or moving on to another storyline with the new scope and severity.

## Quest Types

Each quest type represents a distinct objective pattern. Quests may combine types — a quest can require both gathering and delivering, for instance — or feature one as the primary hook.

### Gather
Collect a number of items from the environment (not from monsters) and return them.
- Core mechanic: item count vs. environmental availability
- Scaling: item count, spread across the zone, environmental danger while gathering
- Common combinations: often paired with Kill in the same quest, or gated by a Quest Item Use condition

### Kill
Slay a number of monsters, or defeat a single powerful one without necessarily slaying it.
- Core mechanic: monster count vs. player combat capability
- Scaling: monster count (typically 1-15, sometimes up to 20; 8 is the memetic *average*, not a floor or ceiling — outliers exist, most famously 60: https://warcraft.wiki.gg/wiki/Consumed_by_Hatred_(Classic)), monster rank (see boss-mechanics.md's Enemy Rank & Level Progression)
- **Loot & Return variant:** the tracked count is items looted from kills, not kills themselves — the more common real form of a "kill quest," since most surface-level kill quests are actually this underneath. Drop rate governs whether required kills match, exceed, or fall short of the stated count: a sub-100%-drop-rate item needs more kills than the stated number, a monster carrying 2+ qualifying drops needs fewer.

### Deliver
Transport an item, often a letter or package, from one NPC to another.
- Core mechanic: travel from point A to point B
- Scaling: distance, danger along the route
- Common combinations: often the follow-up to a Gather or Kill quest — deliver the thing just collected or looted

### Escort
Perhaps the most notorious quest type: follow an often-slowly-moving NPC from one place to another, ensuring the NPC stays alive even as it invariably walks near patrolling monsters who descend on it. The NPC is inevitably poorly-equipped for survival against the monsters it attracts. Usually this is the entire in-world reason for the quest — the NPC is aware of this and is hiring the player as an armed guard — but sometimes the NPC is merely oblivious to the situation, irking many players.
- Core mechanic: keep an NPC alive while it moves between two points
- Scaling: distance, monster density along the route, NPC fragility
- Common combinations: often paired with Kill — clear the monsters that threaten the escort target

### Find & Speak
Talk to another NPC, with no other condition required. The quest is picked up from one NPC and turned in to (or continued by) another.
- Core mechanic: travel to and interact with a specific NPC
- Scaling: distance, whether the destination is already known or must be discovered
- **Breadcrumb variant:** the NPC being sought represents a new area of content — a new zone, or a new hub within the current zone (see Zone & Questline Shape below). Mechanically identical to a plain Find & Speak; the only difference is what the destination represents narratively.

### Explore
Visit a specific location and report back, or simply discover it.
- Core mechanic: travel to and reveal/witness a location
- Scaling: distance, path difficulty
- Rare relative to other types, but a real and valuable pattern — worth including occasionally rather than defaulting away from it.

### Vehicle Use ("Bombing Run")
Enter an often-autonomously-moving vehicle that deals massive damage across a large area, letting the player slay huge numbers of monsters (sometimes triple digits) with ease.
- Core mechanic: use vehicle abilities to clear large numbers of monsters quickly
- Scaling: vehicle power, monster density, time limit if any
- **Tone-gated:** a comparatively recent, retail-associated pattern. Whether it's in scope depends on Tone's difficulty/modernity signal — users specifying an easier or more modern feel are more likely to want it; users specifying a harder or more old-school feel are less likely to.

### Deferred or Out of Scope
- **Profession-based** — deferred until the Professions toggle (see spec.md) is actually enabled; not fully specified here yet.
- **Reputation** — out of scope. Better modeled later as a reward property attached to other quest types (turning in kills/gathers for reputation) than as a quest type of its own — and it requires multiple factions in meaningful opposition, which isn't the Realm-creation default (spec.md suggests Factions/reputation not be used for Realm creation).
- **PvP-kill** (kill enemy-faction players, loot a token) — deferred alongside Reputation, for the same reason: it needs an opposing faction to exist meaningfully. Note for later: races can start with pre-set reputation standing toward different factions — the actual mechanism tying Race to Faction in real Classic (see races.md once expanded).
- **Combo, and the wider retail-adjacent list** (World Quests, Emissary, Callings, Legendary, Campaign, Bonus Objectives, Daily/Weekly/Monthly/Seasonal, Dungeon/Heroic/Raid) — not relevant here; either retail-only systems, or in the case of instanced content, out of scope per boss-mechanics.md's open-world design decision.

## NPC Roles

NPCs in a questline play distinct functional roles. A single NPC can hold more than one role at once — a Quest Giver is very often also the Turn-in NPC.

### Quest Giver
Offers the quest.
- Mobility: stationary
- Function: presents the Quest Hook
- Usage: the default/most common role; may double as the Turn-in NPC

### Turn-in NPC
Receives the completed quest, when distinct from the Quest Giver.
- Mobility: stationary
- Function: completes the quest, may present a Chain Link to the next one
- Usage: routes the player to a second NPC, e.g. as the objective of a Find & Speak quest

### Escort Target
The NPC being escorted.
- Mobility: mobile, moving toward a destination
- Function: defines the Escort quest type; vulnerable, poorly equipped for the dangers it attracts
- Usage: the in-world reason for an Escort quest is usually built around this NPC's awareness (or obliviousness) of its own vulnerability

### Rescue Target
Trapped or imprisoned NPC.
- Mobility: stationary until freed
- Function: must be reached and freed or healed
- Usage: ties directly to boss-mechanics.md's Rescue challenge type and NPC element

### Trainer
Teaches abilities or professions.
- Mobility: stationary
- Function: grants class/profession progression
- Usage: ties to classes.md

### Vendor
Buys and sells.
- Mobility: stationary
- Function: implies a Currency system (see below)
- Usage: may eventually gate rewards behind reputation (deferred, see Quest Types above)

### Banker
Manages player inventory expansion via banking services.
- Mobility: stationary
- Function: allows players to store items beyond their carrying capacity, typically in a town or settlement
- Usage: provides a mechanical reason for players to visit towns and creates a progression gate (limited early-game bank space); ties to inventory/bag management systems

### Hostile-until-Quest
Starts as a hostile Enemy (see boss-mechanics.md), and becomes an ally or Quest Giver once some condition is met.
- Mobility: varies
- Function: state flips from hostile to friendly — e.g. defeated in combat but not killed, or freed from a mind-controlling effect
- Usage: bridges boss-mechanics.md's Enemy Behaviors and Story's NPC Roles

### Ambient/Flavor NPC
No mechanical function.
- Mobility: varies
- Function: world-building only
- Usage: may carry a Readable Item

## Narrative Elements

Atomic building blocks that populate a questline.

### Quest Hook
- Properties: giver (NPC or Readable Item), prerequisite (if any)
- Interaction: presents the quest to the player
- Grounding: the origin point of a questline; see Narrative Beats

### Readable Item
Some items dropped by monsters (or found in containers, or on corpses) may be read. These can provide narrative beats where quests do not, and/or can themselves give quests to the player.
- **Lore Book/Tome** — lore-only, no mechanical hook; found in containers/libraries
- **Letter/Note** — often the quest hook itself; found on corpses
- **Journal/Diary** — multi-part, assembled piecemeal across a zone; structurally resembles a Gather quest
- **Codex/Manual** — teaches a recipe/ability on read; ties to Professions/Classes (deferred alongside Professions)

### Chain Link
- Properties: prerequisite (what quest/condition unlocks this one), unlocks (what becomes available on completion), position (early/mid/late), branching (linear vs. branching)
- Interaction: completing a quest makes the next one available
- Grounding: what turns a pile of one-off quests into an actual questline; see Zone & Questline Shape

## Quest Modifiers

Conditions that attach to the Quest Types above, rather than standing as types of their own.

### Quest Item Use
A specific item must be used as part of completing the quest. Variants include: using an item to summon a boss or render it killable; using an item to flip a friendly NPC hostile or vice versa; using an item on every corpse of a kill-quest's targets; using an item at a hard-to-reach location behind monsters or exploration; and myriad other variants. All are equally legitimate parts of the taxonomy — a variant being tedious to remember as a player is a personal-taste/Tone-level concern for an individual Realm, not a reason to suppress it from the shared corpus.

### Class Restriction
A quest is only available to a specific class. Freely usable, bounded by two things: required/major storylines that everyone is expected to play through should generally stay class-agnostic, and this only applies when a Realm actually has more than one class to differentiate between.

## Zone & Questline Shape

Retail WoW settled into a standardized shape: a zone breaks into roughly 4-7 quest hubs, each with a handful of one-off quests and short follow-up chains, plus a zone-wide story arc threading across all hubs and culminating in a single boss (or, more recently, a dungeon). **This is a retail convenience, not the Classic pattern, and should not be the default assumption.**

Classic questing varied along at least two axes instead of following one fixed shape:
- **Hub count:** zones could have as few as 1, or even 0, dedicated quest hubs — nothing like retail's standardized range.
- **Questline locality:** long questlines (running into the double digits of quests) could and often did span multiple zones, and might not even start or finish in the zone where most of their quests actually took place. Even questlines that stayed within a single zone would often send the player all over that zone, rather than clustering conveniently near one hub the way retail does.

When generating a Realm's zone and questline structure, vary these parameters rather than defaulting to retail's tidy model — a zone with a sparse or absent hub structure, or a questline that wanders across the whole map, is more authentically Classic than a clean 4-7-hub layout.

## Story Scaling

### By Narrative Scope
Early content in a zone or patch tends to be local (see Narrative Beats); later content escalates in scope and severity, typically culminating in a boss fight or handing off to a new storyline.

### By Zone/Questline Position
See boss-mechanics.md's Enemy Rank & Level Progression for the mechanical side of this: monster levels climb across a zone from a floor (one below zone-minimum, clamped at 1) up to the zone's stated maximum, with +1/+2/+3 reserved beyond that for progressively rarer encounters. The +3 tier specifically is reserved for the climactic encounter of a **major questline** — the kind running into the double digits of quests, often spanning multiple zones per Zone & Questline Shape above — not every zone's own finale, which more commonly resolves at +1 or +2, as a single monster, a boss gauntlet, or a multi-phase fight.

## Currency

The gold/silver/copper trichotomy is close to a universal default across this genre — assume it unless Tone explicitly calls for something else. Standard conversion mirrors Classic itself: 100 copper = 1 silver, 100 silver = 1 gold. Quest rewards, vendor prices, and drop values are denominated this way by default.

## Design Notes

**Copyright:** avoid proper nouns for factions, characters, and locations. races.md maintains the canonical list of terms to avoid; cross-reference it rather than duplicating here. Broad plot shapes — invasion, corruption, rebellion, elemental uprising — are generic fantasy tropes, not ownable, and safe to reuse structurally regardless of their association with Warcraft specifically. The risk is specifically in verbatim proper nouns, not story shapes.

**Coherence:** a generated questline should reference entities that actually exist in the zone/patch being generated — the monsters, NPCs, and items the other taxonomy outputs actually created — not invent free-floating references.

**Uniqueness:** as with boss-mechanics.md, questlines become unique through combination — quest type, NPC role, narrative element, and modifier — rather than through hand-scripting individual storylines.

# Framework Brainstorm So Far

This is a transcript of a conversation with north-mini-code-1.0:latest as to how to design the framework. ***It's pretty good so far, but I'd like the language stack to reuse as much as possible of what exists and simplify what languages are involved otherwise.***

## Transcript

Here is the decoded content:

**has the determining ports (same JK/Vite/Express/flix.io stack):**
- using static ones (imports Endured Script) (dumbs in that same role: constants, to compare with numbers from fits by of 
variable's, as a test purpose.)
- * import slide.ttx of grid-colors.ds and factual
-, exiting with those gringing pong, have pleanty showered rings, and hang root stops.
< /html>
= - - -- **with bilined-blued font to enrypt:**
xl: http://w3.org/SCSI/hide
shards in this parentjP>
**Parameters**
- * import the data part name: [inq] and outset of those
---
**Effective user url**
- - *import slide.ttx

**Design ports only (GDScript/ Swift):** * *reported as server-authoritative Js:*

- $take-a-stab (Godot 4) **shipped real-time me combine:** enume chass/attack log ($zombie.gd $ _physis__process // $bite / 
$die), hit geometry, definitely ramp. (Easy to for this repo that it's listed.)
- - $combo-spell (Godot) **unit/enemy AI behavior catlog ($docs/behaviors.md: attack, define-a-point, enforce, etc.)**
- - $master-dungeonable (Swift) **turn-based bosses mechanics (see $oss mechaic aboves)**
- **Aggro radial, pathfinding, respawn, and XP designs are covered these three.**

**Taxonomy source of truth:** the docs in taxonomy/ are canonical + entry types, this project's anlogue of the Master 4D source 
that cry-with-me's types.js encoded rather than intended. ENT_ry_TYPES gets encoded 'from*' those docs, and some docs also feed 
the runtime retreive corps (cry-with-me's $corpus // $retrieve.js pattern). Real Zero is a test fixture (generate-then-freeze; 
hand-write as failure), not the taxonomy-definitive act.

**Build order:** scaffold + port cry-with-me plumbing to generate Realm ZeRo, freeze as fixture Jscob from the design ports that 
JK combine wise the generation verb verb
# **Design ports:**
scaffold + port cry-with-me sim from the design ports (JK) wise the generation verb verb

>>> This is very interesting. Is there more you'd like to explain now, or is there something you'd like for me to do next? You seem to
...  have a really solid grip on all this!

You’re welcome! I’m glad the decode gave you something useful.  
Here are a few ways we can keep the momentum going:

1. **Deep‑dive on the architecture** – If you’d like, I can walk through:
   * The “design ports” (the GDScript/Swift parts) in more detail.
   * How the taxonomy source‑of‑truth works and how it feeds the runtime.
   * Any particular patterns or code snippets that caught your eye.

2. **Concrete artifacts** – Do you have any specific files, logs, or specs you want me to help interpret, extend, or validate? I 
can:
   * Pull in additional GitHub content (e.g., a `README.md`, other scripts).
   * Generate small test fixtures (like the “Zero fixture” you mentioned).
   * Sketch out new behaviors or UI components.

3. **Next‑step tasks** – If there’s something concrete you need done (e.g., setting up the GDScript project, wiring up the Swift server, creating a PR, etc.), just let me know and 
I’ll break it down into actionable steps.

4. **Q&A / Clarifications** – If any part of the decoded text or the surrounding context is still fuzzy, point it out and we can unpack it together.

What would you like to focus on next? Or is there another piece of the repo/project that you’d like me to pull in so we can continue exploring?

>>> It sounds like you have a fairly clear idea of the architecture we're pulling from. Something I'd like to add is that the Club Penguin Builder runs pretty much entirely on JavaScript (
... using that to render its 2D chatrooms), while Take a Stab runs on GDScript for its 3D rendering, and Master Dungeon runs on Swift (probably not relevant here for this online, not-exclu
... sively-iOS game). How does this inform your ideal next step?

## TL;DR  
**Your multi‑language stack is a great opportunity to build a **central “source‑of‑truth” that all three runtimes can consume**, coupled with thin adapters so each part stays in its 
native environment. The ideal next step is therefore:

> **Create (or formalise) a language‑agnostic configuration layer and an automation pipeline that materialises the required assets/code for each of your JS, GDScript, and Swift 
components.**

Below is a concrete roadmap that shows why this makes sense, how it aligns with your three “projects”, and exactly what you can start doing right now.

---

## 1. Why a **single source‑of‑truth** matters in a polyglot world

| Language | Primary Concern | Typical Data Flow |
|----------|------------------? |-----------------|
| **JavaScript (Club Penguin Builder)** | UI, DOM‑based chatrooms, static assets (HTML/JS/CSS) | Pull JSON/YAML configs → render rooms dynamically (e.g., via e.g. a Node/Express 
server or client‑side bundle). |
| **GDScript (Take a Stab)** | 3D world logic, physics, game‑state, UI HUD (in‑engine UI) | Load serialized data (JSON/TXT/TSV) → spawn objects, define AI/behaviour trees, bind 
events. |
| **Swift (Master Dungeon)** | iOS/macOS client logic, native networking, platform‑specific features (AR, push notifications, etc.) | Consume the same configs as GDScript but via a 
lightweight Swift client or optional server bridge. |

**Key pain points when each part lives in its own silo**

1. **Duplicate metadata** – You already have a `taxonomy/` folder that’s meant to be the “source of truth”. If every language keeps its own copy, drift is inevitable.
2. **Inconsistent behaviour** – e.g., a room ID defined in JS but not reflected in GDScript → the 3D world never spawns the correct environment.
3. **Harder CI/CD** – you’d need separate pipelines for each runtime just to verify that configs match.

**Solution:** Turn `taxonomy/` (or a sibling folder) into **one canonical schema** (e.g., JSON Schema + YAML files). Both JS, GDScript, and Swift adapters read from this single 
source; any validation runs once in CI before any language‑specific build.

---

## 2. The **Adapter Pattern** – thin, focused wrappers

For each runtime you can expose the same logical view but with a friendly API:

| Adapter | Example File | Responsibilities |
|--------|--------------|-------------------|
| **JS Adapter** (Club Penguin Builder) | `src/server/api.mjs` | Express route(s) that read taxonomy JSON and serve HTML/JSON for chatrooms. Handles static asset generation 
(`slide.ttx` → HTML). |
| **GDScript Adapter** (Take a Stab) | `godot/project/scripts/core/TaxonomyLoader.gd` | Load the same JSON (via HTTP request or local file) into GDScript data structures, then feed 
them to scene loaders (`.tscn`) and AI behaviours. |
| **Swift Adapter** (Master Dungeon) | `Sources/DDLTaxonomyLoader.swift` | Same JSON → Swift structs → use for UI, networking, or platform‑specific features. |

These adapters are *thin* – they don’t contain business logic; they merely translate the canonical representation into whatever data type their runtime expects.

---

## 3. **Automation Pipeline** – one‑click sync

A typical flow looks like this (you can implement with a simple `makefile`, `npm` script, or something like **Nx/monorepo** if you already use it):

```
# package.json / Makefile
generate: validate-taxonomy compile-js compile-gd compile-swift

validate-taxonomy:
  node scripts/validate.mjs   # runs against taxonomy/ and fails CI on schema violation

compile-js:
  npm run build          # e.g. generate static HTML pages, bundle JS

compile-gd:
  godot --headless --export "Template" . scripts/export_godot.sh   # optional WebAssembly export for testing

compile-swift:
  xcodebuild -project MasterDungeon.xcodeproj build
```

**What the pipeline actually does**

1. **Schema validation** (`scripts/validate.mjs`) ensures that every entry has required fields (e.g., `id`, `type`, `sceneRef`).
2. **Template rendering**:
   * `js`: runs a Handlebars/EJS template → writes out HTML files (`rooms/[id].html`) and any static JavaScript assets.
   * `gd`: runs a code‑gen script that outputs GDScript snippets (e.g., `export class TaxonomyLoader extends Node: ...`). You can also generate a CSV/TSV for easy import into Godot’s 
*Import* UI if you prefer manual steps.
   * `swift`: generates Swift structs/enums (`Taxonomy.swift`) and maybe a simple JSON decoder file.
3. **Copy‑forward** the generated assets to their respective source trees (JS under `client/rooms`, GDScript under `godot/data/`, Swift under `Sources/Generated/`).

All of this lives in *one* repo (or a monorepo) so that a single `git push` triggers builds for every language.

---

## 4. Concrete **Next‑Step Checklist** (you can start today)

| # | Task | Approx effort | Why it matters |
|---|------|---------------|----------------|
| 1️⃣ | **Formalise the taxonomy schema** – write a JSON Schema (`taxonomy-schema.json`) that captures `id`, `type`, `displayName`, `sceneRef`, `jsPath`, `gdScene`, `swiftResource`, 
any extra fields you need. | 30 min‑1 hr (depends on existing doc) | Single source of truth; auto‑validation later. |
| 2️⃣ | **Create a validation script** (`scripts/validate.mjs`) that reads every YAML/JSON file under `taxonomy/` and validates against the schema, printing human‑readable errors. | 
1‑2 hrs | CI will fail fast on drift. |
| 3️⃣ | **Write adapters** (one per language) – minimal wrappers that read the validated JSON and expose convenient data structures. | 2‑4 hrs each (≈6‑12 hrs total) | Keeps each 
runtime independent while sharing data. |
| 4️⃣ | **Add code‑gen templates**: <br>• JS: e.g., `templates/js-room.hbs` → writes out HTML files.<br>• GDScript: a script that emits `.gd` snippets or a CSV for Godot import.<br>• 
Swift: a script that generates `Taxonomy.swift`. | 3‑5 hrs per language (≈9‑15 hrs) | Removes manual duplication; updates propagate automatically. |
| 5️⃣ | **Integrate into CI** – e.g., GitHub Actions workflow that runs `npm run validate-taxonomy && npm run build` and optionally triggers a Godot export test, an iOS unit test run, 
etc. | 1‑2 hrs setup | Guarantees consistency across pushes. |
| 6️⃣ | **Document the “data contract”** – README section explaining how to add a new room/behaviour in taxonomy, what fields are required, and how each language reads them. | 30 min 
| Prevents future drift and onboarding friction. |

> **Start small.**  
> If you feel overwhelmed, start with #1 (schema) + #2 (validation). That alone will give you immediate visibility into mismatches between the languages.

---

## 5. How this aligns with your three “projects”

| Project | Immediate gain |
|---------|----------------|
| **Club Penguin Builder (JS)** | *One‑click generation* of chatroom HTML/JS from taxonomy, eliminating manual editing of `slide.ttx` and `grid-colors.ds`. The generated pages will 
be ready for the existing JS runtime. |
| **Take a Stab (GDScript)** | *Deterministic world state*. The same taxonomy JSON drives both scene placement and AI behaviour trees, meaning you can iterate on room layout in JS ↔︎ 
instant test the 3D layout in Godot. |
| **Master Dungeon (Swift)** | *Optional data sharing*. If you ever need a Swift‑only UI (e.g., iOS companion app), you already have a ready‑made JSON feed—no need to maintain 
another config. |

In short, the work you’ll do is **investing in a unified world model** that every component can lean on.

---

## 6. Quick “starter” implementation sketch

Below is a minimal but functional layout you could adopt right away.

```
repo/
├─ /gdads/                # Godot project (if needed)
│   └─ addons/
│       └─ taxonomy/     # maybe a C# or GDScript helper
├─ /webapp/              # Your existing web/front‑end (JS/TS)
│   └─ src/
│       ├─ components/
│       │   └─ RoomViewer.jsx
│       └─ data/
│           └─ rooms.json         # generated from taxonomy schema
├─ /shared/              # Common assets, languages, etc.
│   └─ schemas/
│       └─ room-schema.json      # JSON Schema for validation
└─ scripts/
    ├─ generate.js             # Node script that reads YAMLs and outputs:
    │   ├─ webapp/src/data/rooms.json
    │   ├─ godot/resource/room.gdres  (optional)
    │   └─ ... (any other artifacts)
    ├─ validate.mjs            # runs against json-schema
    └─ ci.yml                   # GitHub Actions workflow
```

**`generate.js`** could look like this (pseudo‑code):

```js
const fs = require('fs');
const path = require('path');

// 1. Load all YAML definitions from ./data/rooms/
const yamlFiles = glob.sync('./data/*.yaml');
const catalog = [];

for (const file of yamlFiles) {
  const content = yamlParse(fs.readFileSync(file, 'utf8'));
  catalog.push(content);
}

// 2. Validate against schema
const Ajv = require('ajv');
const ajv = new Ajv();
const validate = ajv.compile(roomSchema);
catalog.forEach(item => { if (!validate(item)) throw new Error(validate.errors); });

// 3. Write out JSON for the webapp
fs.writeFileSync('./webapp/src/data/rooms.json', JSON.stringify(catalog, null, 2));

// 4. Generate a Godot resource (optional)
// ... invoke godot CLI or your own exporter

// 5. Write TypeScript typings if desired
```

Running this script as part of your CI will keep everything in sync.

---

## 7. TL;DR – What to do next?

1. **Document the taxonomy** you already have (maybe in a Markdown file). Identify all fields that need to be shared across JS, GDScript, and Swift.
2. **Create a JSON Schema** for that taxonomy (use ` Draft-07` or later).
3. **Write a validation script** that can be run locally and in CI.
4. **Pick one language ecosystem to kick‑start first** – likely the WebApp/JS side because it’s already there, then mirror the changes into Godot and Swift.

Doing this will give you:
* ✅ A single source of truth for all three runtimes.
* ✅ Automated safety nets (no more broken promises).
* ✅ An easy way for new team members to understand the data model.

---

**Bottom line:** The path forward is to **centralise your world‑model**, make it machine‑readable, and then automatically surface that model to each of your runtimes. Starting with a 
clear schema and validation will pay dividends in maintainability, especially as you continue adding rooms, items, or quests across the three domains.

Happy building! 🎮✨ If you need help setting up any specific part (e.g., the Node script, Godot exporter, or iOS integration), just let me know which piece you’d like to tackle 
first.

>>> Okay, let's reorient. I'm glad you laid out what's relevant about each node.js/JavaScript proper, GDScript/other Godot methods, and Swift; I think that reveals that the Swift layer is 
... totally uncalled for, as all it ever had in it that was relevant was certain enemy behaviors, and these are not actually well-enough written by the previous agent that I'd ask for them
...  to be ported over in any way. (I've removed references to master-dungeon in the documentation accordingly.) So the next question is what language or languages it makes sense to use fo
... r coding the tool, which may include one or more of JS-like and Godot-like languages. Worth noting that the taxonomy files are about what should be generated by each of the prompt boxe
... s in the tool, which are on a smaller scale than the core design decisions we're discussing here. If they help, I can nonetheless copy-paste them in in some form or other, but I think 
... they're unnecessary at this stage. What's your take on the language question?

**Hey there!**

I’m excited to help figure out the right tech stack for your new tool! However, a good language/stack recommendation depends on **how** you want it to behave and **where** it will 
run. To give you the most practical guidance, I’d love to ask a few quick questions:

---

### 📋 Quick discovery

| # | Question | Why it matters |
|---|----------?|----------------|
| 1️⃣ | **What does this tool do?** (e.g., GUI prompt builder, file‑organizer, code generator, data visualizer, API wrapper…) | Different functionality maps to different primary 
languages and frameworks. |
| 2️⃣ | **Where will users interact with it?** <br>• **Desktop app** (native window) <br>• **Web‑app** (browser) <br>• **CLI tool only** <br>• **Both** (e.g., Electron, Tauri) | 
Determines if you need UI frameworks and cross‑platform support. |
| 3️⃣ | **Supported platforms?** (Windows/macOS/Linux, iOS/Android, etc.) | Influences which runtime/engine can ship easily to all targets. |
| 4️⃣ | **Existing codebase or third‑party integrations?** <br>• Already have a Python backend? <br>• Using Godot assets? <br>• Any libraries you must call? | You might want to reuse 
that foundation rather than start from scratch. |
| 5️⃣ | **Team expertise** (e.g., some devs are strong in JavaScript, others in C#)? | Pick a stack where your team can ship quickly and with low friction. |
| 6️⃣ | **Performance / size constraints?** <br>• Tiny CLI vs. heavy data‑processing <br>• Mobile‑friendly? | Some languages (e.g., Rust) excel at performance, others (Go, C#) are 
great for rapid UI dev. |
| 7️⃣ | **Future scalability?** <br>• Plan to add more features later?<br>• Need easy CI/CD? | Consider whether the chosen stack makes future changes painless. |

---

### 🎯 Common patterns I often see

| Scenario | Recommended core stack(s) | Typical tooling (1‑3 lines) |
|----------|----------------------------"> | --------------------------- |
| **Cross‑platform desktop UI** (menu bar, drag‑and‑drop, offline features) | • **Electron** (Node + Chromium)<br>• **Tauri** (Rust + Vite)<br>• **Qt/QML** <br>• **WinUI/WPF / 
SwiftUI** (if you want native per‑platform) | `npm create electron-app mytool` → plug in React/Vue/Svelte. |
| **Web service with API** (JSON endpoints, internal tooling) | • **Node/Express** + TypeScript <br>• **Python/Flask/Django** <br>• **Go** (very fast networking) | `npm init`, run 
`node server.js`. |
| **CLI‑only utility** (e.g., file renaming, text processing) | • **Rust** (fast, safe, great tooling)<br>• **Node** + `oclif` / `yargs`<br>• **Python** (if you love one‑liners) | 
`cargo new app && cargo run`, or `npm i -g yo generator-...`. |
| **Game/editor style tools** (dragging nodes, real‑time previews) | • **Godot Engine** (GDScript)<br>• **Unity** (C#)<br>• **Unreal** (Blueprints/CPP)<br>• **Electron + WebGL** (if 
you already have a web frontend) | Create a new Godot project → add scripts for tool logic. |
| **Data‑heavy analysis / ML** | • **Python** (pandas, scikit‑learn)<br>• **Julia** (scientific computing) <br>• **R** (statistics) | `pip install pandas matplotlib`. |
| **Mixed frontend/backend** where you already have a React/Vue SPA and need server logic | • Keep the **frontend** language as is (JS/TS, Vue/React), add **Node/Express** or 
**Go/Fiber** for backend. | Nothing fancy; just connect via HTTP. |

---

### 🔍 Example recommendations based on possible answers

| Goal | Suggested stack (quick starter) |
|------|---------------------------------|
| **Simple prompt‑builder GUI with drag‑and‑drop UI, works offline** | Electron + TypeScript + React (or Svelte/Vue). Use `electron-builder` for easy installers. |
| **Command‑line tool that reads/writes YAML/JSON and does some processing** | **Rust** (if you want zero‑cost performance & safety) **OR** Python if it’s a quick script. |
| **Editor for creating “prompt templates” with live preview** | **Godot** (GDScript) – great for UI, scene graphs, and built‑in visual scripting; or Unity + C#. |
| **Web app that lets users configure settings, then triggers background jobs** | **Node/Express** backend + **React/Vue** frontend. Consider **pm2** or Docker for deployment. |

---

### 📌 What to do next

1. **Answer the discovery questions above** (feel free to be as detailed or terse as you like).  
   - If you’d rather give a high‑level description, that’s fine too.
2. I can then: <br>• Draft a concrete tech‑stack plan. <br>• Outline an implementation roadmap (MVP features, module order). <br>• Suggest specific libraries and best practices.

---

**Bottom line:** Your goal is just to land on the right combination of language/framework that lets you build **what you need**, **where you need it**, and **with your team’s 
strengths**.

Let me know what answers you have (or even just a one‑sentence summary), and we can get you a solid recommendation! 🚀

>>> 1. Much like the Club Penguin Builder or Cry with Me, it should have two interfaces. One should be a simple set of text boxes that define core parameters of Realms. When the user activ
... ates the Cry with Me-derived box to go build a Realm, the tool should then go and do that. The other, which is sidelined in Cry with Me but core to Club Penguin Builder, is the one whe
... re the user actually goes and plays Realms. In the Club Penguin Builder, this is built with JavaScript the same way the Builder interfaces in CPB and CwM are; however, here, since 3D r
... endering might well be required (unless going with a Warcraft/Diablo-like top-down/isometric view), that might be good to build with a different language (and so the Builder might be d
... ifferently-built accordingly). 2. Website if possible; I'd rather not require users to download a client the way WoW and FF14 do. 3. Every platform if possible; this doesn't come out t
... he best in CPB, but maybe it could here in mobile landscape (not as doable in CPB due to its chat log positioning; maybe I should fix that there?). 4. I already have comprehensive JS b
... ackends for CPB and, to a degree, CwM, as well as what I need in Godot for Take a Stab, all of which could be reused. 5. I'm the sole developer, and I'm most skilled in Python, but the
... se days I usually have AI code for me, and am getting to understand some of whatever's used. 6. Performance probably not required, given how slow Classic was (authenticity ftw! ;P ), t
... hough mobile-friendliness would be nice to have despite not being around in Classic (but not required). 7. There will definitely be lots more features in the future; the current look i
... s what's required for an MVP, and I'm expecting to need to heavily overhaul things, discover I forgot a lot, etc.

## TL;DR – My recommended architecture for **The Real Classic**

| Layer | What it does | Suggested stack (why it fits your constraints) |
|-------|--------------| -------------------------------------------------|
| **1️⃣ Realm‑building UI** | Simple text‑boxes → “Create Realm” request  <br>Shows preview, validates JSON/YAML, hits a backend API. | **Web‑first** – React + TypeScript (Vite)  
<br>PWA / Tailwind CSS for responsive desktop & mobile layouts. |
| **2️⃣ Real‑time game client** | The actual “play” experience – 3D (or isometric) world, avatars, networking to the server. | **Godot 4.x** (GDScript + optional C#)  <br>• Export to 
WebGL/WASM → runs in a `<canvas>` inside the same site (no native download). <br>• Native builds for Windows/macOS/Linux/iOS/Android if you later ship a desktop/mobile app. |
| **3️⃣ Backend API & logic** | Persists realm definitions, processes creation requests, supplies world‑data to the game client, handles authentication/authorization, any background 
jobs (e.g., asset generation). | **Node.js + TypeScript** (keeps your existing CPB/CwM JS code untouched) <br>• Express / Fastify for REST endpoints. <br>• Socket.IO or native `ws` 
for bidirectional “action” streams (commands, chat, player sync). |
| **4️⃣ Mobile‑friendly UI fallback** | If you ever want a pure mobile app, just drop the web PWA in a shell (e.g., Capacitor) or use Godot's built‑in iOS/Android exports. | 
**Capacitor/Capacitor‑WebView** for a “mobile‑shell” around the same React/Vite site (optional). |
| **5️⃣ DevOps & delivery** | CI/CD, versioning, testing, packaging of WebGL / native builds, containerisation. | **Docker + GitHub Actions** <br>• Separate pipelines: `frontend` 
(Vite), `backend` (Node/Typescript), `godot-web` (export). <br>• Optional Electron/Tauri shell for a “desktop app” that just loads the PWA and optionally embeds a Godot native 
window. |

---

## 1️⃣ Why React + TypeScript for the builder UI?

* **Rapid UI dev** – component‑based, state‑management (`Zustand`/`Redux Toolkit`) lets you keep the simple text‑box forms maintainable as more fields are added.
* **Responsive & PWA** – Tailwind + `vite-plugin-pwa` → works nicely on desktop, tablet and phone (the “simple set of text boxes” can shrink to a modal on mobile).
* **Type safety** – TypeScript catches mistyped property names early, which is valuable when you start wiring up realm‑definition schemas.
* **Reuse existing code** – The builder UI can be built exactly like CPB/CwM’s current JS frontends (if any) by importing their React components or even by running those client‑side 
scripts in the same page.

---

## 2️⃣ Why Godot for the “play” side?

| Requirement | How Godot solves it |
|-------------|---------------------" |-
| **3D / isometric world** (or 2D “top‑down”) | Built‑in 3D engine, particle system, physics. You can import assets from Unity/Blender or create them natively. |
| **Cross‑platform without a native client download** | Export to **HTML5/WASM** → runs in the browser (`.html` file). No installer needed – just open a URL (the same domain you host 
everything under). |
| **Mobile friendliness** | Godot can export to iOS/Android; if you ever want a stand‑alone mobile app, you already have the source code. |
| **Fast iteration for a solo dev + AI assistance** | GDScript is very close to Python syntax → easy for you (and any LLM) to write scripts on. Also supports C# if you prefer that 
language later. |
| **Networking** | Built‑in `SceneTree` networking (RPC) and `MultiplayerAPI`; can also talk to your Node/JS backend via HTTP/WebSocket – perfect for syncing players, realm state, 
etc. |
| **Existing Godot assets (Take a Stab)** | Reuse the same project; you just need to hook in new assets, levels, or UI overlays. |

**Packaging options**

* **WebGL (HTML5) export** → drop `index.html` + `engine.wasm`/`game.pck` into your web root. This is the lightest solution and works everywhere.
* **Native builds** (iOS, Android, macOS, Windows, Linux) – use Godot’s project exporter; you get an `.app`/`.exe` that can be distributed through stores or side‑loaded.

You could even keep both paths around and let the user automatically choose based on capability (e.g., detect if running in a browser vs native OS).

---

## 3️⃣ Backend / API Design

### Core Services

| Service | Purpose |
|---------|---------|
| **RealmService** | Create, validate, store realm definitions (JSON). Provides CRUD endpoints. |
| **WorldStateService** | Persistent map of player positions, chat, etc. Can be a simple key‑value store (Redis) or a small SQL DB for scaling. |
| **AuthService** | Handles user sessions (JWT or cookie), registration. |
| **NotificationService** | Broadcasts system events (e.g., new realm created, player joined). |

All services expose REST/JSON APIs that the front‑end can call. You can implement them in a single Node/TS project, using `nestjs` and `ts-node`.

### Front‑End Interaction Flow (example)

1. **Create Realm** → UI sends `{ name, seed, settings }` to `/api/realms`.
2. Server validates, saves, emits `realm:created`. The response includes the realm’s *instance id* (e.g., URL slug).
3. UI loads the realm via an embedded `<canvas>` tag or WebGPU view.
4. **Enter World** → Client requests `/api/rooms/{id}/join` (POST) → server generates a session token.
5. Server pushes real‑time updates via **WebSocket** (`socket.io`) for chat, player movement, etc.

All of this can be implemented with Node + Express + Socket.io; the Godot client can connect to the same socket (or use HTTP REST if you prefer a pure game‑only protocol).

---

## 4️⃣ Deployment & DevOps

### Docker Compose (example)

```yaml
version: "3.8"
services:
  api:
    build: ./api   # Node.js + Nest
    ports: ["3000:3000"]
    environment:
      - NODE_ENV=production
    depends_on: [redis]

  redis:
    image: redis:alpine
    ports: ["6379:6379"]

  web:
    # Vite React build (or your static site)
    image: nginx:stable-alpine
    ports: ["80:80"]
    volumes:
      - ./dist:/usr/share/nginx/html
```

*If you need a native client, you can add an `electron` service that loads the index.html and injects the Godot runtime.*

### CI/CD (GitHub Actions)

- **Lint/Type‑check**: ESLint, Prettier, tsc.
- **Unit tests** (`jest`, `mocha`).
- **Integration test**: spin up Docker compose, hit API endpoints.
- **Deploy**:
  - For web: run `npm run build` and push artifacts to a static host (Netlify/Vercel).
  - For native Godot builds: export with GitHub Actions using the official `godot-export` action; publish releases.

---

## 5️⃣ Roadmap – From Vision to Reality

| Phase | Goal | Key Tasks |
|------|------|-----------|
| **Phase 1** (Now) | Prototype the core experience. | • Set up Node/Nest API skeleton.<br>• Create a simple “Hello Realm” UI using React + Vite.<br>• Build a minimal Godot scene 
with a cube and network stub. |
| **Phase 2** (2‑4 weeks) | Full web client & backend. | • Implement CRUD for realms.<br>• Add WebSocket chat.<br>• Integrate Godot as an overlay/webview inside Electron window. |
| **Phase 3** (4‑8 weeks) | Polish UI & cross‑platform builds. | • Port Godot scene to full 3D world.<br>• Export native binaries for iOS/Android/Windows/macOS.<br>• Create 
installers for desktop. |
| **Phase 4** (Ongoing) | Scale & maintain. | • Add Redis/PostgreSQL for persistence.<br>• Implement matchmaking, leaderboards.<br>• Set up automated deployment pipelines. |

---

## 6 – Bonus: Keeping the “Open‑World” Feel

Since you mentioned an open world with infinite or semi‑infinite terrain, consider:

1. **Procedural Generation** – Use a server‑side algorithm (e.g., Perlin noise) to seed realms on demand; cache generated chunks in Redis.
2. **Dynamic Loading** – Let the Godot client request chunk metadata from the API and load only visible areas (similar to Minecraft’s classic approach).
3. **Social Features** – Allow users to “follow” friends, invite them to private islands, or visit public worlds.

---

## 7 – Summary

* **Frontend UI**: React + Vite (TypeScript) → simple, modern SPA.
* **Game Logic & World Rendering**: Godot Engine → native browser/web build for instant play; optional native builds for richer experience.
* **Backend API**: NestJS / Node.js → RESTful endpoints + WebSocket real‑time updates.
* **Persistence**: Redis / PostgreSQL (optional) for world state, user profiles.
* **Deployment**: Docker Compose + GitHub Actions (CI/CD). Nginx/Vercel for static assets, Electron wrapper optional for desktop.

This stack lets you:

* Launch quickly with a working web version that runs in the browser.
* Expand to native platforms when needed without rewriting huge chunks of code.
* Keep development pain‑free: reuse NestJS for both server and tooling, keep Godot focused on rendering, and use React for a familiar developer experience.

If any part feels like it needs deeper dive (e.g., specific networking protocols, authentication flows, or asset pipeline), just shout—I'm happy to flesh those details out too! Happy 
building 🚀.

# Existing Code Snippets

Below are some key chunks of code that may well be critical to the desired creation of The Real Classic with a **simplified language stack mostly drawing on what already exists**.

## Club Penguin Builder

### clubPenguins.js

import db from './db.js';
import { getPenguinCountForCP } from './state.js';

// Determine next ID from existing data
const maxRow = db.prepare('SELECT id FROM club_penguins ORDER BY CAST(SUBSTR(id, 4) AS INTEGER) DESC LIMIT 1').get();
let nextId = maxRow ? parseInt(maxRow.id.slice(3)) + 1 : 1;

function rowToCP(row) {
  return {
    id: row.id,
    name: row.name,
    rooms: JSON.parse(row.rooms),
    spawnRoom: row.spawn_room,
    spawnConfig: row.spawn_config ? JSON.parse(row.spawn_config) : { mode: 'fixed', x: 400, y: 350 },
    creatorId: row.creator_id || null,
    createdAt: row.created_at,
  };
}

export function createClubPenguin(name, rooms, creatorId = null, spawnConfig = null) {
  const id = 'cp_' + (nextId++);
  const spawnRoom = Object.keys(rooms).find(k => !rooms[k].hidden) || Object.keys(rooms)[0];
  const createdAt = Date.now();
  const sc = spawnConfig || { mode: 'fixed', x: 400, y: 350 };
  db.prepare('INSERT INTO club_penguins (id, name, rooms, spawn_room, created_at, creator_id, spawn_config) VALUES (?, ?, ?, ?, ?, ?, ?)').run(id, name, JSON.stringify(rooms), spawnRoom, createdAt, creatorId, JSON.stringify(sc));
  return { id, name, rooms, spawnRoom, spawnConfig: sc, creatorId, createdAt };
}

export function getClubPenguin(cpId) {
  const row = db.prepare('SELECT * FROM club_penguins WHERE id = ?').get(cpId);
  return row ? rowToCP(row) : undefined;
}

export function updateClubPenguin(cpId, name, rooms, spawnConfig = null) {
  const spawnRoom = Object.keys(rooms).find(k => !rooms[k].hidden) || Object.keys(rooms)[0];
  if (spawnConfig) {
    const result = db.prepare('UPDATE club_penguins SET name = ?, rooms = ?, spawn_room = ?, spawn_config = ? WHERE id = ?').run(name, JSON.stringify(rooms), spawnRoom, JSON.stringify(spawnConfig), cpId);
    if (result.changes === 0) return null;
    return { id: cpId, name, rooms, spawnRoom, spawnConfig };
  }
  const result = db.prepare('UPDATE club_penguins SET name = ?, rooms = ?, spawn_room = ? WHERE id = ?').run(name, JSON.stringify(rooms), spawnRoom, cpId);
  if (result.changes === 0) return null;
  const existing = getClubPenguin(cpId);
  return { id: cpId, name, rooms, spawnRoom, spawnConfig: existing?.spawnConfig || { mode: 'fixed', x: 400, y: 350 } };
}

export function updateRoomItemPosition(cpId, roomId, itemIndex, x, y) {
  const cp = getClubPenguin(cpId);
  if (!cp || !cp.rooms[roomId]) return false;
  const items = cp.rooms[roomId].items;
  if (!items || itemIndex < 0 || itemIndex >= items.length) return false;
  items[itemIndex].x = x;
  items[itemIndex].y = y;
  db.prepare('UPDATE club_penguins SET rooms = ? WHERE id = ?').run(JSON.stringify(cp.rooms), cpId);
  return true;
}

export function listClubPenguins() {
  const rows = db.prepare(`
    SELECT cp.*, (SELECT MAX(launched_at) FROM parties WHERE cp_id = cp.id) AS latest_party
    FROM club_penguins cp
  `).all();
  return rows.map(row => ({
    id: row.id,
    name: row.name,
    roomCount: Object.keys(JSON.parse(row.rooms)).length,
    penguinCount: getPenguinCountForCP(row.id),
    creatorId: row.creator_id || null,
    createdAt: row.created_at,
    latestParty: row.latest_party || null,
  }));
}

### db.js

import Database from 'better-sqlite3';
import { mkdirSync } from 'fs';

mkdirSync('data', { recursive: true });

const db = new Database('data/clubpenguins.db');
db.pragma('journal_mode = WAL');

db.exec(`
  CREATE TABLE IF NOT EXISTS club_penguins (
    id TEXT PRIMARY KEY,
    name TEXT NOT NULL,
    rooms TEXT NOT NULL,
    spawn_room TEXT NOT NULL,
    created_at INTEGER NOT NULL
  )
`);

db.exec(`
  CREATE TABLE IF NOT EXISTS accounts (
    id TEXT PRIMARY KEY,
    username TEXT UNIQUE NOT NULL,
    password_hash TEXT NOT NULL,
    created_at INTEGER NOT NULL
  )
`);

db.exec(`
  CREATE TABLE IF NOT EXISTS parties (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    cp_id TEXT NOT NULL,
    name TEXT NOT NULL,
    launched_at INTEGER NOT NULL
  )
`);

db.exec(`
  CREATE TABLE IF NOT EXISTS sessions (
    token TEXT PRIMARY KEY,
    account_id TEXT NOT NULL,
    created_at INTEGER NOT NULL
  )
`);

db.exec(`
  CREATE TABLE IF NOT EXISTS account_preferences (
    account_id TEXT PRIMARY KEY,
    sort_field TEXT NOT NULL DEFAULT 'name',
    sort_dir TEXT NOT NULL DEFAULT 'asc'
  )
`);

db.exec(`
  CREATE TABLE IF NOT EXISTS catalog_items (
    id TEXT PRIMARY KEY,
    name TEXT NOT NULL,
    image TEXT NOT NULL,
    uploader_id TEXT,
    created_at INTEGER NOT NULL,
    width INTEGER,
    height INTEGER
  )
`);

db.exec(`
  CREATE TABLE IF NOT EXISTS account_inventory (
    account_id TEXT NOT NULL,
    catalog_id TEXT NOT NULL,
    name TEXT NOT NULL,
    image TEXT NOT NULL,
    wear_offset_x INTEGER NOT NULL DEFAULT 0,
    wear_offset_y INTEGER NOT NULL DEFAULT 0,
    wear_width INTEGER NOT NULL DEFAULT 40,
    wear_height INTEGER NOT NULL DEFAULT 40,
    equipped INTEGER NOT NULL DEFAULT 0,
    UNIQUE(account_id, catalog_id, wear_offset_x, wear_offset_y, wear_width, wear_height)
  )
`);

// Migration: add creator_id to club_penguins
const columns = db.prepare("PRAGMA table_info(club_penguins)").all().map(c => c.name);
if (!columns.includes('creator_id')) {
  db.exec('ALTER TABLE club_penguins ADD COLUMN creator_id TEXT');
}

// Migration: add attribution to catalog_items
const catalogCols = db.prepare("PRAGMA table_info(catalog_items)").all().map(c => c.name);
if (!catalogCols.includes('attribution')) {
  db.exec("ALTER TABLE catalog_items ADD COLUMN attribution TEXT NOT NULL DEFAULT ''");
}

// Migration: add equip_order, attribution, collected_at to account_inventory
const invCols = db.prepare("PRAGMA table_info(account_inventory)").all().map(c => c.name);
if (!invCols.includes('equip_order')) {
  db.exec('ALTER TABLE account_inventory ADD COLUMN equip_order INTEGER NOT NULL DEFAULT 0');
}
if (!invCols.includes('attribution')) {
  db.exec("ALTER TABLE account_inventory ADD COLUMN attribution TEXT NOT NULL DEFAULT ''");
}
if (!invCols.includes('collected_at')) {
  db.exec('ALTER TABLE account_inventory ADD COLUMN collected_at INTEGER NOT NULL DEFAULT 0');
}

// Migration: add catalog/inventory sort prefs to account_preferences
const prefCols = db.prepare("PRAGMA table_info(account_preferences)").all().map(c => c.name);
if (!prefCols.includes('catalog_sort_field')) {
  db.exec("ALTER TABLE account_preferences ADD COLUMN catalog_sort_field TEXT NOT NULL DEFAULT 'name'");
  db.exec("ALTER TABLE account_preferences ADD COLUMN catalog_sort_dir TEXT NOT NULL DEFAULT 'asc'");
  db.exec("ALTER TABLE account_preferences ADD COLUMN inv_sort_field TEXT NOT NULL DEFAULT 'name'");
  db.exec("ALTER TABLE account_preferences ADD COLUMN inv_sort_dir TEXT NOT NULL DEFAULT 'asc'");
}

// Migration: add hide_emoji to account_preferences
if (!prefCols.includes('hide_emoji')) {
  db.exec("ALTER TABLE account_preferences ADD COLUMN hide_emoji INTEGER NOT NULL DEFAULT 0");
}

// Favorites table
db.exec(`
  CREATE TABLE IF NOT EXISTS account_favorites (
    account_id TEXT NOT NULL,
    catalog_id TEXT NOT NULL,
    UNIQUE(account_id, catalog_id)
  )
`);

// Migration: add pearl_balance to accounts
const acctCols = db.prepare("PRAGMA table_info(accounts)").all().map(c => c.name);
if (!acctCols.includes('pearl_balance')) {
  db.exec('ALTER TABLE accounts ADD COLUMN pearl_balance INTEGER NOT NULL DEFAULT 0');
}

// Migration: add price to catalog_items
const catCols2 = db.prepare("PRAGMA table_info(catalog_items)").all().map(c => c.name);
if (!catCols2.includes('price')) {
  db.exec('ALTER TABLE catalog_items ADD COLUMN price INTEGER NOT NULL DEFAULT 0');
}

// Pearl transactions
db.exec(`
  CREATE TABLE IF NOT EXISTS pearl_transactions (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    account_id TEXT NOT NULL,
    amount INTEGER NOT NULL,
    type TEXT NOT NULL,
    reference TEXT,
    created_at INTEGER NOT NULL DEFAULT (unixepoch())
  )
`);

// Stripe checkout sessions
db.exec(`
  CREATE TABLE IF NOT EXISTS stripe_sessions (
    session_id TEXT PRIMARY KEY,
    account_id TEXT NOT NULL,
    pearls INTEGER NOT NULL,
    status TEXT NOT NULL DEFAULT 'pending',
    created_at INTEGER NOT NULL DEFAULT (unixepoch())
  )
`);

// Item purchases (tracks who bought what)
db.exec(`
  CREATE TABLE IF NOT EXISTS item_purchases (
    account_id TEXT NOT NULL,
    catalog_id TEXT NOT NULL,
    purchased_at INTEGER NOT NULL DEFAULT (unixepoch()),
    UNIQUE(account_id, catalog_id)
  )
`);

// Migration: add Stripe Connect fields to accounts
const acctCols2 = db.prepare("PRAGMA table_info(accounts)").all().map(c => c.name);
if (!acctCols2.includes('stripe_connect_id')) {
  db.exec("ALTER TABLE accounts ADD COLUMN stripe_connect_id TEXT");
  db.exec("ALTER TABLE accounts ADD COLUMN stripe_onboarding_complete INTEGER NOT NULL DEFAULT 0");
}

// Cash-out transfers
db.exec(`
  CREATE TABLE IF NOT EXISTS cashout_transfers (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    account_id TEXT NOT NULL,
    pearls INTEGER NOT NULL,
    amount_cents INTEGER NOT NULL,
    stripe_transfer_id TEXT,
    status TEXT NOT NULL DEFAULT 'pending',
    error TEXT,
    created_at INTEGER NOT NULL DEFAULT (unixepoch())
  )
`);

// Migration: add attribution_name to accounts
const acctCols3 = db.prepare("PRAGMA table_info(accounts)").all().map(c => c.name);
if (!acctCols3.includes('attribution_name')) {
  db.exec("ALTER TABLE accounts ADD COLUMN attribution_name TEXT NOT NULL DEFAULT ''");
}

// Game bundles (collections of items-with-behaviors)
db.exec(`
  CREATE TABLE IF NOT EXISTS catalog_games (
    id TEXT PRIMARY KEY,
    name TEXT NOT NULL,
    creator_id TEXT NOT NULL,
    items TEXT NOT NULL,
    width INTEGER NOT NULL,
    height INTEGER NOT NULL,
    gravity_direction TEXT,
    price INTEGER NOT NULL DEFAULT 0,
    attribution TEXT NOT NULL DEFAULT '',
    created_at INTEGER NOT NULL DEFAULT (unixepoch())
  )
`);

// Game purchases (tracks who bought what game)
db.exec(`
  CREATE TABLE IF NOT EXISTS game_purchases (
    account_id TEXT NOT NULL,
    game_id TEXT NOT NULL,
    purchased_at INTEGER NOT NULL DEFAULT (unixepoch()),
    UNIQUE(account_id, game_id)
  )
`);

// Migration: add spawn_config to club_penguins
const cpCols2 = db.prepare("PRAGMA table_info(club_penguins)").all().map(c => c.name);
if (!cpCols2.includes('spawn_config')) {
  db.exec("ALTER TABLE club_penguins ADD COLUMN spawn_config TEXT NOT NULL DEFAULT '{\"mode\":\"fixed\",\"x\":400,\"y\":350}'");
}

// Migration: add width/height to catalog_items and backfill from stored images
const catCols = db.prepare("PRAGMA table_info(catalog_items)").all().map(c => c.name);
if (!catCols.includes('width')) {
  db.exec("ALTER TABLE catalog_items ADD COLUMN width INTEGER");
  db.exec("ALTER TABLE catalog_items ADD COLUMN height INTEGER");
  // Backfill dimensions from stored base64 images
  const items = db.prepare("SELECT id, image FROM catalog_items").all();
  const update = db.prepare("UPDATE catalog_items SET width = ?, height = ? WHERE id = ?");
  for (const item of items) {
    try {
      const match = item.image.match(/^data:image\/\w+;base64,(.+)$/);
      if (!match) continue;
      const buf = Buffer.from(match[1], 'base64');
      let w, h;
      // PNG
      if (buf[0] === 0x89 && buf[1] === 0x50) { w = buf.readUInt32BE(16); h = buf.readUInt32BE(20); }
      // JPEG
      else if (buf[0] === 0xFF && buf[1] === 0xD8) {
        let off = 2;
        while (off < buf.length - 8) {
          if (buf[off] !== 0xFF) break;
          const m = buf[off + 1];
          if (m === 0xC0 || m === 0xC2) { w = buf.readUInt16BE(off + 7); h = buf.readUInt16BE(off + 5); break; }
          off += 2 + buf.readUInt16BE(off + 2);
        }
      }
      // GIF
      else if (buf[0] === 0x47 && buf[1] === 0x49) { w = buf.readUInt16LE(6); h = buf.readUInt16LE(8); }
      if (w && h) update.run(w, h, item.id);
    } catch (e) { /* skip unparseable */ }
  }
}

// Stats persistence tables
db.exec(`
  CREATE TABLE IF NOT EXISTS stats_operations (
    operation TEXT PRIMARY KEY,
    count INTEGER NOT NULL DEFAULT 0,
    total_ms REAL NOT NULL DEFAULT 0,
    max_ms REAL NOT NULL DEFAULT 0
  )
`);

db.exec(`
  CREATE TABLE IF NOT EXISTS stats_cp_operations (
    cp_id TEXT NOT NULL,
    operation TEXT NOT NULL,
    count INTEGER NOT NULL DEFAULT 0,
    total_ms REAL NOT NULL DEFAULT 0,
    max_ms REAL NOT NULL DEFAULT 0,
    UNIQUE(cp_id, operation)
  )
`);

db.exec(`
  CREATE TABLE IF NOT EXISTS stats_meta (
    key TEXT PRIMARY KEY,
    value TEXT NOT NULL
  )
`);

export default db;

### index.js

import express from 'express';
import { createServer } from 'http';
import { Server } from 'socket.io';
import { fileURLToPath } from 'url';
import { dirname, join } from 'path';
import { adjustMoveTarget, lineRectIntersection, simulateSkid, simulateGravity } from '../shared/collision.js';
import db from './db.js';
import { getClubPenguin, createClubPenguin, updateClubPenguin, updateRoomItemPosition, listClubPenguins } from './clubPenguins.js';
import { createAccount, login, getAccount, createSession, getSession, deleteSession, updateAttributionName } from './accounts.js';
import { launchParty, getPartyLog } from './parties.js';
import { createCatalogItem, getCatalogItem, listCatalogItems, catalogItemExistsByName } from './catalog.js';
import { createGame, getGame, listGames, gameExistsByName } from './games.js';
import { loadInventory, saveInventoryItem, setEquipped } from './inventory.js';
import { moderateUpload } from './moderation.js';
import { trackStart, getStats, getCPStats, getStatsSince, resetStats } from './stats.js';
import {
  isStripeEnabled, getBundles, createCheckoutSession, handleWebhook,
  getBalance, getTransactions, purchaseItem, canAccessItem, getPurchasedItems,
  acquireFreeItem, createConnectAccount, createOnboardingLink, getConnectStatus, cashOut,
  purchaseGame, canAccessGame, acquireFreeGame, getPurchasedGames,
} from './payments.js';
import {
  addPenguin,
  removePenguin,
  getPenguin,
  movePenguin,
  addToInventory,
  equipItem,
  unequipItem,
  changePenguinRoom,
  getPenguinsInCPRoom,
  getPenguinCountForCP,
  startDrag,
  moveDragItem,
  stopDrag,
  getDragOverrides,
  clearDragLocks,
  setItemPosition,
} from './state.js';

const __dirname = dirname(fileURLToPath(import.meta.url));

const BLOCKED_COUNTRIES = ['CA', 'GB'];

const app = express();

// Geo-restriction: block countries with active Club Penguin trademarks
// Uses Fly.io's Fly-Client-Country header (free, no lookup needed); skips in local dev
app.use((req, res, next) => {
  const country = req.headers['fly-client-country'];
  if (country && BLOCKED_COUNTRIES.includes(country)) {
    return res.status(451).send('Club Penguin Builder is not available in your region due to trademark restrictions.');
  }
  next();
});

// Stripe webhook needs raw body (must be before express.json)
app.post('/api/payments/webhook', express.raw({ type: 'application/json' }), (req, res) => {
  try {
    handleWebhook(req.body, req.headers['stripe-signature']);
    res.json({ received: true });
  } catch (err) {
    console.warn('Stripe webhook error:', err.message);
    res.status(400).json({ error: err.message });
  }
});

app.use(express.json({ limit: '1mb' }));
app.use('/assets', express.static(join(__dirname, '..', 'dist', 'assets'), {
  maxAge: '1y',
  immutable: true,
}));
app.use(express.static(join(__dirname, '..', 'dist')));

let io;

// Track all HTTP requests (lightweight — just count + time)
app.use((req, res, next) => {
  const done = trackStart('http:all');
  res.on('finish', done);
  next();
});

// CPU/time stats endpoint (sorted by total time descending)
app.get('/api/admin/stats', (req, res) => {
  const raw = getStats();
  const sorted = Object.entries(raw)
    .sort((a, b) => b[1].totalMs - a[1].totalMs)
    .map(([name, s]) => ({ operation: name, ...s }));
  const uptime = Math.round(process.uptime());
  const mem = process.memoryUsage();
  // Per-CP breakdown sorted by total time, with names
  const rawCP = getCPStats();
  const cpBreakdown = Object.entries(rawCP)
    .sort((a, b) => b[1].totalMs - a[1].totalMs)
    .map(([cpId, data]) => {
      const cp = getClubPenguin(cpId);
      return { cpId, name: cp ? cp.name : '(deleted)', ...data };
    });

  res.json({
    sinceTimestamp: getStatsSince(),
    uptimeSeconds: uptime,
    memoryMB: {
      rss: Math.round(mem.rss / 1024 / 1024),
      heapUsed: Math.round(mem.heapUsed / 1024 / 1024),
      heapTotal: Math.round(mem.heapTotal / 1024 / 1024),
    },
    operations: sorted,
    clubPenguins: cpBreakdown,
  });
});

app.post('/api/admin/stats/reset', (req, res) => {
  resetStats();
  res.json({ ok: true });
});

// Auth endpoints
app.post('/api/auth/register', async (req, res) => {
  const { username, password } = req.body;
  if (!username || !/^[a-zA-Z0-9_]{1,20}$/.test(username)) {
    return res.status(400).json({ error: 'Username must be 1-20 alphanumeric characters or underscores' });
  }
  if (!password || password.length < 6) {
    return res.status(400).json({ error: 'Password must be at least 6 characters' });
  }
  const account = await createAccount(username, password);
  if (!account) {
    return res.status(409).json({ error: 'Username already taken' });
  }
  const token = createSession(account.id);
  res.json({ token, account });
});

app.post('/api/auth/login', async (req, res) => {
  const { username, password } = req.body;
  if (!username || !password) {
    return res.status(400).json({ error: 'Username and password are required' });
  }
  const account = await login(username, password);
  if (!account) {
    return res.status(401).json({ error: 'Invalid username or password' });
  }
  const token = createSession(account.id);
  res.json({ token, account });
});

app.post('/api/auth/logout', (req, res) => {
  const token = (req.headers.authorization || '').replace('Bearer ', '');
  if (token) deleteSession(token);
  res.json({ ok: true });
});

app.get('/api/auth/me', (req, res) => {
  const token = (req.headers.authorization || '').replace('Bearer ', '');
  const accountId = getSession(token);
  if (!accountId) return res.status(401).json({ error: 'Not authenticated' });
  const account = getAccount(accountId);
  if (!account) return res.status(401).json({ error: 'Not authenticated' });
  res.json({ account });
});

// Update attribution name
app.put('/api/auth/attribution-name', (req, res) => {
  const token = (req.headers.authorization || '').replace('Bearer ', '');
  const accountId = getSession(token);
  if (!accountId) return res.status(401).json({ error: 'Not authenticated' });
  const { attributionName } = req.body;
  if (typeof attributionName !== 'string' || attributionName.length > 60) {
    return res.status(400).json({ error: 'Attribution name must be 60 characters or fewer' });
  }
  updateAttributionName(accountId, attributionName.trim());
  res.json({ ok: true });
});

// Sort preferences
app.get('/api/auth/preferences', (req, res) => {
  const token = (req.headers.authorization || '').replace('Bearer ', '');
  const accountId = getSession(token);
  if (!accountId) return res.status(401).json({ error: 'Not authenticated' });
  const row = db.prepare('SELECT sort_field, sort_dir, catalog_sort_field, catalog_sort_dir, inv_sort_field, inv_sort_dir, hide_emoji FROM account_preferences WHERE account_id = ?').get(accountId);
  res.json(row || { sort_field: 'name', sort_dir: 'asc', catalog_sort_field: 'name', catalog_sort_dir: 'asc', inv_sort_field: 'name', inv_sort_dir: 'asc', hide_emoji: 0 });
});

app.put('/api/auth/preferences', (req, res) => {
  const token = (req.headers.authorization || '').replace('Bearer ', '');
  const accountId = getSession(token);
  if (!accountId) return res.status(401).json({ error: 'Not authenticated' });
  const { sort_field, sort_dir, catalog_sort_field, catalog_sort_dir, inv_sort_field, inv_sort_dir, hide_emoji } = req.body;
  const validCpFields = ['name', 'createdAt', 'latestParty', 'penguinCount', 'roomCount'];
  const validItemFields = ['name', 'createdAt', 'attribution'];
  const validDirs = ['asc', 'desc'];

  // Validate whichever fields are provided
  if (sort_field !== undefined && (!validCpFields.includes(sort_field) || !validDirs.includes(sort_dir))) {
    return res.status(400).json({ error: 'Invalid sort options' });
  }
  if (catalog_sort_field !== undefined && (!validItemFields.includes(catalog_sort_field) || !validDirs.includes(catalog_sort_dir))) {
    return res.status(400).json({ error: 'Invalid catalog sort options' });
  }
  if (inv_sort_field !== undefined && (!validItemFields.includes(inv_sort_field) || !validDirs.includes(inv_sort_dir))) {
    return res.status(400).json({ error: 'Invalid inventory sort options' });
  }

  // Upsert all preference columns
  const existing = db.prepare('SELECT * FROM account_preferences WHERE account_id = ?').get(accountId);
  const merged = {
    sort_field: sort_field || (existing?.sort_field ?? 'name'),
    sort_dir: sort_dir || (existing?.sort_dir ?? 'asc'),
    catalog_sort_field: catalog_sort_field || (existing?.catalog_sort_field ?? 'name'),
    catalog_sort_dir: catalog_sort_dir || (existing?.catalog_sort_dir ?? 'asc'),
    inv_sort_field: inv_sort_field || (existing?.inv_sort_field ?? 'name'),
    inv_sort_dir: inv_sort_dir || (existing?.inv_sort_dir ?? 'asc'),
    hide_emoji: hide_emoji !== undefined ? (hide_emoji ? 1 : 0) : (existing?.hide_emoji ?? 0),
  };
  db.prepare(
    `INSERT INTO account_preferences (account_id, sort_field, sort_dir, catalog_sort_field, catalog_sort_dir, inv_sort_field, inv_sort_dir, hide_emoji)
     VALUES (?, ?, ?, ?, ?, ?, ?, ?)
     ON CONFLICT(account_id) DO UPDATE SET sort_field = ?, sort_dir = ?, catalog_sort_field = ?, catalog_sort_dir = ?, inv_sort_field = ?, inv_sort_dir = ?, hide_emoji = ?`
  ).run(accountId, merged.sort_field, merged.sort_dir, merged.catalog_sort_field, merged.catalog_sort_dir, merged.inv_sort_field, merged.inv_sort_dir, merged.hide_emoji,
        merged.sort_field, merged.sort_dir, merged.catalog_sort_field, merged.catalog_sort_dir, merged.inv_sort_field, merged.inv_sort_dir, merged.hide_emoji);
  res.json(merged);
});

// Favorites
app.get('/api/auth/favorites', (req, res) => {
  const token = (req.headers.authorization || '').replace('Bearer ', '');
  const accountId = getSession(token);
  if (!accountId) return res.status(401).json({ error: 'Not authenticated' });
  const rows = db.prepare('SELECT catalog_id FROM account_favorites WHERE account_id = ?').all(accountId);
  res.json(rows.map(r => r.catalog_id));
});

app.put('/api/auth/favorites/:catalogId', (req, res) => {
  const token = (req.headers.authorization || '').replace('Bearer ', '');
  const accountId = getSession(token);
  if (!accountId) return res.status(401).json({ error: 'Not authenticated' });
  const { catalogId } = req.params;
  const existing = db.prepare('SELECT 1 FROM account_favorites WHERE account_id = ? AND catalog_id = ?').get(accountId, catalogId);
  if (existing) {
    db.prepare('DELETE FROM account_favorites WHERE account_id = ? AND catalog_id = ?').run(accountId, catalogId);
    res.json({ favorited: false });
  } else {
    db.prepare('INSERT INTO account_favorites (account_id, catalog_id) VALUES (?, ?)').run(accountId, catalogId);
    res.json({ favorited: true });
  }
});

// Config endpoint (public — frontend needs Stripe publishable key)
app.get('/api/config', (req, res) => {
  res.json({
    stripePublishableKey: process.env.STRIPE_PUBLISHABLE_KEY || null,
    stripeEnabled: isStripeEnabled(),
    bundles: getBundles(),
  });
});

// Pearl balance
app.get('/api/account/balance', (req, res) => {
  const token = (req.headers.authorization || '').replace('Bearer ', '');
  const accountId = getSession(token);
  if (!accountId) return res.status(401).json({ error: 'Not authenticated' });
  res.json({ pearls: getBalance(accountId) });
});

// Pearl transaction history
app.get('/api/account/transactions', (req, res) => {
  const token = (req.headers.authorization || '').replace('Bearer ', '');
  const accountId = getSession(token);
  if (!accountId) return res.status(401).json({ error: 'Not authenticated' });
  const txns = getTransactions(accountId).map(tx => {
    if ((tx.type === 'item_buy' || tx.type === 'item_sale') && tx.reference) {
      const item = getCatalogItem(tx.reference);
      if (item) tx.itemName = item.name;
    }
    return tx;
  });
  res.json(txns);
});

// Create Stripe checkout session for Pearl purchase
app.post('/api/payments/create-checkout', async (req, res) => {
  const token = (req.headers.authorization || '').replace('Bearer ', '');
  const accountId = getSession(token);
  if (!accountId) return res.status(401).json({ error: 'Not authenticated' });

  const { pearls } = req.body;
  try {
    const origin = `${req.protocol}://${req.get('host')}`;
    const result = await createCheckoutSession(accountId, pearls, origin);
    res.json(result);
  } catch (err) {
    res.status(400).json({ error: err.message });
  }
});

// Purchase a priced catalog item with Pearls
app.post('/api/catalog/:id/purchase', (req, res) => {
  const token = (req.headers.authorization || '').replace('Bearer ', '');
  const accountId = getSession(token);
  if (!accountId) return res.status(401).json({ error: 'Not authenticated' });
  const result = purchaseItem(accountId, req.params.id);
  if (!result.ok) return res.status(400).json({ error: result.error });
  res.json({ ok: true, pearls: getBalance(accountId) });
});

// Acquire a free catalog item (adds to user's library)
app.post('/api/catalog/:id/acquire', (req, res) => {
  const token = (req.headers.authorization || '').replace('Bearer ', '');
  const accountId = getSession(token);
  if (!accountId) return res.status(401).json({ error: 'You must be logged in to acquire items' });
  const result = acquireFreeItem(accountId, req.params.id);
  if (!result.ok) return res.status(400).json({ error: result.error });
  res.json({ ok: true });
});

// Check if user can access a priced item
app.get('/api/catalog/:id/access', (req, res) => {
  const token = (req.headers.authorization || '').replace('Bearer ', '');
  const accountId = getSession(token);
  if (!accountId) return res.json({ access: false });
  res.json({ access: canAccessItem(accountId, req.params.id) });
});

// Get all items user has purchased
app.get('/api/account/purchases', (req, res) => {
  const token = (req.headers.authorization || '').replace('Bearer ', '');
  const accountId = getSession(token);
  if (!accountId) return res.status(401).json({ error: 'Not authenticated' });
  res.json(getPurchasedItems(accountId));
});

// Stripe Connect — seller cash-out
app.post('/api/connect/setup', async (req, res) => {
  const token = (req.headers.authorization || '').replace('Bearer ', '');
  const accountId = getSession(token);
  if (!accountId) return res.status(401).json({ error: 'Not authenticated' });

  try {
    await createConnectAccount(accountId);
    const origin = `${req.protocol}://${req.get('host')}`;
    const { url } = await createOnboardingLink(accountId, origin);
    res.json({ url });
  } catch (err) {
    res.status(400).json({ error: err.message });
  }
});

app.get('/api/connect/status', async (req, res) => {
  const token = (req.headers.authorization || '').replace('Bearer ', '');
  const accountId = getSession(token);
  if (!accountId) return res.status(401).json({ error: 'Not authenticated' });

  try {
    const status = await getConnectStatus(accountId);
    res.json(status);
  } catch (err) {
    res.status(400).json({ error: err.message });
  }
});

app.post('/api/connect/cashout', async (req, res) => {
  const token = (req.headers.authorization || '').replace('Bearer ', '');
  const accountId = getSession(token);
  if (!accountId) return res.status(401).json({ error: 'Not authenticated' });

  const { pearls } = req.body;
  try {
    const result = await cashOut(accountId, pearls);
    res.json({ ...result, balance: getBalance(accountId) });
  } catch (err) {
    res.status(400).json({ error: err.message });
  }
});

app.get('/api/connect/onboarding-link', async (req, res) => {
  const token = (req.headers.authorization || '').replace('Bearer ', '');
  const accountId = getSession(token);
  if (!accountId) return res.status(401).json({ error: 'Not authenticated' });

  try {
    const origin = `${req.protocol}://${req.get('host')}`;
    const { url } = await createOnboardingLink(accountId, origin);
    res.json({ url });
  } catch (err) {
    res.status(400).json({ error: err.message });
  }
});

// REST endpoint for listing Club Penguins
app.get('/api/clubpenguins', (req, res) => {
  res.json(listClubPenguins());
});

app.get('/api/clubpenguins/:id', (req, res) => {
  const cp = getClubPenguin(req.params.id);
  if (!cp) return res.status(404).json({ error: 'Not found' });
  res.json(cp);
});

app.get('/api/clubpenguins/:id/parties', (req, res) => {
  const cp = getClubPenguin(req.params.id);
  if (!cp) return res.status(404).json({ error: 'Not found' });
  res.json(getPartyLog(req.params.id));
});

// Catalog endpoints
app.get('/api/catalog', (req, res) => {
  res.json(listCatalogItems());
});

app.get('/api/catalog/:id', (req, res) => {
  const item = getCatalogItem(req.params.id);
  if (!item) return res.status(404).json({ error: 'Not found' });
  res.json(item);
});

app.post('/api/catalog', async (req, res) => {
  const done = trackStart('http:POST /api/catalog');
  const token = (req.headers.authorization || '').replace('Bearer ', '');
  const accountId = getSession(token);
  if (!accountId) { done(); return res.status(401).json({ error: 'You must be logged in to upload items' }); }

  // Check upload ban
  const banExpiry = uploadBans.get(accountId);
  if (banExpiry && Date.now() < banExpiry) {
    const hoursLeft = Math.ceil((banExpiry - Date.now()) / 3600000);
    return res.status(429).json({ error: `Upload access temporarily suspended. Try again in ${hoursLeft} hour${hoursLeft === 1 ? '' : 's'}.` });
  }

  // Upload rate limit: 3 per hour
  const now = Date.now();
  const uploads = (uploadRateLimits.get(accountId) || []).filter(t => now - t < 3600000);
  if (uploads.length >= 3) {
    return res.status(429).json({ error: 'Upload limit reached (3 per hour). Please try again later.' });
  }

  const { name, image, attribution, price } = req.body;
  if (!name || !name.trim()) return res.status(400).json({ error: 'Name is required' });
  const itemPrice = Math.max(0, Math.floor(Number(price) || 0));
  if (!image || !image.startsWith('data:image/')) return res.status(400).json({ error: 'Image must be a data URL' });
  if (image.length > 128 * 1024) return res.status(400).json({ error: 'Image too large (max 128KB)' });
  if (catalogItemExistsByName(name.trim())) return res.status(409).json({ error: 'An item with that name already exists' });

  // Decode image to check pixel dimensions
  let imgWidth = null, imgHeight = null;
  try {
    const base64Match = image.match(/^data:image\/\w+;base64,(.+)$/);
    if (base64Match) {
      const buf = Buffer.from(base64Match[1], 'base64');
      const dims = getImageDimensions(buf);
      if (dims) {
        imgWidth = dims.width;
        imgHeight = dims.height;
        if (dims.width > 800 || dims.height > 600) {
          return res.status(400).json({ error: `Image dimensions too large (${dims.width}x${dims.height}). Maximum is 800x600.` });
        }
      }
    }
  } catch (e) {
    // If we can't parse dimensions, allow it through
  }

  // AI moderation (runs after cheap checks, before creation)
  const modResult = await moderateUpload(image, name.trim());
  if (!modResult.ok) {
    // Track rejection for ban logic
    const rejections = (uploadRejections.get(accountId) || []).filter(t => now - t < 3600000);
    rejections.push(now);
    uploadRejections.set(accountId, rejections);
    if (rejections.length >= 3) {
      uploadBans.set(accountId, now + 86400000); // 24-hour ban
    }
    return res.status(400).json({ error: modResult.reason });
  }

  // Track successful upload for rate limiting
  uploads.push(now);
  uploadRateLimits.set(accountId, uploads);

  // Default attribution to account's attribution_name, then username
  let attr = (attribution || '').trim();
  if (!attr) {
    const account = getAccount(accountId);
    if (account) attr = account.attribution_name || account.username;
  }

  const item = createCatalogItem(name.trim(), image, accountId, attr, itemPrice, imgWidth, imgHeight);
  done();
  res.json(item);
});

// Game endpoints
app.get('/api/games', (req, res) => {
  res.json(listGames());
});

app.get('/api/games/:id', (req, res) => {
  const game = getGame(req.params.id);
  if (!game) return res.status(404).json({ error: 'Not found' });
  res.json(game);
});

app.post('/api/games/upload', express.json({ limit: '50kb' }), (req, res) => {
  const token = (req.headers.authorization || '').replace('Bearer ', '');
  const accountId = token ? getSession(token) : null;
  if (!accountId) return res.status(401).json({ error: 'Login required' });

  const { name, items, width, height, gravityDirection, price, attribution: clientAttribution } = req.body;
  if (!name || !name.trim()) return res.status(400).json({ error: 'Name is required' });
  if (!items || !Array.isArray(items) || items.length === 0) return res.status(400).json({ error: 'Game must have at least one item' });
  if (!width || !height || width <= 0 || height <= 0) return res.status(400).json({ error: 'Invalid game dimensions' });

  if (gameExistsByName(name.trim())) return res.status(400).json({ error: 'A game with that name already exists' });

  // Validate all items use creator's own uploads
  for (const item of items) {
    const catItem = getCatalogItem(item.catalogId);
    if (!catItem) return res.status(400).json({ error: `Item ${item.catalogId} not found in catalog` });
    if (catItem.uploaderId !== accountId) return res.status(400).json({ error: `Item "${catItem.name}" was uploaded by someone else — games can only use your own uploads` });
  }

  const account = getAccount(accountId);
  const attribution = (clientAttribution && clientAttribution.trim()) || account?.attribution_name || account?.username || '';
  const game = createGame(name.trim(), items, width, height, gravityDirection || null, accountId, attribution, price || 0);
  res.json({ success: true, game });
});

app.post('/api/games/:id/purchase', (req, res) => {
  const token = (req.headers.authorization || '').replace('Bearer ', '');
  const accountId = token ? getSession(token) : null;
  if (!accountId) return res.status(401).json({ error: 'Login required' });
  const result = purchaseGame(accountId, req.params.id);
  if (!result.ok) return res.status(400).json({ error: result.error });
  res.json({ success: true, pearls: getBalance(accountId) });
});

app.post('/api/games/:id/acquire', (req, res) => {
  const token = (req.headers.authorization || '').replace('Bearer ', '');
  const accountId = token ? getSession(token) : null;
  if (!accountId) return res.status(401).json({ error: 'Login required' });
  const result = acquireFreeGame(accountId, req.params.id);
  if (!result.ok) return res.status(400).json({ error: result.error });
  res.json({ success: true });
});

app.get('/api/games/:id/access', (req, res) => {
  const token = (req.headers.authorization || '').replace('Bearer ', '');
  const accountId = token ? getSession(token) : null;
  if (!accountId) return res.json({ access: false });
  res.json({ access: canAccessGame(accountId, req.params.id) });
});

app.get('/api/account/game-purchases', (req, res) => {
  const token = (req.headers.authorization || '').replace('Bearer ', '');
  const accountId = token ? getSession(token) : null;
  if (!accountId) return res.status(401).json({ error: 'Login required' });
  res.json(getPurchasedGames(accountId));
});

// Parse image dimensions from buffer (supports PNG and JPEG headers)
function getImageDimensions(buf) {
  // PNG: bytes 16-23 contain width and height as 4-byte big-endian integers
  if (buf[0] === 0x89 && buf[1] === 0x50 && buf[2] === 0x4E && buf[3] === 0x47) {
    return { width: buf.readUInt32BE(16), height: buf.readUInt32BE(20) };
  }
  // JPEG: scan for SOF0/SOF2 markers
  if (buf[0] === 0xFF && buf[1] === 0xD8) {
    let offset = 2;
    while (offset < buf.length - 8) {
      if (buf[offset] !== 0xFF) break;
      const marker = buf[offset + 1];
      if (marker === 0xC0 || marker === 0xC2) {
        return { width: buf.readUInt16BE(offset + 7), height: buf.readUInt16BE(offset + 5) };
      }
      const segLen = buf.readUInt16BE(offset + 2);
      offset += 2 + segLen;
    }
  }
  // GIF: bytes 6-9 contain width and height as 2-byte little-endian integers
  if (buf[0] === 0x47 && buf[1] === 0x49 && buf[2] === 0x46) {
    return { width: buf.readUInt16LE(6), height: buf.readUInt16LE(8) };
  }
  return null;
}

// Broadcast to all sockets whose penguin is in the given CP + room.
function cpSummary(cpId) {
  const cp = getClubPenguin(cpId);
  if (!cp) return null;
  return { id: cp.id, name: cp.name, roomCount: Object.keys(cp.rooms).length, penguinCount: getPenguinCountForCP(cpId), creatorId: cp.creatorId || null };
}

// Transform a point from screen space to game-local space (un-rotate around game center, shift to 0-origin)
function toLocalSpace(x, y, gb) {
  const gcx = gb.x + gb.w / 2;
  const gcy = gb.y + gb.h / 2;
  const rot = -(gb.rotation || 0) * Math.PI / 180;
  const cos = Math.cos(rot);
  const sin = Math.sin(rot);
  const dx = x - gcx;
  const dy = y - gcy;
  return { x: dx * cos - dy * sin + gb.w / 2, y: dx * sin + dy * cos + gb.h / 2 };
}

// Transform a point from game-local space back to screen space
function toScreenSpace(x, y, gb) {
  const gcx = gb.x + gb.w / 2;
  const gcy = gb.y + gb.h / 2;
  const rot = (gb.rotation || 0) * Math.PI / 180;
  const cos = Math.cos(rot);
  const sin = Math.sin(rot);
  const dx = x - gb.w / 2;
  const dy = y - gb.h / 2;
  return { x: gcx + dx * cos - dy * sin, y: gcy + dx * sin + dy * cos };
}

// Expand game entries in a room's items array into individual items.
// Each game entry becomes N items with gameGroup, scaled/translated to the game's placement rect.
// Returns a new items array with games expanded, plus a mapping for catalog resolution.
function expandRoomItems(room) {
  if (!room.items || room.items.length === 0) return [];
  const expanded = [];
  for (const item of room.items) {
    if (item.gameId) {
      const game = getGame(item.gameId);
      if (!game) continue;
      const sx = item.width / game.width;
      const sy = item.height / game.height;
      const gameRot = (item.rotation || 0) * Math.PI / 180;
      const cx = item.x + item.width / 2;
      const cy = item.y + item.height / 2;
      // Unique group key per placement (same game placed twice = two groups)
      const groupKey = item.gameId + ':' + expanded.length;
      for (const gi of game.items) {
        // Position relative to game center (before rotation)
        let ex = item.x + gi.x * sx + gi.width * sx / 2 - cx;
        let ey = item.y + gi.y * sy + gi.height * sy / 2 - cy;
        // Apply rotation around game center
        let fx, fy;
        if (gameRot) {
          const cos = Math.cos(gameRot);
          const sin = Math.sin(gameRot);
          fx = cx + ex * cos - ey * sin;
          fy = cy + ex * sin + ey * cos;
        } else {
          fx = cx + ex;
          fy = cy + ey;
        }
        // Convert back from center to top-left
        const ew = gi.width * sx;
        const eh = gi.height * sy;
        expanded.push({
          ...gi,
          x: fx - ew / 2,
          y: fy - eh / 2,
          width: ew,
          height: eh,
          rotation: (gi.rotation || 0) + (item.rotation || 0),
          gameGroup: groupKey,
          gameBounds: { x: item.x, y: item.y, w: item.width, h: item.height, rotation: item.rotation || 0 },
          gameGravityDirection: game.gravityDirection,
        });
      }
    } else {
      expanded.push(item);
    }
  }
  return expanded;
}

// Resolve catalog item images for a room's items (including expanded game items)
function resolveCatalogItems(room, expandedItems) {
  const items = expandedItems || room.items || [];
  if (items.length === 0) return {};
  const catalogItems = {};
  for (const item of items) {
    if (item.catalogId && !catalogItems[item.catalogId]) {
      const catItem = getCatalogItem(item.catalogId);
      if (catItem) {
        catalogItems[item.catalogId] = { name: catItem.name, image: catItem.image };
      }
    }
  }
  return catalogItems;
}

function broadcastToCPRoom(cpId, roomId, event, data, excludeSocketId = null) {
  for (const [id, s] of io.sockets.sockets) {
    if (id === excludeSocketId) continue;
    const p = getPenguin(id);
    if (p && p.cpId === cpId && p.roomId === roomId) {
      s.emit(event, data);
    }
  }
}

// Upload rate limiting: per-account tracking
const uploadRateLimits = new Map(); // accountId → [timestamps]
const uploadRejections = new Map(); // accountId → [timestamps]
const uploadBans = new Map(); // accountId → ban expiry timestamp

// Chat rate limiting: per-socket tracking
const chatRateLimits = new Map();

// Resolve current item positions for a room (accounting for drag overrides)
// Uses expanded items (games already exploded into individual items).
function resolveRoomItems(room, cpId, roomId) {
  const dragOverrides = getDragOverrides(cpId, roomId);
  return room.items.map((i, idx) => {
    const ov = dragOverrides && dragOverrides[idx];
    return {
      x: (ov && ov.x != null) ? ov.x : i.x,
      y: (ov && ov.y != null) ? ov.y : i.y,
      w: i.width, h: i.height,
      blocksMovement: i.blocksMovement,
      skid: i.skid,
      gravity: i.gravity,
      behavior: i.behavior,
      gameGroup: i.gameGroup || null,
      gameBounds: i.gameBounds || null,
      gameGravityDirection: i.gameGravityDirection || null,
      idx,
    };
  });
}

// Settle all gravity items in a room. Sorts by proximity to gravity floor
// so items stack correctly. Groups by gameGroup for scoped physics.
function settleGravityItems(cpId, roomId, room) {
  const resolved = resolveRoomItems(room, cpId, roomId);
  const gravityItems = resolved.filter(i => i.gravity);
  if (gravityItems.length === 0) return [];

  // Group items by gameGroup (null = room-level items)
  const groups = new Map();
  for (const item of gravityItems) {
    const key = item.gameGroup || '__room__';
    if (!groups.has(key)) groups.set(key, []);
    groups.get(key).push(item);
  }

  const events = [];

  for (const [groupKey, items] of groups) {
    // Determine gravity direction and bounds for this group
    const isGame = groupKey !== '__room__';
    const direction = isGame ? (items[0].gameGravityDirection || 'down') : (room.gravityDirection || 'down');
    const boundsX = isGame && items[0].gameBounds ? items[0].gameBounds.x : 0;
    const boundsY = isGame && items[0].gameBounds ? items[0].gameBounds.y : 0;
    const boundsW = isGame && items[0].gameBounds ? items[0].gameBounds.w : 800;
    const boundsH = isGame && items[0].gameBounds ? items[0].gameBounds.h : 600;

    // Sort by proximity to gravity "floor" (items closest to floor settle first)
    items.sort((a, b) => {
      switch (direction) {
        case 'down': return (b.y + b.h) - (a.y + a.h);
        case 'up': return a.y - b.y;
        case 'right': return (b.x + b.w) - (a.x + a.w);
        case 'left': return a.x - b.x;
        case 'center': {
          const cx = boundsX + boundsW / 2;
          const cy = boundsY + boundsH / 2;
          const distA = Math.sqrt((a.x + a.w / 2 - cx) ** 2 + (a.y + a.h / 2 - cy) ** 2);
          const distB = Math.sqrt((b.x + b.w / 2 - cx) ** 2 + (b.y + b.h / 2 - cy) ** 2);
          return distA - distB;
        }
        default: return 0;
      }
    });

    const gb = isGame ? items[0].gameBounds : null;
    const isRotated = gb && gb.rotation;

    for (const item of items) {
      // Use already-resolved items (updated in-place below) — scoped to same gameGroup
      let blockers = resolved
        .filter(i => i.blocksMovement && i.idx !== item.idx && i.gameGroup === item.gameGroup)
        .map(i => ({ x: i.x, y: i.y, w: i.w, h: i.h }));

      let simX = item.x, simY = item.y;
      if (isRotated) {
        // Transform item and blockers into game-local space
        const local = toLocalSpace(item.x + item.w / 2, item.y + item.h / 2, gb);
        simX = local.x - item.w / 2;
        simY = local.y - item.h / 2;
        blockers = blockers.map(b => {
          const bl = toLocalSpace(b.x + b.w / 2, b.y + b.h / 2, gb);
          return { x: bl.x - b.w / 2, y: bl.y - b.h / 2, w: b.w, h: b.h };
        });
      }

      const frames = simulateGravity(simX, simY, item.w, item.h, direction, blockers,
        isRotated ? boundsW : boundsW, isRotated ? boundsH : boundsH,
        isRotated ? 0 : boundsX, isRotated ? 0 : boundsY);
      const localFinal = frames[frames.length - 1];

      let finalX, finalY;
      if (isRotated) {
        const screen = toScreenSpace(localFinal.x + item.w / 2, localFinal.y + item.h / 2, gb);
        finalX = screen.x - item.w / 2;
        finalY = screen.y - item.h / 2;
      } else {
        finalX = localFinal.x;
        finalY = localFinal.y;
      }

      if (Math.abs(finalX - item.x) > 0.5 || Math.abs(finalY - item.y) > 0.5) {
        setItemPosition(cpId, roomId, item.idx, finalX, finalY);
        // Update resolved array in-place so subsequent items see settled positions
        resolved[item.idx].x = finalX;
        resolved[item.idx].y = finalY;
        // Only persist for non-game draggable-persist items
        if (!item.gameGroup && room.items[item.idx]?.behavior === 'draggable-persist') {
          updateRoomItemPosition(cpId, roomId, item.idx, finalX, finalY);
        }
        events.push({ itemIndex: item.idx, startX: item.x, startY: item.y, direction });
      }
    }
  }
  return events;
}

// Run gravity on a single item and broadcast. Returns final position or null if no movement.
function applyGravityToItem(cpId, roomId, room, itemIndex) {
  const resolved = resolveRoomItems(room, cpId, roomId);
  const item = resolved[itemIndex];
  if (!item || !item.gravity) return null;

  // Use game gravity direction and bounds if this is a game item
  const isGame = !!item.gameGroup;
  const direction = isGame ? (item.gameGravityDirection || 'down') : (room.gravityDirection || 'down');
  const boundsX = isGame && item.gameBounds ? item.gameBounds.x : 0;
  const boundsY = isGame && item.gameBounds ? item.gameBounds.y : 0;
  const boundsW = isGame && item.gameBounds ? item.gameBounds.w : 800;
  const boundsH = isGame && item.gameBounds ? item.gameBounds.h : 600;

  // Scope blockers to same gameGroup
  const gb = isGame ? item.gameBounds : null;
  const isRotated = gb && gb.rotation;
  let blockers = resolved
    .filter(i => i.blocksMovement && i.idx !== itemIndex && i.gameGroup === item.gameGroup)
    .map(i => ({ x: i.x, y: i.y, w: i.w, h: i.h }));

  let simX = item.x, simY = item.y;
  if (isRotated) {
    const local = toLocalSpace(item.x + item.w / 2, item.y + item.h / 2, gb);
    simX = local.x - item.w / 2;
    simY = local.y - item.h / 2;
    blockers = blockers.map(b => {
      const bl = toLocalSpace(b.x + b.w / 2, b.y + b.h / 2, gb);
      return { x: bl.x - b.w / 2, y: bl.y - b.h / 2, w: b.w, h: b.h };
    });
  }

  const frames = simulateGravity(simX, simY, item.w, item.h, direction, blockers,
    boundsW, boundsH, isRotated ? 0 : boundsX, isRotated ? 0 : boundsY);
  const localFinal = frames[frames.length - 1];

  let finalX, finalY;
  if (isRotated) {
    const screen = toScreenSpace(localFinal.x + item.w / 2, localFinal.y + item.h / 2, gb);
    finalX = screen.x - item.w / 2;
    finalY = screen.y - item.h / 2;
  } else {
    finalX = localFinal.x;
    finalY = localFinal.y;
  }

  if (Math.abs(finalX - item.x) < 0.5 && Math.abs(finalY - item.y) < 0.5) return null;

  setItemPosition(cpId, roomId, itemIndex, finalX, finalY);
  if (!isGame && room.items[itemIndex]?.behavior === 'draggable-persist') {
    updateRoomItemPosition(cpId, roomId, itemIndex, finalPos.x, finalPos.y);
  }
  return { itemIndex, startX: item.x, startY: item.y, direction };
}

// Compute spawn coordinates based on spawn config (room-level overrides CP-level)
function computeSpawnCoords(cp, roomId, prevX, prevY) {
  const room = cp.rooms[roomId];
  const config = (room && room.spawnConfig) || cp.spawnConfig || { mode: 'fixed', x: 400, y: 350 };
  switch (config.mode) {
    case 'random':
      return { x: Math.floor(Math.random() * 800), y: Math.floor(Math.random() * 600) };
    case 'opposite':
      if (prevX != null && prevY != null) {
        return { x: 800 - prevX, y: 600 - prevY };
      }
      // No previous position (first join) — fall back to center
      return { x: 400, y: 350 };
    case 'fixed':
    default:
      return { x: config.x ?? 400, y: config.y ?? 350 };
  }
}

function wireSocketEvents() {
io.on('connection', (socket) => {
  console.log(`Connected: ${socket.id}`);
  chatRateLimits.set(socket.id, []);

  socket.on('join', ({ name, cpId, token }) => {
    const done = trackStart('socket:join', cpId);
    const cp = getClubPenguin(cpId);
    if (!cp) { done(); return; }

    // If authenticated, use account username
    let accountId = null;
    if (token) {
      accountId = getSession(token);
      if (accountId) {
        const account = getAccount(accountId);
        if (account) name = account.username;
      }
    }

    // Validate name length
    if (!name || name.length < 1 || name.length > 20) return;

    // If already in a CP, leave it first
    const existing = getPenguin(socket.id);
    if (existing) {
      broadcastToCPRoom(existing.cpId, existing.roomId, 'penguinLeft', { id: existing.id, name: existing.name }, socket.id);
      removePenguin(socket.id);
      io.emit('clubPenguinUpdated', cpSummary(existing.cpId));
    }

    const visibleRooms = Object.keys(cp.rooms).filter(k => !cp.rooms[k].hidden);
    const spawnRoom = visibleRooms.length > 0
      ? visibleRooms[Math.floor(Math.random() * visibleRooms.length)]
      : cp.spawnRoom;
    const spawn = computeSpawnCoords(cp, spawnRoom, null, null);
    const penguin = addPenguin(socket.id, name, cpId, spawnRoom, accountId, spawn.x, spawn.y);

    // Restore saved inventory and preferences for logged-in users
    if (accountId) {
      const saved = loadInventory(accountId);
      for (const item of saved) {
        penguin.inventory.push(item);
        if (item.equipped) {
          penguin.clothes.push(item);
        }
      }
      const prefs = db.prepare('SELECT hide_emoji FROM account_preferences WHERE account_id = ?').get(accountId);
      if (prefs?.hide_emoji) penguin.hideEmoji = true;
    }

    const room = cp.rooms[penguin.roomId];
    const expandedItems = expandRoomItems(room);
    const expandedRoom = { ...room, items: expandedItems };

    // Settle gravity items before sending room state
    if (expandedItems.length > 0) {
      settleGravityItems(cpId, penguin.roomId, expandedRoom);
    }

    socket.emit('roomState', {
      room: expandedRoom,
      penguins: getPenguinsInCPRoom(cpId, penguin.roomId),
      you: penguin.id,
      catalogItems: resolveCatalogItems(room, expandedItems),
      inventory: penguin.inventory,
      clothes: penguin.clothes,
      dragOverrides: getDragOverrides(cpId, penguin.roomId),
    });

    broadcastToCPRoom(cpId, penguin.roomId, 'penguinJoined', penguin, socket.id);
    io.emit('clubPenguinUpdated', cpSummary(cpId));
    done();
  });

  socket.on('move', ({ x, y }) => {
    // Clamp to room bounds
    x = Math.max(0, Math.min(800, x));
    y = Math.max(0, Math.min(600, y));
    const penguin = getPenguin(socket.id);
    if (!penguin) return;
    const done = trackStart('socket:move', penguin.cpId);

    const cp = getClubPenguin(penguin.cpId);
    if (cp) {
      const room = cp.rooms[penguin.roomId];
      if (room && room.items) {
        // Use expanded items (games exploded into individual items) for physics
        const expandedItems = expandRoomItems(room);
        const expandedRoom = { ...room, items: expandedItems };
        const resolvedItems = resolveRoomItems(expandedRoom, penguin.cpId, penguin.roomId);

        // Save original target for skid detection (before blocker adjustment)
        const origX = x;
        const origY = y;

        // Apply collision with blocking items — only non-game items block penguins
        // (penguins walk freely through game areas, game blockers only affect game items)
        const blockers = resolvedItems.filter(i => i.blocksMovement && !i.gameGroup);
        if (blockers.length > 0) {
          const adjusted = adjustMoveTarget(penguin.x, penguin.y, x, y, blockers);
          x = adjusted.x;
          y = adjusted.y;
        }

        // Check for skid item pushes using the ORIGINAL path (pre-blocker adjustment)
        const origDistance = Math.sqrt((origX - penguin.x) ** 2 + (origY - penguin.y) ** 2);
        if (origDistance > 1) {
          const dirX = (origX - penguin.x) / origDistance;
          const dirY = (origY - penguin.y) / origDistance;

          for (const item of resolvedItems) {
            if (!item.skid) continue;
            // Check if penguin's original path crosses this item
            const hit = lineRectIntersection(penguin.x, penguin.y, origX, origY, item);
            if (!hit) continue;

            // Calculate push velocity from original movement distance
            const speed = Math.min(origDistance * 0.6, 400);
            const vx = dirX * speed / 60; // per-frame velocity
            const vy = dirY * speed / 60;

            // Get blockers for the skid sim — scoped by gameGroup
            const skidGb = item.gameBounds;
            const skidRotated = skidGb && skidGb.rotation;
            let skidBlockers = resolvedItems
              .filter(i => i.blocksMovement && i.idx !== item.idx && i.gameGroup === item.gameGroup)
              .map(i => ({ x: i.x, y: i.y, w: i.w, h: i.h }));

            // Use game bounds for game items, room bounds for room items
            const boundsW = skidGb ? skidGb.w : 800;
            const boundsH = skidGb ? skidGb.h : 600;
            const boundsX = skidGb ? skidGb.x : 0;
            const boundsY = skidGb ? skidGb.y : 0;

            let simSkidX = item.x, simSkidY = item.y;
            let simVx = vx, simVy = vy;
            if (skidRotated) {
              const local = toLocalSpace(item.x + item.w / 2, item.y + item.h / 2, skidGb);
              simSkidX = local.x - item.w / 2;
              simSkidY = local.y - item.h / 2;
              // Rotate velocity into local space
              const rot = -(skidGb.rotation) * Math.PI / 180;
              const cos = Math.cos(rot);
              const sin = Math.sin(rot);
              simVx = vx * cos - vy * sin;
              simVy = vx * sin + vy * cos;
              skidBlockers = skidBlockers.map(b => {
                const bl = toLocalSpace(b.x + b.w / 2, b.y + b.h / 2, skidGb);
                return { x: bl.x - b.w / 2, y: bl.y - b.h / 2, w: b.w, h: b.h };
              });
            }

            const frames = simulateSkid(simSkidX, simSkidY, item.w, item.h, simVx, simVy, skidBlockers,
              boundsW, boundsH, skidRotated ? 0 : boundsX, skidRotated ? 0 : boundsY);
            const localFinalSkid = frames[frames.length - 1];

            let finalSkidX, finalSkidY;
            if (skidRotated) {
              const screen = toScreenSpace(localFinalSkid.x + item.w / 2, localFinalSkid.y + item.h / 2, skidGb);
              finalSkidX = screen.x - item.w / 2;
              finalSkidY = screen.y - item.h / 2;
            } else {
              finalSkidX = localFinalSkid.x;
              finalSkidY = localFinalSkid.y;
            }

            // Store final position (use expanded index)
            setItemPosition(penguin.cpId, penguin.roomId, item.idx, finalSkidX, finalSkidY);
            // Only persist for non-game draggable-persist items
            if (!item.gameGroup && expandedItems[item.idx]?.behavior === 'draggable-persist') {
              updateRoomItemPosition(penguin.cpId, penguin.roomId, item.idx, finalSkidX, finalSkidY);
            }

            // Broadcast push to all clients (include hit.t so clients can delay animation)
            broadcastToCPRoom(penguin.cpId, penguin.roomId, 'itemPushed', {
              itemIndex: item.idx,
              startX: item.x,
              startY: item.y,
              vx, vy,
              hitT: hit.t,
              penguinDistance: origDistance,
            });

            // If pushed item has gravity, apply gravity after skid settles
            if (expandedItems[item.idx]?.gravity) {
              const gravEvent = applyGravityToItem(penguin.cpId, penguin.roomId, expandedRoom, item.idx);
              if (gravEvent) {
                broadcastToCPRoom(penguin.cpId, penguin.roomId, 'itemGravity', gravEvent);
              }
            }
          }
        }
      }
    }

    movePenguin(socket.id, x, y);
    broadcastToCPRoom(penguin.cpId, penguin.roomId, 'penguinMoved', {
      id: penguin.id,
      x,
      y,
    }, socket.id);
    done();
  });

  socket.on('chat', (message) => {
    const penguin = getPenguin(socket.id);
    if (!penguin) return;

    // Rate limit: max 5 messages per 3 seconds
    const now = Date.now();
    const times = chatRateLimits.get(socket.id) || [];
    const recent = times.filter(t => now - t < 3000);
    if (recent.length >= 5) {
      socket.emit('chatError', 'Slow down! Too many messages.');
      return;
    }
    recent.push(now);
    chatRateLimits.set(socket.id, recent);

    broadcastToCPRoom(penguin.cpId, penguin.roomId, 'chatMessage', {
      id: penguin.id,
      name: penguin.name,
      message,
    });
  });

  socket.on('changeRoom', (roomId) => {
    const penguin = getPenguin(socket.id);
    if (!penguin) return;
    const done = trackStart('socket:changeRoom', penguin.cpId);

    const cp = getClubPenguin(penguin.cpId);
    if (!cp || !cp.rooms[roomId]) return;

    const oldRoom = penguin.roomId;
    const prevX = penguin.x;
    const prevY = penguin.y;

    broadcastToCPRoom(penguin.cpId, oldRoom, 'penguinLeft', { id: penguin.id, name: penguin.name }, socket.id);

    const spawn = computeSpawnCoords(cp, roomId, prevX, prevY);
    changePenguinRoom(socket.id, roomId, spawn.x, spawn.y);

    const newRoom = cp.rooms[roomId];
    const expandedItems = expandRoomItems(newRoom);
    const expandedNewRoom = { ...newRoom, items: expandedItems };

    // Settle gravity items before sending room state
    if (expandedItems.length > 0) {
      settleGravityItems(penguin.cpId, roomId, expandedNewRoom);
    }

    socket.emit('roomState', {
      room: expandedNewRoom,
      penguins: getPenguinsInCPRoom(penguin.cpId, roomId),
      you: penguin.id,
      catalogItems: resolveCatalogItems(newRoom, expandedItems),
      dragOverrides: getDragOverrides(penguin.cpId, roomId),
    });

    broadcastToCPRoom(penguin.cpId, roomId, 'penguinJoined', penguin, socket.id);
    done();
  });

  socket.on('collectItem', ({ catalogId, wearOffsetX, wearOffsetY, wearWidth, wearHeight }) => {
    const penguin = getPenguin(socket.id);
    if (!penguin) return;

    const catItem = getCatalogItem(catalogId);
    if (!catItem) return;

    const inventoryEntry = {
      catalogId,
      name: catItem.name,
      image: catItem.image,
      wearOffsetX: wearOffsetX || 0,
      wearOffsetY: wearOffsetY || 0,
      wearWidth: wearWidth || 40,
      wearHeight: wearHeight || 40,
      attribution: catItem.attribution || '',
    };

    addToInventory(socket.id, inventoryEntry);

    // Persist for logged-in users
    if (penguin.accountId) {
      saveInventoryItem(penguin.accountId, inventoryEntry);
    }

    socket.emit('itemCollected', { item: inventoryEntry, inventory: penguin.inventory });
  });

  socket.on('equipItem', (inventoryIndex) => {
    const penguin = getPenguin(socket.id);
    if (!penguin) return;

    equipItem(socket.id, inventoryIndex);

    // Persist equipped state for logged-in users
    if (penguin.accountId && inventoryIndex < penguin.inventory.length) {
      const item = penguin.inventory[inventoryIndex];
      setEquipped(penguin.accountId, item.catalogId, item.wearOffsetX, item.wearOffsetY, item.wearWidth, item.wearHeight, true);
    }

    socket.emit('inventoryUpdated', { inventory: penguin.inventory, clothes: penguin.clothes });
    broadcastToCPRoom(penguin.cpId, penguin.roomId, 'penguinClothesChanged', {
      id: penguin.id,
      clothes: penguin.clothes,
      hideEmoji: penguin.hideEmoji,
    });
  });

  socket.on('unequipItem', (clothesIndex) => {
    const penguin = getPenguin(socket.id);
    if (!penguin) return;

    // Get item info before unequipping
    const item = clothesIndex < penguin.clothes.length ? penguin.clothes[clothesIndex] : null;

    unequipItem(socket.id, clothesIndex);

    // Persist equipped state for logged-in users
    if (penguin.accountId && item) {
      setEquipped(penguin.accountId, item.catalogId, item.wearOffsetX, item.wearOffsetY, item.wearWidth, item.wearHeight, false);
    }

    socket.emit('inventoryUpdated', { inventory: penguin.inventory, clothes: penguin.clothes });
    broadcastToCPRoom(penguin.cpId, penguin.roomId, 'penguinClothesChanged', {
      id: penguin.id,
      clothes: penguin.clothes,
      hideEmoji: penguin.hideEmoji,
    });
  });

  socket.on('setHideEmoji', (hide) => {
    const penguin = getPenguin(socket.id);
    if (!penguin) return;

    penguin.hideEmoji = !!hide;

    // Persist for logged-in users
    if (penguin.accountId) {
      db.prepare(
        `INSERT INTO account_preferences (account_id, hide_emoji) VALUES (?, ?)
         ON CONFLICT(account_id) DO UPDATE SET hide_emoji = ?`
      ).run(penguin.accountId, hide ? 1 : 0, hide ? 1 : 0);
    }

    // Broadcast to room (reuse clothes changed event since it's visual)
    broadcastToCPRoom(penguin.cpId, penguin.roomId, 'penguinClothesChanged', {
      id: penguin.id,
      clothes: penguin.clothes,
      hideEmoji: penguin.hideEmoji,
    });
    socket.emit('hideEmojiUpdated', { hideEmoji: penguin.hideEmoji });
  });

  // --- Drag events ---

  socket.on('dragStart', ({ itemIndex }) => {
    const penguin = getPenguin(socket.id);
    if (!penguin) return;
    const cp = getClubPenguin(penguin.cpId);
    if (!cp) return;
    const room = cp.rooms[penguin.roomId];
    if (!room || !room.items) return;
    // Use expanded items (client sees expanded indices)
    const expandedItems = expandRoomItems(room);
    if (itemIndex < 0 || itemIndex >= expandedItems.length) return;
    const item = expandedItems[itemIndex];
    if (!item.behavior || !item.behavior.startsWith('draggable')) return;

    if (!startDrag(penguin.cpId, penguin.roomId, itemIndex, socket.id)) {
      return; // locked by another penguin
    }

    broadcastToCPRoom(penguin.cpId, penguin.roomId, 'itemDragStart', {
      itemIndex,
      draggedBy: penguin.id,
    }, socket.id);
  });

  socket.on('dragMove', ({ itemIndex, x, y }) => {
    const penguin = getPenguin(socket.id);
    if (!penguin) return;
    const done = trackStart('socket:dragMove', penguin.cpId);
    const cp = getClubPenguin(penguin.cpId);
    if (!cp) return;
    const room = cp.rooms[penguin.roomId];
    if (!room) return;
    // Clamp to game bounds or room bounds
    const expandedItems = expandRoomItems(room);
    const item = expandedItems[itemIndex];
    if (item?.gameBounds && item.gameBounds.rotation) {
      const gb = item.gameBounds;
      const gcx = gb.x + gb.w / 2;
      const gcy = gb.y + gb.h / 2;
      const rot = -gb.rotation * Math.PI / 180;
      const cos = Math.cos(rot);
      const sin = Math.sin(rot);
      // Un-rotate to local space
      let lx = (x + item.width / 2 - gcx) * cos - (y + item.height / 2 - gcy) * sin;
      let ly = (x + item.width / 2 - gcx) * sin + (y + item.height / 2 - gcy) * cos;
      // Clamp in local bounds
      lx = Math.max(-gb.w / 2 + item.width / 2, Math.min(gb.w / 2 - item.width / 2, lx));
      ly = Math.max(-gb.h / 2 + item.height / 2, Math.min(gb.h / 2 - item.height / 2, ly));
      // Rotate back
      const cos2 = Math.cos(-rot);
      const sin2 = Math.sin(-rot);
      const sx = gcx + lx * cos2 - ly * sin2;
      const sy = gcy + lx * sin2 + ly * cos2;
      x = sx - item.width / 2;
      y = sy - item.height / 2;
    } else if (item?.gameBounds) {
      x = Math.max(item.gameBounds.x, Math.min(item.gameBounds.x + item.gameBounds.w - item.width, x));
      y = Math.max(item.gameBounds.y, Math.min(item.gameBounds.y + item.gameBounds.h - item.height, y));
    } else {
      x = Math.max(0, Math.min(800, x));
      y = Math.max(0, Math.min(600, y));
    }
    moveDragItem(penguin.cpId, penguin.roomId, itemIndex, x, y);
    broadcastToCPRoom(penguin.cpId, penguin.roomId, 'itemDragMoved', {
      itemIndex, x, y,
    }, socket.id);
    done();
  });

  socket.on('dragEnd', ({ itemIndex }) => {
    const penguin = getPenguin(socket.id);
    if (!penguin) return;
    const entry = stopDrag(penguin.cpId, penguin.roomId, itemIndex);
    if (!entry) return;

    const cp = getClubPenguin(penguin.cpId);
    const room = cp && cp.rooms[penguin.roomId];
    const expandedItems = room ? expandRoomItems(room) : null;

    if (cp && entry.x != null && entry.y != null && expandedItems) {
      const item = expandedItems[itemIndex];
      // Only persist for non-game draggable-persist items
      if (item && !item.gameGroup && item.behavior === 'draggable-persist') {
        updateRoomItemPosition(penguin.cpId, penguin.roomId, itemIndex, entry.x, entry.y);
      }
    }

    broadcastToCPRoom(penguin.cpId, penguin.roomId, 'itemDragEnd', {
      itemIndex,
      x: entry.x,
      y: entry.y,
    }, socket.id);

    // If released item has gravity, apply gravity from release point
    if (cp && expandedItems) {
      const expandedRoom = { ...room, items: expandedItems };
      const item = expandedItems[itemIndex];
      if (item?.gravity) {
        setItemPosition(penguin.cpId, penguin.roomId, itemIndex, entry.x, entry.y);
        const gravEvent = applyGravityToItem(penguin.cpId, penguin.roomId, expandedRoom, itemIndex);
        if (gravEvent) {
          broadcastToCPRoom(penguin.cpId, penguin.roomId, 'itemGravity', gravEvent);
        }
      }
    }
  });

  function validateItemAccess(rooms, accountId) {
    for (const room of Object.values(rooms)) {
      for (const item of (room.items || [])) {
        if (item.gameId) {
          // Game placement — check game access
          if (!canAccessGame(accountId, item.gameId)) {
            const game = getGame(item.gameId);
            const label = game ? `"${game.name}"` : item.gameId;
            return `You don't have access to game ${label} — acquire it from the Catalog first`;
          }
        } else if (item.catalogId && !canAccessItem(accountId, item.catalogId)) {
          const cat = getCatalogItem(item.catalogId);
          const label = cat ? `"${cat.name}"` : item.catalogId;
          return `You don't have access to item ${label} — acquire it from the Catalog first`;
        }
      }
    }
    return null;
  }

  socket.on('createClubPenguin', (data, callback) => {
    // Auth check: must be logged in
    const creatorAccountId = data.token ? getSession(data.token) : null;
    if (!creatorAccountId) {
      return callback({ success: false, error: 'You must be logged in to create a Club Penguin' });
    }

    // Validate
    if (!data.name || !data.name.trim()) {
      return callback({ success: false, error: 'Name is required' });
    }
    if (!data.rooms || Object.keys(data.rooms).length === 0) {
      return callback({ success: false, error: 'At least one room is required' });
    }

    const roomIds = Object.keys(data.rooms);
    if (roomIds.every(k => data.rooms[k].hidden)) {
      return callback({ success: false, error: 'At least one room must not be hidden' });
    }

    // Validate exit targets
    for (const roomId of roomIds) {
      const room = data.rooms[roomId];
      if (room.exits) {
        for (const exit of room.exits) {
          if (!roomIds.includes(exit.targetRoom)) {
            return callback({ success: false, error: `Exit target "${exit.targetRoom}" does not exist` });
          }
        }
      }
    }

    const itemError = validateItemAccess(data.rooms, creatorAccountId);
    if (itemError) return callback({ success: false, error: itemError });

    const cp = createClubPenguin(data.name.trim(), data.rooms, creatorAccountId, data.spawnConfig || null);
    const summary = cpSummary(cp.id);
    callback({ success: true, cp: summary });
    io.emit('clubPenguinCreated', summary);
  });

  socket.on('editClubPenguin', (data, callback) => {
    // Auth check: must be logged in and be the creator
    const editorAccountId = data.token ? getSession(data.token) : null;
    if (!editorAccountId) {
      return callback({ success: false, error: 'You must be logged in to throw a party' });
    }
    const existingCp = getClubPenguin(data.id);
    if (existingCp && existingCp.creatorId && existingCp.creatorId !== editorAccountId) {
      return callback({ success: false, error: 'You can only edit Club Penguins you created' });
    }

    if (!data.id || !data.name || !data.name.trim()) {
      return callback({ success: false, error: 'Name is required' });
    }
    if (!data.rooms || Object.keys(data.rooms).length === 0) {
      return callback({ success: false, error: 'At least one room is required' });
    }

    const roomIds = Object.keys(data.rooms);
    if (roomIds.every(k => data.rooms[k].hidden)) {
      return callback({ success: false, error: 'At least one room must not be hidden' });
    }

    for (const roomId of roomIds) {
      const room = data.rooms[roomId];
      if (room.exits) {
        for (const exit of room.exits) {
          if (!roomIds.includes(exit.targetRoom)) {
            return callback({ success: false, error: `Exit target "${exit.targetRoom}" does not exist` });
          }
        }
      }
    }

    const itemError = validateItemAccess(data.rooms, editorAccountId);
    if (itemError) return callback({ success: false, error: itemError });

    const cp = updateClubPenguin(data.id, data.name.trim(), data.rooms, data.spawnConfig || null);
    if (!cp) {
      return callback({ success: false, error: 'Club Penguin not found' });
    }
    const summary = cpSummary(cp.id);
    if (data.partyName && data.partyName.trim()) {
      launchParty(data.id, data.partyName.trim());
    }
    callback({ success: true, cp: summary });
    io.emit('clubPenguinUpdated', summary);
  });

  function releaseDragLocks() {
    const released = clearDragLocks(socket.id);
    for (const r of released) {
      const [cpId, roomId] = r.key.split(':');
      broadcastToCPRoom(cpId, roomId, 'itemDragEnd', {
        itemIndex: r.itemIndex,
        x: r.x,
        y: r.y,
      });
    }
  }

  socket.on('leaveCP', () => {
    releaseDragLocks();
    const penguin = removePenguin(socket.id);
    if (penguin) {
      broadcastToCPRoom(penguin.cpId, penguin.roomId, 'penguinLeft', { id: penguin.id, name: penguin.name });
      io.emit('clubPenguinUpdated', cpSummary(penguin.cpId));
    }
  });

  socket.on('disconnect', () => {
    releaseDragLocks();
    const penguin = removePenguin(socket.id);
    if (penguin) {
      broadcastToCPRoom(penguin.cpId, penguin.roomId, 'penguinLeft', { id: penguin.id, name: penguin.name });
      io.emit('clubPenguinUpdated', cpSummary(penguin.cpId));
    }
    chatRateLimits.delete(socket.id);
    console.log(`Disconnected: ${socket.id}`);
  });
});
} // end wireSocketEvents

// Catch-all: serve index.html for client-side routing
app.get('*', (req, res) => {
  res.sendFile(join(__dirname, '..', 'dist', 'index.html'));
});

// Called by bootstrap.js once the HTTP server is already listening
export function setup(httpServer) {
  // Attach Express as the request handler
  httpServer.removeAllListeners('request');
  httpServer.on('request', app);

  // Attach Socket.io
  io = new Server(httpServer, {
    cors: {
      origin: '*',
      methods: ['GET', 'POST'],
    },
  });

  // Wire up socket events
  wireSocketEvents();
}

// Standalone mode (npm run dev)
if (!process.env.FLY_APP_NAME) {
  const httpServer = createServer(app);
  io = new Server(httpServer, {
    cors: {
      origin: '*',
      methods: ['GET', 'POST'],
    },
  });
  wireSocketEvents();
  const PORT = process.env.PORT || 3001;
  httpServer.listen(PORT, () => {
    console.log(`Server running on http://localhost:${PORT}`);
  });
}


### inventory.js

import db from './db.js';

export function loadInventory(accountId) {
  const rows = db.prepare(
    'SELECT catalog_id, name, image, wear_offset_x, wear_offset_y, wear_width, wear_height, equipped, equip_order, attribution, collected_at FROM account_inventory WHERE account_id = ? ORDER BY equip_order ASC'
  ).all(accountId);
  return rows.map(r => ({
    catalogId: r.catalog_id,
    name: r.name,
    image: r.image,
    wearOffsetX: r.wear_offset_x,
    wearOffsetY: r.wear_offset_y,
    wearWidth: r.wear_width,
    wearHeight: r.wear_height,
    equipped: !!r.equipped,
    attribution: r.attribution || '',
    collectedAt: r.collected_at || 0,
  }));
}

export function saveInventoryItem(accountId, item) {
  db.prepare(
    `INSERT OR IGNORE INTO account_inventory (account_id, catalog_id, name, image, wear_offset_x, wear_offset_y, wear_width, wear_height, equipped, attribution, collected_at)
     VALUES (?, ?, ?, ?, ?, ?, ?, ?, 0, ?, ?)`
  ).run(accountId, item.catalogId, item.name, item.image, item.wearOffsetX, item.wearOffsetY, item.wearWidth, item.wearHeight, item.attribution || '', Date.now());
}

export function setEquipped(accountId, catalogId, wearOffsetX, wearOffsetY, wearWidth, wearHeight, equipped) {
  if (equipped) {
    const max = db.prepare(
      'SELECT COALESCE(MAX(equip_order), 0) AS m FROM account_inventory WHERE account_id = ? AND equipped = 1'
    ).get(accountId);
    db.prepare(
      `UPDATE account_inventory SET equipped = 1, equip_order = ? WHERE account_id = ? AND catalog_id = ? AND wear_offset_x = ? AND wear_offset_y = ? AND wear_width = ? AND wear_height = ?`
    ).run((max?.m || 0) + 1, accountId, catalogId, wearOffsetX, wearOffsetY, wearWidth, wearHeight);
  } else {
    db.prepare(
      `UPDATE account_inventory SET equipped = 0, equip_order = 0 WHERE account_id = ? AND catalog_id = ? AND wear_offset_x = ? AND wear_offset_y = ? AND wear_width = ? AND wear_height = ?`
    ).run(accountId, catalogId, wearOffsetX, wearOffsetY, wearWidth, wearHeight);
  }
}

### state.js

const penguins = new Map();
const dragState = new Map(); // key: "cpId:roomId", value: Map<itemIndex, { x, y, draggedBy }>

export function addPenguin(socketId, name, cpId, spawnRoom, accountId = null, spawnX = 400, spawnY = 350) {
  const penguin = {
    id: socketId,
    name,
    cpId,
    roomId: spawnRoom,
    accountId,
    x: spawnX,
    y: spawnY,
    inventory: [], // all collected items
    clothes: [],   // currently worn items (subset of inventory)
    hideEmoji: false,
  };
  penguins.set(socketId, penguin);
  return penguin;
}

export function removePenguin(socketId) {
  const penguin = penguins.get(socketId);
  penguins.delete(socketId);
  return penguin;
}

export function getPenguin(socketId) {
  return penguins.get(socketId);
}

export function movePenguin(socketId, x, y) {
  const penguin = penguins.get(socketId);
  if (penguin) {
    penguin.x = x;
    penguin.y = y;
  }
  return penguin;
}

export function addToInventory(socketId, item) {
  const penguin = penguins.get(socketId);
  if (penguin) {
    const duplicate = penguin.inventory.some(i =>
      i.catalogId === item.catalogId &&
      i.wearOffsetX === item.wearOffsetX &&
      i.wearOffsetY === item.wearOffsetY &&
      i.wearWidth === item.wearWidth &&
      i.wearHeight === item.wearHeight
    );
    if (!duplicate) {
      penguin.inventory.push(item);
    }
  }
  return penguin;
}

export function equipItem(socketId, inventoryIndex) {
  const penguin = penguins.get(socketId);
  if (penguin && inventoryIndex >= 0 && inventoryIndex < penguin.inventory.length) {
    const item = penguin.inventory[inventoryIndex];
    // Check if already worn (by index reference)
    if (!penguin.clothes.some(c => c === item)) {
      penguin.clothes.push(item);
    }
  }
  return penguin;
}

export function unequipItem(socketId, clothesIndex) {
  const penguin = penguins.get(socketId);
  if (penguin && clothesIndex >= 0 && clothesIndex < penguin.clothes.length) {
    penguin.clothes.splice(clothesIndex, 1);
  }
  return penguin;
}

export function changePenguinRoom(socketId, roomId, spawnX = 400, spawnY = 350) {
  const penguin = penguins.get(socketId);
  if (penguin) {
    penguin.roomId = roomId;
    penguin.x = spawnX;
    penguin.y = spawnY;
  }
  return penguin;
}

export function getPenguinCountForCP(cpId) {
  let count = 0;
  for (const penguin of penguins.values()) {
    if (penguin.cpId === cpId) count++;
  }
  return count;
}

export function getPenguinsInCPRoom(cpId, roomId) {
  const result = [];
  for (const penguin of penguins.values()) {
    if (penguin.cpId === cpId && penguin.roomId === roomId) {
      result.push(penguin);
    }
  }
  return result;
}

// --- Drag state ---

function dragKey(cpId, roomId) {
  return cpId + ':' + roomId;
}

export function startDrag(cpId, roomId, itemIndex, socketId) {
  const key = dragKey(cpId, roomId);
  if (!dragState.has(key)) dragState.set(key, new Map());
  const room = dragState.get(key);
  const existing = room.get(itemIndex);
  if (existing && existing.draggedBy !== socketId) return false;
  room.set(itemIndex, { x: null, y: null, draggedBy: socketId });
  return true;
}

export function setItemPosition(cpId, roomId, itemIndex, x, y) {
  const key = dragKey(cpId, roomId);
  if (!dragState.has(key)) dragState.set(key, new Map());
  const room = dragState.get(key);
  const existing = room.get(itemIndex);
  if (existing) {
    existing.x = x;
    existing.y = y;
  } else {
    room.set(itemIndex, { x, y, draggedBy: null });
  }
}

export function moveDragItem(cpId, roomId, itemIndex, x, y) {
  const key = dragKey(cpId, roomId);
  const room = dragState.get(key);
  if (!room) return;
  const entry = room.get(itemIndex);
  if (entry) {
    entry.x = x;
    entry.y = y;
  }
}

export function stopDrag(cpId, roomId, itemIndex) {
  const key = dragKey(cpId, roomId);
  const room = dragState.get(key);
  if (!room) return null;
  const entry = room.get(itemIndex);
  room.delete(itemIndex);
  if (room.size === 0) dragState.delete(key);
  return entry;
}

export function getDragOverrides(cpId, roomId) {
  const key = dragKey(cpId, roomId);
  const room = dragState.get(key);
  if (!room || room.size === 0) return null;
  const overrides = {};
  for (const [idx, entry] of room) {
    overrides[idx] = { x: entry.x, y: entry.y, draggedBy: entry.draggedBy };
  }
  return overrides;
}

export function clearDragLocks(socketId) {
  const released = [];
  for (const [key, room] of dragState) {
    for (const [idx, entry] of room) {
      if (entry.draggedBy === socketId) {
        released.push({ key, itemIndex: idx, x: entry.x, y: entry.y });
        room.delete(idx);
      }
    }
    if (room.size === 0) dragState.delete(key);
  }
  return released;
}

### stats.js (relevant for logging server costs so I can charge appropriate subscription fees later)

// Lightweight per-operation CPU/time tracking with SQLite persistence
// Tracks call count, total wall-clock ms, and max ms per named operation
// Optionally tracks per-CP breakdowns for socket operations
// Stats survive server restarts — loaded from DB on startup, flushed periodically + on shutdown

import db from './db.js';

const stats = new Map();
const cpStats = new Map(); // cpId -> Map(operation -> {count, totalMs, maxMs})

// --- DB statements ---
const upsertOp = db.prepare(`
  INSERT INTO stats_operations (operation, count, total_ms, max_ms)
  VALUES (?, ?, ?, ?)
  ON CONFLICT(operation) DO UPDATE SET
    count = count + excluded.count,
    total_ms = total_ms + excluded.total_ms,
    max_ms = MAX(max_ms, excluded.max_ms)
`);

const upsertCpOp = db.prepare(`
  INSERT INTO stats_cp_operations (cp_id, operation, count, total_ms, max_ms)
  VALUES (?, ?, ?, ?, ?)
  ON CONFLICT(cp_id, operation) DO UPDATE SET
    count = count + excluded.count,
    total_ms = total_ms + excluded.total_ms,
    max_ms = MAX(max_ms, excluded.max_ms)
`);

const getMeta = db.prepare('SELECT value FROM stats_meta WHERE key = ?');
const setMeta = db.prepare(`
  INSERT INTO stats_meta (key, value) VALUES (?, ?)
  ON CONFLICT(key) DO UPDATE SET value = excluded.value
`);

// Initialize "since" timestamp if not set
if (!getMeta.get('since')) {
  setMeta.run('since', String(Date.now()));
}

// --- Flush in-memory deltas to DB ---
// We accumulate in-memory, then flush deltas to DB and clear in-memory maps.
const flushToDB = db.transaction(() => {
  for (const [name, entry] of stats) {
    upsertOp.run(name, entry.count, entry.totalMs, entry.maxMs);
  }
  for (const [cpId, opMap] of cpStats) {
    for (const [name, entry] of opMap) {
      upsertCpOp.run(cpId, name, entry.count, entry.totalMs, entry.maxMs);
    }
  }
  stats.clear();
  cpStats.clear();
});

// Flush every 5 minutes
const flushInterval = setInterval(() => {
  try { flushToDB(); } catch (e) { console.error('Stats flush error:', e); }
}, 5 * 60 * 1000);
flushInterval.unref();

// Flush on shutdown
function onExit() {
  try { flushToDB(); } catch (e) { /* shutting down */ }
}
process.on('SIGTERM', onExit);
process.on('SIGINT', onExit);
process.on('beforeExit', onExit);

// --- Public API (same interface as before) ---

function record(map, key, elapsed) {
  let entry = map.get(key);
  if (!entry) {
    entry = { count: 0, totalMs: 0, maxMs: 0 };
    map.set(key, entry);
  }
  entry.count++;
  entry.totalMs += elapsed;
  if (elapsed > entry.maxMs) entry.maxMs = elapsed;
}

export function trackStart(name, cpId) {
  const start = performance.now();
  return () => {
    const elapsed = performance.now() - start;
    record(stats, name, elapsed);
    if (cpId) {
      if (!cpStats.has(cpId)) cpStats.set(cpId, new Map());
      record(cpStats.get(cpId), name, elapsed);
    }
  };
}

function formatEntry(entry) {
  return {
    count: entry.count,
    totalMs: Math.round(entry.totalMs * 100) / 100,
    avgMs: entry.count > 0 ? Math.round((entry.totalMs / entry.count) * 100) / 100 : 0,
    maxMs: Math.round(entry.maxMs * 100) / 100,
  };
}

// Merges DB rows + in-memory (unflushed) data for a complete view
function mergedOpStats() {
  const merged = new Map();
  // DB rows first
  for (const row of db.prepare('SELECT * FROM stats_operations').all()) {
    merged.set(row.operation, { count: row.count, totalMs: row.total_ms, maxMs: row.max_ms });
  }
  // Layer in-memory on top
  for (const [name, entry] of stats) {
    const existing = merged.get(name);
    if (existing) {
      existing.count += entry.count;
      existing.totalMs += entry.totalMs;
      existing.maxMs = Math.max(existing.maxMs, entry.maxMs);
    } else {
      merged.set(name, { ...entry });
    }
  }
  return merged;
}

function mergedCPStats() {
  const merged = new Map(); // cpId -> Map(op -> entry)
  // DB rows
  for (const row of db.prepare('SELECT * FROM stats_cp_operations').all()) {
    if (!merged.has(row.cp_id)) merged.set(row.cp_id, new Map());
    merged.get(row.cp_id).set(row.operation, { count: row.count, totalMs: row.total_ms, maxMs: row.max_ms });
  }
  // In-memory
  for (const [cpId, opMap] of cpStats) {
    if (!merged.has(cpId)) merged.set(cpId, new Map());
    const target = merged.get(cpId);
    for (const [name, entry] of opMap) {
      const existing = target.get(name);
      if (existing) {
        existing.count += entry.count;
        existing.totalMs += entry.totalMs;
        existing.maxMs = Math.max(existing.maxMs, entry.maxMs);
      } else {
        target.set(name, { ...entry });
      }
    }
  }
  return merged;
}

export function getStats() {
  const result = {};
  for (const [name, entry] of mergedOpStats()) {
    result[name] = formatEntry(entry);
  }
  return result;
}

export function getCPStats() {
  const result = {};
  for (const [cpId, opMap] of mergedCPStats()) {
    const ops = {};
    let totalMs = 0;
    let totalCount = 0;
    for (const [name, entry] of opMap) {
      ops[name] = formatEntry(entry);
      totalMs += entry.totalMs;
      totalCount += entry.count;
    }
    result[cpId] = {
      totalMs: Math.round(totalMs * 100) / 100,
      totalCount,
      operations: ops,
    };
  }
  return result;
}

export function getStatsSince() {
  const row = getMeta.get('since');
  return row ? Number(row.value) : Date.now();
}

export function resetStats() {
  stats.clear();
  cpStats.clear();
  db.prepare('DELETE FROM stats_operations').run();
  db.prepare('DELETE FROM stats_cp_operations').run();
  setMeta.run('since', String(Date.now()));
}

## Cry with Me

### index.js

import express from 'express';
import './db.js'; // side-effect: open + initialize the SQLite database
import { getProvider } from './providers/index.js';
import { build } from './build.js';
import { proposeModify, applyModify } from './modify.js';
import { proposeRebuild, applyRebuild } from './rebuild.js';
import { takeSnapshot, listSnapshots, restoreSnapshot } from './model/snapshot.js';
import { getSystem, loadGraph, listSystems, toggleMarking, renameSystem, deleteSystem } from './model/entries.js';
import { partition } from './model/graph.js';

export function setup(server) {
  // Fail closed at BOOT on a bad provider/model config (MODEL-LOG #044: a typo'd
  // env var once silently ran a hard-excluded model for three tests). Dying loud
  // here beats a wrong model discovered in a post-op meter line.
  try {
    const p = getProvider();
    console.log(`[cwm] provider: ${p.name}${p.model ? ` / ${p.model}` : ''}`);
  } catch (e) {
    console.error(`[cwm] FATAL: ${e.message}`);
    process.exit(1);
  }

  const app = express();
  app.use(express.json({ limit: '5mb' }));

  app.get('/api/health', (req, res) => {
    const p = getProvider();
    res.json({ ok: true, app: 'cry-with-me', provider: p.name, model: p.model, ts: Date.now() });
  });

  // The Build verb: prompt -> generated typed entries -> validated + stored (BUILDER §3).
  app.post('/api/build', async (req, res) => {
    const { systemId, name, prompt } = req.body || {};
    if (!prompt || !String(prompt).trim()) return res.status(400).json({ error: 'prompt is required' });
    try {
      const result = await build({ systemId, name, prompt: String(prompt) });
      res.json(result);
    } catch (e) {
      console.error('[build]', e);
      res.status(500).json({ error: e.message });
    }
  });

  // List saved systems, newest first — the client's "your systems" picker, so a
  // build can be reopened (and later modified) instead of evaporating (BUILDER §2).
  app.get('/api/systems', (req, res) => {
    res.json({ systems: listSystems() });
  });

  // Read a system's graph (entries + edges + the sacred/disposable partition).
  app.get('/api/systems/:id', (req, res) => {
    const system = getSystem(req.params.id);
    if (!system) return res.status(404).json({ error: 'system not found' });
    const g = loadGraph(req.params.id);
    res.json({ system, entries: g.entries, edges: g.edges, partition: partition(g) });
  });

  // Rename a saved system (free; the player names what they built).
  app.post('/api/systems/:id/rename', (req, res) => {
    const { name } = req.body || {};
    if (typeof name !== 'string' || !name.trim()) return res.status(400).json({ error: 'name is required' });
    try {
      res.json({ system: renameSystem(req.params.id, name.trim()) });
    } catch (e) {
      res.status(404).json({ error: e.message });
    }
  });

  // Delete a saved system — destructive + unrecoverable (drops entries + edges +
  // row; no snapshot survives it). The client gates it behind a type-the-name
  // confirm; we re-check the typed name here (defense in depth) so a stray request
  // can't nuke a named system. Untitled systems (no stored name) skip the match.
  app.post('/api/systems/:id/delete', (req, res) => {
    const system = getSystem(req.params.id);
    if (!system) return res.status(404).json({ error: 'system not found' });
    const stored = (system.name || '').trim();
    const typed = String((req.body && req.body.confirmName) || '').trim();
    if (stored && typed !== stored) {
      return res.status(400).json({ error: 'name does not match — type the system name to confirm deletion' });
    }
    deleteSystem(req.params.id);
    res.json({ ok: true, id: req.params.id });
  });

  // Set/clear a marking on an entry — free + deterministic (BUILDER §2; the player
  // marks, the builder never imposes). Toggles, and returns the updated graph.
  app.post('/api/systems/:id/mark', (req, res) => {
    const { entryId, kind } = req.body || {};
    if (!entryId || !kind) return res.status(400).json({ error: 'entryId and kind are required' });
    try {
      const marked = toggleMarking(req.params.id, String(entryId), String(kind));
      const g = loadGraph(req.params.id);
      res.json({ ...marked, system: getSystem(req.params.id), entries: g.entries, edges: g.edges, partition: partition(g) });
    } catch (e) {
      res.status(400).json({ error: e.message });
    }
  });

  // Modify — the paid "stray" step (BUILDER §3), in two gates (ECONOMY §6):
  // propose (the model proposes a surgical op-list; metered) then commit (apply the
  // accepted ops; free). The client previews the proposal, then echoes back the ops.
  app.post('/api/systems/:id/modify', async (req, res) => {
    const { instruction } = req.body || {};
    if (!instruction || !String(instruction).trim()) return res.status(400).json({ error: 'instruction is required' });
    try {
      res.json(await proposeModify({ systemId: req.params.id, instruction: String(instruction) }));
    } catch (e) {
      console.error('[modify]', e);
      res.status(500).json({ error: e.message });
    }
  });

  app.post('/api/systems/:id/modify/commit', (req, res) => {
    const { ops } = req.body || {};
    if (!Array.isArray(ops)) return res.status(400).json({ error: 'ops array is required' });
    try {
      res.json(applyModify({ systemId: req.params.id, ops }));
    } catch (e) {
      console.error('[modify/commit]', e);
      res.status(500).json({ error: e.message });
    }
  });

  // Rebuild — collapse→regenerate (BUILDER §2–3). propose (model regenerates the
  // gap toward the aim; metered) then commit (drop disposable + add regenerated;
  // free, snapshots first). Two gates like Modify (ECONOMY §6).
  app.post('/api/systems/:id/rebuild', async (req, res) => {
    try {
      res.json(await proposeRebuild({ systemId: req.params.id, instruction: req.body && req.body.instruction }));
    } catch (e) {
      console.error('[rebuild]', e);
      res.status(500).json({ error: e.message });
    }
  });

  app.post('/api/systems/:id/rebuild/commit', (req, res) => {
    const { dropIds, regenerated } = req.body || {};
    try {
      res.json(applyRebuild({ systemId: req.params.id, dropIds: dropIds || [], regenerated: regenerated || [] }));
    } catch (e) {
      console.error('[rebuild/commit]', e);
      res.status(500).json({ error: e.message });
    }
  });

  // Snapshots — the undo layer (ECONOMY §9). List / take one / restore one.
  app.get('/api/systems/:id/snapshots', (req, res) => {
    res.json({ snapshots: listSnapshots(req.params.id) });
  });

  app.post('/api/systems/:id/snapshots', (req, res) => {
    try {
      res.json(takeSnapshot(req.params.id, String((req.body && req.body.label) || 'manual')));
    } catch (e) {
      res.status(404).json({ error: e.message });
    }
  });

  app.post('/api/snapshots/:snapId/restore', (req, res) => {
    try {
      const sysId = restoreSnapshot(req.params.snapId);
      const g = loadGraph(sysId);
      res.json({ system: getSystem(sysId), entries: g.entries, edges: g.edges, partition: partition(g) });
    } catch (e) {
      res.status(404).json({ error: e.message });
    }
  });

  server.on('request', app);
  return app;
}

// Direct run (npm run dev) — create our own bare HTTP server. In production,
// bootstrap.js owns the server and calls setup() after the early static handler.
if (import.meta.url === `file://${process.argv[1]}`) {
  const { createServer } = await import('http');
  const PORT = process.env.PORT || 3001;
  const server = createServer();
  setup(server);
  server.listen(PORT, () => console.log(`[cwm] dev server on http://localhost:${PORT}`));
}

### meter.js (again, for figuring out how much server space is used for charging)

import db from './db.js';

// The metering layer (ECONOMY.md §6 / BUILDER.md §4): record tokens + cost for
// every paid op, "from request one." Local/self-hosted models are compute-only
// (≈ $0, MODEL-EVAL Phase 0); paid model rates fill in from MODEL-EVAL.md when
// those providers are wired.
const RATES = {
  'ollama:*': { in: 0, out: 0 },
  'stub:*': { in: 0, out: 0 },
  // e.g. 'cohere:command-r7b': { in: 0.0375, out: 0.15 },  // $/Mtok
};

function rate(provider, model) {
  return RATES[`${provider}:${model}`] || RATES[`${provider}:*`] || { in: 0, out: 0 };
}

export function costUsd(provider, model, usage = {}) {
  const r = rate(provider, model);
  return ((usage.inputTokens || 0) * r.in + (usage.outputTokens || 0) * r.out) / 1e6;
}

const ins = db.prepare(`
  INSERT INTO ledger (system_id, op, provider, model, input_tokens, output_tokens, cost_usd, duration_ms, created_at)
  VALUES (?, ?, ?, ?, ?, ?, ?, ?, ?)
`);

// `durationMs` = the op's wall-clock server time (ECONOMY §11): on local models
// inference is ~$0 but not ~0 *time*, and server time is what a host actually bills
// — so we meter it from request one alongside tokens, the way CPB tracked its
// processing time (the "91% of server time from 3.5% of requests" shape).
export function record({ systemId, op, provider, model, usage = {}, durationMs = 0 }) {
  const cost = costUsd(provider, model, usage);
  ins.run(systemId, op, provider, model, usage.inputTokens || 0, usage.outputTokens || 0, cost, Math.max(0, Math.round(durationMs)), Date.now());
  return cost;
}

### modify.js

import { getProvider } from './providers/index.js';
import { modifySchema } from '../shared/schema.js';
import { groundingFor, typeGuide } from './build.js';
import { coerce, applyRollBands, refTargetsOf, resolveMechanicRefs } from './model/compose.js';
import { getSystem, loadGraph, addEntry, updateEntry, removeEntry, addEdge, validateEntry, setMarking, setMechanic } from './model/entries.js';
import { isMarkingKind } from '../shared/types.js';
import { partition } from './model/graph.js';
import { takeSnapshot } from './model/snapshot.js';
import { record } from './meter.js';

// The Modify verb (BUILDER §3): the loop's paid "stray" step. A loaded system +
// the player's instruction -> the model proposes a SMALL surgical op-list (add /
// update / remove) -> we coerce + balance (code owns the numbers) + validate ->
// PREVIEW. The player accepts -> applyModify runs deterministically (free). The
// player's markings ride in as context (honor Stars, never rebuild toward Lines);
// the builder still never sets them.

function serializeSystem(graph) {
  const marks = new Map(); // entryId -> [kind]
  for (const e of graph.edges) {
    if (e.rel !== 'marks') continue;
    const kind = graph.byId.get(e.from)?.mechanic?.kind;
    if (kind) { if (!marks.has(e.to)) marks.set(e.to, []); marks.get(e.to).push(kind); }
  }
  const lines = [];
  for (const e of graph.entries) {
    if (e.type === 'marking') continue;
    const refs = graph.edges.filter((g) => g.from === e.id && g.rel === 'ref').map((g) => g.to);
    const mk = marks.get(e.id) || [];
    const note = e.meaning?.note ? `  — ${e.meaning.note}` : '';
    lines.push(`[${e.id}] ${e.type} "${e.name}"${mk.length ? ` {${mk.join(', ')}}` : ''}  mechanic:${JSON.stringify(e.mechanic || {})}${refs.length ? `  refs:[${refs.join(', ')}]` : ''}${note}`);
  }
  return lines.join('\n') || '(empty system)';
}

function modifyPrompt(grounding, systemText, instruction) {
  return `You are the author inside "Cry with Me", EDITING an existing tabletop RPG toward the player's instruction. You are the system's author, not a game master. Make the SMALLEST set of surgical changes that satisfies the instruction — change what's asked, keep the rest. Impose nothing; never narrate the story.

THE CURRENT SYSTEM (each entry by id; the player's markings are in {braces}):
<<<
${systemText}
>>>

CHANGE THE MECHANICS, NOT JUST THE NOTE — this is the most important rule. If the instruction asks to limit, gate, cost, deplete, cap, reorder, or rebalance something, you MUST change the actual mechanic fields and refs — never just rewrite the "note" to claim it. A note that describes a change you didn't make to the mechanics is a FAILED edit. Concretely:
- To GATE/LIMIT an Armor or Modifier so it can't always apply: add a small limiter entry (e.g. an Armor named "Once per Session") and list its id in the thing's "built_from", or lower its "reduces"/"effect". The limit must exist as mechanics.
- To make a Roll DEPLETE or fill a Track: put that Track's id in the Roll's "refs", and write the deplete/fill into the specific outcome text ("…and lose 1 box of Loss's Shadow").
- To make something COST a resource: reference the resource's id and state the cost in a mechanic-bearing field, not only the note.
- Every reference must RESOLVE to a real entry: use an existing entry's id, or a localId you add in this op-list — never reference a Track/Roll that doesn't exist. If you need one (an Armor's built_from, a Roll that depletes a Track), CREATE it with an "add" op in the same list.

MARKINGS — honor the player's, and SET new ones ONLY from what they explicitly say. Keep/feature {STAR} entries; never rebuild toward {LINE} entries. When the player EXPLICITLY says they value / love / want to KEEP a specific entry, add a { "op": "mark", "id": "<that entry's id>", "kind": "STAR" } op (WISH for "I wish/aspire to", LINE for "ban/never/avoid", VEIL for "hide"). Only from an explicit statement about a specific entry — never infer an unstated preference, and never mark on your own initiative.

CRAFT: a small working MACHINE — entries interlock via refs; be CONCRETE; earn the emotion through the MECHANICS; honor the DARKNESS (loss, cost, what's been taken).

${grounding ? `GROUNDING — real CC-BY source material, distilled. Imitate its mechanical precision; do not copy its text or names.\n<<<\n${grounding}\n>>>\n\n` : ''}Entry types (the "type" field) and their mechanic fields:
${typeGuide()}

Output a list of OPS, each exactly one of:
- { "op": "add", "localId", "type", "name", "mechanic", "meaning", "refs" } — a NEW entry (reference others by existing id or a localId added here).
- { "op": "update", "id", "type", "name", "mechanic", "meaning", "refs" } — REPLACE that entry's content (full new entry; id stays). Use to re-type, re-balance, or rewire it.
- { "op": "remove", "id" } — delete an entry.
- { "op": "mark", "id", "kind" } — set a player marking (only from an explicit statement; see above).

For a roll, each outcome is { "result": "<what happens>", "quality": <integer: how good this is for the PLAYER, −3 = worst … +3 = best> }. The system orders outcomes by quality (worst→best) and assigns die bands by odds — you NEVER sort them or write numbers. ONE exception: if the player themself assigns die numbers to results ("put X on 2-3"), copy exactly their numbers into each outcome's "on" ("1", "2-3", "4") — every die result covered exactly once, no gaps or overlaps — and omit "quality"; the system verifies the numbers and falls back to computed bands if they don't add up. To REORDER a roll's bands (e.g. "worst lowest, best highest"), return an op:"update" that keeps every existing result text VERBATIM and only assigns each a "quality" — do NOT rewrite, replace, sanitize, or remove-and-re-add the outcomes; a reorder changes ranking, never wording. "dice" is plain NdM; you MAY change the die (e.g. 2d6 → 3d6) if it fits the bands more cleanly. Always include a grounded "meaning.note".

Change as little as possible, but make every change REAL in the mechanics. Output ONLY JSON: { "ops": [ ... ] }.`;
}

// Propose (paid): the model returns an op-list; we coerce + balance + validate it
// and METER the call. Nothing is applied yet — this is the preview.
export async function proposeModify({ systemId, instruction }) {
  const startedAt = Date.now();
  const provider = getProvider();
  if (!getSystem(systemId)) throw new Error(`system not found: ${systemId}`);
  const graph = loadGraph(systemId);
  const grounding = groundingFor(instruction);
  const system = modifyPrompt(grounding, serializeSystem(graph), instruction);
  const messages = [{ role: 'user', content: String(instruction) }];

  const quote = await provider.countTokens({ system, messages });
  const { json, text, usage } = await provider.generate({ system, messages, schema: modifySchema(), op: 'modify' });

  let parsed = json;
  if (!parsed && text) { try { parsed = JSON.parse(text); } catch { /* leave null */ } }
  const rawOps = parsed && Array.isArray(parsed.ops) ? parsed.ops : [];

  const ids = new Set(graph.entries.map((e) => e.id));
  const existingMarks = new Set();
  for (const e of graph.edges) {
    if (e.rel === 'marks') { const k = graph.byId.get(e.from)?.mechanic?.kind; if (k) existingMarks.add(`${e.to}::${k}`); }
  }
  const ops = [];
  const rejects = [];
  for (const o of rawOps) {
    const op = String(o.op || '').toLowerCase();
    if (op === 'remove') {
      // REMOVE-guard (#038: a dense Modify silently deleted the very Track its own
      // rename referenced). A removal is destructive and the model sometimes proposes
      // one nobody asked for — so carry the target's NAME + TYPE (a raw id is
      // illegible in the preview) and who still REFERENCES it (graph edges in), so
      // the player can see exactly what would be deleted and what would dangle.
      // Soft-surface, never auto-drop: the player decides per-removal in the preview.
      if (ids.has(o.id)) {
        const target = graph.byId.get(o.id);
        const referencedBy = graph.edges
          .filter((g) => g.rel === 'ref' && g.to === o.id && g.from !== o.id)
          .map((g) => graph.byId.get(g.from)?.name)
          .filter(Boolean);
        ops.push({ op, id: o.id, name: target?.name, type: target?.type, referencedBy });
      } else rejects.push({ op, id: o.id, errors: ['no such entry'] });
      continue;
    }
    if (op === 'mark') {
      const kind = String(o.kind || '').toUpperCase();
      if (!ids.has(o.id)) rejects.push({ op, id: o.id, errors: ['no such entry'] });
      else if (!isMarkingKind(kind)) rejects.push({ op, kind: o.kind, errors: ['unknown marking'] });
      else if (!existingMarks.has(`${o.id}::${kind}`)) ops.push({ op, id: o.id, kind });
      continue;
    }
    if (op !== 'add' && op !== 'update') { rejects.push({ op, errors: ['unknown op'] }); continue; }
    if (op === 'update' && !ids.has(o.id)) { rejects.push({ op, id: o.id, errors: ['no such entry'] }); continue; }
    const type = o.type;
    const mechanic = coerce(type, o.mechanic || {});
    if (type === 'roll') applyRollBands(mechanic);
    const errors = validateEntry({ type, mechanic });
    if (errors.length) { rejects.push({ op, id: o.id, name: o.name, type, errors }); continue; }
    ops.push({
      op, id: o.id, localId: o.localId != null ? String(o.localId) : undefined,
      type, name: o.name || '(unnamed)', mechanic, meaning: o.meaning || {},
      refs: Array.isArray(o.refs) ? o.refs.map(String) : [],
    });
  }

  const summary = ops.map((o) =>
    o.op === 'remove' ? `remove ${o.name ? `${o.type} "${o.name}"` : o.id}`
      : o.op === 'mark' ? `mark ${o.kind} on ${o.id}`
        : o.op === 'update' ? `update [${o.id}] → ${o.type} "${o.name}"`
          : `add ${o.type} "${o.name}"`);

  const durationMs = Date.now() - startedAt;
  const cost = record({ systemId, op: 'modify', provider: provider.name, model: provider.model, usage, durationMs });
  if (rejects.length) console.warn(`[modify] ${rejects.length} ops rejected:`, JSON.stringify(rejects));
  return {
    systemId, provider: provider.name, model: provider.model, grounded: !!grounding,
    instruction: String(instruction), ops, rejects, summary,
    quote, usage, cost, durationMs,
    raw: parsed ? undefined : (text || '').slice(0, 500),
  };
}

// Apply accepted ops deterministically (free — the model already ran in propose).
// Two passes so refs to freshly-added entries resolve, then an edge pass folds in
// built_from/applies_to (the seam fix). A bad op is skipped, not fatal.
export function applyModify({ systemId, ops = [] }) {
  if (!getSystem(systemId)) throw new Error(`system not found: ${systemId}`);
  takeSnapshot(systemId, 'before modify'); // undo point (ECONOMY §9)
  const graph = loadGraph(systemId);
  const ids = new Set(graph.entries.map((e) => e.id));
  const nameMap = new Map();
  for (const e of graph.entries) if (e.name) nameMap.set(e.name.toLowerCase(), e.id);
  const localMap = new Map();
  const touched = [];
  const applied = [];
  const skipped = [];

  for (const o of ops) {
    try {
      if (o.op === 'add' || o.op === 'update') {
        // Re-balance here too, so apply is self-sufficient and idempotent on the
        // already-banded ops a propose returns (code owns the Roll numbers).
        const mechanic = applyRollBands(coerce(o.type, o.mechanic || {}));
        if (o.op === 'add') {
          const id = addEntry(systemId, { type: o.type, name: o.name, mechanic, meaning: o.meaning, refs: [] });
          if (o.localId) localMap.set(String(o.localId), id);
          ids.add(id); if (o.name) nameMap.set(String(o.name).toLowerCase(), id);
          touched.push({ entryId: id, mechanic, refs: o.refs });
          applied.push({ op: 'add', id });
        } else {
          updateEntry(o.id, { type: o.type, name: o.name, mechanic, meaning: o.meaning });
          if (o.name) nameMap.set(String(o.name).toLowerCase(), o.id);
          touched.push({ entryId: o.id, mechanic, refs: o.refs });
          applied.push({ op: 'update', id: o.id });
        }
      } else if (o.op === 'remove') {
        removeEntry(o.id); ids.delete(o.id);
        applied.push({ op: 'remove', id: o.id });
      } else if (o.op === 'mark') {
        setMarking(systemId, o.id, o.kind);
        applied.push({ op: 'mark', id: o.id, kind: o.kind });
      } else {
        skipped.push({ op: o.op, error: 'unknown op' });
      }
    } catch (e) {
      skipped.push({ op: o.op, id: o.id, error: e.message });
    }
  }

  // edge pass: refs + built_from + applies_to -> resolved ids (localId | id | name)
  const resolve = (raw) => localMap.get(String(raw)) || (ids.has(raw) ? raw : nameMap.get(String(raw).toLowerCase()));
  for (const t of touched) {
    const resolved = resolveMechanicRefs(t.mechanic, resolve); // rewrite built_from/applies_to to real ids (so the entry can price itself)
    if (resolved !== t.mechanic) setMechanic(t.entryId, resolved);
    for (const raw of refTargetsOf(resolved, t.refs)) {
      const to = resolve(raw);
      if (to && to !== t.entryId && ids.has(to)) addEdge(systemId, t.entryId, to, 'ref');
    }
  }

  const after = loadGraph(systemId);
  if (skipped.length) console.warn(`[modify/commit] ${skipped.length} ops skipped:`, JSON.stringify(skipped));
  return { systemId, applied, skipped, system: getSystem(systemId), entries: after.entries, edges: after.edges, partition: partition(after) };
}

## Take a Stab (only one file: main.gd; note that there are Godot #, ##, etc. signs below for comments; those are not part of this file's structural delineation)

extends Node3D
## Main scene: builds the hallway, manages lighting, spawns player and zombies.

const HALLWAY_WIDTH := 4.0
const HALLWAY_HEIGHT := 3.0
const HALLWAY_LENGTH := 2000.0
const WALL_THICKNESS := 0.2

var player: CharacterBody3D
var zombie_scene: PackedScene = preload("res://scenes/zombie/zombie.tscn")
var player_scene: PackedScene = preload("res://scenes/player/player.tscn")
var spawn_cooldown := 0.0


func _ready() -> void:
	_setup_lighting()
	_build_hallway()
	_spawn_player()
	_spawn_zombie()

	GameManager.zombie_killed.connect(_on_zombie_killed)
	GameManager.player_died.connect(_on_player_died)
	GameManager.game_reset.connect(_on_game_reset)


func _process(delta: float) -> void:
	if not GameManager.is_playing:
		return

	# Maintain minimum zombie count
	spawn_cooldown -= delta
	var active := _get_active_zombie_count()
	if active < 1:
		_spawn_zombie()
		spawn_cooldown = GameManager.get_spawn_interval()
	elif active < GameManager.get_max_zombies() and spawn_cooldown <= 0:
		_spawn_zombie()
		spawn_cooldown = GameManager.get_spawn_interval()


func _setup_lighting() -> void:
	var light := DirectionalLight3D.new()
	light.rotation_degrees = Vector3(-45, -15, 0)
	light.light_energy = 1.0
	light.shadow_enabled = false  # Shadows can be unreliable in web/Compatibility renderer
	add_child(light)

	# Second light from behind for fill
	var fill_light := DirectionalLight3D.new()
	fill_light.rotation_degrees = Vector3(-30, 165, 0)
	fill_light.light_energy = 0.4
	fill_light.shadow_enabled = false
	add_child(fill_light)

	var env_node := WorldEnvironment.new()
	var environment := Environment.new()
	environment.background_mode = Environment.BG_COLOR
	environment.background_color = Color(0.08, 0.08, 0.1)
	environment.ambient_light_source = Environment.AMBIENT_SOURCE_COLOR
	environment.ambient_light_color = Color(0.4, 0.4, 0.45)
	environment.ambient_light_energy = 0.7
	env_node.environment = environment
	add_child(env_node)


func _build_hallway() -> void:
	var half_w := HALLWAY_WIDTH / 2.0
	var half_t := WALL_THICKNESS / 2.0

	# Floor (surface at y=0)
	_add_static_box(
		Vector3(HALLWAY_WIDTH, WALL_THICKNESS, HALLWAY_LENGTH),
		Vector3(0, -half_t, 0),
		Color(0.3, 0.3, 0.3)
	)
	# Ceiling
	_add_static_box(
		Vector3(HALLWAY_WIDTH, WALL_THICKNESS, HALLWAY_LENGTH),
		Vector3(0, HALLWAY_HEIGHT + half_t, 0),
		Color(0.22, 0.22, 0.24)
	)
	# Left wall
	_add_static_box(
		Vector3(WALL_THICKNESS, HALLWAY_HEIGHT, HALLWAY_LENGTH),
		Vector3(-half_w - half_t, HALLWAY_HEIGHT / 2.0, 0),
		Color(0.35, 0.33, 0.32)
	)
	# Right wall
	_add_static_box(
		Vector3(WALL_THICKNESS, HALLWAY_HEIGHT, HALLWAY_LENGTH),
		Vector3(half_w + half_t, HALLWAY_HEIGHT / 2.0, 0),
		Color(0.35, 0.33, 0.32)
	)


func _add_static_box(size: Vector3, pos: Vector3, color: Color) -> void:
	var body := StaticBody3D.new()
	body.position = pos
	body.collision_layer = 1
	body.collision_mask = 0

	var col := CollisionShape3D.new()
	var shape := BoxShape3D.new()
	shape.size = size
	col.shape = shape
	body.add_child(col)

	var mesh_inst := MeshInstance3D.new()
	var mesh := BoxMesh.new()
	mesh.size = size
	mesh_inst.mesh = mesh
	var mat := StandardMaterial3D.new()
	mat.albedo_color = color
	mesh_inst.set_surface_override_material(0, mat)
	body.add_child(mesh_inst)

	add_child(body)


func _spawn_player() -> void:
	player = player_scene.instantiate()
	player.position = Vector3(0, 0, 0)
	add_child(player)


func _spawn_zombie() -> void:
	var zombie := zombie_scene.instantiate()
	var half_w := HALLWAY_WIDTH / 2.0 - 0.5
	var spawn_x := randf_range(-half_w, half_w)
	var spawn_z := player.position.z - randf_range(15.0, 25.0)
	zombie.position = Vector3(spawn_x, 0, spawn_z)
	zombie.target = player
	add_child(zombie)


func _get_active_zombie_count() -> int:
	var count := 0
	for zombie in get_tree().get_nodes_in_group("zombies"):
		if not zombie.is_dead:
			count += 1
	return count


func _on_zombie_killed() -> void:
	spawn_cooldown = GameManager.get_spawn_interval()


func _on_player_died() -> void:
	# Death sequence (camera pan, Play Again) handled by player.gd
	# Zombies freeze via is_playing check in their _physics_process
	pass


func _on_game_reset() -> void:
	spawn_cooldown = 0.0
	if _get_active_zombie_count() < 1:
		_spawn_zombie()

# Conclusion
Just a reminder that I'd like you to help me outline the language stack for an application called The Real Classic (detailed especially near the top of this prompt, but generally throughout), reusing as much as possible from previous applications (key code snippets of which are listed above) while also being as simple as possible language-wise (not using too many languages).