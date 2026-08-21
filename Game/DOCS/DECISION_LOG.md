# Star Spirit — журнал нерешённых решений

## 1. Godot version

**Категория:** technical  
**Статус:** TECHNICAL DECISION PENDING  
**Классификация:** CONFLICTING

- Фактический `Game/project.godot`: feature `4.7`.
- Целевая версия проекта: Godot 4.8.

**Влияние:** необходимо определить базовую версию до начала технической реализации, но исправлять `project.godot` в рамках аудита не следует.

## 2. Star Spirit и объект №1817

**Категория:** narrative  
**Статус:** решение не принято  
**Классификация:** UNCERTAIN

Есть Star Spirit, связанный с героем и сохранениями, и есть объект №1817 — разумная слизь из отчётов Лямбды. Источники не дают прямого утверждения, что это одно и то же существо.

**Рекомендация:** REQUIRED для narrative specification — определить связь до детализации сюжета и игровых систем, которые от неё зависят.

## 3. Главный герой

**Категория:** narrative  
**Статус:** решение не принято  
**Классификация:** UNCERTAIN

Подтверждено создание героя в Лаборатории и предательство братом, но имя, личность, точное происхождение и история до начала игры не раскрыты.

**Рекомендация:** REQUIRED — разработать минимальный канонический профиль героя.

## 4. Лаборатория и Лямбда

**Категория:** narrative/world  
**Статус:** решение не принято  
**Классификация:** UNCERTAIN

Лаборатория является местом создания героя и целью его противостояния. Корпус Лямбда проводит эксперименты над объектом №1817. Не установлено, являются ли Лямбда и Лаборатория одной организацией/объектом.

**Рекомендация:** REQUIRED — установить организационную и географическую связь.

## 5. Система слизи

**Категория:** gameplay/progression  
**Статус:** решение не принято  
**Классификация:** CONFIRMED concept, UNCERTAIN rules

Подтверждены разные варианты слизи, отдельные ветки развития и различное число слотов. Точные правила отсутствуют.

**Рекомендация:** STRONGLY RECOMMENDED — следующий gameplay-агент должен определить границы системы, не переходя сразу к технической архитектуре.

## 6. Сложности

**Категория:** gameplay  
**Статус:** решение не принято  
**Классификация:** UNCERTAIN

Источник говорит, что «наиболее вероятно» будет две сложности. Вторая имеет одну жизнь и отсутствие сохранений, а также открывается после неуточнённой концовки.

**Рекомендация:** OPTIONAL на текущем этапе, если это не блокирует ближайшую разработку.

## 7. Мир и карта

**Категория:** world/gameplay  
**Статус:** решение не принято  
**Классификация:** UNCERTAIN

Большой мир, backtracking и metroidvania-прогрессия подтверждены, но конкретная карта и связи регионов не описаны.

**Рекомендация:** STRONGLY RECOMMENDED — отдельная world specification после фиксации основных сюжетных регионов.

## 8. DOCX-источники

**Категория:** documentation  
**Статус:** решение не принято  
**Классификация:** UNCERTAIN

В архиве присутствуют DOCX, но их текст не удалось надёжно извлечь доступным интерфейсом. Нельзя использовать их неподтверждённое содержимое как канон.

**Рекомендация:** REQUIRED перед финализацией asset bible — провести отдельный локальный бинарный анализ DOCX и сверить результаты с TXT и изображениями.

## 9. Правило для будущих агентов

### CONFIRMED

Ни один из перечисленных вопросов не должен закрываться молча через реализацию. Если решение меняет gameplay, narrative или структуру проекта, оно должно появиться как отдельное решение с понятным статусом.

### PROPOSED

Следующие агенты должны ссылаться на этот журнал при создании подробных спецификаций и переводить вопрос в `CONFIRMED` только после явного подтверждения источником или утверждённым решением.

## 10. Narrative specification: герой и №1817

**Категория:** narrative  
**Статус:** решение не принято  
**Классификация:** UNCERTAIN

После повторной сверки `CONSEPT.txt` и `STORY.txt` подтверждено только следующее: герой создан в Лаборатории и связан со слизью; №1817 является разумной слизью, которая связывается с живыми носителями и исчезает через портал. Прямого утверждения, что это один объект, нет.

**Нельзя:** считать героя №1817, носителем №1817 или считать слизь героя самим №1817 без отдельного авторского решения.

## 11. Narrative specification: Star Spirit

**Категория:** narrative  
**Статус:** решение не принято  
**Классификация:** UNCERTAIN

`SOME INFO.txt` прямо вводит Звёздного Духа как отдельного действующего персонажа, который помогает создавать сохранения. `STORY.txt` не называет №1817 Звёздным Духом.

**Нельзя:** объединять Star Spirit и №1817 только на основании темы слизи, способностей или сохранений.

## 12. Narrative/world: Лаборатория и Лямбда

**Категория:** narrative/world  
**Статус:** решение не принято  
**Классификация:** UNCERTAIN

`CONSEPT.txt` использует Лабораторию как место создания героя и цель уничтожения. `STORY.txt` использует исследовательский корпус Лямбда как субъект отчётов об №1817. Источник не устанавливает, что это одна организация, один объект или географически одно место.

**Нельзя:** автоматически считать Лабораторию Лямбдой или утверждать, что эксперименты №1817 проходили именно там.

## 13. World: Королевство и названия локаций

**Категория:** world  
**Статус:** решение не принято  
**Классификация:** UNCERTAIN

Архив содержит широкую категорию `Королевство` для врагов, NPC, окружения, подбираемых предметов и фонов. Также существуют материалы с названиями `Магический лес` и `Пиратская бухта`.

