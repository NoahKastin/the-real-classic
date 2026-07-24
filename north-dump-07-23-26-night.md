Hey North. I'd like you to help me figure out how to make an appropriate language stack for generating new visual assets as requested by users for the tool below. The existing language stack assumes that only zombies and hallways need to be drawn; in fact, much more needs to be able to be drawn, as dynamically requested by users.

# What is this project that needs drawing for?

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

## What's the bulk of what needs drawing?

Mostly custom races. Zones and armor don't need too much art, but users may want arbitrarily customized races. Race design is the visual foundation of the player experience. A player commits to looking at the player's chosen race for potentially dozens of hours of gameplay; aesthetic appeal and visual distinctiveness matter more than lore consistency or mechanical balance alone. A variety of preset race varieties to draw from are listed below.

### Humans
- **Appearance:** No special appearance of note; everything else in this file is weighted against Humans, who get average appearances.

### Orcs
- **Appearance:** Strapping, sometimes hunched, often with porcine features or protruding canines (fangs/tusks); read above all as a fearsome sight to enemies.

### Elves
- **Appearance:** Slender, usually tall, pointy-eared (sometimes with very long ears on the sides or top of the head), almost always long-lived or outright immortal, with features reflecting an ancient yet still supernaturally beautiful bearing.
- **Variants:** Trolls (the WoW/D&D sense — folklore trolls don't fit this entry; see Ogres below) follow the same profile but tusked, sometimes hunched, and usually less beautiful, with every non-Agility attribute +1 except Intellect, which lands at 16–19 instead. Shivarra, if requested, get six arms.

### Dwarves
- **Appearance:** Short, broad, muscular, usually bearded — whether females share the beard is an open subject of fan debate. Ensure that users' requests are warranted as to whether female dwarves have beards or no beards; not listening to this request may well alienate the users.

### Gnomes/goblins/halflings/imps/pygmies
- **Appearance:** Diminutive, sometimes earth spirits, frequently long-armed with few digits, almost always exaggerated (large heads, large and sometimes pointed ears). Split by tone: played childlike and cute, or adult and hideous (grins, sometimes horns) — read which the user is going for (gnomes skew cute, imps skew hideous/horned).
- **Variants:** Mechanical prosthetics are fine for customization — the issue is only the name Mechagnomes, not the concept. Watch for fully artificial, golem-like tiny beings if Wechselkind are requested; the line between the two is thin and not worth stressing over.

### Vampires/dhampir
- **Appearance:** Blood-sucking, usually undead, batlike features and/or bat transformation — a very common trope, fuzzily defined in WoW itself, where vampires read as either undead elves or elf/troll progenitors.

### Other undead
- **Appearance:** Almost-universally hunched and gruesome; the spectrum runs from fleshy abominations to lean, hirsute ghouls to fleshless skeletons to fleshless-and-shimmery liches to transparent ghosts and banshees, distinguished mainly by hair/skin/transparency. Zombies sit in the middle of that spectrum (except transparency) and sometimes are missing an arm — though player characters wouldn't be.

### Satyrs
- **Appearance:** Widely varying amounts of hair; a prominent set of races in the original universe.
- **Variants:** Wings, if a demonic archetype is requested (Ered'ruin, Incubi, Nathrezim, Sayaads, Succubi, Terrorguards — the link is Pan's association with Satan). Facial tentacles only if specified, or if Draenei/Eredar are requested.

### Naga/siren/undine
- **Appearance:** Graceful but deadly, aquatic, sometimes draconic and serpentine — rooted in Indian folklore but blurring heavily into Western mermaids visually: scales, head protrusions that could read as fins or snake-hoods, long tails instead of legs.

### Frogmen/fishmen
- **Appearance:** Little distinction between frogmen and fishmen as a category, especially since WoW's Murlocs blend both. Often (not always) small, hunched, large-headed and grotesque, with fins or other head protrusions and eyes on the side or top of the head.

### Ogres/half-giants/hobgoblins/ettins
- **Appearance:** Like humans, but much bigger and usually far more muscular; sometimes multiple heads, sometimes one eye per head. Weight-to-height varies widely — ogres and hobgoblins run heavyset, other types in the category run slenderer.
- **Variants:** One-eyed, if Magnaron, Gronn, or Ogron are requested. Made of stone, if a stone variant is requested (Mogu or Magnaron). Folklore trolls (the bridge-dwelling sort) conform to this entry — unlike WoW/D&D trolls, which fit the Elves entry instead.

### Harpies
- **Appearance:** Winged, feathered, taloned, often hunched — unless meant to read as angelic, which WoW folds into this same category quite often. Size varies widely.

### Foxmen/raccoonmen/squirrelmen/rabbitmen/mousemen
- **Appearance:** Short, furry, scrappy, with prominent ears corresponding to the specific animal.
- **Variants:** Distinguished from Catmen (below) by an emphasis on scavenging rather than deception, and by being exclusively diminutive — Catmen aren't always small and lean crafty/tricky instead. If Viera are requested, that's the Elves entry, not this one.

### Catmen
- **Appearance:** A common fantasy race, ranging from lithe, sometimes diminutive housecat-like humanoids to more leonine and physically imposing variants.
- **Variants:** Six-limbed, if Tol'vir or six limbs are requested — WoW's own version of this race.

### Other large animal-men (werewolves/minotaurs/centaurs/dryads/tarands)
- **Appearance:** Heads and/or bodies of wolves, horses, cows, bears, monkeys, or other animals — moose, deer, reindeer, hyenas, even something as different as elephants.
- **Variants:** Werewolves/wolfmen are the exception to the attribute pattern above: Agility +2 (22–25), Spirit and Stamina −0–1 (19/20–22), with Strength and Intellect still following the general rule.

### Dragonkin
- **Appearance:** Dragons themselves usually run too large to be playable, but their humanoid ilk often are — wings, horns, usually scales, sometimes other draconic features like reptilian snouts, but roughly the size of other playable races, if more innately magical than most.

### Epiphagi
- **Appearance:** Headless. May have floating headgear (masks and the like) or simply no head at all. If corporeal, facial features may relocate elsewhere on the body (eyes in the shoulders or nipples, mouths in the neck or stomach); otherwise the features are just missing, with only any headgear hinting at them.

### Insectmen
- **Appearance:** Wide variety across the WoW universe, often cast as servants of evil races, corrupted by evil magic, or both — no more specific visual description given.

### Plantmen/spriggans/treants
- **Appearance:** Woody skin, leaves or branches for hair or limbs. Size is inconsistent across the category — spriggans usually tiny, treants usually enormous, plain plantmen somewhere in between (tall and slender, or merely large).

# The Existing Language Stack
Below is a **compact language‑stack blueprint** for “The Real Classic” that

* **re‑uses every code snippet you already have** (the entry‑management helpers and the hallway‑builder),
* stays **as small as possible**, and
* lets us ship a working prototype with only three runtime languages + a little glue.

---

## 1️⃣ Quick‑look Table (What lives where)

| Layer / Concern                              | Primary language(s) | Why this language?                                            | What code from the past is reused? |
|----------------------------------------------||-----------------------|--------------------------------------------------------------|------------------------------
| **Data‑model & mutation API**                | TypeScript → Node.js | • Strongly‑typed business logic (applyRollBands, addEntry…) <br>• Easy HTTP JSON API for frontend / game sync  
<br>• Can be run locally (`node`) or in the cloud | `applyRollBands`, `addEntry`/`updateEntry`/`removeEntry`/`setMarking`, the whole **modify/commit** logic |
| **Live gameplay & world**                    | GDScript (Godot)     | • 3‑D engine, built‑in physics, scene system <br>• All of *main.gd* already implements hallway, lighting and 
zombie spawning <br>• Can expose a tiny HTTP helper so the backend can push “game‑state” events (`GameManager` signals) | `_setup_lighting`, `_build_hallway`, `_add_static_box`, 
`_spawn_player`, `_spawn_zombie`, `GameManager.zombie_killed`, `GameManager.player_died`, `GameManager.game_reset` |
| **Admin / UI (optional, for config, logs)**  | Vanilla JavaScript + HTML + CSS (no framework) | • Zero‑dependencies – “simple as possible” <br>• Can talk directly to the TypeScript 
API via fetch/XHR <br>• Easy to host on the same CDN as the game | Nothing new; just thin wrappers that call `/api/entries`, `/api/game-state` etc. |
| **Deployment helpers**                      | Bash (Linux/macOS)  &amp; JSON configs | • `npm run dev`, `node dist/` scripts <br>• Godot export templates, scene build steps | N/A – 
pure glue |

> **Bottom line:** If you ever need something else later (e.g. a desktop client), you can always add it on top of the existing three layers without touching core logic.

---

## 2️⃣ In‑depth rationale

### A. Data‑model & mutation API (`TypeScript / Node.js`)
* **Location** – `src/` folder → `api.ts`, `entries.ts`, `modify.ts`, `system.ts`, etc.
* **Core pieces (directly copied from the earlier snippets)**
  * `applyRollBands(coerce(o.type, o.mechanic || {}))` – stays in TypeScript so we get compile‑time safety on its shape.
  * CRUD helpers (`addEntry`, `updateEntry`, `removeEntry`, `setMarking`) – these now talk to a **single JSON file** (`data.json`) as the “document store”. That keeps the runtime 
dependency list tiny (just Node built‑ins + `fs`).
  * The whole **`modify/commit`** flow you posted: `applied[]`, `skipped[]`, `loadGraph`, `partition`. This becomes a set of exported functions that any consumer (admin UI or Godot 
script) can call via HTTP.
* **Why TypeScript?**
  * Your existing snippets were written in a style that looks like TS (interfaces, `const enum`s, try/catch). Re‑using them as‑is eliminates re‑writing logic.
  * It gives you **type‑guarded state** – essential when we start exposing the API to a JavaScript UI or Godot side (the latter can receive JSON and `JSON.parse`).
* **Endpoints (example)**
  ```ts
  // src/routes.ts
  app.post('/api/entries', async (req, res) => {
    const result = await applyEntry(req.body);
    res.json(result);
  });
  // GET /api/game-state → returns light‑weight snapshot of world
  ```
* **Testing** – Simple unit tests with Jest for business logic; the UI can be manually tested.

### B. Game Engine (Godot) – The “World”
* Keep everything that’s visual and interactive in Godot.
* **Scene hierarchy**
  * `MainMenu.tscn` – title screen + play button
  * `GameWorld.tscn` – hallway, walls, zombies (prefabs)
  * `PlayerCharacter.tsc` – controller for the hero
* The existing `_spawn`/`_update` logic that you have in your current project can stay untouched; we just need to wire up the new API calls.
* **Integration with the back‑end**
  * When a player presses “Restart” or when a zombie is killed, fire an HTTP request to `POST /game/events`.
  * The server acknowledges and may trigger a “save checkpoint” event that updates the persistent state (the same JSON file the client reads for next time).
* **Light‑weight networking** – For small‑scale desktop play, we can keep everything local; if you want remote leaderboards later, add a WebSocket connection.

### C. Admin / Debug UI (optional)
If you ever need to tweak game parameters (e.g., spawn rates, enemy health) without recompiling the engine, you could expose:
* A lightweight web server that serves an HTML page with form inputs.
* Those inputs POST to the same `/api/config` endpoint used by the game logic.
This keeps the “God mode” completely separate from the production build.

### D. Packaging & Distribution
* **Desktop** – Use Godot’s built‑in exporter (Windows/macOS/Linux). The engine already ships with a `template.conf` that can point to our custom runtime.
* **Web** – If you want a browser version, export to Web assembly; it will use the same C#/.NET core but without native plugins. For now, keep the focus on desktop.

---

## 3️⃣ Putting It All Together – Suggested Project Layout

```
project-root/
├─ server/               # Node.js back‑end
│   ├─ src/
│   │   ├─ api.ts        # express app with /api/*
│   │   └─ db.json       # simple JSON store for game state
│   └─ package.json
├─ engine/               # Godot project (C#)
│   ├─ GODOT_VERSION.txt
│   ├─ export.cfg
│   └─ scene/
│        ├─ MainMenu.tscn
│        └─ GameWorld/
│              ├─ hallway.png
│              └─ zombie.prefab
├─ admin/                # optional web admin (optional)
└─ README.md            # quick-start guide
```

**Workflow for a typical developer**

1. Edit the Godot scene, adjust zombie prefabs.
2. In `engine/` run `godot` → export to desktop or use live‑play in the built‑editor.
3. For any changes to the underlying data (e.g., new enemy stats), update `server/src/models/enemy.ts`, re‑run `npm run dev`.
4. Open a browser, type `http://localhost:8080` → see the admin panel (if enabled).
5. Close everything; push to repo.

---

## 4️⃣ Summary – Why This Design?

| Goal | How It’s Achieved |
|------|-------------------|
| **Clear separation of concerns** | TypeScript → business logic & API, Godot → visual gameplay, simple JSON for persistence |
| **Fast iteration** | Edit a Godot scene and see changes instantly; modify server logic and restart Node (no build pipeline) |
| **Low operational overhead** | No heavy containers, just `node` + `godot` binaries. Optional Docker ignore unless you want containerised deployments. |
| **Extensible** | Adding new game features = new scenes or API routes; no need to rework the whole stack. |
| **Maintainable** | Small number of files per domain → easy for a single developer (or small team) to understand and fix bugs. |

# Code Snippets
These give an idea as to what visual structures are already in place, which can be built upon for generation of new image assets, game positioning, and so on.

## club-penguin-builder/server/state.js

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

## take-a-stab/scenes/main.gd (note that there are Godot #, ##, etc. signs below for comments; those are not part of this file's structural delineation)

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

## take-a-stab/scenes/zombie/zombie.gd (note that there are Godot #, ##, etc. signs below for comments; those are not part of this file's structural delineation)

extends CharacterBody3D
## Floating eye monster: drifts toward the player, bites when close.
## Builds its own mesh (body sphere, eye, pupil, spikes) with random colors.

const MOVE_SPEED := 2.0
const BITE_RANGE := 1.0
const GRAVITY := 9.8
const FLOAT_HEIGHT := 1.6  # Eye level, matching player camera height
const BOB_AMOUNT := 0.08
const BOB_SPEED := 2.5
const SPIKE_COUNT := 4

var target: Node3D = null
var is_dead := false
var has_bitten := false
var bob_phase := 0.0

var body_node: Node3D
var body_mesh: MeshInstance3D
var eye_mesh: MeshInstance3D
var pupil_mesh: MeshInstance3D
var spike_meshes: Array[MeshInstance3D] = []
var collision_shape: CollisionShape3D
var body_color: Color
var eye_color: Color


func _ready() -> void:
	add_to_group("zombies")

	# Collision: layer 2 (characters), mask 1|2 (env + characters)
	collision_layer = 2
	collision_mask = 3

	# Collision sphere near ground so CharacterBody3D origin stays at floor level
	collision_shape = CollisionShape3D.new()
	var sphere_shape := SphereShape3D.new()
	sphere_shape.radius = 0.25
	collision_shape.shape = sphere_shape
	collision_shape.position = Vector3(0, 0.25, 0)  # Bottom of sphere at y=0
	add_child(collision_shape)

	# Body node at float height (all visual meshes are children of this)
	body_node = Node3D.new()
	body_node.name = "Body"
	body_node.position = Vector3(0, FLOAT_HEIGHT, 0)
	add_child(body_node)

	bob_phase = randf() * TAU  # Random start phase so they don't bob in sync

	_build_meshes()
	_randomize_colors()


func _build_meshes() -> void:
	# Main body sphere
	body_mesh = MeshInstance3D.new()
	var body_sphere := SphereMesh.new()
	body_sphere.radius = 0.2
	body_sphere.height = 0.4
	body_mesh.mesh = body_sphere
	body_mesh.cast_shadow = GeometryInstance3D.SHADOW_CASTING_SETTING_OFF
	body_node.add_child(body_mesh)

	# Eye: flattened sphere protruding from the front
	eye_mesh = MeshInstance3D.new()
	var eye_sphere := SphereMesh.new()
	eye_sphere.radius = 0.1
	eye_sphere.height = 0.12  # Flattened
	eye_mesh.mesh = eye_sphere
	eye_mesh.cast_shadow = GeometryInstance3D.SHADOW_CASTING_SETTING_OFF
	eye_mesh.position = Vector3(0, 0, -0.16)  # Protruding forward
	body_node.add_child(eye_mesh)

	# Pupil: small dark sphere in front of the eye
	pupil_mesh = MeshInstance3D.new()
	var pupil_sphere := SphereMesh.new()
	pupil_sphere.radius = 0.04
	pupil_sphere.height = 0.05
	pupil_mesh.mesh = pupil_sphere
	pupil_mesh.cast_shadow = GeometryInstance3D.SHADOW_CASTING_SETTING_OFF
	pupil_mesh.position = Vector3(0, 0, -0.22)
	body_node.add_child(pupil_mesh)

	# Spikes: triangular prisms pointing outward (PrismMesh point is +Y by default)
	# Each entry: [position offset, rotation to point outward]
	var spike_data := [
		[Vector3(0, 0.22, 0.04), Vector3(0, 0, 0)],                          # Top (point already +Y)
		[Vector3(0, -0.22, 0.04), Vector3(0, 0, deg_to_rad(180))],            # Bottom (flip)
		[Vector3(0.22, 0.04, 0.03), Vector3(0, 0, deg_to_rad(-90))],          # Right
		[Vector3(-0.22, 0.04, 0.03), Vector3(0, 0, deg_to_rad(90))],          # Left
	]
	for data in spike_data:
		var spike := MeshInstance3D.new()
		var prism := PrismMesh.new()
		prism.size = Vector3(0.06, 0.12, 0.06)
		spike.mesh = prism
		spike.cast_shadow = GeometryInstance3D.SHADOW_CASTING_SETTING_OFF
		spike.position = data[0]
		spike.rotation = data[1]
		body_node.add_child(spike)
		spike_meshes.append(spike)

	# Teeth: ring of small sharp prisms around the front-bottom, below the eye
	var tooth_count := 8
	for i in range(tooth_count):
		var tooth := MeshInstance3D.new()
		var prism := PrismMesh.new()
		prism.size = Vector3(0.02, 0.06, 0.02)  # Small, pointy
		tooth.mesh = prism
		tooth.cast_shadow = GeometryInstance3D.SHADOW_CASTING_SETTING_OFF

		# Arrange in a semicircle on the front-bottom of the body
		var angle := deg_to_rad(-80 + float(i) / float(tooth_count - 1) * 160.0)
		var ring_radius := 0.14
		tooth.position = Vector3(
			sin(angle) * ring_radius,
			-0.08,
			-cos(angle) * ring_radius - 0.04
		)
		# Point teeth outward/forward: tilt so points face away from center
		tooth.rotation = Vector3(deg_to_rad(-70), angle, 0)

		var mat := StandardMaterial3D.new()
		mat.albedo_color = Color(0.95, 0.92, 0.8)  # Off-white bone
		tooth.set_surface_override_material(0, mat)
		body_node.add_child(tooth)


func _randomize_colors() -> void:
	body_color = Color(randf(), randf(), randf())
	eye_color = Color(randf(), randf(), randf())
	_set_mesh_color(body_mesh, body_color)
	_set_mesh_color(eye_mesh, eye_color)
	_set_mesh_color(pupil_mesh, Color(0.02, 0.02, 0.02))  # Near-black pupil
	for spike in spike_meshes:
		_set_mesh_color(spike, body_color.darkened(0.3))


func _set_mesh_color(mesh: MeshInstance3D, color: Color) -> void:
	var mat := StandardMaterial3D.new()
	mat.albedo_color = color
	mesh.set_surface_override_material(0, mat)


func _physics_process(delta: float) -> void:
	if is_dead or target == null or not GameManager.is_playing:
		return

	# Gravity
	if not is_on_floor():
		velocity.y -= GRAVITY * delta
	else:
		velocity.y = 0.0

	# Float bob
	bob_phase += delta * BOB_SPEED
	body_node.position.y = FLOAT_HEIGHT + sin(bob_phase) * BOB_AMOUNT

	# Drift toward the player (horizontal only)
	var to_player := target.global_position - global_position
	to_player.y = 0.0
	var dist := to_player.length()

	if dist > 0.1:
		var direction := to_player.normalized()
		velocity.x = direction.x * MOVE_SPEED
		velocity.z = direction.z * MOVE_SPEED

		# Face the player (horizontal only)
		var look_target := Vector3(target.global_position.x, global_position.y, target.global_position.z)
		look_at(look_target, Vector3.UP)
	else:
		velocity.x = 0.0
		velocity.z = 0.0

	move_and_slide()

	# Despawn if too far behind the player
	if global_position.z > target.global_position.z + 10.0:
		is_dead = true
		queue_free()
		return

	# Bite check
	if dist < BITE_RANGE and not has_bitten:
		_bite()


func _bite() -> void:
	has_bitten = true
	GameManager.player_bitten(self)


func get_head_position() -> Vector3:
	return body_node.global_position


func die(blood_color: Color, _blood_dir: Vector3) -> void:
	if is_dead:
		return
	is_dead = true
	set_physics_process(false)

	# Disable collision
	collision_shape.set_deferred("disabled", true)

	# Hide the monster meshes
	body_node.visible = false

	# Explode into small spheres
	_spawn_sphere_explosion(blood_color)

	# Clean up after explosion
	var timer := get_tree().create_timer(0.8)
	timer.timeout.connect(queue_free)


func _spawn_sphere_explosion(color: Color) -> void:
	var origin := body_node.global_position
	var scene_root := get_tree().current_scene
	var sphere_count := 10 + randi() % 6  # 10-15 spheres

	for i in range(sphere_count):
		var particle := MeshInstance3D.new()
		var sphere := SphereMesh.new()
		sphere.radius = randf_range(0.02, 0.06)
		sphere.height = sphere.radius * 2.0
		particle.mesh = sphere
		particle.cast_shadow = GeometryInstance3D.SHADOW_CASTING_SETTING_OFF

		# Mix blood color with body/eye colors for variety
		var mix := randf()
		var particle_color: Color
		if mix < 0.5:
			particle_color = color
		elif mix < 0.8:
			particle_color = body_color
		else:
			particle_color = eye_color

		var mat := StandardMaterial3D.new()
		mat.albedo_color = particle_color
		particle.set_surface_override_material(0, mat)

		scene_root.add_child(particle)
		particle.global_position = origin

		# Fly outward in all directions
		var direction := Vector3(
			randf_range(-1, 1),
			randf_range(-0.5, 1),  # Bias upward
			randf_range(-1, 1),
		).normalized()
		var target_pos := origin + direction * randf_range(0.3, 1.0)

		var tween := create_tween()
		tween.set_parallel(true)
		tween.tween_property(particle, "global_position", target_pos, randf_range(0.3, 0.6)).set_ease(Tween.EASE_OUT)
		tween.tween_property(particle, "scale", Vector3.ZERO, randf_range(0.4, 0.7)).set_delay(0.1)
		tween.set_parallel(false)
		tween.tween_callback(particle.queue_free)

# Conclusion
As a reminder, I'd like you to help me figure out how to make an appropriate language stack for generating new visual assets as requested by users for the tool below. The existing language stack assumes that only zombies and hallways need to be drawn; in fact, much more needs to be able to be drawn, as dynamically requested by users, especially custom races.