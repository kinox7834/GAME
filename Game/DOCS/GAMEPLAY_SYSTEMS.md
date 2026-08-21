# Star Spirit — Gameplay Systems Specification

**Status:** implementation-ready gameplay boundary specification  
**Branch:** `docs/gameplay-specification-2026-08-21`  
**Date:** 2026-08-21  
**Scope:** gameplay rules and system boundaries only; no Godot architecture, scene design, resource classes, nodes, signals, save architecture, or code.

> **Source governance:** This document separates source-derived facts from reconstruction and design proposals. Numerical values transcribed from DOCX are `DOCX-SOURCE VALUE` and remain `DESIGN DECISION PENDING` unless a later explicit decision promotes them.

## 0. Evidence protocol

### Statuses used

- **CONFIRMED** — directly established by a source.
- **CROSS-SOURCE CONFIRMED** — established by multiple independent sources, or by source content plus the archived asset structure.
- **DOCX TRANSCRIPTION** — present in the provided transcription of the seven DOCX files; the historical DOCX audit originally recorded the binary extraction as incomplete.
- **DOCX-SOURCE VALUE** — concrete value/mechanic recorded from that transcription.
- **INFERRED** — logical model needed to connect confirmed material without asserting new canon.
- **PROPOSED** — implementation-neutral recommendation; not canon.
- **UNCERTAIN** — insufficient evidence.
- **DESIGN DECISION PENDING** — requires explicit design approval before being treated as final.

### Primary source set

- `Game/DOCS/01_SOURCE_AUDIT.md`
- `Game/DOCS/GAME_BIBLE.md`
- `Game/DOCS/STORY_BIBLE.md`
- `Game/DOCS/WORLD.md`
- `Game/DOCS/DECISION_LOG.md`
- `Game/DOCS/04_DOCX_SOURCE_AUDIT.md` on the DOCX-audit branch `audit/docx-source-extraction-2026-08-21`
- `Game/DOCS/DOCX_EXTRACTED/2026-08-21_EXTRACTED_FACTS.md` on that same audit branch
- `IMPORT(INCOMPLETED, DONT DELETE)/DOCS AND STORY/CONSEPT.txt`
- `IMPORT(INCOMPLETED, DONT DELETE)/DOCS AND STORY/START.txt`
- `IMPORT(INCOMPLETED, DONT DELETE)/DOCS AND STORY/SOME INFO.txt`
- `IMPORT(INCOMPLETED, DONT DELETE)/DOCS AND STORY/CONTROLS.txt`
- `IMPORT(INCOMPLETED, DONT DELETE)/DOCS AND STORY/STORY.txt`
- archived asset structure under `IMPORT(INCOMPLETED, DONT DELETE)/`

## 1. Gameplay identity and loop

### 1.1 Core fantasy — CONFIRMED

Star Spirit is a 2D metroidvania/action game built around a large world with many locations, threats, bosses, weapons, active items and passive items. The player follows routes, removes threats, receives rewards, becomes stronger, and uses acquired capabilities to continue progressing. Backtracking and early access to some locations when the player has the required items are explicitly part of the concept.

### 1.2 Minimal gameplay loop — CROSS-SOURCE CONFIRMED

`EXPLORE → ENCOUNTER THREAT/OBSTACLE → FIGHT OR PASS → REWARD / NEW CAPABILITY → NEW ROUTE OR BACKTRACK → CONTINUE TOWARD OBJECTIVE`

This is a documentation-level synthesis of the stated core loop and metroidvania progression. It is not a newly invented sequence of mandatory events.

### 1.3 Build loop — INFERRED

The combat/build layer sits inside the main loop:

`ACQUIRE EQUIPMENT → SELECT BUILD → USE BUILD IN COMBAT → FIND MORE EQUIPMENT / UPGRADES → RECONFIGURE BUILD`

The sources confirm build variety, passive items, active items, slime variants, upgrade branches and differing slot counts, but do not define the exact inventory/build management procedure.

## 2. Player movement and world traversal

### Movement

