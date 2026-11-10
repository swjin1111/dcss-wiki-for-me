# 지팡이 (Magical Staves)

> 기준: DCSS 0.34.1 · [아이템 목록으로](index.md)

마법 지팡이(magical staff)는 **학파 하나의 마법을 강화**하고, 일부는 저항을 주며, 근접 무기로 휘두르면 **추가 데미지**를 줄 수 있다. 무기인 quarterstaff·lajatang은 [무기 문서](weapons.md#staves) 참고.

---

## 1. 종류

| 지팡이 | 마법 강화 | 저항 | 근접 추가 데미지 종류 | 데미지 배율 | AC 적용 |
|---|---|---|---|---|---|
| staff of fire | Fire | rF +1 | Fire | 63 | 전부 |
| staff of cold | Ice | rC +1 | Cold | 63 | 전부 |
| staff of air | Air | rElec | Electricity | 50 | **절반** |
| staff of earth | Earth | — | 순수 물리(저항 불가) | 63 | 전부 |
| staff of alchemy | Alchemy | rPois | Poison + 중독 | 63 | 전부 |
| staff of necromancy | Necromancy | rN +1 | Negative energy | 63 | 전부 (\*) |
| staff of conjuration | Conjurations | — | 순수 마법(저항 불가) | 50 | 전부 |

- 0.34.1에서 생성되는 지팡이는 위 **7종**이다. wizardry, power, energy, enchantment, summoning, channelling 지팡이는 세이브 호환용으로만 남아 있고 생성되지 않는다(`removed_items`).
- Hexes, Summoning, Translocations, Forgecraft 학파의 지팡이는 없다.
- 지팡이는 그 칸에 올라서면 자동 감정된다.
- (\*) **게임 내 설명과 다른 점**: staff of necromancy의 설명문은 추가 데미지가 "방어구를 무시한다(bypasses armour)"고 하지만, 코드(`item-prop.cc`의 `Staff_prop`)에는 `ac_type::normal`로 되어 있어 **대상의 AC가 그대로 적용된다**(0.34.1).

## 2. 마법 강화 (Enhancer)
- 지팡이를 **들고 있으면** 그 학파의 마법 강화 +1단계. 강화 1단계마다 **Spell power ×1.5**.
- 여러 학파에 속한 마법은 학파마다 강화를 따로 더한다. 예: Fire/Alchemy 마법은 staff of fire와 Fire 강화 방어구를 같이 쓰면 +2단계.
- 모든 출처를 합친 강화는 **최대 +3단계**(×3.375)까지, 약화는 −3단계까지 반영된다. 약화(−)는 1단계마다 ×1/2.
- **Attunement 방어구 에고**가 있으면 지팡이의 강화가 +2단계가 된다. → [방어구 에고](brands-egos.md#마법-강화)
- 그 밖의 강화 출처(방어구 에고, Archmagi, 아티팩트 속성 등)는 [마법 강화](brands-egos.md#공통-마법-강화enhancer) 참고. Alchemy는 amulet of chemistry도 같은 +1을 준다. → [반지·목걸이](jewellery.md#47-chemistry)

## 3. 저항
- 들고 있는 동안 위 표의 저항을 준다. rF·rC·rN은 다른 출처와 합산된다.
- 몬스터가 들어도 같은 저항을 얻는다.

---

## 4. 근접 무기로서의 지팡이
### 4.1 기본 수치
모든 마법 지팡이가 같은 무기 수치를 쓴다.

| 데미지 | 명중 | 딜레이 | 최소 딜레이 (필요 스킬) | 손 | 스킬 |
|---|---|---|---|---|---|
| 5 | +5 | 1.2 | 0.6 (12) | **한손** (몸집 Little 이상) | Staves |

- **인챈트(+N)가 없다.** 브랜드도 붙지 않는다(randart 지팡이에도 브랜드는 없다).
- 공격 공식은 일반 무기와 같다. → [무기 문서](weapons.md#2-명중)

### 4.2 추가 데미지
지팡이로 **명중했을 때**, 일정 확률로 지팡이 학파의 추가 데미지를 준다.

1. **발동 확률** = `(Evocations × 2 + 학파 스킬) / 30` (최대 100%)
2. **추가 데미지** = `0 ~ (학파 스킬 × 2 + Evocations) × 배율 / 80 − 1` 사이의 무작위 값
   - 배율은 [종류 표](#1-종류)의 63 또는 50.
3. 대상의 AC를 적용한다(staff of air는 AC 절반만). 이 단계에는 GDR이 적용되지 않는다.
4. 대상의 저항을 적용한다(예: staff of fire는 rF, staff of alchemy는 rPois).
5. 종류별 추가 규칙
   - **staff of earth**: 날고 있는 대상에게는 데미지 1/3.
   - **staff of alchemy**: 데미지가 들어가면 대상을 추가로 **중독**시킨다(중독 수치 2).
   - **staff of necromancy**: 데미지가 들어가면 Evil 행위로 처리된다(선한 신이 싫어함).
   - **staff of fire**: 플레이어가 맞으면 얼음 계열 강화 효과가 녹을 수 있다.
- 확률 계산에는 Evocations가 2배, 데미지 계산에는 학파 스킬이 2배로 들어간다.
- 스킬은 소수점 진행도까지 반영된다.
- Ru의 Sacrifice Artifice(`MUT_NO_ARTIFICE`)를 받았으면 추가 데미지가 없다.
- 그 학파 스킬을 배울 수 없는 캐릭터는 학파 스킬 0으로 계산된다(설명문에 경고가 나온다).
- Attunement 방어구 에고가 있으면, 지팡이로 명중할 때마다(추가 데미지 발동과 무관) MP가 최대치 미만이면 MP 1~3 회복(평균 약 1.67).

### 4.3 추가 데미지 예시
AC 0, 저항 없는 대상 기준. "기대값"은 `발동 확률 × 발동 시 평균`.

**배율 63** (fire, cold, earth, alchemy, necromancy)

| 학파 스킬 | Evocations | 발동 확률 | 발동 시 최대 | 발동 시 평균 | 기대값 |
|---|---|---|---|---|---|
| 5 | 0 | 17% | 6 | 3.0 | 0.5 |
| 10 | 0 | 33% | 14 | 7.0 | 2.3 |
| 15 | 0 | 50% | 22 | 11.0 | 5.5 |
| 20 | 0 | 67% | 30 | 15.0 | 10.0 |
| 27 | 0 | 90% | 41 | 20.5 | 18.4 |
| 10 | 10 | 100% | 22 | 11.0 | 11.0 |
| 20 | 10 | 100% | 38 | 19.0 | 19.0 |
| 27 | 27 | 100% | 62 | 31.0 | 31.0 |

**배율 50** (air, conjuration)

| 학파 스킬 | Evocations | 발동 확률 | 발동 시 최대 | 발동 시 평균 | 기대값 |
|---|---|---|---|---|---|
| 5 | 0 | 17% | 5 | 2.5 | 0.4 |
| 10 | 0 | 33% | 11 | 5.5 | 1.8 |
| 15 | 0 | 50% | 17 | 8.5 | 4.2 |
| 20 | 0 | 67% | 24 | 12.0 | 8.0 |
| 27 | 0 | 90% | 32 | 16.0 | 14.4 |
| 10 | 10 | 100% | 17 | 8.5 | 8.5 |
| 20 | 10 | 100% | 30 | 15.0 | 15.0 |
| 27 | 27 | 100% | 49 | 24.5 | 24.5 |

### 4.4 몬스터가 든 지팡이
몬스터도 같은 공식으로 추가 데미지를 준다. 몬스터의 스킬은 HD로 정해진다.
- Evocations = HD
- 학파 스킬 = 그 학파 마법을 쓰는 몬스터(실제 시전자)면 HD, 아니면 HD/3
  - Necromancy만 예외: Necromancy 마법이 있으면 HD×2, 없으면 HD/2
- 몬스터 설명 화면에 지팡이 추가 데미지의 최대값이 표시된다.

---

## 5. 신앙
- **staff of necromancy는 Evil 아이템**이다. 선한 신(The Shining One, Zin, Elyvilon)이 싫어한다. 근접 추가 데미지가 들어갈 때마다 Evil 행위로도 처리된다.
- 신마다 싫어하는 아이템과 그 대가는 신 문서(예정)에서 다룬다.

## 6. 랜덤 아티팩트 지팡이
- 기본 효과(강화, 저항, 근접 추가 데미지)는 그대로 유지된다.
- 지팡이에는 Slay, MP 속성이 붙지 않는다. 쉽게 바꿔 드는 장비라서 Regen, +Inv, Harm, Rampage, −Tele, \*Silence도 붙지 않는다. ^Fragile은 붙을 수 있다. → [아티팩트 속성](artefact-properties.md)
- 기본 효과와 반대 방향의 속성은 붙지 않는다(예: staff of fire에 rF−).

## 7. 생성 (간략)
- **바닥 무작위 생성**: 무작위 아이템 종류 중 지팡이의 가중치는 10 / 1661(약 0.6%). 7종 중 균등.
  - randart: 아이템 레벨이 0보다 크면 `(101 + 3L) / 8000`.
  - **바닥에서 생성되는 지팡이는 언랜드가 되지 않는다.** 언랜드 지팡이는 무기 쪽 언랜드 생성으로 나온다(`makeitem.cc` 주석: "they also generate as OBJ_WEAPONS").
- **Acquirement(획득)·신의 선물**: 1/100 확률(좋은 아이템 지정 시 1/27)로 언랜드 지팡이를 먼저 시도한다. 지팡이 종류는 **해당 학파 스킬 레벨을 가중치**로 고르고, 별도로 가중치 5의 "완전 무작위" 선택지가 있다. 이미 감정한 종류는 가능하면 피한다.
- **몬스터 장비**(`mon-gear.cc`):
  - Jorgrun: 1/3 확률로 staff of earth.
  - Josephina: staff of cold.
  - Fannar: staff of cold 또는 quarterstaff.
  - Arachne: staff of alchemy.

> 출처: item-prop.cc, item-prop-enum.h, melee-attack.cc, attack.cc, actor.cc, ac-type.h, player.cc, spl-cast.cc, artefact.cc, makeitem.cc, acquire.cc, mon-gear.cc, monster.cc, god-item.cc, describe.cc, dat/descript/items.txt (0.34.1)
