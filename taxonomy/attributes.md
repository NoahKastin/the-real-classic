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