- Walking exists — **CONFIRMED** (`CONSEPT.txt`, `CONTROLS.txt`).
- Default movement input is the left stick / WASD — **CONFIRMED**.
- Camera is side-top / side-overhead — **CONFIRMED**.
- The player character is intended to remain centered on screen — **CONFIRMED** from `CONSEPT.txt`.
- Exact movement speed, acceleration, deceleration, friction, collision rules and traversal modifiers are **UNCERTAIN**.

### Dodge / roll

- A roll/dodge exists — **CONFIRMED**.
- It is mapped to Circle on PlayStation and Shift on keyboard — **CONFIRMED**.
- Exact invulnerability, distance, duration, cooldown/resource cost and interaction with hazards are **DESIGN DECISION PENDING**.
- Do not infer an invulnerability model merely from the word "перекат".

### Traversal progression

The world may contain regions whose access becomes possible later through metroidvania progression — **CONFIRMED**. The actual gate may conceptually be an item, ability, weapon, story event or world state, but no specific gate assignment is canonically defined — **CONFIRMED LIMIT / UNCERTAIN CONTENT**.

## 3. Player combat state model

### 3.1 Player health

- The player can heal — **CONFIRMED** by the healing control.
- The player can die — **CONFIRMED** by the one-life difficulty description.
- A normal health model is therefore strongly supported, but player max HP, current HP representation, damage thresholds and death threshold are **UNCERTAIN**.
- Player HP should not be assigned a number from enemy DOCX values.

### 3.2 Player defense

- Defense is explicitly used as an enemy stat in the extracted DOCX material — **DOCX TRANSCRIPTION**.
- Player defense is **NOT confirmed** by the current sources.
- Any player defense stat or mitigation formula is **DESIGN DECISION PENDING**.

### 3.3 Receiving damage

The sources establish that combat applies damage to enemies and that enemies can damage the player through contact/projectiles. Exact player hit reaction, invulnerability windows, knockback and damage cooldown are **UNCERTAIN**.

### 3.4 Healing

- Healing is an explicit player action — **CONFIRMED**.
- PlayStation: L1. Keyboard: Space — **CONFIRMED**.
- The healing item type, charge count, recovery amount, animation lock and availability rules are **UNCERTAIN**.

### 3.5 Death

Normal difficulty has saves. The second described difficulty removes saving and gives the player one life — **CONFIRMED**, while the source itself says two difficulties are only "most likely".

The exact respawn/reset state on normal difficulty is **UNCERTAIN**.

The exact unlock condition for the one-life difficulty is **UNCERTAIN**.

## 4. Hands and equipment

### 4.1 Hand slots — CONFIRMED concept

- The player has **2 hands**.
- Some upgrades can change the number of hands.
- Equipment capacity is constrained by the number of hands.
- The Slime Pistol occupies **1 hand** — `DOCX-SOURCE VALUE`.

### 4.2 Neutral hand/equipment model — INFERRED

A hand is best treated at design level as a capacity slot for equipment that requires a hand.

```text
PLAYER
├── HAND CAPACITY (base: 2, upgradeable)
├── HAND SLOT A
└── HAND SLOT B
```

This diagram is a neutral model, not a Godot architecture decision.

### 4.3 Multiple-hand weapons — DESIGN DECISION PENDING

The sources establish that weapon use is limited by available hands but do not explicitly state whether a single weapon can consume more than one hand.

Do not add two-handed weapons or dual-wield rules as canon until explicitly decided.

### 4.4 Free-hand behavior — UNCERTAIN

No source defines whether a free hand can be used for a second weapon, an active item, a non-combat action, or nothing. The only safe rule is that hand capacity limits equipment.

### 4.5 Weapon slots vs hands — DESIGN DECISION PENDING

Controls expose **Weapon 1** and **Weapon 2**. The concept exposes a hand-count limitation. The exact relationship between these two concepts is not stated.

Do not assume that Weapon 1 and Weapon 2 literally equal Hand A and Hand B. The final mapping needs an explicit design decision.

## 5. Active and passive items

### Active items

