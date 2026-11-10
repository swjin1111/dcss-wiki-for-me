# 탈리스만 (Talismans)

> 기준: DCSS 0.34.1 · [아이템 목록으로](index.md)
>
> **작성 진행**: 공통 규칙, 전체 목록, 1~3등급 형태 상세 작성. **4~5등급(granite, hive, dragon-coil, sanguine, riddle, storm, death) 상세는 다음 작업에서 이어서 쓴다.**

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

반지·목걸이를 녹이는 형태는 1~3등급에는 없다.

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
| 4 | granite | Statue | 17~25 | 장갑, 부츠, 바딩, 몸통 | (다음 작업) |
| 4 | hive | Hive | 17~25 | 몸통, 투구 | (다음 작업) |
| 4 | dragon-coil | Dragon | 17~25 | physical | (다음 작업) |
| 4 | sanguine | Vampire | 17~25 | 없음 | (다음 작업) |
| 4 | riddle | Sphinx | 17~25 | 무기·방패·몸통·부츠·투구·장갑 | (다음 작업) |
| 5 | storm | Storm | 23~27 | physical | (다음 작업) |
| 5 | talisman of death | Death | 26~27 | 없음 | (다음 작업) |
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
- **Water splatter**: 한 번에 최대 HP의 10% 이상 피해를 받으면(그 미만도 낮은 확률로) 주변 반경 3에 **얕은 물**을 만든다(피해 비율의 절반 정도의 칸 수).
- **Watery Grave**(능력, MP 6): 반경 4 안에 물이 있어야 쓸 수 있다. **반경 4 안의 모든 적대 몬스터**에게 물 공격 `4d(1 + 6s/5)`(스킬 12 → 4d15, 20 → 4d25)를 하고, 숨 쉬는 몬스터는 익사 상태(Flooded)로 만든다. 사용 후 **반경 4 안의 얕은 물은 모두 바닥으로 바뀐다.** 재사용은 경험치로 충전된다.
- **약점**:
  - 냉기 피해를 받으면 1/2 확률로 **Frozen**(5~10턴, 상한 50; 이동 시간 ×1.5).
  - 화염 피해를 받으면 `피해 / (최대 HP × 2/3)` 확률로 몸 일부가 증기로 변해 **증기 구름**이 생긴다.

---

## 6. 생성 (간략)
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
