# 탈리스만 (Talismans)

> 기준: DCSS 0.34.1 · [아이템 목록으로](index.md)
>

탈리스만은 장착하면 플레이어를 특정 **변신 형태(form)**로 바꾸는 아이템이다. 형태의 수치는 **Shapeshifting** 스킬에 따라 오른다. 형태별 고유 효과와 공통 규칙, 생성 규칙을 정리한다.

지속 시간은 **턴**(10 aut = 1턴) 단위다. 아래에서 `s`는 Shapeshifting 스킬 레벨(형태의 최대 스킬에서 잘림)이다.

---

## 1. 공통 규칙

### 1.1 사용과 해제
- 탈리스만을 **"착용(put on)"하면 변신이 시작**되고, **3턴에 걸쳐** 변신한다(`TransformDelay`). 도중에 방해받으면 계속할지 묻는다.
- 착용 중인 탈리스만을 다시 사용(벗기)하면 같은 방식으로 원래 모습으로 돌아온다. 다른 탈리스만을 사용하면 그 형태로 바로 바뀐다.
- **탈리스만 형태는 지속 시간이 없다.** 벗을 때까지 유지되는 "기본 형태(default form)"가 된다.
  - potion of cancellation 등 해제 효과로 풀리지 않는다. → [cancellation](potions.md#312-cancellation)
  - 다른 일시적 형태(potion of lignification, 신의 능력 등)가 걸리면 그 형태가 우선하고, 끝나면 탈리스만 형태로 돌아온다. **일시적 형태 중에는 탈리스만을 사용할 수 없다.**
- 랜덤 아티팩트 탈리스만의 속성은 그 형태로 변신해 있는 동안 적용된다. 아티팩트 탈리스만 확률은 [아티팩트 속성](artefact-properties.md) 참고.
- 변신하면 그 자리의 지형이 위험해지는 경우(용암·깊은 물), 또는 벗겨질 장비가 저주(Ashenzari)·^Fragile인 경우에는 변신할 수 없다.

### 1.2 사용할 수 없는 경우
- **언데드**(Mummy, Poltergeist, Revenant 등 살아 있지 않은 종족)는 탈리스만 형태가 될 수 없다.
- Ru의 희생으로 형태 변화 능력을 잃은 경우(`MUT_NO_FORMS`).
- Gargoyle은 granite talisman(statue form)을 쓸 수 없다.
- hive talisman은 Okawaru 신자, Sacrifice Love를 한 경우 쓸 수 없다.
- **Zin 신자가 탈리스만을 사용하면 즉시 파문(excommunication)된다**(`god_despises_item`: Zin은 모든 탈리스만). 선한 신(Elyvilon, The Shining One, Zin)은 sanguine talisman과 talisman of death도 같은 처리다.

### 1.3 Shapeshifting 스킬과 형태 수치
각 형태에는 **최소 스킬(min)**과 **최대 스킬(max)**이 있다.

- 형태의 수치(AC·EV·맨손 데미지·특수 효과 등)는 대부분 **최소 스킬에서 기본값, 최대 스킬에서 기본값 + 증가분**이 되도록 선형으로 변한다.
  - 공식: `기본값 + 증가분 × (s − min) / (max − min)`. s는 최대 스킬에서 잘린다(더 올려도 효과 없음).
  - **최소 스킬보다 낮으면 같은 비율로 기본값보다 낮아진다**(AC·EV·맨손 보너스는 0 아래로 내려가지 않음).
- **HP 페널티**: 스킬이 최소 스킬보다 낮으면 **부족한 스킬 1레벨당 최대 HP −10%**(최대 −90%). 형태 자체의 HP 배율(hp_mod)에 곱해진다.
- Shapeshifting 스킬은 탈리스만 형태에서 **근접 공격을 할 때** 1/2 확률로 훈련된다. 그 형태의 최대 스킬 이상이면 훈련되지 않고, 최대 스킬까지 5 이하로 남으면 훈련 확률이 다시 절반이 된다.
- amulet of wildshape(Shapeshifting +5)처럼 스킬을 올려주는 효과도 반영된다. → [wildshape](jewellery.md#46-wildshape)

### 1.4 장비 녹아듦 (Meld)
형태마다 일부 장비 슬롯이 **녹아든다(meld)**: 착용은 유지되지만 **효과가 사라진다.**

| 표기 | 녹아드는 슬롯 |
|---|---|
| aux | 투구, 장갑, 부츠, 바딩, 망토 |
| held | 무기, 방패(보조손) |
| physical | 무기, 방패, 몸통, aux 전부 |

반지·목걸이를 녹이는 탈리스만 형태는 없다(physical에도 장신구는 포함되지 않음).

### 1.5 형태가 바꾸는 수치 (공통 항목)
- **AC / EV**: 형태가 주는 고정 보너스. 
- **몸통 방어구 AC 배율**: 몸통 방어구의 기본 AC에 퍼센트로 곱한다(예: −75%면 1/4만 적용).
- **맨손 공격 데미지**: 모든 형태는 맨손 기본 데미지 3에 형태 보너스를 더한다. → [무기 문서](weapons.md)
- **HP 배율, 몸집(size), Str/Dex 보너스, 저항, 비행·수영 가능 여부, 주문 시전 가능 여부** 등.

### 1.6 protean talisman
- 사용하려면 **Shapeshifting 6 이상**이 필요하다. 사용하면 **rimehorn, scarab, medusa, spore 중 무작위 하나로 바뀌고** 그 탈리스만으로 변신한다.
- 바닥 무작위 생성 등급표에 없어서 일반적으로 생성되지 않는다(Xom의 선물 등 특수 경로). scroll of acquirement로는 나오지 않는다.

---

## 2. 전체 목록

| 등급 | 탈리스만 | 형태 | 스킬 (min~max) | 녹아드는 슬롯 | 요약 |
|---|---|---|---|---|---|
| 1 | [quill](#quill-talisman) | Quill | 0~7 | aux | 근접 공격받으면 가시 반격, 조임 면역 |
| 1 | [inkwell](#inkwell-talisman) | Walking Scroll | 0~7 | physical | 마법 스킬 +0.5~4, 최대 MP +4~9, 4레벨 이하 주문만 |
| 2 | [rimehorn](#rimehorn-talisman) | Rime Yak | 8~14 | physical | 근처 벽을 얼려 적에게 냉기 피해, Ice 주문 실패율 감소 |
| 2 | [scarab](#scarab-talisman) | Sun Scarab | 8~14 | physical | 아군 solar ember 동반, Fire 주문 실패율 감소 |
| 2 | [medusa](#medusa-talisman) | Medusa | 8~14 | 투구, 망토 | 근접 공격 시 주변 적 독침, 중상 시 석화 |
| 2 | [spore](#spore-talisman) | Spore | 8~14 | 방패, 부츠 | 근접 명중 시 폭발 버섯 생성, 약화 |
| 2 | [maw](#maw-talisman) | Maw | 12~20 | 없음 | 물기 보조 공격, 처치한 적을 삼켜 재생 |
| 3 | [serpent](#serpent-talisman) | Serpent | 12~20 | 무기·방패·몸통·장갑·부츠·바딩·망토 | 조이기, 투구 2개 |
| 3 | [blade](#blade-talisman) | Blade | 17~25 | 없음 | 칼날 보조 공격 2회, 공격 중 SH |
| 3 | [eel](#eel-talisman) | Eel Hands | 12~20 | held, 장갑 | 명중 시 연쇄 전격, 중상 시 방전 |
| 3 | [fortress](#fortress-talisman) | Fortress Crab | 12~20 | 방패, aux | 몸통 방어구 강화(속성 2배), Breathe Rust |
| 3 | [lupine](#lupine-talisman) | Werewolf | 12~20 | 장갑, 부츠, 바딩 | 처치 시 Slaying, 울부짖음, Bestial Takedown |
| 3 | [spider](#spider-talisman) | Spider | 12~20 | physical | 거미줄, Rampage, Jump, 좋은 암습 |
| 3 | [wellspring](#wellspring-talisman) | Aqua | 12~20 | 몸통 | 근접 사거리 +2, Watery Grave |
| 4 | [granite](#granite-talisman) | Statue | 17~25 | 장갑, 부츠, 바딩, 몸통 | AC +27~38, 모든 행동 느림, 근접 데미지 ×1.5 |
| 4 | [hive](#hive-talisman) | Hive | 17~25 | 몸통, 투구 | 재생 증가, 중상 시 아군 벌떼 |
| 4 | [dragon-coil](#dragon-coil-talisman) | Dragon | 17~25 | physical | Giant, HP ×1.5, 비행, 브레스 |
| 4 | [sanguine](#sanguine-talisman) | Vampire | 17~25 | 없음 | 흡혈, 노예(thrall), 박쥐 떼 변신, 최면 시선 |
| 4 | [riddle](#riddle-talisman) | Sphinx | 17~25 | 무기·방패·몸통·부츠·투구·장갑 | 비행, 명중 시 airstrike, Hexes 강화 |
| 5 | [storm](#storm-talisman) | Storm | 23~27 | physical | 전격 맨손 27~33(모든 방향 cleave), EV +20~27, Blinkbolt |
| 5 | [talisman of death](#talisman-of-death) | Death | 26~27 | 없음 | 언데드, 공격 시 Slow·Weak·Drain, Siphon Essence |
| — | [protean](#16-protean-talisman) | — | 6 이상 필요 | — | 2등급 탈리스만 중 하나로 변함 |

(blade는 등급표상 3등급이지만 스킬 범위는 17~25다.)

---

## 3. 1등급

### quill talisman
**Quill form** · 스킬 0~7 · 녹아듦: aux

- **가시 반격**: 인접한 몬스터가 플레이어에게 근접 공격을 하면(막히지 않았을 때, 그 몬스터의 첫 공격에만) **2/5 확률**로 피해 `1d(2 + 6s/7)`(스킬 0 → 1d2, 7 → 1d8).
  - 코드상 이 피해에 **몬스터 AC가 두 번 적용된다**(`melee-attack.cc` do_spines에서 `apply_ac`를 두 번 호출, 0.34.1). 같은 함수의 spiny 돌연변이 반격은 한 번만 적용한다.
- **조임(constriction) 면역.**
- 그 밖의 수치 변화는 없다(맨손 데미지 3, AC·EV 보너스 없음).

### inkwell talisman
**Walking Scroll form** · 스킬 0~7 · 녹아듦: physical (무기·방패·방어구 전부)

| 항목 | 값 |
|---|---|
| 몸집 | Tiny |
| 성질 | nonliving(살아 있지 않음), 피 없음 |
| 저항 | **rF−** |
| 수영 | 불가 |

- **마법 스킬 보너스**: 모든 마법 학파 스킬(Conjurations ~ Alchemy. Spellcasting은 제외)에 **`(1 + s) / 2`레벨**(스킬 0 → +0.5, 7 → +4) 가산.
- **최대 MP +`4 + 5s/7`**(+4~+9).
- **4레벨을 넘는 주문은 시전할 수 없다.**
- **근접 데미지 절반**(최종 데미지에 ×1/2).
- 근접 공격이 명중하면 1/2 확률로 **MP +1**(고정물 제외).

---

## 4. 2등급

### rimehorn talisman
**Rime Yak form** · 스킬 8~14 · 녹아듦: physical

| 항목 | 값 |
|---|---|
| 몸집 | Large |
| HP | ×1.15 |
| AC | +6 ~ +12 |
| 맨손 데미지 | 3 + 4 = 7 |
| 저항 | **rC++**, rF− |
| 수영 | 가능 |

- **Frigid Aura**: 적(아군·고정물 제외)에게 근접 공격할 때마다
  1. 대상과 인접한 벽 중 하나(없으면 플레이어와 인접한 벽)를 **frigid wall**로 바꾼다(2턴).
  2. 플레이어 반경 2 안의 모든 frigid wall 지속을 3~6턴(30~59 aut)으로 갱신한다.
  - 즉 계속 근접 공격해야 벽이 유지된다.
- 매 턴, 시야 안의 적대 몬스터 중 **frigid wall과 인접한 몬스터**는 냉기 피해 `2d(1 + 3s/5)`(스킬 8 → 2d5, 14 → 2d9)를 받는다. 인접한 frigid wall이 2개 이상이면 1개 늘 때마다 +1/6(약 16.7%). AC와 rC가 적용된다.
- **Ice 주문 실패율 ×2/3.**
- frigid wall은 파낼 수 있는 벽이다. 형태가 끝나면 모두 사라진다.

### scarab talisman
**Sun Scarab form** · 스킬 8~14 · 녹아듦: physical

| 항목 | 값 |
|---|---|
| 몸집 | Small |
| AC | +5 ~ +9 |
| 저항 | **rF++**, **rPois−** |
| 수영 | 불가 |

- **solar ember**: 변신하면 아군 solar ember(HD 5, HP 약 32, AC 5, EV 15, 비행, rF+++, rC−, Willpower ∞, 빠른 재생)가 옆에 생긴다. 플레이어 옆을 떠나지 않으며(leash 1) 계단도 따라온다.
  - **충전과 폭발**: 근접 공격을 하면(공격 행동당 1회) ember가 7~9턴 동안 "충전"된다. 충전된 상태에서 다시 근접 공격하면 **ember와 인접한 모든 적에게 화염 피해 `2d(2 + 8s/5)`**(스킬 8 → 2d14, 14 → 2d24, AC·rF 적용)를 주고, ember는 7~10 피해를 입는다. 즉 **두 번 공격할 때마다 한 번 터진다.**
  - ember와 **자리를 바꾸면** ember가 최대 HP의 3/4만큼 회복한다.
  - ember가 죽으면 **20~32턴 뒤** 다시 생긴다. 형태를 풀었다가 다시 변신해도 이 대기 시간은 줄지 않는다. 형태를 풀면 ember는 사라진다.
- **Searing attack**: 근접 공격이 명중하면 1/2 확률로 대상에게 **화염 취약(rF−)** `5 + random2(데미지)`턴.
- **Fire 주문 실패율 ×2/3.** (게임 내 설명은 Fire는 "much more easily", rimehorn의 Ice는 "more easily"로 다르게 쓰지만 코드상 둘 다 ×2/3이다.)

### medusa talisman
**Medusa form** · 스킬 8~14 · 녹아듦: 투구, 망토

- 저항: **rPois**.
- **Stinger hair**: 근접 공격을 하면(공격 행동당 1회) **반경 2 안의 적대 몬스터 중 무작위 `2.5 + 1.5×(s−8)/6`마리**(반올림 무작위; 스킬 8 → 2~3, 14 → 4)에게 독침 보조 공격을 한다. 독침은 기본 데미지 0이고 맞으면 **중독 1~2단계**.
- **Lithotoxin**: 피해를 받아 **HP가 최대의 60% 이하**가 되면, **반경 3 안의 중독된 적대 몬스터**를 각각 **`55 + 15×(s−8)/6`%**(55~70%) 확률로 **석화(petrify)**시킨다. Willpower 판정은 없다. 한 번 발동하면 **HP가 가득 찰 때까지** 다시 발동하지 않는다.

### spore talisman
**Spore form** · 스킬 8~14 · 녹아듦: 방패, 부츠

- 맨손 데미지 3 + 4 = 7, 방패 손으로도 펀치(offhand punch) 가능.
- **Sporulate**: 근접 공격이 명중하면(아군·고정물 제외) **대상 뒤쪽(플레이어 반대편) 인접 칸 최대 3곳**에 아군 **burstshroom**(HD `s/2`)이 자란다.
  - burstshroom은 3~5턴 뒤 터져서 **인접한 적대 몬스터 중 숨을 쉬는 몬스터**에게 `2d(1 + 4s/5)`(스킬 8 → 2d7, 14 → 2d12) 피해를 주고, `(s × 10) / (HD × 30)` 확률로 2~5턴 **Daze**(멍해짐)를 건다.
  - 터질 때 플레이어가 볼 수 없는 위치면 그냥 사라진다.
- **Weakening spores**: 근접 공격이 명중하면 1/2 확률로, 숨을 쉬고 공격 수단이 있는 대상을 **Weak**(약화)시킨다.

### maw talisman
**Maw form** · 스킬 12~20 (2등급이지만 스킬 범위는 3등급과 같다) · 녹아듦: 없음

- **몸통 방어구 AC −75%**(기본 AC의 1/4만 적용).
- **Maw 보조 공격**: 근접 공격할 때마다 **항상(100%)** 물기 보조 공격을 한다. 기본 데미지 `8 + 6×(s−12)/8 + Str × 3/4`.
- **Devour**: 근접 공격으로 인접한 적을 죽이면, 그 적이 natural·plant이고 소환수가 아니면 **삼킨다**(시체가 남지 않음, 용 비늘 등 부산물은 떨어짐).
  - **Engorged** 지속 +`(10 + HD×10/3 ~ HD×20/3)` aut(상한 40턴). 그동안 **HP 재생 +`220 + 280×(s−12)/8`**(턴당 HP 약 +2.2 ~ +5).
  - Beogh 신자는 오크를 삼키지 않는다. Gozag 신자(시체가 금으로 변함)는 삼킬 수 없다.
- **Growling stomach**: 먹을 수 있어 보이는(natural·plant, 소환수 아님) 몬스터를 새로 발견하면 **1/6 확률로 그 몬스터에게 Mesmerised**(6~10턴)되고 큰 소리(외침과 같은 크기)를 낸다. Clarity가 있으면 Mesmerised는 막지만 소리는 낸다.

---

## 5. 3등급

### serpent talisman
**Serpent form** · 스킬 12~20 · 녹아듦: 무기, 방패, 몸통, 장갑, 부츠, 바딩, 망토 (투구·반지·목걸이만 남음)

| 항목 | 값 |
|---|---|
| 몸집 | Large |
| HP | ×1.2 |
| AC | +10 ~ +16 |
| Str | +5 |
| 맨손 데미지 | 3 + 7 = 10 |
| 저항 | rPois |
| 수영 | 가능 |

- **Constrict 보조 공격**: 근접 공격할 때 조이기 보조 공격(100%)을 해서 대상을 조인다. 조이는 동안 매 턴 피해(플레이어 기본 조이기 공식).
- **투구 2개**: 머리가 둘이라 투구·모자를 2개 쓸 수 있다(Felid처럼 방어구를 못 입는 종족은 제외).
- **Cold-blooded**: rC가 0 이하일 때 냉기 피해를 받으면 1/2 확률로 Slow. 원래 종족 특성으로 cold-blooded가 있어도 이 형태에서는 이 규칙으로 대체된다.

### blade talisman
**Blade form** · 스킬 17~25 · 녹아듦: 없음

- **몸통 방어구 AC −50% → −20%**(스킬에 따라 감소 폭이 줄어듦).
- **칼날 보조 공격 2회**: 근접 공격할 때마다 독립적으로 **60% 확률**인 slice 보조 공격이 2번. 기본 데미지 `10 + 6×(s−17)/8`(10~16).
- **Blade parry**: 그 턴에 공격(시도)을 했으면 다음 턴까지 **SH + `(6 + 6×(s−17)/8) + Slaying`**(표시 SH 기준). → [SH](armour.md)

### eel talisman
**Eel Hands form** · 스킬 12~20 · 녹아듦: held(무기·방패), 장갑

- 무기와 방패를 쓸 수 없다. 맨손 데미지 `3 + (3 + 4×(s−12)/8)` = 6~10, 방패 손으로도 펀치 가능.
- 저항: **rElec**.
- **Eel punch**: 근접 공격이 명중하면 1/2 확률로 대상에서 시작하는 **연쇄 전격**(대상 포함 3~6곳), 각 `1d(23s/10 − 2)`(스킬 12 → 1d25, 20 → 1d44).
- **Eeljolt**: 피해를 받아 **HP가 최대의 40% 이하**가 되면 반경 2 안을 기점으로 하는 연쇄 전격을 일으킨다(데미지 주사위 크기 2배). 한 번 발동하면 HP가 가득 찰 때까지 다시 발동하지 않는다.

### fortress talisman
**Fortress Crab form** · 스킬 12~20 · 녹아듦: 방패, aux

| 항목 | 값 |
|---|---|
| AC | +3 |
| **몸통 방어구 AC** | **+70% ~ +150%**(기본 AC의 1.7~2.5배) |
| 맨손 데미지 | 3 + (5 ~ 10) = 8~13 |
| 저항 | **rCorr**, rPois− |
| 이동 속도 | **이동 시간 ×1.3** |
| 수영 | 가능 |

- **Armoured shell**: **몸통 방어구의 에고와 아티팩트 속성, 방어구 고유 속성(드래곤 갑옷 저항 등)이 2번 계산된다.** 몸통 방어구가 regeneration 속성(troll leather 등)이면 재생도 2배.
- 방패 슬롯은 녹지만, **양손 무기는 전용 슬롯으로 옮겨져 계속 쓸 수 있다.**
- **Breathe Rust**(능력): 비용 **HP 10% + 12**. 사거리 4 지점을 겨냥해, 그 주변(반경 2)에 **rust 구름 `9 + 16×(s−12)/8`개**(9~25)를 깐다. 구름 지속 `5 + 개수×2/3`턴.
  - rust 구름: 산성 피해(기본 2 + 무작위 3), **Corrosion**과 **Weak**를 건다. **Fortress Crab 형태인 플레이어는 rust 구름 면역.**

### lupine talisman
**Werewolf form** · 스킬 12~20 · 녹아듦: 장갑, 부츠, 바딩

| 항목 | 값 |
|---|---|
| Str / Dex | +3 / +3 |
| 발톱 | claws 3단계 상당 |
| 저항 | rC+ |
| Willpower | −1단계 |
| HP 재생 | +80(턴당 +0.8) |

- **Werefury**: 근접 공격으로 소환수가 아닌 적을 죽이면 일시적 **Slaying** 획득. 처치당 `(12 + 10×(s−12)/8)/10`(1.2~2.2), 첫 처치는 1.5배. **Slaying 최대 +12.** 지속은 처치마다 +7~11턴(상한 20턴).
- **Werehowl**: Werefury로 Slaying이 **5 이상이 되는 순간**, 그 뒤로는 처치 때마다 1/4 확률로(Bestial Takedown 처치는 항상) 울부짖는다.
  - 시야 안의 적 중 공포를 느낄 수 있는 몬스터가 Willpower 판정(위력 `80 + 40×(s−12)/8`)에 실패하면 **4~7턴 Fear + 그 자리에 묶임(Bound)**.
  - 울부짖을 때 외침 크기의 소음. Silence 상태면 울부짖지 못한다.
- **Bestial Takedown**(능력, MP 4, 사거리 5): **Fear 상태인 적**에게 뛰어들어 인접 칸에 착지하고 **반드시 명중하는 공격**을 한다. 데미지 ×`(175 + 50×(s−12)/8)/100`(×1.75~×2.25). 소음 5.

### spider talisman
**Spider form** · 스킬 12~20 · 녹아듦: physical

| 항목 | 값 |
|---|---|
| 몸집 | **Tiny** |
| Dex | +5 |
| AC / EV | +3 / +5 ~ +15 |
| 맨손 데미지 | 3 + 3 = 6 |
| 저항 | rPois− |
| 수영 | 불가 |

- **Ensnaring attack**: 근접 공격이 명중하면 `20 + 20×(s−12)/8`%(20~40%) 확률로 대상을 **거미줄에 묶는다.**
- **Rampage +1**(다른 Rampage와 합쳐 최대 3).
- **거미줄 면역.**
- **좋은 암습**: Short Blades처럼 암습 보너스를 받는다(은신 & 암습 문서에서 다룰 예정).
- **Jump**(능력, 비용 없음): 시야 안의 무작위 칸(되도록 인접하지 않은 칸)으로 뛴다. 그 턴 동안 자동 회피(autododge). 플레이어를 노리던 몬스터 각각이 `(그런 몬스터 수 + 3)/9` 확률로 플레이어를 놓친다. 이후 2~5턴 Blink 재사용 대기. **−Tele의 영향을 받지 않는다.**

### wellspring talisman
**Aqua form** · 스킬 12~20 · 녹아듦: 몸통 방어구

- EV +6 ~ +13. 수영 가능. **amorphous**(조임 면역 등).
- **Water reaching**: 근접 공격 **사거리 +2**(맨손 3칸, reach 무기는 무기 사거리 + 2). 보조 공격도 3칸까지 나간다.
- **Water splatter**: 한 번에 최대 HP의 10% 이상 피해를 받으면(그 미만도 낮은 확률로) 주변 반경 3에 **얕은 물**을 만든다(피해 비율(%)의 절반 칸 수, 8~11턴 유지).
- **Watery Grave**(능력, MP 6): 반경 4 안에 물이 있어야 쓸 수 있다. **반경 4 안의 모든 적대 몬스터**에게 물 공격 `4d(1 + 6s/5)`(스킬 12 → 4d15, 20 → 4d25)를 하고, 숨 쉬는 몬스터는 익사 상태(Flooded)로 만든다. 사용 후 **반경 4 안의 얕은 물은 모두 바닥으로 바뀐다.** 재사용은 경험치로 충전된다.
- **약점**:
  - 냉기 피해를 받으면 1/2 확률로 **Frozen**(5~10턴, 상한 50; 이동 시간 ×1.5).
  - 화염 피해를 받으면 `피해 / (최대 HP × 2/3)` 확률로 몸 일부가 증기로 변해 **증기 구름**이 생긴다.

---

## 6. 4등급

### granite talisman
**Statue form** · 스킬 17~25 · 녹아듦: 장갑, 부츠, 바딩, 몸통 (무기·방패·투구·망토는 사용 가능)

| 항목 | 값 |
|---|---|
| HP | ×1.3 |
| AC | **+27 ~ +38** |
| Str | +7 |
| 맨손 데미지 | 3 + 5 = 8 |
| 저항 | rElec, rN+, **석화 면역**, Torment 피해 절반 |
| 성질 | nonliving |

- **모든 행동 시간 ×1.5**(이동·공격·주문 등, `player_speed`).
- **근접 데미지 ×1.5**(AC 적용 후). 느려진 공격 속도를 정확히 상쇄하도록 만든 배율이다.
- **EV ×4/5**(자연 EV에 곱함).
- Lee's Rapid Deconstruction의 대상이 될 수 있고, Shatter에 맞을 때의 피해 주사위가 Gargoyle·Revenant와 같은 최대 단계(6)다.
- Gargoyle은 이 탈리스만을 쓸 수 없다.

### hive talisman
**Hive form** · 스킬 17~25 · 녹아듦: 몸통, 투구

- AC +5.
- **재생**: HP 재생 `+160 + 120×(s−17)/8`(턴당 +1.6 ~ +2.8), MP 재생 `+60 + 40×(s−17)/8`.
- **Hive swarm**: 피해를 받아 **HP가 최대의 50% 이하**가 되면 아군 **killer bee**(HD 5) `3.2 + 2.3×(s−17)/8`마리(반올림 무작위, 3~6마리)가 주변(반경 1~3)에 나온다. 벌은 **Berserk**와 **Concentrate Venom** 상태이고 12~18턴 지속. 한 번 발동하면 **HP가 가득 찰 때까지** 다시 발동하지 않는다.
- 아군을 가질 수 없는 경우(Sacrifice Love)와 Okawaru 신자는 사용할 수 없다. Okawaru는 hive form 상태의 플레이어를 신자로 받지 않는다.

### dragon-coil talisman
**Dragon form** · 스킬 17~25 · 녹아듦: physical

| 항목 | 값 |
|---|---|
| 몸집 | **Giant** |
| HP | ×1.5 |
| AC | +12 ~ +18 (Draconian은 −6) |
| Str | +10 |
| 맨손 데미지 | 3 + (8 ~ 18) = 11~21, claws 3단계 상당, 방패 손 펀치 가능 |
| 저항 | rF+, rC+, rPois (Draconian은 rF·rC를 형태에서 받지 않고 종족 색의 저항을 따름) |
| 비행 | **가능**(항상 비행) |
| 수영 | 불가 |

- **브레스**: Draconian이 아니면 **Golden Breath**(사거리 5)를 쓴다. 화염 볼트와 냉기 볼트를 같은 방향으로 **한 번씩 관통 발사**(각 `3d(2 + 4p/3)`)하고, 경로에 독 구름(4~8턴)을 남긴다.
  - 브레스 위력 `p = s − 5`(Draconian은 여기에 XL을 더한다). 스킬 17 → 각 3d18, 25 → 각 3d28.
  - 브레스는 **충전식**(최대 3회). 경험치를 얻으면 충전되며, **dragon form에서는 2배 빨리** 충전된다. 처음 dragon form이 되면(Draconian 제외) 1회분을 받는다.
  - Draconian은 자기 종족 브레스를 쓰고, dragon form에서 브레스 실패율 −20%, 위력에 형태 보너스가 더해진다. 형태 이름도 종족 색에 맞는 용이 된다.

### sanguine talisman
**Vampire form** · 스킬 17~25 · 녹아듦: 없음

- 저항: rC+, **rN++**, Torment 피해 절반. 성질에 **undead가 추가**된다(살아 있는 상태는 유지).
- **Stealth +2단계.**
- **흡혈**: 인접한 대상에게 근접 공격할 때, **암습(stab)이거나 HP가 최대의 50% 이하**이면(후자는 2/3 확률) 입힌 피해의 `random2(데미지)`만큼 회복(흡혈 가능한 대상만, Death's Door 중 불가).
- **Bloodcurse**: 암습으로 소환수가 아닌 natural·plant·demonic 몬스터를 죽이면 그 몬스터가 **아군 vampiric thrall로 일어난다**(최대 HP로 부활, 주문을 쓰는 몬스터는 Vampiric Draining 추가). **동시에 1마리만** 가능하다. thrall의 유지 시간은 (미확인).
- **Hypnotic gaze**: 몬스터가 플레이어를 처음 알아채고 외치려 할 때(서로 보이는 경우, natural·demonic·holy 몬스터) 3/4 확률로 Willpower 판정(위력 `70 + 75×(s−17)/8`). 실패하면 3~5턴 **Daze**, 성공해도 한 턴 분의 행동을 잃는다.
- **Bat Swarm**(능력, MP 6, 즉시): 12~20턴 동안 **bat swarm form**이 되고 주변에 박쥐 구름을 만든다. 재사용은 경험치로 충전되며, 스킬이 높을수록 빨리 충전된다(필요량 `11000 / (100 + 100×(s−17)/8)`).
  - bat swarm form: Tiny, Dex +5, EV +15 ~ +35, **이동 시간 절반**, 비행, **주문 시전 불가**, 맨손 공격 약함, 녹아듦 physical. 흡혈·Bloodcurse·Stealth·rN++은 그대로.
- **약점**: 시야에 몬스터가 있으면 **HP가 재생되지 않는다**(inhibited regeneration). Doom과 Bane에서 더 느리게 회복한다(accursed).
- 선한 신(Zin, The Shining One, Elyvilon) 신자가 사용하면 파문된다.

### riddle talisman
**Sphinx form** · 스킬 17~25 · 녹아듦: 무기, 방패, 몸통, 부츠, 투구, 장갑 (망토·바딩·장신구만 남음)

- HP ×1.15, AC +7, **비행**, **Willpower +1단계**.
- **망토와 바딩을 입을 수 있다**(원래 바딩을 못 입는 종족도. 방어구를 전혀 못 입는 종족은 제외).
- **Airstrike attack**: 근접 공격이 명중하면 추가 피해 `(1 + 빈칸/2)d(1 + 5s/7)`(빈칸 = 대상 주변의 막히지 않은 칸 수, 최대 7). AC 적용.
- **Hex mastery**: **Hexes 주문 실패율 ×2/3**. 또한 플레이어가 거는 **모든 Willpower 판정에서 대상의 Willpower −1단계**(코드상 Hexes에 한정되지 않음, `beam.cc` apply_willpower_bypass).
- **Riddle compulsion**: 새로 몬스터를 발견하면(그 턴에 발견한 수를 n이라 할 때 `n/(n+5)` 확률, 유니크가 있으면 항상) 가장 지능이 높은 몬스터에게 수수께끼를 낸다. 외침과 같은 크기의 **소음**이 나고, 1/20 확률로 그 몬스터를 Vex(5~8턴) 또는 Confusion에 빠뜨린다.

---

## 7. 5등급

### storm talisman
**Storm form** · 스킬 23~27 · 녹아듦: physical

| 항목 | 값 |
|---|---|
| AC / EV | +12 ~ +15 / **+20 ~ +27** |
| 맨손 데미지 | 3 + (24 ~ 30) = **27~33, electrocution 브랜드**, 방패 손 펀치 가능 |
| 저항 | rElec |
| 성질 | nonliving, **insubstantial**(석화·그물/거미줄·Sticky Flame 등 면역) |
| 비행 | 가능 |

- **모든 근접 공격이 cleave**(주변 모든 적을 함께 공격).
- **Blinkbolt**(능력, 비용 없음, 사거리 시야): 번개가 되어 목표까지 이동하며 경로의 대상에게 `1d(11 + 3p/5)` 피해(p = `s × 200/27`, 스킬 23 → 약 1d113, 27 → 1d131). 이후 **5~20턴 재사용 대기**. −Tele 등 순간이동 금지의 영향을 받는다.

### talisman of death
**Death form** · 스킬 **26~27** · 녹아듦: 없음

- 성질 **undead**. 저항: rC+, **rN+++**, **Torment 면역**. **Willpower +1단계.**
- 맨손 데미지 3 + 6 = 9, **draining 브랜드**.
- **Vile attack**: 근접 공격으로 피해를 주면, nonliving이 아닌 대상에게 3~6턴 동안 **Slow**(Stasis 제외), **Weak**(공격 수단이 있으면), **Drain**(natural·plant만)을 건다.
- **Siphon Essence**(능력, MP 20): **반경 2 안의 적대 몬스터 중 Torment 면역이 아닌 대상**의 **현재 HP를 절반**으로 만든다. 입힌 피해 합계와 `19 + 3s` 중 작은 값의 2/3만큼 HP 회복(최대 약 67). 이후 12~16턴 재사용 대기.
- **포션을 마실 수 없다.** Doom과 Bane에서 더 느리게 회복한다(accursed).
- Death's Door 상태에서는 변신할 수 없다. 선한 신 신자가 사용하면 파문되고, 이 형태로는 선한 신에 입교할 수 없다.

---

## 8. 생성 (간략)
- **바닥 무작위 생성**: 무작위 아이템 종류 중 탈리스만의 가중치는 25 / 1661(약 1.5%).
- **등급 선택**: 아이템 레벨(최대 35)에 따라 등급을 고른 뒤, 그 등급 안에서 균등하게 고른다.

| 아이템 레벨 | 1등급 | 2등급 | 3등급 | 4등급 | 5등급 |
|---|---|---|---|---|---|
| 0 (D:1) | 57% | 30% | 4% | 4% | 4% |
| 5 | 35% | 50% | 6% | 4% | 4% |
| 10 | 12% | 62% | 16% | 5% | 5% |
| 15 | 6% | 45% | 29% | 14% | 6% |
| 20 | 6% | 21% | 40% | 24% | 9% |
| 27 이상 | 5% | 12% | 35% | 29% | 20% |

- **아티팩트 확률**: `max(0, L − (등급−1)×6) × 2.5 + 5`%. 낮은 등급일수록 아티팩트가 흔하다. → [아티팩트 속성](artefact-properties.md)
- scroll of acquirement의 탈리스만은 아직 본 적 없는 종류와 Shapeshifting 스킬에 맞는 등급을 우대하고, 1/4 확률로 아티팩트다. → [acquirement](scrolls.md#32-분류별-규칙-요약)

> 출처: transform.cc, dat/forms/*.yaml, util/form-gen.py, item-use.cc, item-prop.cc, god-item.cc, makeitem.cc, artefact.cc, melee-attack.cc, fight.cc, ouch.cc, player.cc, player-reacts.cc, player-equip.cc, player-act.cc, mon-abil.cc, mon-act.cc, mon-death.cc, movement.cc, spl-damage.cc, spl-transloc.cc, spl-cast.cc, spl-util.cc, skills.cc, exercise.cc, ability.cc, beam.cc, cloud.cc, terrain.cc, dat/mons/solar-ember.yaml (0.34.1)