- Active items exist — **CONFIRMED**.
- They can provide a temporary advantage or deal damage — **CONFIRMED** (`CONSEPT.txt`).
- R2 / E activates an active item — **CONFIRMED**.
- Exact slot count, activation semantics, cooldowns, resource costs and interruption rules are **UNCERTAIN**.

### Passive items

- Passive items exist — **CONFIRMED**.
- They form part of the build system — **CONFIRMED**.
- Their slot counts vary with slime variants / progression concepts — **CONFIRMED** at concept level.
- Exact passive effects, stacking, replacement rules and slot management are **UNCERTAIN**.

### Boundary

The following classification is useful as a design boundary but should remain marked **INFERRED**:

- **ACTIVE:** player explicitly triggers the item's effect.
- **PASSIVE:** item changes player/combat state without an explicit activation action.

Do not invent cooldown/resource rules simply from this classification.

## 6. Weapon lifecycle

The root weapon DOCX gives a generic behavior sequence. It is currently `DOCX TRANSCRIPTION` / `DOCX-SOURCE VALUE`, not a universal rule for all future weapons.

### Source-described lifecycle

```text
UNARMED
  ↓ first weapon attack-button press
DRAW / EQUIP ANIMATION
  ↓
READY
  ↓ subsequent press
ATTACK
  ↓
READY
  ↓ unused for 10 seconds (source-described weapon behavior)
UNEQUIP / DISAPPEAR ANIMATION
```

### Confidence boundaries

**Confirmed by DOCX transcription:**

- first attack-button press triggers draw/equip animation;
- later attack presses perform the normal attack;
- 10 seconds of non-use triggers disappearance/unequip animation.

**Not confirmed:**

- that the 10-second timeout applies to every future weapon;
- whether switching weapons resets the timer;
- whether damage can occur during draw;
- whether attack input is buffered during draw/unequip;
- whether active-item use cancels the lifecycle;
- whether the player can manually unequip.

### Decision status

**DESIGN DECISION PENDING:** decide whether the lifecycle is a universal weapon contract or a behavior shared only by the currently documented weapon set.

## 7. Slime system

### 7.1 Confirmed concept

- Slime exists on the player's body — **CONFIRMED**.
- Slime can sometimes transform into a weapon — **CONFIRMED**.
- While a slime weapon is in the player's hand, slime is not displayed on the body — **CONFIRMED**.
- There are multiple slime variants — **CONFIRMED**.
- Each variant has its own progression branch — **CONFIRMED**.
- Variants differ in equipment/active-item/hand slot counts — **CONFIRMED**.

### 7.2 Slime state abstraction — INFERRED

At design level, slime has at least two visibly distinct presentation states:

```text
BODY SLIME PRESENT
        ↕
SLIME TRANSFORMED INTO HELD WEAPON
```

This is a presentation/gameplay relationship, not an implementation architecture.

### 7.3 Slime resource model

The Slime Pistol source says each shot consumes **5 slime health** — `DOCX-SOURCE VALUE`.

This establishes a consumable cost tied to slime health for this weapon. It does **not** yet establish:

- a universal slime-health resource;
- maximum slime health;
- regeneration;
- whether slime can reach zero;
- whether slime can die;
- whether slime health is shared across all slime weapons;
- whether different slime variants use different resources;
- whether the cost is fixed or weapon-specific.

All of the above are **DESIGN DECISION PENDING**.

Do not create a separate resource system simply because it is technically convenient.

## 8. Resource model

### Confirmed resources / resource-like values

| Resource / value | Status | Current meaning |
|---|---|---|
| Player health | CONFIRMED concept | Player can heal and die; max/value unknown |
| Enemy HP | CROSS-SOURCE CONFIRMED concept + DOCX values | Enemy durability; values are source values, not final balance |
| Enemy defense | DOCX-SOURCE VALUE for documented rats | Defense value on those enemies |
| Slime health | DOCX-SOURCE VALUE as a cost on Slime Pistol | 5 consumed per shot for this weapon; full resource model pending |
| Chestnut | DOCX-SOURCE VALUE | Main ammunition for a chestnut launcher |
| Weapons | CONFIRMED | Equipment and rewards; exact inventory rules pending |

