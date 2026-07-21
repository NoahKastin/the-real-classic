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
