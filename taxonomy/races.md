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
- **Appearance:** Short, broad, muscular, usually bearded — whether females share the beard is an open subject of fan debate.
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