### Explicitly not established

No general currency, XP bar, stamina meter, ammo pool beyond the documented chestnut role, or universal combat energy system is confirmed by the sources.

## 9. Enemy stat model

### 9.1 Conceptual fields

The current material supports the following design-level fields:

```text
HP
DEFENSE
DAMAGE
ATTACK BEHAVIOR
MOVEMENT BEHAVIOR
STATUS / DEBUFF BEHAVIOR (where present)
```

**HP / Defense / Damage** are directly represented in the extracted enemy material. **Movement** and attack behavior are described for the two documented rats. Status/debuff behavior is demonstrated by the Blood Staff against enemies, but not established as a universal enemy stat field.

### 9.2 Damage formula

A formula such as:

`Damage = Attack - Defense`

is **PROPOSED only** and requires design approval.

No mitigation formula is canonically established. Do not implement one as a fact.

## 10. Damage types and hit model

### Confirmed examples

- Enemy contact damage exists — **DOCX TRANSCRIPTION**.
- Enemy projectile damage exists — **DOCX TRANSCRIPTION**.
- Blood Staff can deal direct projectile damage — **DOCX TRANSCRIPTION**.
- Blood Staff can apply a temporary defense reduction — **DOCX TRANSCRIPTION**.
- Slime Pistol explicitly has no status effects — **DOCX-SOURCE VALUE**.

### Not established

No universal damage taxonomy, elemental system, critical-hit system, armor penetration system, status-effect catalog, stagger system or hit-stop system is confirmed.

## 11. Weapons

### Blood Staff — documented design contract

- Existence: **CROSS-SOURCE CONFIRMED**.
- Type: weapon; exact hand requirement is **UNCERTAIN**.
- One attack creates **3 blood spikes** — `DOCX-SOURCE VALUE`.
- Spikes form a wedge — `DOCX-SOURCE VALUE`.
- All three are created simultaneously — `DOCX-SOURCE VALUE`.
- The wedge travels toward enemies — `DOCX-SOURCE VALUE`.
- Each spike deals **5 damage** — `DOCX-SOURCE VALUE`.
- On hit, a projectile remains attached for **2 seconds**, then disappears — `DOCX-SOURCE VALUE`.
- If all three spikes hit the same enemy simultaneously, defense is reduced by **5 for 6 seconds** — `DOCX-SOURCE VALUE`.

Unknown: range, speed, attack cadence, multi-target behavior, whether each attached spike can independently interact after impact, what happens when only 1–2 spikes hit, exact debuff stacking/refresh, and hand consumption.

### Slime Pistol — documented design contract

- Existence: **CROSS-SOURCE CONFIRMED**.
- Slime weapon: **DOCX-SOURCE VALUE** and consistent with the concept source.
- Uses **1 hand** — `DOCX-SOURCE VALUE`.
- Fires a projectile — `DOCX-SOURCE VALUE`.
- Deals **15 damage per shot** — `DOCX-SOURCE VALUE`.
- Consumes **5 slime health per shot** — `DOCX-SOURCE VALUE`.
- Applies **no status effects** — `DOCX-SOURCE VALUE`.

Unknown: fire rate, projectile speed/range, hit behavior, whether damage is per projectile or a direct hit event, weapon lifecycle exceptions and maximum slime state.

### Demon Glove — asset only

The archived assets contain a `Демоническая перчатка` cluster with appearance, disappearance, AFK and attack visuals — **CONFIRMED asset structure**. No matching gameplay parameter set has been established in the current sources.

Do not assign damage, hand use, status, resource cost or progression role from the asset filenames alone.

### Unnamed weapon document — DOCX-only generic behavior

The root `Оружия/Новый документ.docx` describes generic weapon behavior but does not provide a canonical weapon name in the transcription. Keep it as a generic lifecycle source, not a new named weapon.

Do not invent properties or a title for it.

## 12. Enemy specifications

### 12.1 Rotating Rat (`Крыса(Крутящаяся)`)

