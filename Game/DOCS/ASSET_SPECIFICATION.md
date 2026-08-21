# Star Spirit — Asset Specification

**Status:** implementation-ready asset/gameplay boundary  
**Branch:** `docs/gameplay-specification-2026-08-21`  
**Date:** 2026-08-21  
**Scope:** archived asset clusters and their known gameplay meaning. This document does not define Godot scenes, nodes, resources, scripts, import settings or final balance.

## 0. Asset evidence protocol

The archive is treated as a source layer, not as a canonical finished-game content database.

- **CONFIRMED** — asset or property directly exists in the repository.
- **CROSS-SOURCE CONFIRMED** — repository asset structure and a separate textual/source document agree.
- **DOCX TRANSCRIPTION** — property recorded from the supplied seven-document transcription.
- **DOCX-SOURCE VALUE** — concrete value/mechanic from that transcription; not final balance.
- **INFERRED** — documentation-level interpretation.
- **UNCERTAIN** — asset exists but gameplay meaning is not established.
- **DESIGN DECISION PENDING** — gameplay meaning requires explicit approval.

## 1. Archived asset layer overview

The source audit identifies these gameplay-relevant clusters inside `IMPORT(INCOMPLETED, DONT DELETE)/`:

- `Враги/Королевство/`
- `Неписи/Королевство/`
- `Окружение/Королевство/`
- `Оружия/`
- `Подбираемые предметы/Королевство/`
- `Фон локаций/Королевство/`

The archive is historical material and should not be treated as the implemented Godot content tree. `Game/` currently contains only the minimal Godot project files according to the source audit.

## 2. Enemy asset specification

### 2.1 Rotating Rat — `Крыса(Крутящаяся)`

**Archive location:** `IMPORT(INCOMPLETED, DONT DELETE)/Враги/Королевство/Крыса(Крутящаяся)/`

**Asset existence:** **CROSS-SOURCE CONFIRMED**.

The directory contains visual attack/death material; the archive also contains a dedicated DOCX. The source audit explicitly states that the cluster contains directed sprites and attack/death animations.

**Gameplay data:** supplied by the DOCX transcription.

| Property | Source status | Current value |
|---|---|---:|
| HP | DOCX-SOURCE VALUE | 20 |
| Defense | DOCX-SOURCE VALUE | 0 |
| Moving contact damage | DOCX-SOURCE VALUE | 3 |
| Spin duration | DOCX-SOURCE VALUE | 5 s |
| Damage while contact-hit | DOCX-SOURCE VALUE | 5 / s |
| Approach toward player while spinning | DOCX-SOURCE VALUE | Yes |

**Design boundary:**

The animation asset can represent the attack visually, but AI pathing, target acquisition, cooldowns, exact hitbox dimensions and reset behavior remain unresolved.

### 2.2 Shooting Rat — `Крыса(Стреляющая)`

**Archive location:** `IMPORT(INCOMPLETED, DONT DELETE)/Враги/Королевство/Крыса(Стреляющая)/`

**Asset existence:** **CROSS-SOURCE CONFIRMED**.

The source audit identifies directed images plus visual material for firing, HP/death-related states, mouth open/close and related animation sheets. A dedicated DOCX is present in the asset directory.

**Gameplay data:**

| Property | Source status | Current value |
|---|---|---:|
| HP | DOCX-SOURCE VALUE | 30 |
| Defense | DOCX-SOURCE VALUE | 3 |
| Moving contact damage | DOCX-SOURCE VALUE | 3 |
| Contact damage condition | DOCX-SOURCE VALUE | while moving |
| Tracking behavior | DOCX-SOURCE VALUE | stops and tracks player |
| Shot damage | DOCX-SOURCE VALUE | 15 |

**Post-death state:**

The rat becomes the `пельмешка` state. The DOCX transcription provides:

- 400 HP — **DOCX-SOURCE VALUE**;
- 0 defense — **DOCX-SOURCE VALUE**;
- own hitbox — **DOCX-SOURCE VALUE**;
- wall-like pushable behavior — **DOCX-SOURCE VALUE**;
- several damage states — **DOCX-SOURCE VALUE**;
- explosion after maximum damage — **DOCX-SOURCE VALUE**.

A possible ability for another enemy to throw the `пельмешка` is **UNCERTAIN** and must not become a required asset behavior without a new decision.

### 2.3 Fish — `Рыба`

**Archive location:** `Враги/Королевство/Рыба/`

**Asset existence:** **CONFIRMED**.

No gameplay parameters, attack rules or AI are established in the current source set. Do not infer them from the asset name or image.

## 3. Weapon asset specification

### 3.1 Blood Staff — `Кровавый посох`

**Archive location:** `IMPORT(INCOMPLETED, DONT DELETE)/Оружия/Кровавый посох/`

**Asset existence:** **CROSS-SOURCE CONFIRMED**.

