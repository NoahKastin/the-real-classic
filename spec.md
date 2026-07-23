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

**Direct code ports (same JS/Vite/Express/fly.io stack):**
- `club-penguin-builder` — the platform skeleton: accounts, Socket.IO multiplayer presence, SQLite persistence, Stripe payments, Phaser+React client, fly.io deploy with auto-stop. Feature-complete and deployed.
- `cry-with-me` — the AI layer: `server/build.js`/`modify.js`/`rebuild.js` generation verbs, `shared/types.js` ENTRY_TYPES taxonomy format + `shared/schema.js` structured outputs, `server/providers/` model abstraction, `server/meter.js` token/$ metering, and retrieval grounding (retrieval-only won the A/B; the curated pack is opt-in). Author the Realm patch schema as a new ENTRY_TYPES vocabulary in this format so the whole pipeline carries over.

**Design ports only (GDScript — logic gets rewritten as server-authoritative JS):**
- `take-a-stab` (Godot 4) — shipped real-time melee combat: enemy chase/attack loop (`zombie.gd` `_physics_process`/`_bite`/`die`), hit geometry, difficulty ramp. (Easy to forget this repo exists — that's why it's listed.)
- `combo-spell` (Godot) — unit/enemy AI behavior catalog (`docs/behaviors.md`: attack, defend-a-point, encircle, etc.)
- Aggro radius, pathing, respawn, and XP designs are covered across these three.

**Taxonomy source of truth:** the docs in `taxonomy/` are canonical — statistics + entry types, this project's analogue of the Master 4E source that cry-with-me's `types.js` encoded rather than invented. ENTRY_TYPES gets encoded *from* those docs, and the same docs feed the runtime retrieval corpus (cry-with-me's `corpus/` + `retrieval.js` pattern). Realm Zero is a test fixture (generate-then-freeze; hand-write as fallback), not the taxonomy-defining act.

**Build order:** scaffold + port cry-with-me plumbing → ENTRY_TYPES from the taxonomy docs → taxonomy docs into the corpus → generate Realm Zero, freeze as fixture → JS combat sim from the design ports → wire the generation verbs.
