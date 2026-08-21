# Star Spirit — Extracted DOCX Facts

**Date:** 2026-08-21  
**Source:** user-provided transcription of all seven DOCX documents in the documented order  
**Status:** SOURCE EXTRACTION RECORDED / FINAL DESIGN STATUS PENDING

> The contents below are recorded as source facts from the seven DOCX files. They are not automatically canonical gameplay values. Numeric values and concrete mechanics are marked `DOCX-SOURCE VALUE` unless independently confirmed elsewhere.

## 1. Крыса(Крутящаяся)

**Classification:** asset existence = CROSS-SOURCE CONFIRMED; parameters/mechanics = DOCX-ONLY.

### Показатели

- Health: **20** — `DOCX-SOURCE VALUE`
- Defense: **0** — `DOCX-SOURCE VALUE`
- Contact damage: **3** — `DOCX-SOURCE VALUE`
- Contact damage is applied only while the mob is moving — `DOCX-SOURCE VALUE`

### Attack

- Spins for **5 seconds** while moving toward the player — `DOCX-SOURCE VALUE`
- On hit, deals **5 damage/second** — `DOCX-SOURCE VALUE`

### Final design status

**PENDING.** No automatic gameplay implementation or balancing applied.

---

## 2. Крыса(Стреляющая)

**Classification:** asset existence = CROSS-SOURCE CONFIRMED; parameters/mechanics = DOCX-ONLY.

### Показатели

- Health: **30** — `DOCX-SOURCE VALUE`
- Defense: **3** — `DOCX-SOURCE VALUE`
- Contact damage: **3** — `DOCX-SOURCE VALUE`
- Contact damage is applied only while the mob is moving — `DOCX-SOURCE VALUE`

### Attack

- Stops moving and tracks the player — `DOCX-SOURCE VALUE`
- At some point stops spinning, opens its mouth and fires — `DOCX-SOURCE VALUE`
- Shot damage: **15 per shot** — `DOCX-SOURCE VALUE`
- After firing, closes its mouth — `DOCX-SOURCE VALUE`

### Death / post-death state

- Compresses its tail and becomes a "пельмешка" state — `DOCX-SOURCE VALUE`
- In that state: **400 health**, **0 defense** — `DOCX-SOURCE VALUE`
- Has its own hitbox and behaves as a wall that can be pushed by walking into it — `DOCX-SOURCE VALUE`
- Has several damage states — `DOCX-SOURCE VALUE`
- Explodes after reaching maximum damage — `DOCX-SOURCE VALUE`
- The source says it will probably be possible for some enemy to throw it while in the "пельмешка" state — **UNCERTAIN / speculative wording in source**

### Final design status

**PENDING.** The speculative enemy-throw interaction is not treated as confirmed.

---

## 3. Базовый крестьянский дом 1 — Описания действиЙ

**Classification:** building existence and door/window interaction assets = CROSS-SOURCE CONFIRMED; exact interaction text = DOCX-ONLY.

### Door interaction

Text presented by the source:

> "Кто бы мог подумать,что дверь чужого дома в чужом города окажется закрытой"

Recorded as a source dialogue/interaction line. **DOCX-ONLY.**

### Window interaction

Text presented by the source:

> "О боже…. Там столько ПИВА…"

Recorded as a source dialogue/interaction line. **DOCX-ONLY.**

### Final design status

**PENDING.** The lines are source material; they do not by themselves establish final dialogue canon or exact gameplay consequences of interacting with the door/window.

---

## 4. Кровавый посох

**Classification:** weapon existence = CROSS-SOURCE CONFIRMED; attack rules/values = DOCX-ONLY.

### Attack

- Each attack creates **3 blood spikes** arranged as a wedge — `DOCX-SOURCE VALUE`
- All three spikes are created simultaneously — `DOCX-SOURCE VALUE`
- The wedge travels toward enemies — `DOCX-SOURCE VALUE`
- On hit, a projectile remains attached to the enemy for **2 seconds**, then disappears — `DOCX-SOURCE VALUE`
- Each spike deals **5 damage** — `DOCX-SOURCE VALUE`
- If all three spikes hit the same enemy simultaneously, that enemy's defense is reduced by **5 for 6 seconds** — `DOCX-SOURCE VALUE`

### Final design status

**PENDING.** The 3-spike, damage and defense-debuff values are not promoted to final balance.

---

## 5. Оружия/Новый документ.docx — generic weapon behavior

**Classification:** DOCX-ONLY until independently confirmed.

- On the **first weapon attack-button press**, a draw/equip animation is activated — `DOCX-SOURCE VALUE`
- On subsequent attacks, the weapon attacks normally — `DOCX-SOURCE VALUE`
- If the weapon is unused for **10 seconds**, a disappearance/unequip animation is activated — `DOCX-SOURCE VALUE`