**Role:** enemy — **CROSS-SOURCE CONFIRMED**. Exact role wording beyond the documented attack is **INFERRED**.

**Source values:**

- HP: **20** — `DOCX-SOURCE VALUE`
- Defense: **0** — `DOCX-SOURCE VALUE`
- Contact damage: **3** — `DOCX-SOURCE VALUE`
- Contact damage applies while the mob is moving — `DOCX-SOURCE VALUE`
- Spins for **5 seconds** while moving toward the player — `DOCX-SOURCE VALUE`
- On hit, deals **5 damage/second** — `DOCX-SOURCE VALUE`

**Design state model — INFERRED:**

```text
MOVE / APPROACH
    ↓
SPIN / ATTACK MOVEMENT
    ↓
CONTACT HIT (if contact conditions are met)
    ↓
CONTINUE / EXIT ATTACK
    ↓
DEATH
```

The exact state transition timing, AI search range, retargeting, cooldown and post-hit behavior are **UNCERTAIN**. Do not add them as implementation requirements.

### 12.2 Shooting Rat (`Крыса(Стреляющая)`)

**Source values:**

- HP: **30** — `DOCX-SOURCE VALUE`
- Defense: **3** — `DOCX-SOURCE VALUE`
- Contact damage: **3** — `DOCX-SOURCE VALUE`
- Contact damage applies while moving — `DOCX-SOURCE VALUE`
- It stops moving and tracks the player — `DOCX-SOURCE VALUE`
- It stops spinning, opens its mouth and fires — `DOCX-SOURCE VALUE`
- Shot damage: **15** — `DOCX-SOURCE VALUE`
- It closes its mouth after firing — `DOCX-SOURCE VALUE`

**Design state model — INFERRED:**

```text
MOVE
  ↓
STOP / TRACK PLAYER
  ↓
ATTACK PREPARATION
  ↓
OPEN MOUTH / FIRE
  ↓
CLOSE MOUTH
  ↓
RESUME MOVEMENT OR TRACKING (EXACT RULE UNKNOWN)
```

Do not invent a firing cooldown, range, projectile speed or aim logic beyond "tracks the player".

## 13. Shooting Rat post-death "пельмешка"

The extracted source describes a special state reached after the shooting rat dies.

### Confirmed by DOCX transcription

- The rat compresses its tail and becomes a `пельмешка` state.
- State HP: **400** — `DOCX-SOURCE VALUE`.
- Defense: **0** — `DOCX-SOURCE VALUE`.
- It has its **own hitbox** — `DOCX-SOURCE VALUE`.
- It behaves as a wall that can be **pushed by walking into it** — `DOCX-SOURCE VALUE`.
- It has **several damage states** — `DOCX-SOURCE VALUE`.
- It **explodes after maximum damage** — `DOCX-SOURCE VALUE`.

### Explicit uncertainty

"Another enemy can probably throw the `пельмешка`" is **UNCERTAIN** because the source itself uses speculative wording.

### Design boundaries — DESIGN DECISION PENDING

Still unresolved:

- Is the `пельмешка` the same gameplay identity in a new state, or a separate object that inherits source identity?
- Can it receive all ordinary damage types?
- What exactly are its damage stages?
- What triggers explosion beyond reaching maximum damage?
- Does the explosion damage the player, enemies, or environment?
- Can it be pushed in every direction?
- Can pushing it interact with world gates?

No answer should be invented until separately decided.

## 14. Items and pickups

### Chestnut (`Каштан`)

- Existence: **CROSS-SOURCE CONFIRMED**.
- It has separate visual states for `Можно подобрать` / `Нельзя подобрать` — **CONFIRMED asset structure**.
- It is the **main ammunition for the chestnut launcher** — `DOCX-SOURCE VALUE`.
- The source description calls it an ordinary chestnut — `DOCX-ONLY`.

Unknown: stack size, pickup conditions, max carry amount, respawn, world placement, launcher existence as a final weapon, ammo consumption timing, reserve/storage model and economy role.

### Inventory/economy boundary