The source audit records visual material for drawing/holstering, attack, projectile appearance and projectile destruction, plus a dedicated DOCX.

**Gameplay behavior:**

- One attack creates **3 blood spikes** — **DOCX-SOURCE VALUE**.
- Spikes form a wedge — **DOCX-SOURCE VALUE**.
- All three are created simultaneously — **DOCX-SOURCE VALUE**.
- The wedge travels toward enemies — **DOCX-SOURCE VALUE**.
- Each spike deals **5 damage** — **DOCX-SOURCE VALUE**.
- On hit, a projectile remains attached to the enemy for **2 seconds**, then disappears — **DOCX-SOURCE VALUE**.
- If all three spikes hit the same enemy simultaneously, defense is reduced by **5 for 6 seconds** — **DOCX-SOURCE VALUE**.

**Unknown:** hand consumption, attack cadence, projectile speed/range, collision rule, effect stacking/refresh and the precise behavior when fewer than three spikes hit.

**Balance status:** **DESIGN DECISION PENDING**. The values are source values, not final balancing.

### 3.2 Slime Pistol — `Слаймовый пистолет`

**Archive location:** `IMPORT(INCOMPLETED, DONT DELETE)/Оружия/Слаймовый пистолет/`

**Asset existence:** **CROSS-SOURCE CONFIRMED**.

The source audit identifies a draw animation plus the dedicated DOCX. The concept independently confirms that slime can transform into weapons and that slime weapons are used in the hand.

**Gameplay behavior:**

| Property | Source status | Current value |
|---|---|---|
| Weapon category | DOCX TRANSCRIPTION | slime weapon |
| Hand requirement | DOCX-SOURCE VALUE | 1 hand |
| Projectile | DOCX-SOURCE VALUE | yes |
| Damage | DOCX-SOURCE VALUE | 15 / shot |
| Slime cost | DOCX-SOURCE VALUE | 5 slime health / shot |
| Enemy status effects | DOCX-SOURCE VALUE | none |

**Description text:** the transcription records the source description `Пистолет из слайма,тут нечего сказать.` as DOCX-only material.

**Unknown:** projectile speed/range, fire cadence, draw exceptions, hit reaction and complete slime resource rules.

### 3.3 Demon Glove — `Демоническая перчатка`

**Archive location:** `Оружия/Демоническая перчатка/`

**Asset existence:** **CONFIRMED**.

The archive contains appearance, disappearance, AFK and attack visual material.

No dedicated gameplay stat set is currently established. Therefore:

- damage — **UNCERTAIN**;
- hand count — **UNCERTAIN**;
- active/passive classification — **UNCERTAIN**;
- resource cost — **UNCERTAIN**;
- status effects — **UNCERTAIN**;
- progression role — **UNCERTAIN**.

### 3.4 Generic weapon DOCX

`Оружия/Новый документ.docx` is associated with the root of the weapon category and has no canonical weapon name in the provided transcription.

Its source-described lifecycle is:

1. first weapon attack-button press → draw/equip animation;
2. subsequent presses → normal attack;
3. 10 seconds without use → disappearance/unequip animation.

This is **DOCX-ONLY**. Do not invent an item name or weapon statistics from the file name.

### 3.5 Weapon lifecycle visual requirement

Where the archive provides appearance/disappearance or AFK/attack states, the asset set supports authoring distinct presentation states. The generic timing/transition rule is still pending universalization.

## 4. Pickup/item asset specification

### 4.1 Chestnut — `Каштан`

**Archive location:** `IMPORT(INCOMPLETED, DONT DELETE)/Подбираемые предметы/Королевство/Каштан/`

**Asset existence:** **CROSS-SOURCE CONFIRMED**.

The archive contains at least two pickup-state visuals:

- `Можно подобрать.png`
- `Нельзя подобрать.png`

This confirms distinct pickup availability states at the asset level.

**Gameplay meaning added by DOCX transcription:**

- Chestnut is the **main ammunition for the chestnut launcher** — **DOCX-SOURCE VALUE**.
- Source description text exists and is preserved as DOCX-only source material.

**Unknown / pending:**

- stack size;
- maximum carry amount;
- pickup trigger;
- whether non-pickable is caused by inventory capacity, world state or another condition;
- respawn;
- launcher final status;
- storage/economy role.

Do not create a general currency or inventory economy from this single item.

## 5. Building / world-interaction asset specification

### 5.1 Basic Peasant House 1

**Archive location:** `IMPORT(INCOMPLETED, DONT DELETE)/Окружение/Королевство/Постройки/Базовый крестьянский дом 1/`

**Asset existence:** **CROSS-SOURCE CONFIRMED**.

The source audit records authored variants for:

- non-interactive/base house state;
- door interaction state;
- window interaction state.

The associated DOCX is `Описания действиЙ.docx`.

**Door interaction text:**

> `"Кто бы мог подумать,что дверь чужого дома в чужого города окажется закрытой"`