### Final design status

**PENDING.** This is recorded as behavior described by the root `Оружия` DOCX. It has not been generalized to every weapon without further validation.

---

## 6. Слаймовый пистолет

**Classification:** weapon existence + slime relation = CROSS-SOURCE CONFIRMED; exact numeric rules and status behavior = DOCX-ONLY.

- Occupies **one hand** — `DOCX-SOURCE VALUE`
- Is a **slime weapon** — `DOCX-SOURCE VALUE`; consistent with the concept that slime can transform into weapons
- Each shot fires a projectile/ammunition dealing **15 damage** — `DOCX-SOURCE VALUE`
- Each shot consumes **5 slime health** — `DOCX-SOURCE VALUE`
- Does **not** apply status effects to enemies — `DOCX-SOURCE VALUE`

### Description

> "Пистолет из слайма,тут нечего сказать."

Recorded as source text. **DOCX-ONLY.**

### Final design status

**PENDING.** Do not infer that the 5 slime-health cost is the universal cost model for other slime weapons.

---

## 7. Каштан

**Classification:** item existence = CROSS-SOURCE CONFIRMED; ammunition role = DOCX-ONLY.

- Chestnut is the **main ammunition for the chestnut launcher** — `DOCX-SOURCE VALUE`

### Description

> "Самый обычный каштан. Будь это другой сорт,его можно было бы приготовить и съесть. Жаль,что судьба сложилась иначе."

Recorded as source text. **DOCX-ONLY.**

### Final design status

**PENDING.** The source confirms an ammunition role in the DOCX transcription, but does not by itself establish the launcher as an implemented/final weapon.

---

# Cross-source review

## CROSS-SOURCE CONFIRMED

- The rotating rat and shooting rat are established asset clusters in `Враги/Королевство/`; the new DOCX transcription now supplies their missing gameplay descriptions and parameters. Existing documentation had explicitly withheld HP, damage, AI and attack parameters before extraction.
- The basic peasant house exists in the Kingdom environment assets and already has door/window interaction variants. The DOCX adds the actual interaction lines but does not establish a broader house-state system.
- The Blood Staff exists as an archived weapon asset with attack/projectile animations. The DOCX now supplies attack behavior and numeric values; those values remain pending.
- The Slime Pistol exists as an archived weapon asset. `CONSEPT.txt` independently confirms that slime on the hero can transform into a weapon and that slime weapons can be held in a hand; the DOCX identifies this particular weapon as slime-based and one-handed. This confirms the category/relationship, not the numeric balance.
- Chestnut exists as a collectible item and has separate pickability visual states. The DOCX adds an ammunition role for a chestnut launcher, which is new source information.

## DOCX-ONLY

- Rotating rat: 20 HP, 0 defense, 3 moving contact damage, 5-second spin, 5 damage/second while hitting.
- Shooting rat: 30 HP, 3 defense, 3 moving contact damage, tracking/shot sequence, 15 shot damage.
- Shooting rat post-death "пельмешка" state: 400 HP, 0 defense, pushable wall behavior, damage stages, explosion at maximum damage.
- Shooting rat being thrown by another enemy: explicitly speculative in the source and therefore `UNCERTAIN`.
- Blood Staff: 3 simultaneous wedge spikes, 5 damage per spike, 2-second persistence on hit, defense -5 for 6 seconds when all three hit the same enemy.
- Generic weapon root behavior: draw on first attack, normal attack on later presses, disappearance animation after 10 seconds unused.
- Slime Pistol: 15 damage per shot, 5 slime-health cost, no status effects, one-hand slot, description text.
- Chestnut: main ammunition role for the chestnut launcher and description text.
- Peasant house: exact door/window interaction quotations.

## CONFLICTS

No direct numerical conflict with the reviewed `GAME_BIBLE.md`, `WORLD.md`, `DECISION_LOG.md`, or `CONSEPT.txt` was found because those sources previously did not establish these values.

Important non-conflicts:

- `CONSEPT.txt` says the player has two hands, and upgrades can affect the count. The Slime Pistol occupying one hand is compatible with that concept.
- `CONSEPT.txt` says slime can sometimes transform into a weapon and is not displayed on the body while a slime weapon is in hand. The Slime Pistol being slime-based is compatible with this concept.
- Existing house assets already establish door/window interaction variants, so the DOCX interaction lines add text rather than contradicting the asset structure.

## Governance

No values here are treated as final balance. Every numeric gameplay value is explicitly a `DOCX-SOURCE VALUE` with `FINAL DESIGN STATUS: PENDING` unless separately approved by a future design decision.

No `DECISION_LOG.md` item is closed automatically by this extraction.