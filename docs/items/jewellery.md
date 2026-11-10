# 반지·목걸이 (Jewellery)

> 기준: DCSS 0.34.1 · [아이템 목록으로](index.md)

반지(ring)와 목걸이(amulet)의 종류별 효과와 수치, 착용 슬롯, 생성 규칙을 정리한다. 랜덤 아티팩트 속성은 [아티팩트 속성](artefact-properties.md), 언랜드 장신구는 [언랜드 장신구](unrands-jewellery.md) 참고.

---

## 1. 슬롯

| 슬롯 | 기본 개수 | 바뀌는 경우 |
|---|---|---|
| 반지 | 2 | **Octopode 8개.** 손 하나가 없는 돌연변이(`MUT_MISSING_HAND`) −1. 언랜드 macabre finger necklace +1, Vainglory +2 |
| 목걸이 | 1 | 언랜드 Justicar's Regalia를 착용하면 2 |

- **Coglin은 반지·목걸이를 낄 수 없다**(`MUT_NO_JEWELLERY`).
- 변신 형태에 따라 반지·목걸이 슬롯이 막힐 수 있다(탈리스만 문서에서 다룰 예정).
- 반지·목걸이는 그 칸에 올라서면 자동 감정된다. → [감정](index.md#감정-identification)

## 2. 수치(+N)가 있는 반지
**바닥에서 생성되는 일반 반지의 수치는 무작위가 아니라 종류마다 고정이다.**

| 반지 | 고정 수치 | 효과 |
|---|---|---|
| ring of strength | +6 | Str +6 |
| ring of dexterity | +6 | Dex +6 |
| ring of intelligence | +6 | Int +6 |
| ring of protection | +4 | AC +4 |
| ring of slaying | +4 | Slaying(근접·원거리 명중과 데미지) +4 |
| ring of evasion | +5 | EV +5 |

- ring of protection의 AC는 **Armour 스킬 배율을 받지 않는** 고정값이다. → [AC 계산](armour.md#21-계산)
- ring of evasion의 EV도 고정 가산이다. → [EV 계산](armour.md#31-계산)
- Slaying이 명중·데미지에 더해지는 방식은 [무기 문서](weapons.md#31-계산-순서) 참고. Slaying은 근접·원거리 공격 모두에 적용된다.
- Acquirement(획득)로 나온 반지도 같은 고정 수치를 받는다.
- 수치가 다른 반지는 언랜드나 볼트 지정 아이템(`.des`) 등에서만 나온다.

## 3. 반지 목록

| 반지 | 효과 | 2개 착용 시 중첩 |
|---|---|---|
| strength / dexterity / intelligence | 능력치 +6 | 중첩 (+12) |
| protection | AC +4 | 중첩 |
| slaying | Slaying +4 | 중첩 |
| evasion | EV +5 | 중첩 |
| protection from fire | rF +1 | 중첩 (rF++) |
| protection from cold | rC +1 | 중첩 (rC++) |
| positive energy | rN +1 | 중첩 |
| willpower | Willpower(의지력) +1단계(내부값 +40) | 중첩 |
| wizardry | 마법 실패율 감소 (아래) | 중첩 |
| magical power | 최대 MP +9 | 중첩 |
| poison resistance | rPois | 중첩 안 됨 |
| resist corrosion | rCorr | 중첩 안 됨 |
| see invisible | SInv(투명 감지) | 중첩 안 됨 |
| flight | 비행 | 중첩 안 됨 |

"중첩"은 같은 반지 2개를 꼈을 때 효과가 더 커지는지 여부다(`ring_has_stackable_effect`).

### 3.1 ring of wizardry
마법 실패율을 계산한 뒤 마지막에 **실패율 × 6 / (7 + n)** 을 곱한다. n은 Wizardry 효과의 개수.

| Wizardry 개수 | 실패율 배율 |
|---|---|
| 1 | ×0.75 |
| 2 | ×0.667 |
| 3 | ×0.6 |

- Wizardry 개수에는 ring of wizardry, 아티팩트 Wiz 속성, `MUT_BIG_BRAIN` 3단계가 포함된다.
- Vehumet의 실패율 감소(×2/3), 일부 방어구 에고·변신 형태의 감소와 곱으로 함께 적용된다.

### 3.2 ring of magical power
- 최대 MP +9. 스킬·레벨·종족 보정을 모두 계산한 **뒤에 더해진다.**
- Antimagic 브랜드 무기를 들면 최대 MP 전체(반지의 +9 포함)가 1/3이 된다.
- **반지를 빼면 현재 MP에서 9를 소모한다.**
- Djinni(`MUT_HP_CASTING`, MP 대신 HP로 시전)에게는 효과가 없다.

### 3.3 그 밖의 반지
- **flight**: 끼고 있는 동안 계속 비행. 빼면 착지한다.
- **see invisible**: 투명한 몬스터를 볼 수 있다. 빼는 순간 보이지 않게 된 몬스터는 위치를 모르는 상태로 표시된다.
- 능력치 반지를 끼고 빼면 그 즉시 능력치가 바뀐다.

### 3.4 삭제된 반지
아래 반지는 세이브 호환용으로 코드에만 남아 있고 **0.34.1에서는 생성되지 않는다**(`removed_items`).

- ring of **stealth**, regeneration, sustain attributes, teleportation, teleport control, attention, fire, ice

ring of stealth는 없어졌지만, 아티팩트의 Stlth 속성은 여전히 나온다. → [아티팩트 속성](artefact-properties.md)

---

## 4. 목걸이 목록

| 목걸이 | 효과 요약 |
|---|---|
| [regeneration](#41-regeneration--magic-regeneration) | HP 재생 증가 (동조 필요) |
| [magic regeneration](#41-regeneration--magic-regeneration) | MP 재생 증가 (동조 필요) |
| [guardian spirit](#42-guardian-spirit) | 받는 데미지를 HP와 MP로 나눠 받음 |
| [faith](#43-faith) | Piety 획득·손실 ×1.25 |
| [reflection](#44-reflection) | SH +5, 막은 투사체를 반사 |
| [the acrobat](#45-the-acrobat) | 이동·대기 직후 EV +15 |
| [wildshape](#46-wildshape) | Shapeshifting 스킬 +5 |
| [chemistry](#47-chemistry) | Alchemy 마법 강화 +1, 포션을 마시면 MP 회복 (동조 필요) |
| [dissipation](#48-dissipation) | 나쁜 상태이상과 마법 오염이 2배 빨리 사라짐 |
| nothing | 효과 없음. 언랜드 목걸이의 기반으로만 쓰이고 그 자체로는 생성되지 않는다 |

목걸이에는 +N 수치가 없다.

### 4.1 regeneration / magic regeneration
**동조(attunement)**: 이 목걸이들은 착용한 상태에서 **HP(regeneration) 또는 MP(magic regeneration)가 가득 찬 적이 있어야** 효과가 켜진다.
- 가득 찬 상태에서 끼면 바로 동조된다. 아니면 다음에 가득 찰 때 동조된다.
- HP 재생과 MP 재생을 둘 다 주는 아티팩트는 HP와 MP가 **둘 다** 가득 차야 동조된다.
- 한 번 동조되면 뺄 때까지 유지된다. 다시 끼면 처음부터 다시 동조해야 한다.

**재생량** (턴(10 aut)당, 100이 HP·MP 1):

| | 기본 | 목걸이 효과 |
|---|---|---|
| HP 재생 | `20 + 최대HP/6` | **+80** (regeneration) |
| MP 재생 | `7 + 최대MP/2` | **+40** (magic regeneration) |

| 예시 | 목걸이 없음 | 목걸이 착용 |
|---|---|---|
| 최대 HP 60 | 턴당 0.30 HP | 턴당 1.10 HP |
| 최대 HP 150 | 턴당 0.45 HP | 턴당 1.25 HP |
| 최대 MP 20 | 턴당 0.17 MP | 턴당 0.57 MP |
| 최대 MP 40 | 턴당 0.27 MP | 턴당 0.67 MP |

- HP 재생 +80은 troll leather armour, 아티팩트 Regen 속성, `MUT_REGENERATION` 1단계와 같은 크기다.
- MP 재생이 없는 캐릭터(Djinni 등)가 magic regeneration을 끼면 "cold and inert" 메시지와 함께 동조되지 않는다.
- 상태이상 Sickness나 HP 재생이 막힌 상태에서는 regeneration도 효과가 없다.
- magic regeneration 목걸이에는 랜덤 아티팩트일 때 \*Silence 속성이 붙지 않는다.

### 4.2 guardian spirit
데미지를 받을 때 **데미지 × 현재MP / (현재HP + 현재MP)** 만큼을 MP로 대신 받는다.
- 예: HP 60, MP 20일 때 데미지 20 → MP 5, HP 15.
- 나눠 받은 결과로 죽게 되는 경우, MP가 남아 있으면 HP가 1 남도록 MP를 더 쓴다.
- **Poison 데미지와 Flay 데미지는 나눠 받지 않는다.**
- Spirit Shield 방어구 에고, `MUT_MANA_SHIELD`와 같은 효과다(중복해도 비율은 같다).
- MP가 0이면 효과가 없다. Djinni에게는 의미가 없다.

### 4.3 faith
- **Piety 획득량 ×1.25** (`piety + piety/4`, 1/4 부분은 확률적 반올림).
- **신앙 위반에 의한 Piety 손실과 Penance(징벌)도 ×1.25.**
- Ru: 다음 희생이 제시될 때까지의 대기 시간 ×2/3.
- Xom: Xom이 느끼는 흥미(interestingness)와 Piety 변동 폭이 같은 배율로 커지고, Xom이 행동할 확률이 2/6 → 3/6.
- **빼면 현재 Piety의 1/3을 잃는다.** Ru 신자는 대신 희생 제시가 늦어진다.
- 아래 경우에는 효과가 없거나 빼도 페널티가 없다.

| 상황 | 효과 | 뺄 때 페널티 |
|---|---|---|
| Gozag, Ashenzari, Ignis 신자 | 신이 무시한다는 메시지가 나옴(\*) | 없음 |
| Ru 신자, Piety ★5 이상 | 신이 무시한다는 메시지가 나옴(\*) | 없음 |
| Xom, Uskayaw 신자 | 있음 | 없음 |
| 무신앙 | 의미 없음 | 없음 |
| Mummy (선천적 `MUT_FAITH`) | 이미 같은 효과를 가짐 | 없음 |
| Demigod (`MUT_FORLORN`, 신앙 불가) | 없음 | 없음 |

(\*) 메시지와 해제 페널티만 이렇게 처리된다. ×1.25 배율 자체는 `you.faith()`가 신을 구분하지 않아서 계산상 그대로 적용되지만, 이 신들은 Piety를 일반적인 방식으로 얻지 않으므로 실제로 차이가 생기는지는 (미확인).

### 4.4 reflection
- **표시 SH +5**(내부값 10). Shields 스킬과 Dex의 영향을 받지 않는 고정값이며, 방패를 들었으면 방패 SH에 더해진다. → [SH와 막기](armour.md#5-sh와-막기-shields--blocking)
- 방패 없이 이 목걸이만 있어도 SH가 생겨 막기 판정을 한다(방패가 없으면 턴당 막기 1회).
- **막아낸 투사체·볼트를 쏜 쪽으로 반사한다.** 남은 사거리가 없는 볼트는 반사되지 않는다.
- Reflection 방패 에고와 같은 반사 효과다. → [방어구 에고](brands-egos.md#저항방어)
- 몬스터가 끼면 몬스터의 SH가 같은 만큼 오르고 반사도 한다.

### 4.5 the acrobat
- **이동하거나 대기한 직후 EV +15.** 지속 시간은 그 행동에 걸린 시간 + 1 aut라서, 다음 행동을 하기 전까지(=몬스터가 행동하는 동안) 유지된다.
- 공격, 마법 시전, 아이템 사용, 계단 이동 등 다른 행동 뒤에는 보너스가 없다. 단, 유지형 마법(channelled spell)을 대기로 계속하는 경우는 대기로 취급된다.
- **그물 등에 걸렸거나(caught) 조임(constricted) 당한 상태에서는 보너스가 없다.**
- Tengu는 선천적으로 같은 효과(`MUT_ACROBATIC`)를 가지고 있어 중첩되지 않는다.
- Bane of Stumbling은 같은 조건에서 EV −25를 준다(같은 타이머를 쓴다).

### 4.6 wildshape
- **Shapeshifting 스킬 +5레벨**(최대 27). 탈리스만 변신 형태의 수치는 Shapeshifting 스킬에 따라 오르므로 변신 형태 전반이 강해진다(탈리스만 문서 예정).
- 끼고 빼면 최대 HP·MP가 다시 계산된다(형태의 HP 보너스 등이 스킬을 따라 바뀌기 때문).
- 스킬 화면의 목표치 계산에도 +5가 반영된다.
- **Chaotic 아이템**이다. 끼고 있으면 매 턴 Chaos 행위로 처리되어 **Zin**이 싫어한다.

### 4.7 chemistry
- **Alchemy 학파 마법 강화(enhancer) +1단계** (Spell power ×1.5). 지팡이 staff of alchemy와 같은 크기다. → [마법 강화](brands-egos.md#공통-마법-강화enhancer)
- **포션을 마시면 MP 5~9 회복.** MP가 가득 찬 상태에서는 회복하지 않는다. 마신 포션의 효과가 실제로 발동했을 때만 회복한다.
  - Alistair's Walking Alembic이 주는 포션에도 적용된다. → [Alchemy](../spells/alchemy.md#alistairs-walking-alembic)
- **MP 회복 효과는 동조가 필요하다**(MP가 가득 찬 상태가 된 적이 있어야 함). 마법 강화 효과는 동조와 상관없이 바로 적용된다.
- MP 재생 속도 자체는 올리지 않는다.

### 4.8 dissipation
- **"나쁜(negative) + 해제 가능(dispellable)"으로 분류된 상태이상의 지속 시간이 2배 빨리 줄어든다.** 33종이 해당한다(Slow, Sticky Flame은 별도 처리 코드에서 같은 배율을 적용). 주요 예:
  - Confusion, Paralysis, Sleep, Petrifying·Petrified, Slow, Sticky Flame, Corrosion, Weak, Vertigo, Blind, Afraid, Mesmerised, Sickness, Lowered Willpower, Fire/Poison Vulnerability, No Cast(주문 봉인), Sap Magic, Diminished Spells, Vitrified, Frozen, Corona, Attractive, Dimension Anchor, Blinkitis, Sign of Ruin, Slimifying
- **Poison(중독)은 해당하지 않는다**(해제 가능 상태로 분류되지 않음).
- **마법 오염(contamination)이 줄어드는 속도도 2배.** 오염이 쌓이는 속도는 그대로다.

---

## 5. 랜덤 아티팩트 장신구
- 반지·목걸이도 randart가 될 수 있다. 속성을 정하는 방식은 [아티팩트 속성](artefact-properties.md#속성-개수-정하기)과 같다.
- **기본 효과는 그대로 유지된다.** 예: randart ring of strength는 Str +6에 무작위 속성이 더해진다. 수치(+N)도 일반 반지와 같은 고정값이다.
- 기본 효과와 **반대 방향의 속성은 붙지 않는다.** 예: ring of protection from fire에 rF−, ring of strength에 Str−는 나오지 않는다. **ring of wizardry에는 Int−가 붙지 않는다.**
- 장신구 종류에 따라 붙지 않는 속성:
  - **반지**에는 Regen, +Inv, Harm, Rampage, −Tele, \*Silence, ^Fragile이 붙지 않는다(쉽게 바꿔 낄 수 있는 장비라서).
  - **목걸이**에는 위 속성이 붙을 수 있다(Silence는 magic regeneration 목걸이 제외).

## 6. 생성 (간략)
- **바닥 무작위 생성**: 무작위 아이템 종류 중 장신구의 가중치는 45 / 1661(약 2.7%).
  - 장신구 안에서 **반지 3/4, 목걸이 1/4.** 각 안에서는 생성되는 종류끼리 균등하다(반지 16종, 목걸이 9종).
  - 언랜드 시도: 아이템 레벨이 0보다 크면 `1/20 × (101 + 3L)/2000` 확률로 언랜드 장신구를 시도한다.
  - randart: 아이템 레벨이 0보다 크면 `(101 + 3L)/4000`. → [아이템 생성](index.md#아이템-생성-간략)
- **Acquirement(획득)**: 장신구가 나오면 언랜드가 아닌 경우 1/2 확률로 randart가 된다. Coglin에게는 장신구가 나오지 않는다.
- **몬스터 장비**(`mon-gear.cc`, 대표 예):
  - Erica: scimitar를 받으면 무작위 반지 1개.
  - Fannar: quarterstaff를 받으면 ring of protection from cold.
  - Josephina: randart ring of protection from cold.
  - Cassandra: 1/2 확률로 무작위 목걸이, 그중 1/4은 Bane 속성이 붙은 randart.
  - Beogh의 Apostle(사도): 힘에 비례한 확률로 rF·rPois·rC·EV·rN·AC 반지 중 하나.

## 7. 몬스터의 장신구 착용
- 몬스터는 장신구 슬롯이 **1개**다(반지와 목걸이 공용).
- 몬스터에게 효과가 있는 것: protection(AC), evasion(EV), slaying, 저항(rF·rC·rPois·rN·rCorr), willpower, see invisible, flight, reflection(SH +5와 반사). 그 밖의 장신구는 몬스터에게 효과가 없다.
- 몬스터는 위 효과의 합으로 가치를 매겨 더 좋은 장신구를 줍는다. 이미 가진 저항(예: 독 면역 몬스터의 rPois)은 가치에서 빠진다.

> 출처: item-prop.cc, item-prop-enum.h, makeitem.cc, makeitem.h, artefact.cc, player-equip.cc, player.cc, player-reacts.cc, player-stats.cc, spl-cast.cc, religion.cc, god-abil.cc, xom.cc, ouch.cc, actor.cc, beam.cc, potion.cc, spl-summoning.cc, skills.cc, god-item.cc, status.cc, duration-data.h, acquire.cc, mon-gear.cc, monster.cc, describe.cc (0.34.1)