The existence of a pickup does not justify creating a broad inventory or economy system. The only safe requirement is that the player can acquire the documented pickup and that its relationship to the chestnut launcher must be representable.

## 15. Progression and metroidvania

### Confirmed

- Large connected/linked world concept.
- Gradual access to locations.
- Backtracking.
- Earlier-than-expected access when the player possesses required items.
- Equipment can be hidden or dropped by enemies.
- Build growth and slime upgrades are part of the concept.
- Hand capacity can change through upgrades.

### Neutral progression model — INFERRED

```text
CURRENT ACCESS
   ↓
DISCOVER/ACQUIRE REQUIREMENT
   ↓
NEW ACCESS
   ↓
EXPLORE / BACKTRACK
   ↓
ACQUIRE MORE BUILD / COMBAT OPTIONS
```

### Gate taxonomy — documentation requirement

A locked route may be marked with one or more unresolved requirement categories:

- `ITEM`
- `ABILITY`
- `WEAPON`
- `STORY EVENT`
- `WORLD STATE`
- `UNKNOWN`

These categories describe the kind of data a future level designer must provide. They do not assign actual keys or abilities.

## 16. Rewards

### Confirmed reward sources

- quest rewards / valuable game experience — **CONFIRMED**;
- items and weapons — **CONFIRMED**;
- enemy drops — **CONFIRMED**;
- hidden equipment — **CONFIRMED**.

### Not confirmed

No currency, shop economy, XP level system, rarity tiers, crafting or universal loot-table system is established by the current sources.

## 17. Build system structure

### Confirmed components

```text
SLIME VARIANT
├── UNIQUE UPGRADE BRANCH
├── HAND CAPACITY
├── EQUIPMENT SLOTS
├── ACTIVE-ITEM SLOTS
└── AVAILABLE BUILD OPTIONS
```

This is a **structural model**, not a technical class diagram.

### Build boundaries

- Slime variants affect progression and slot availability — **CONFIRMED**.
- Exact variant list — **UNCERTAIN**.
- Exact upgrade tree — **UNCERTAIN**.
- Exact slot counts — **UNCERTAIN**.
- Whether passive and active items use independent slot pools — **UNCERTAIN but implied by wording**.
- Exact equipment replacement/swap rules — **UNCERTAIN**.

## 18. Exploration and backtracking

### Confirmed

Backtracking is an intended part of the game. Some areas may be reached early with the correct items.

### Design implication — INFERRED

Previously visited areas must remain potentially relevant after progression. Relevance may be through access, rewards, dialogue, equipment, or route changes, but the sources do not specify which mechanisms must occur.

### Not established

Fast travel, map markers, region completion, respawn changes, enemy respawns, secret-room systems and procedural route changes are all **UNCERTAIN**.

## 19. World interaction

### NPCs and dialogue

- Characters react to player actions and dialogue — **CONFIRMED**.
- NPC dialogue exists — **CONFIRMED**.
- Exact interaction input is not present in `CONTROLS.txt` — **CONFIRMED**.

### Door/window interactions

The house asset cluster includes interaction variants for doors and windows — **CROSS-SOURCE CONFIRMED** via asset structure plus DOCX transcription.

DOCX-transcribed interaction text:

- Door: `"Кто бы мог подумать,что дверь чужого дома в чужого города окажется закрытой"` — **DOCX-ONLY**.
- Window: `"О боже…. Там столько ПИВА…"` — **DOCX-ONLY**.

The text does not by itself establish a universal interaction architecture or gameplay consequence.

### Pickup interaction

The chestnut assets show pickable/non-pickable states — **CONFIRMED asset structure**. The exact pickup trigger and inventory behavior are **UNCERTAIN**.

### Object state

A gameplay object may have multiple authored states where the archive provides them (for example chestnut pickup state, house door/window variants, weapon visibility states). This is an **INFERRED design boundary**, not a generic runtime architecture.

## 20. Controls matrix

The controls below are transcribed from `CONTROLS.txt` and should not be changed in this specification.

