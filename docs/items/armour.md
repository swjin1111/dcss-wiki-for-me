# 방어구 (Armour)

> 기준: DCSS 0.34.1 · [아이템 목록으로](index.md)

방어구의 수치와 **AC(방어)·EV(회피)·SH(막기)·방해도가 계산되는 방식**, 그리고 몬스터의 공격이 이 수치들과 어떻게 비교되는지 정리한다. 에고 효과는 [브랜드·에고](brands-egos.md#방어구-에고), 아티팩트 속성은 [아티팩트 속성](artefact-properties.md) 참고.

---

## 1. 슬롯과 착용 제한

| 슬롯 | 장비 |
|---|---|
| 몸통 | robe, leather armour, ring mail, scale mail, chain mail, plate armour, crystal plate armour, animal skin, troll leather armour, 드래곤 비늘 10종 |
| 망토 | cloak, scarf |
| 머리 | helmet(단단한 투구), hat |
| 손 | gloves |
| 발 | boots, barding(하반신이 뱀·짐승인 종족용) |
| 보조손 | buckler, kite shield, tower shield, orb |

### 1.1 몸집에 따른 제한
**몸통 방어구와 보조손 장비**는 몸통 크기(torso size)가 맞아야 입을 수 있다. 몸집 구분은 [무기 문서](weapons.md#12-한손양손과-몸집) 참고.

| 장비 | 입을 수 있는 몸집 |
|---|---|
| robe | Little ~ Large |
| leather / ring / scale / chain / plate / crystal plate | **Small ~ Medium** |
| animal skin, troll leather armour, 드래곤 비늘 | 모든 몸집 |
| buckler | Little ~ Medium |
| kite shield | Small ~ Large |
| tower shield | **Medium 이상** |
| orb | 모든 몸집 |

- 예: Troll·Oni(Large)는 몸통에 robe, animal skin, troll leather armour, 드래곤 비늘만 입을 수 있고, 방패는 kite·tower shield만 쓸 수 있다.
- 예: Spriggan(Little)은 몸통에 robe, animal skin, troll leather armour, 드래곤 비늘만 입을 수 있고(leather armour 등은 Small부터), 방패는 buckler만 쓸 수 있다.

### 1.2 단단한 투구(helmet)
helmet은 아래에 해당하면 쓸 수 없다. hat은 해당 없음.
- 몸집 Large 이상 또는 Little 이하
- Draconian, Octopode
- 뿔(Horns), 더듬이(Antennae), 부리(Beak) 돌연변이

그 밖의 보조 장비 슬롯(장갑·부츠 등)을 쓸 수 있는지는 종족마다 다르다. → 종족 문서(예정)

---

## 2. AC (Armour Class)
### 2.1 계산
**AC = Σ(방어구마다 `기본 AC × (1 + Armour 스킬/22)` + 인챈트) + 기타 보너스**

- **Armour 스킬 배율은 몸통·보조 방어구 전부의 기본 AC에 적용된다.** 인챈트(+N)에는 적용되지 않는다.
- **방패는 AC를 주지 않는다.** 방패의 기본값과 인챈트는 SH로 간다.
- 기타 보너스: Protection 에고 +3, ring of protection, 아티팩트 AC 속성, 변신 형태, 종족(Draconian `4 + XL/3`, Naga `XL/3`), 돌연변이, 일시 효과(Protection 브랜드 +7 등).
- **부식(Corrosion)은 AC를 깎는다.** 부식 수치 1당 AC −1. 부식 상태, 슬라임 벽 근처, **Dis에 있는 동안 항상 −8**. (같은 수치가 무기 데미지에서도 빠진다 → [무기 문서](weapons.md#31-계산-순서))

### 2.2 몸통 방어구의 AC (Armour 스킬별)
인챈트 +0 기준.

| 몸통 방어구 | 기본 AC | Armour 0 | 10 | 20 | 27 |
|---|---|---|---|---|---|
| robe | 2 | 2.0 | 2.9 | 3.8 | 4.5 |
| animal skin | 2 | 2.0 | 2.9 | 3.8 | 4.5 |
| leather armour | 3 | 3.0 | 4.4 | 5.7 | 6.7 |
| troll leather armour | 3 | 3.0 | 4.4 | 5.7 | 6.7 |
| ring mail | 5 | 5.0 | 7.3 | 9.5 | 11.1 |
| scale mail | 6 | 6.0 | 8.7 | 11.5 | 13.4 |
| chain mail | 8 | 8.0 | 11.6 | 15.3 | 17.8 |
| plate armour | 10 | 10.0 | 14.5 | 19.1 | 22.3 |
| crystal plate armour | 14 | 14.0 | 20.4 | 26.7 | 31.2 |

드래곤 비늘은 [6절](#6-특수-몸통-방어구) 참고.

### 2.3 AC가 데미지를 줄이는 방식
몬스터의 근접 공격을 맞을 때:
1. **0 ~ AC 사이의 무작위 값**만큼 데미지를 깎는다.
2. **GDR(보장 감소, Guaranteed Damage Reduction)**: 깎이는 양은 최소 `min(GDR% × 그 공격의 최대 데미지, AC/2)`가 보장된다.
   - **GDR% = 16 × AC의 네제곱근**

| AC | 5 | 10 | 20 | 30 | 40 | 60 |
|---|---|---|---|---|---|---|
| GDR | 23% | 28% | 33% | 37% | 40% | 44% |

- GDR은 **몬스터의 무기·근접 공격과 무기·투척으로 쏘는 원거리 공격**에 적용된다. 마법, 브레스 같은 빔 공격에는 적용되지 않는다.
- 즉 AC가 높으면 "운이 나빠서 AC가 거의 안 먹히는" 경우가 줄어든다. 단 보장분은 AC의 절반을 넘지 않는다.

---

## 3. EV (Evasion)
### 3.1 계산
**EV = 몸집 기본값 + 회피 보너스(방어구 보정 후) − 몸통 방해도 페널티 − 방패 페널티 − 보조 방어구 페널티 + 기타**

1. **몸집 기본값** = `10 + 몸집 보정`. 몸집 보정은 Little +4, Small +2, Medium 0, Large −2.
   - **EV는 몸통이 아니라 전체 몸집 기준**이다. 장비 착용은 몸통 기준이라 Medium 취급인 Naga, Armataur도 EV 계산에서는 Large(−2)다.
2. **회피 보너스** = `(8 + 0.8 × Dodging 스킬 × Dex) / (20 − 몸집 보정)`
   - 예: Medium, Dodging 10, Dex 15 → (8 + 120)/20 = 6.4
3. **몸통 방어구에 의한 회피 보너스 감소**: 몸통 방어구의 ER(방해도)에서 3을 뺀 값을 P라 하면
   - P ≤ 0: 감소 없음
   - P < Str: 회피 보너스 × `(1 − P/(2×Str))`
   - P ≥ Str: 회피 보너스 × `Str/(2×P)`
   - 즉 **Str이 ER보다 충분히 높아야 무거운 갑옷을 입고도 회피가 유지된다.**
4. **몸통 방해도 페널티**(아래 [4.1](#41-몸통-방어구)) 만큼 EV를 뺀다.
5. **방패 페널티**(아래 [4.2](#42-방패)) 만큼 EV를 뺀다.
6. **보조 방어구 페널티**: barding처럼 자체 EV 페널티가 있는 보조 방어구는 그 값의 1/3 (barding −2).
7. **기타**: ring of evasion, 아티팩트 EV, 돌연변이, 변신 형태, 일시 효과.

### 3.2 상황 보정
| 상황 | EV 변화 |
|---|---|
| 보이지 않는 적에게 공격받음 | −10 |
| Vertigo | −5 |
| 조임(constricted) 당함 | −10 |
| 석화 중(Petrifying) 또는 그물에 걸림 | ×1/2 |
| 행동 불능 상태 또는 Tree 형태 | 매우 낮은 값으로 제한 |
| Agility, Devious, Acrobat 등 | 증가 |

### 3.3 EV 예시
조건: Medium 종족, **Dex 15, Str 15, Armour 스킬 0**, 방패 없음, 그 밖의 보너스 없음.

| 몸통 방어구 | Dodging 0 | 10 | 20 | 27 |
|---|---|---|---|---|
| robe | 10.4 | 16.4 | 22.4 | 26.6 |
| leather armour | 10.0 | 15.8 | 21.6 | 25.7 |
| scale mail | 8.1 | 12.7 | 17.3 | 20.5 |
| chain mail | 5.9 | 9.7 | 13.5 | 16.2 |
| plate armour | 3.0 | 6.0 | 9.0 | 11.1 |
| crystal plate armour | −1.6 | 0.6 | 2.9 | 4.5 |

---

## 4. 방해도 (Encumbrance)
### 4.1 몸통 방어구
- **ER(방해도)** = 몸통 방어구의 EV 페널티 수치 ÷ 10. 게임에서 "Encumbrance rating"으로 표시된다. (Sturdy Frame 돌연변이 1단계마다 −2)
- **조정된 방해도 페널티(aevp)** = `0.4 × ER² / (Str + 3) × (1 − Armour 스킬/45)`
  - Str이 높을수록, Armour 스킬이 높을수록 줄어든다. Armour 스킬 최대치 27에서도 0이 되지는 않는다(최대 60% 감소).

| 몸통 방어구 | ER | aevp: Str 10 | Str 15 | Str 20 | Str 15 + Armour 10 | Str 15 + Armour 20 |
|---|---|---|---|---|---|---|
| robe | 0 | 0 | 0 | 0 | 0 | 0 |
| leather armour | 4 | 0.5 | 0.4 | 0.3 | 0.3 | 0.2 |
| ring mail | 7 | 1.5 | 1.1 | 0.9 | 0.8 | 0.6 |
| scale mail | 10 | 3.1 | 2.2 | 1.7 | 1.7 | 1.2 |
| chain mail | 14 | 6.0 | 4.4 | 3.4 | 3.4 | 2.4 |
| plate armour | 18 | 10.0 | 7.2 | 5.6 | 5.6 | 4.0 |
| crystal plate armour | 23 | 16.3 | 11.8 | 9.2 | 9.1 | 6.5 |

**aevp가 영향을 주는 곳**
- **EV**: aevp만큼 감소 ([3.1](#31-계산)의 4번). 회피 보너스 감소(3번)는 이와 별도.
- **마법 실패율**: 실패율 계산의 내부값에 `aevp × 19`가 더해진다. 갑옷이 무거우면 실패율이 크게 오른다(자세한 실패율 공식은 마법 문서에서 다룰 예정).
- **원거리 무기 공격 속도**: aevp만큼 딜레이 증가(1 = 0.1턴). Archery 에고는 ER을 절반으로 계산.
- **근접 명중에는 영향 없음.** ([무기 문서 2.3](weapons.md#23-방어구는-근접-명중에-영향이-없다))

**ER 자체가 영향을 주는 곳**
- **은신(Stealth)**: `ER² × 2/3`만큼 감소. Armour 스킬과 Str로 줄지 않는다. (shadow dragon scales는 예외로 은신 감소가 없다)

### 4.2 방패
- 방패의 방해도 = 방패의 EV 페널티 수치 ÷ 10: buckler 5, kite shield 10, tower shield 15.
- **방패 페널티** = `2 × 방해도² / (25 + 5 × Str) × (1 − Shields 스킬/27)`
  - **Shields 스킬 27이면 0이 된다.**

| 방패 (Str 15) | Shields 0 | 10 | 20 |
|---|---|---|---|
| buckler | 0.5 | 0.3 | 0.1 |
| kite shield | 2.0 | 1.3 | 0.5 |
| tower shield | 4.5 | 2.8 | 1.2 |

**방패 페널티가 영향을 주는 곳**
- **EV**: 그만큼 감소
- **모든 공격 속도**: 그만큼 딜레이 증가(1 = 0.1턴). 근접·원거리·투척 모두
- **마법 실패율**: 내부값에 `방패 페널티 × 19`가 더해진다

---

## 5. SH와 막기 (Shields & Blocking)
### 5.1 방패의 SH
게임에 표시되는 SH 기준:

**SH = 기본SH/2 + 기본SH × Shields/40 + 인챈트 + 0.19 × Shields + 0.57 + Dex × 0.19 × (기본SH×2 + 13)/26**

(기본SH: buckler 3, kite shield 8, tower shield 13)

| 방패 (Dex 15, +0) | Shields 0 | 10 | 20 | 27 |
|---|---|---|---|---|
| buckler | 4.2 | 6.8 | 9.5 | 11.3 |
| kite shield | 7.7 | 11.6 | 15.5 | 18.3 |
| tower shield | 11.3 | 16.5 | 21.6 | 25.2 |

- **Dex가 SH를 꽤 올린다.** 큰 방패일수록 Dex 효과도 크다.
- 방패 외 SH 출처: Parrying 에고(+8), Rebuke 브랜드(+10), amulet of reflection, 아티팩트 SH 속성, 돌연변이 등.

### 5.2 막기 판정
몬스터의 근접·원거리 공격마다:
- **막는 쪽 값** = `random2avg(SH × 4, 2) / 3 − 1` (평균 약 SH × 2/3)
- **뚫는 쪽 값** = `random2(15 + 몬스터 HD × 2/3)`
- 막는 쪽 값 ≥ 뚫는 쪽 값이면 **막기 성공**(공격 무효).
- **보이지 않는 적의 공격**은 막는 쪽 값이 1/3.
- **턴당 막을 수 있는 횟수**: buckler 2회, kite shield 3회, tower shield 4회 (방패 없이 다른 SH만 있으면 1회). 횟수를 다 쓰면 그 턴에는 더 막지 못한다.
- 행동 불능 상태면 막을 수 없다.

### 5.3 막기 확률 예시

| 표시 SH | HD 5 | HD 10 | HD 15 | HD 20 | HD 25 |
|---|---|---|---|---|---|
| 5 | 16% | 14% | 11% | 10% | 9% |
| 10 | 34% | 29% | 25% | 22% | 20% |
| 15 | 53% | 45% | 38% | 34% | 31% |
| 20 | 68% | 60% | 51% | 46% | 41% |
| 25 | 79% | 72% | 63% | 57% | 52% |

(턴당 막기 횟수 제한은 반영하지 않은 1회 판정 기준)

---

## 6. 특수 몸통 방어구
| 방어구 | 기본 AC | ER | 고유 효과 |
|---|---|---|---|
| steam dragon scales | 5 | 0 | rSteam |
| acid dragon scales | 6 | 5 | rCorr |
| swamp dragon scales | 7 | 7 | rPois |
| fire dragon scales | 8 | 9 | **rF++, rC−** |
| quicksilver dragon scales | 9 | 7 | **Will+**, 인챈트 불가 |
| ice dragon scales | 9 | 11 | **rC++, rF−** |
| pearl dragon scales | 10 | 11 | rN+ |
| storm dragon scales | 10 | 15 | rElec |
| shadow dragon scales | 11 | 15 | 은신 증가, **ER에 의한 은신 감소 없음** |
| golden dragon scales | 12 | 23 | rF+, rC+, rPois |
| crystal plate armour | 14 | 23 | 가장 높은 AC |
| troll leather armour | 3 | 4 | **HP 재생 증가** |
| animal skin | 2 | 0 | 모든 몸집이 입을 수 있음 |

- 드래곤 비늘, troll leather armour, animal skin은 모든 몸집이 입을 수 있다.
- 드래곤 비늘의 에고는 고유 저항과 겹치거나 모순되는 것은 붙지 않는다(예: fire dragon scales에 rF 에고 없음).

---

## 7. 몬스터의 공격과 방어
몬스터가 플레이어를 근접 공격할 때의 순서다.

### 7.1 명중
- **몬스터 명중치** = `18 + HD × 1.5` (근접 전문 몬스터(fighter)는 `18 + HD × 2.5`) + 무기 명중·인챈트 + Slaying
- 플레이어가 보이지 않으면(투명 등) 명중치 −35%. 몬스터가 혼란 상태면 −5.
- 이번 공격의 명중치 = `random2(명중치 + 1)`
- **플레이어 EV도 무작위**: `random2avg(EV × 2, 2)` (평균은 EV)
- 명중치 ≥ EV 값이면 명중. 5%는 무조건 결정(2.5% 명중, 2.5% 빗나감).
- 명중하더라도 [막기 판정](#52-막기-판정)에 성공하면 무효.

### 7.2 피격 확률 예시 (일반 몬스터, 무기 보너스 없음)
막기 판정 전, 명중 판정만의 확률이다.

| HD \ EV | 5 | 10 | 15 | 20 | 30 | 40 |
|---|---|---|---|---|---|---|
| 5 | 81% | 63% | 45% | 30% | 15% | 10% |
| 10 | 85% | 71% | 57% | 43% | 24% | 15% |
| 15 | 87% | 75% | 64% | 52% | 32% | 20% |
| 20 | 89% | 79% | 69% | 60% | 41% | 27% |
| 25 | 90% | 81% | 73% | 64% | 47% | 33% |

근접 전문(fighter) 몬스터

| HD \ EV | 5 | 10 | 15 | 20 | 30 | 40 |
|---|---|---|---|---|---|---|
| 5 | 84% | 68% | 53% | 39% | 20% | 13% |
| 10 | 88% | 77% | 66% | 55% | 35% | 22% |
| 15 | 90% | 81% | 73% | 64% | 47% | 33% |
| 20 | 91% | 84% | 78% | 71% | 57% | 43% |
| 25 | 92% | 86% | 80% | 75% | 63% | 51% |

### 7.3 데미지
- **몬스터의 공격 데미지 수치**(몬스터 데이터의 damage)를 D, 무기 데미지를 W라 하면
  - 데미지 = `1 + random2(D)` + (무기가 있으면 `random2(W)` + 무기 인챈트·Slaying)
  - 몬스터 HD가 기본값과 다르면 D가 HD 비율만큼 조정된다(소환수 등).
- 그 뒤 [AC 감소와 GDR](#23-ac가-데미지를-줄이는-방식)이 적용된다. GDR의 "최대 데미지"는 `W + D`.

---

## 8. 전체 방어구 수치표

| 방어구 | 슬롯 | 기본 AC(방패는 SH) | ER / EV 페널티 | 입을 수 있는 몸집 |
|---|---|---|---|---|
| robe | 몸통 | 2 | 0 | Little ~ Large |
| animal skin | 몸통 | 2 | 0 | 전부 |
| leather armour | 몸통 | 3 | 4 | Small ~ Medium |
| troll leather armour | 몸통 | 3 | 4 | 전부 |
| ring mail | 몸통 | 5 | 7 | Small ~ Medium |
| scale mail | 몸통 | 6 | 10 | Small ~ Medium |
| chain mail | 몸통 | 8 | 14 | Small ~ Medium |
| plate armour | 몸통 | 10 | 18 | Small ~ Medium |
| crystal plate armour | 몸통 | 14 | 23 | Small ~ Medium |
| 드래곤 비늘 | 몸통 | 5~12 | 0~23 | 전부 ([6절](#6-특수-몸통-방어구)) |
| cloak | 망토 | 1 | — | — |
| scarf | 망토 | 0 | — | — |
| helmet | 머리 | 1 | — | [1.2](#12-단단한-투구helmet) 참고 |
| hat | 머리 | 0 | — | — |
| gloves | 손 | 1 | — | — |
| boots | 발 | 1 | — | — |
| barding | 발 | 4 | EV −2 | — |
| buckler | 보조손 | SH 3 | 방해도 5 | Little ~ Medium |
| kite shield | 보조손 | SH 8 | 방해도 10 | Small ~ Large |
| tower shield | 보조손 | SH 13 | 방해도 15 | Medium 이상 |
| orb | 보조손 | 0 | 0 | 전부 (항상 에고가 붙음) |

- 인챈트 상한은 [아이템 개요](index.md#스크롤로-올릴-수-있는-상한) 참고 (몸통은 기본 AC까지, 보조 장비 +2, 방패 +3/+5/+8).

## 9. 생성 (간략)
- 바닥 무작위 생성에서 보조 장비는 에고 판정이 한 번 더 있어서 에고가 비교적 흔하다. → [아이템 개요](index.md#아이템-생성-간략)
- 에고별로 붙는 부위는 [브랜드·에고](brands-egos.md#에고-목록) 참고.
- 바닥 무작위 생성에서 부츠는 1/8 확률로 barding이 된다(barding을 입는 종족이 아니어도). 랜덤 아티팩트 부츠는 1/20.

> 출처: item-prop.cc, player.cc, player-equip.cc, actor.cc, attack.cc, fight.cc, melee-attack.cc, spl-cast.cc, makeitem.cc, species.cc (0.34.1)