Это подтверждает существование контентных/визуальных названий, но не подтверждает полную географическую карту или связи между ними.

**Нельзя:** строить карту `Королевство → Магический лес → Пиратская бухта → Лаборатория` без отдельного решения.

## 14. World: progression gates

**Категория:** world/gameplay  
**Статус:** структура подтверждена, конкретика не принята  
**Классификация:** CONFIRMED concept, UNCERTAIN implementation/content

Подтверждены постепенное открытие мира, backtracking и ранний доступ к некоторым областям при наличии нужных предметов. Конкретные способности, предметы и сюжетные события, открывающие конкретные области, не названы.

**Нельзя:** назначать конкретные способности или предметы как канонические progression gates без источника.

## 15. Gameplay: slime resource model

**Категория:** gameplay/progression  
**Статус:** DESIGN DECISION PENDING  
**Классификация:** DOCX-SOURCE VALUE + UNCERTAIN rules

`Слаймовый пистолет` расходует **5 slime health per shot** — источник DOCX-транскрипции.

Не установлено:

- является ли slime health отдельным ресурсом игрока/слизи;
- каков максимум;
- восстанавливается ли ресурс;
- может ли ресурс достигать нуля и что это означает;
- общий ли ресурс у всех slime weapons;
- зависят ли затраты от оружия или slime variant.

**Нельзя:** превращать значение 5 в универсальную стоимость для других slime weapons без отдельного решения.

## 16. Gameplay: hand/equipment model

**Категория:** gameplay/equipment  
**Статус:** DESIGN DECISION PENDING  
**Классификация:** CONFIRMED concept + UNCERTAIN mapping

Подтверждены 2 руки и возможность изменения их количества через upgrades. Подтверждено, что Slime Pistol занимает 1 руку. Управление также содержит Weapon 1 и Weapon 2.

Не установлено:

- являются ли Weapon 1/Weapon 2 физическими hand slots;
- может ли оружие занимать более одной руки;
- могут ли active items занимать руки;
- что делает свободная рука.

**Нельзя:** вводить dual-wield или two-handed rules как канон без решения.

## 17. Gameplay: weapon lifecycle universality

**Категория:** gameplay/equipment  
**Статус:** DESIGN DECISION PENDING  
**Классификация:** DOCX TRANSCRIPTION

Корневой DOCX категории оружия описывает: первое нажатие атаки → draw/equip, следующие нажатия → атака, 10 секунд без использования → unequip/disappear animation.

Не установлено, является ли это обязательным контрактом каждого будущего оружия или только описанием существующего набора.

**Нельзя:** считать 10 секунд универсальным правилом без отдельного решения.

## 18. Gameplay: enemy damage formula

**Категория:** gameplay/combat  
**Статус:** DESIGN DECISION PENDING  
**Классификация:** CONFIRMED stats, formula absent

HP, Defense and concrete damage values существуют в DOCX-source material для двух крыс. Источник не задаёт формулу обработки Defense.

Например, `Damage = Attack - Defense` может существовать только как **PROPOSED**, а не как факт.

**Нельзя:** реализовывать mitigation formula как каноническую без отдельного решения.

## 19. Gameplay: shooting-rat `пельмешка` identity

**Категория:** gameplay/combat/world interaction  
**Статус:** DESIGN DECISION PENDING  
**Классификация:** DOCX-SOURCE VALUE + UNCERTAIN identity

Подтвержден переход стреляющей крысы в `пельмешка`, её отдельные 400 HP / 0 Defense, собственный hitbox, pushability, damage states и explosion at maximum damage.

Не установлено:

- является ли это тем же enemy identity в новом state или отдельным объектом;
- полный damage-stage sequence;
- explosion consequences;
- whether it can be thrown by another enemy. The last item is explicitly speculative in the source.

## 20. Gameplay: chestnut launcher status

**Категория:** gameplay/items  
**Статус:** DESIGN DECISION PENDING  
**Классификация:** DOCX-SOURCE VALUE

Подтверждено только то, что Chestnut is the main ammunition for a chestnut launcher in the DOCX transcription.

Не установлено:

- существует ли launcher как финальный/implemented weapon;
- где он находится в progression;
- hand requirement;
- fire rules;
- stack size / ammo storage;
- whether chestnut is otherwise usable.

**Нельзя:** превращать launcher role в полноценную weapon specification без отдельного источника/решения.

## 21. Gameplay: active/passive item boundary

**Категория:** gameplay/build  
**Статус:** DESIGN DECISION PENDING  
**Классификация:** CONFIRMED categories, rules absent

Active and passive items are confirmed categories. A safe documentation distinction is:

- ACTIVE — explicitly triggered by the player;
- PASSIVE — changes state/behavior without a separate activation.

This distinction is an `INFERRED` organizational boundary, not proof of a specific slot, cooldown, stacking or resource system.

## 22. Gameplay: interaction input

**Категория:** gameplay/world interaction  
**Статус:** DESIGN DECISION PENDING  
**Классификация:** CONFIRMED authored interactions, input absent

Door/window interaction assets and NPC dialogue are confirmed. `CONTROLS.txt` does not define a dedicated interaction input.

**Нельзя:** silently assign an unused button or repurpose an existing control in the gameplay specification.

## 23. Gameplay: player defense and damage model

**Категория:** gameplay/combat  
**Статус:** DESIGN DECISION PENDING  
**Классификация:** UNCERTAIN

Enemy Defense is source-supported. Player Defense is not established. Player healing/death are established, but exact max HP, mitigation, hit invulnerability and knockback are not.

**Нельзя:** copy enemy Defense into the player model by symmetry.
