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