**Status:** **DOCX-ONLY source text**. It establishes the source line, not a universal door rule or final dialogue canon.

**Window interaction text:**

> `"О боже…. Там столько ПИВА…"`

**Status:** **DOCX-ONLY source text**.

**Gameplay implication:** door and window are separate authored interaction states — **CROSS-SOURCE CONFIRMED**. Exact input, consequence and repeat behavior are **DESIGN DECISION PENDING**.

## 6. NPC assets

### Peasant 1 — `Крестьянин 1`

**Asset existence:** **CONFIRMED**.

The source audit records standing and walking animations in multiple directions.

NPC interaction/reaction is part of the game concept, but this asset does not establish:

- role;
- dialogue tree;
- quest assignment;
- faction;
- shop functionality.

### Hat character — `Крутой мужик в шляпе(Возможно,торговец)`

**Asset existence:** **CONFIRMED**.

The filename itself labels the trade function as possible/speculative. Therefore "trader" is **UNCERTAIN**, not confirmed.

Do not implement a shop role from the filename alone.

## 7. Environment asset boundary

The source audit records Kingdom environment materials for:

- animated grass;
- road/city floor stone material;
- `Кратор.jpg`;
- basic peasant house and its door/window variants;
- spruce;
- bushes;
- berry bush with/without berries;
- apple tree with/without apples.

These assets establish content clusters and authored visual states, not a final world map or simulation rules.

### State-bearing environment assets — INFERRED design category

The following asset pairs suggest world objects may have explicit authored state changes:

- bush with / without berries;
- apple tree with / without apples;
- pickup can / cannot be picked up;
- house door/window interaction variants.

This is a useful design boundary for content documentation, but it does not mandate a generic state system or respawn mechanic.

## 8. Background / location reference assets

The archive contains:

- `Магический лес.jpg`;
- `Пиратская бухта.jpg`.

**Status:** **CONFIRMED as asset/reference names**.

These names do not establish:

- complete biomes;
- final map positions;
- story sequence;
- adjacency;
- region ownership;
- gameplay mechanics.

## 9. Asset-to-gameplay mapping table

| Asset cluster | Gameplay role supported | Confidence | Main unresolved point |
|---|---|---|---|
| Rotating Rat | moving/spinning enemy | CROSS-SOURCE CONFIRMED | exact AI, cooldowns, hitbox |
| Shooting Rat | tracking/ranged enemy + `пельмешка` state | CROSS-SOURCE CONFIRMED | projectile details, post-death identity/explosion rules |
| Fish | enemy asset only | CONFIRMED | all gameplay behavior |
| Blood Staff | weapon with 3-spike wedge attack | CROSS-SOURCE CONFIRMED | hand use, cadence, exact hit model |
| Slime Pistol | one-hand slime weapon | CROSS-SOURCE CONFIRMED | slime resource model, fire cadence |
| Demon Glove | weapon visual cluster | CONFIRMED | gameplay role/stats |
| Chestnut | pickup + launcher ammunition | CROSS-SOURCE CONFIRMED | inventory/stack/launcher final status |
| Peasant House 1 | environment with door/window states | CROSS-SOURCE CONFIRMED | interaction input/consequences |
| Peasant 1 | NPC | CONFIRMED | dialogue/role/quests |
| Hat character | NPC/reference | CONFIRMED | trader role is not confirmed |
| Magic Forest | visual reference/background | CONFIRMED as named asset | whether it is a full region |
| Pirate Cove | visual reference/background | CONFIRMED as named asset | whether it is a full region |

## 10. Source integrity rules for assets

1. Asset presence proves **existence**, not final gameplay meaning.
2. File names marked `Возможно...` retain that uncertainty.
3. DOCX values are source values, not final balance.
4. Visual animation names may support a state/animation interpretation only when the meaning is explicit from the name or corroborated by text.
5. Missing gameplay documentation must remain `UNCERTAIN` or `DESIGN DECISION PENDING`.
6. Do not create new weapons, enemies, slime variants or item types from gaps in the archive.
7. Do not alter the historical `IMPORT(INCOMPLETED, DONT DELETE)/` layer as part of gameplay specification work.

## 11. Readiness boundary for implementation

The next implementation agent has sufficient source-level boundaries to create gameplay representations for:

- the two documented rats;
- the Blood Staff;
- the Slime Pistol;
- the documented generic weapon lifecycle;
- the Chestnut pickup/ammunition relationship;
- the `пельмешка` state;
- the house door/window interaction states.

It does **not** yet have approved final rules for:

- player numerical stats;
- damage mitigation;
- universal weapon timeout;
- complete slime resource management;
- exact build-slot counts;
- the chestnut launcher implementation status;
- broad interaction input rules;
- gameplay behavior of undocumented asset clusters.

These gaps are intentionally preserved in `GAMEPLAY_SYSTEMS.md` and `DECISION_LOG.md`.