| Action | PlayStation | Keyboard |
|---|---|---|
| Walk | Left Stick | WASD |
| Roll | Circle | Shift |
| Weapon 1 | Triangle | Right Mouse Button |
| Weapon 2 | Square | Left Mouse Button |
| Active item | R2 | E |
| Map / Inventory | Touchpad | Tab |
| Map/Inventory page switch | R1 / L1 | A / D or Arrow Keys |
| Heal | L1 | Space |
| Pause | Options | Esc |
| Hell Portal | Hold L2 | Hold Q |

### Input design issues to preserve for later review

- Map/inventory multiplexing through Touchpad + R1/L1 / Tab + A/D/arrows — **DESIGN REVIEW PENDING**.
- Weapon 1/Weapon 2 vs two-hand capacity — **DESIGN DECISION PENDING**.
- Separate interaction input is not documented — **DESIGN DECISION PENDING**.
- The portal action is documented but its gameplay prerequisites/effects are outside the current source material — **UNCERTAIN**.

No control mapping has been changed here.

## 21. Difficulty and save implications

### Difficulty 1 — source-described

Ordinary difficulty is available from the beginning. Saves exist.

### Difficulty 2 — source-described, but not final

The source says it will *probably* be a second difficulty. It has:

- one life;
- no saves because the Star Spirit is hit by a meteorite while preparing the resurrection element;
- an unlock tied to an unspecified ending.

Therefore the existence/details of the second difficulty are **UNCERTAIN / DESIGN DECISION PENDING**, despite the source describing its intended behavior.

## 22. Explicitly unresolved system list

The following should remain open rather than being silently resolved during implementation:

1. Player max HP and exact death threshold.
2. Player defense and damage mitigation formula.
3. Healing amount, charges and interruption rules.
4. Roll invulnerability, duration, cooldown and movement behavior.
5. Relationship between Weapon 1/Weapon 2 and hand capacity.
6. Whether any weapon may consume multiple hands.
7. Exact free-hand behavior.
8. Whether active items consume hand slots.
9. Passive-item slot ownership and stacking/replacement rules.
10. Universal vs per-weapon 10-second unequip timeout.
11. Slime health resource model and regeneration.
12. Whether slime can die / reach zero health.
13. Slime variant list, branch layout and exact slot counts.
14. Damage mitigation formula.
15. Exact projectile/hit rules where DOCX descriptions are incomplete.
16. `пельмешка` identity and damage-stage rules.
17. `пельмешка` explosion effects and push interaction.
18. Chestnut launcher final status and ammo storage rules.
19. Active/passive item activation boundaries beyond the current classification.
20. Exact progression gates and route requirements.
21. Reward/loot economy beyond the confirmed item/weapon/drop concepts.
22. Dedicated interaction input and its relation to contextual object states.
23. Second difficulty finalization and unlock condition.

## 23. Implementation boundary for the next agent

The next Godot-architecture agent may safely treat the following as design inputs:

- player movement and roll exist;
- two-hand base concept exists and can be upgraded;
- Weapon 1 / Weapon 2 inputs exist;
- active item exists;
- healing exists;
- active and passive item categories exist;
- slime variants and upgrade branches exist conceptually;
- metroidvania progression and backtracking exist;
- enemy combat uses HP / Defense / Damage concepts;
- the two documented rats and their source values exist as concrete gameplay references;
- Blood Staff, Slime Pistol and Chestnut have the documented source-level behavior above;
- the shooting-rat `пельмешка` is a distinct authored gameplay state with its own source-level values;
- world interactions include NPC/dialogue and authored door/window/pickup states.

The next agent must **not** infer:

- Godot node hierarchy;
- script/resource type names;
- autoloads;
- signals;
- save architecture;
- combat formulas;
- exact cooldowns;
- exact inventory architecture;
- unlisted weapons, enemies, slime variants or abilities.

## 24. Source boundary

This specification intentionally stops where the source material stops. A later implementation should not convert `INFERRED`, `PROPOSED`, `UNCERTAIN` or `DESIGN DECISION PENDING` entries into hidden mechanics. New decisions should be recorded in `Game/DOCS/DECISION_LOG.md` before they become canonical gameplay rules.
