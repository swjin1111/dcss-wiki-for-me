# 브랜드·에고 (Brands & Egos)

> 기준: DCSS 0.34.1 · [아이템 목록으로](index.md)

무기에 붙는 특수 효과를 **브랜드(brand)**, 방어구에 붙는 특수 효과를 **에고(ego)**라고 부른다. 일반 아이템에는 최대 하나가 붙는다. 아티팩트의 브랜드·속성은 [아티팩트 속성](artefact-properties.md) 문서를 참고.

## 브랜드·에고 아이템이 나오는 경로
같은 브랜드·에고라도 **어떤 경로로 생성되느냐에 따라 붙을 수 있는 장비가 다르다.** 이 문서의 "바닥 무작위 생성" 표기는 아래 1번만 가리킨다.

| 경로 | 설명 | 코드 위치 |
|---|---|---|
| 1. 바닥 무작위 생성 | 층에 무작위로 떨어지는 일반 아이템. 무기·방어구 종류별 가중치 표를 따른다 | `makeitem.cc`, `item-prop.cc` |
| 2. 몬스터 장비 | 몬스터가 들고 나오는 장비. 몬스터마다 무기 종류와 브랜드가 따로 정해져 있다. 죽이면 떨어뜨린다 | `mon-gear.cc` |
| 3. 볼트 지정 아이템 | 특정 볼트·포털(Wizard's Laboratory, Trove, Necropolis 등)이 "이 장비에 이 에고"처럼 직접 지정해서 놓는 아이템 | `dat/des/*.des` |
| 4. 아티팩트·획득·신의 선물 | 랜덤 아티팩트, Scroll of Acquirement, 신의 선물은 각자 별도의 규칙을 쓴다 | `artefact.cc`, `acquire.cc` 등 |

예를 들어 Spectral 브랜드는 바닥 무작위 생성으로는 Club·Quarterstaff·Lajatang에만 붙지만, 다른 경로로는 이렇게도 나온다.
- 몬스터 장비: **Asterion**은 demon whip / demon blade / demon trident / morningstar / broad axe 중 하나를 **항상 Spectral로** 들고 나온다. Spriggan druid의 quarterstaff, Killer Klown의 club도 Spectral일 수 있다.
- 볼트 지정: "great sword ego:spectral", "any weapon ego:spectral"처럼 다른 무기에 Spectral을 지정한 볼트가 있다.
- 랜덤 아티팩트: 근접 무기 brand 표에 Spectral이 있어서 계열과 상관없이 붙을 수 있다.

이 문서에서 **"관통 데미지"**는 대상의 AC로 줄어든 뒤 실제로 들어간 데미지를 말한다. 상당수 브랜드는 이 값을 기준으로 추가 데미지를 계산한다.

---

## 무기 브랜드

### 요약

| 브랜드 | 효과 (요약) | 바닥 무작위 생성 시 붙는 무기 |
|---|---|---|
| [Flaming](#flaming--freezing) | 관통 데미지의 약 1/4 Fire 추가 | 대부분 (Mace·Flail 등 기본 M&F, Staves 제외) |
| [Freezing](#flaming--freezing) | 관통 데미지의 약 1/4 Cold 추가, 냉혈 생물 감속 | 대부분 (Mace·Flail 등 기본 M&F, Staves 제외) |
| [Electrocution](#electrocution) | 25% 확률로 8~20 Elec 추가 | Blades·Axes·Whip·Lajatang·원거리 (M&F·Polearms·Quarterstaff 제외) |
| [Venom](#venom) | 75% 확률로 독 | 근접 대부분 |
| [Draining](#draining) | 생물에게 50% 확률로 추가 데미지 + Drain | 대부분 |
| [Vampirism](#vampirism) | 60% 확률로 HP 흡수 | 근접 대부분 |
| [Holy Wrath](#holy-wrath) | 언데드·악마에게 관통 데미지의 최대 1.5배 추가 | 근접 대부분 |
| [Pain](#pain) | Necromancy 스킬 비례 추가 데미지 | 근접 대부분 |
| [Protection](#protection) | 적중 후 AC +7 | Short Blades·M&F·Long Blades·Polearms(spear 제외) |
| [Speed](#speed--heavy) | 공격 속도 ×2/3 | Short Blades(quick blade 제외)·Quarterstaff·Lajatang |
| [Heavy](#speed--heavy) | 기본 데미지 ×1.8, 공격 속도 ×1.5 | M&F·Long Blades·Axes·Polearms·Quarterstaff·원거리 |
| [Antimagic](#antimagic) | 몬스터 주문 방해, 착용자 최대 MP 1/3 | 거의 전부 (낮은 확률) |
| [Distortion](#distortion) | 추가 데미지·블링크·추방 | 근접 거의 전부 (낮은 확률) |
| [Chaos](#chaos) | 매 타격 무작위 브랜드 | 없음 (아티팩트·몬스터 장비·볼트로만) |
| [Devious](#무기-계열-특수-브랜드) | 암습 강화 | Short Blades |
| [Valour](#무기-계열-특수-브랜드) | HP 80% 초과 시 에너지 빔 | Long Blades |
| [Concussion](#무기-계열-특수-브랜드) | 넉백 | Maces & Flails |
| [Sundering](#무기-계열-특수-브랜드) | 연속 공격 후 강타 | Axes |
| [Entangling](#무기-계열-특수-브랜드) | 덩굴로 조이기 | Polearms |
| [Rebuke](#무기-계열-특수-브랜드) | 근접 공격 후 SH +10 | Staves |
| [Spectral](#무기-계열-특수-브랜드) | 영체 무기의 추가 공격 | Club·Staves |
| [Reaping](#그-밖의-브랜드) | 처치한 적을 아군 영체로 부활 | 없음 (아티팩트·볼트로만) |
| [Penetration](#그-밖의-브랜드) | 탄환 관통 | 없음 (아티팩트 크로스보우 등) |
| [Acid / Foul Flame](#그-밖의-브랜드) | — | 없음 (언랜드 전용) |

- 이 열은 [경로 1](#브랜드에고-아이템이-나오는-경로)만 기준이다. 몬스터 장비·볼트·아티팩트로는 다른 무기에도 붙을 수 있다.
- 무기 계열별 정확한 생성 가중치는 무기 문서(예정)에 정리한다.
- 아래의 확률·데미지는 플레이어가 공격할 때 기준이다.

### 브랜드 공통 규칙
- **관통 데미지가 0이면 발동하지 않는 브랜드**: Flaming, Freezing, Holy Wrath, Foul Flame, Antimagic, Vampirism.
- **대상이 이 공격으로 죽으면 대부분의 브랜드는 발동하지 않는다.** 예외는 Flaming, Freezing, Electrocution, Vampirism, Protection.
- 원거리 무기의 브랜드는 쏜 탄에 적용된다.

### Flaming / Freezing
- **추가 데미지**: `random2(관통 데미지)/2 + 1`. 평균 관통 데미지의 약 1/4. 해당 저항(rF/rC)으로 줄어든다.
- **Freezing**: 냉혈(cold-blooded) 생물이 rC가 없으면 50% 확률로 잠시 Slow.
- 얼음 생물이라고 따로 배율이 붙지는 않는다. 대상이 rF−·rC−(취약)이면 저항 규칙대로 1.5배.

### Electrocution
- **25% 확률**로 **8~20** Electricity 데미지 추가.
- **rElec가 조금이라도 있으면 완전히 무효.**
- 관통 데미지가 0이어도 발동한다(명중만 하면 된다).

### Venom
- **75% 확률**로 독을 건다. 독의 양은 `6 + random2(8) + random2(관통 데미지 × 1.5)`.
- 독 저항에 따른 처리는 독 상태이상 규칙을 따른다.

### Draining
- **몬스터에게는 50% 확률**로 발동. **Natural(생물)·Plant 대상에게만** 작동한다.
- 효과:
  - 추가 Negative energy 데미지 `(1 + random2(관통 데미지))/2` (rN으로 감소)
  - 고정 데미지 2~4
  - **Drained** 상태 (몬스터의 HD가 일시적으로 낮아진다. rN이 있으면 지속시간 감소)
- rN 3단계 대상은 면역.

### Vampirism
- 조건: 무기 사용, 관통 데미지 1 이상, 대상이 흡혈 가능한 생물, **시전자의 HP가 가득 차 있지 않을 것**, Death's Door 상태가 아닐 것.
- 조건을 만족하면 **60% 확률**로 `1 + random2(관통 데미지)`만큼 HP 회복. 대상의 rN에 따라 줄어든다.

### Holy Wrath
- **언데드와 악마**에게 `1 + random2(관통 데미지 × 1.5)` 추가 데미지.
- 사용자가 언데드나 악마면 효과가 없다.
- TSO가 축복한 무기(Eudemon Blade, Sacred Scourge, Trishula)는 항상 Holy Wrath.

### Pain
- 발동 확률 약 `N/(N+1)` (N = Necromancy 스킬 레벨, 정수). 스킬 0이면 발동하지 않는다.
- 추가 데미지 `random2(1 + N)`, rN으로 감소.
- **Trog 신자는 발동하지 않는다.**

### Protection
- 적을 맞히면(장애물형 몬스터 제외) **AC +7**, 지속 3~4턴(최대 5턴까지 누적).

### Speed / Heavy
- **Speed**: 공격 딜레이 ×2/3.
- **Heavy**: 무기 기본 데미지 ×1.8, 공격 딜레이 ×1.5.
- 둘 다 최소 공격 딜레이(무기 스킬로 줄이는 한계) 계산에도 반영된다. 어떤 경우에도 공격 딜레이는 3(약 0.3턴)보다 빨라지지 않는다.

### Antimagic
- **착용자의 최대 MP가 1/3로 줄어든다.**
- 맞은 몬스터는 Antimagic 상태가 된다. 지속은 `random2(관통 데미지 × 8 / 대상 HD + 1)`턴.
- Antimagic 상태 몬스터의 주문(마법성 주문) 실패 확률은 `남은 지속 / (남은 지속 + 4턴)`. 예: 4턴 남으면 50%.
- 자연 능력·신성 능력은 막지 못한다.

### Distortion
타격마다 아래 중 하나가 일어난다.

| 결과 | 확률 | 내용 |
|---|---|---|
| 작은 추가 데미지 | 35% | 1~7 |
| 큰 추가 데미지 | 25% | 3~26 |
| 블링크 | 20% | 대상을 무작위로 순간이동 (순간이동 불가 대상 제외) |
| 효과 없음 | 15% | |
| 추방 | 5% | 대상을 Abyss로 추방 |

- **장비를 해제할 때 플레이어가 적 근처로 순간이동하거나 Abyss로 추방될 수 있다.**

### Chaos
- **바닥 무작위 생성 무기에는 붙지 않는다.** 랜덤 아티팩트·언랜드, 일부 몬스터 장비(Crazy Yiuf의 quarterstaff, Kobold fleshcrafter, Killer Klown 등), 볼트 지정 아이템으로 나온다.
- 타격마다 대상에게 통하는 브랜드 중 하나를 무작위로 고른다.

| 선택 | 가중치 |
|---|---|
| Flaming / Freezing / Electrocution / Venom | 각 10 |
| Chaos 고유 효과 (무작위 마법 효과) | 13 |
| Draining / Vampirism / Holy Wrath / Antimagic | 각 5 |
| Foul Flame | 2 |

- 1% 확률로 그 타격에 Reaping 효과가 붙는다.
- **Zin 등 혼돈을 싫어하는 신의 행위 규정에 걸린다.**

### 무기 계열 특수 브랜드
무기 계열마다 하나씩 짝지어진 브랜드다. "짝지어졌다"는 건 두 가지 의미다.
- **바닥 무작위 생성**에서는 그 계열 무기에만 붙는다.
- **랜덤 아티팩트**가 brand 표에서 "특수 브랜드" 칸을 뽑으면 그 무기 계열에 짝지어진 것이 붙는다.

즉 다른 계열에 붙는 것이 규칙상 불가능한 건 아니다. 볼트 지정 아이템이나 몬스터 장비로는 다른 무기에 붙어서 나올 수 있다(위의 Spectral 예시).

| 브랜드 | 계열 | 효과 |
|---|---|---|
| **Devious** | Short Blades | 확정이 아닌 암습(혼란·한눈 판 대상 등)의 성공 판정에 +10. 암습에 성공하면 **5~9턴 동안 EV +4, Slaying +3** (최대 3중첩). |
| **Valour** | Long Blades | **HP가 최대치의 80%를 넘을 때** 적을 맞히면 대상 뒤로 에너지 빔(사거리 4)이 나간다. 빔 데미지 `4d(무기 기본 데미지 × 2/3)`, 명중 20. 아군·장애물형 몬스터를 때릴 때는 나가지 않는다. **해제하면 잠시 Weak.** |
| **Concussion** | Maces & Flails | 맞은 적을 1칸 밀쳐 잠시 경직시킨다. 뒤가 벽이라 밀리지 않으면 대신 `random2(관통 데미지) × 3/4 + 1` 추가 데미지. 밀어낸 뒤 플레이어가 따라 들어간다. |
| **Sundering** | Axes | 공격을 **5번 연속**(중간에 공격 이외의 행동을 하면 초기화) 하면 다음 공격이 **명중 +12, 데미지 +200%**(3배)가 되고, 휩쓸기(cleave) 범위가 1칸 더 넓어진다. |
| **Entangling** | Polearms | 50% 확률로 덩굴로 대상을 조인다(constrict, 2~4 데미지). |
| **Rebuke** | Staves | 직전 행동이 근접 공격이면 **SH +10**. 막아낸 근접 공격을 근처의 다른 적에게 돌려보낸다. |
| **Spectral** | Club, Quarterstaff, Lajatang | 공격하면 무기의 영체가 나와 약간 약한 추가 공격을 한다. 영체가 받는 데미지 일부를 플레이어가 나눠 받는다. |

### 그 밖의 브랜드
- **Reaping**: 바닥 무작위 생성 없음. 랜덤 아티팩트나 볼트 지정 아이템으로 나온다. 생물·신성·악마 적이 죽을 때 `(Reaping으로 준 데미지) / (받은 총 데미지 × 1.5)` 확률로 아군 영체(spectral)로 되살아난다. 혼자 다 때려 잡으면 약 67%.
- **Penetration**: 랜덤 아티팩트 크로스보우(1/6 확률)로만 생성. 탄이 대상을 뚫고 계속 날아간다.
- **Acid**: 언랜드 전용. 2d4 Acid 데미지 + Corrosion.
- **Foul Flame**: 언랜드 전용. 관통 데미지 기준으로 신성 생물에게 최대 1.5배, 그 밖의 대상에게 대상의 저항에 따라 추가 데미지. 신성한 존재나 선한 신 신자는 사용할 수 없다.

---

## 방어구 에고

### 공통: 마법 강화(enhancer)
Fire/Ice/Air/Earth 에고, Archmagi, 지팡이 등은 해당 마법의 **강화 단계를 +1** 올린다.
- 강화 1단계마다 **Spell power ×1.5**. 합계는 최대 3단계.
- 반대로 약화 단계는 단계마다 Spell power ÷2.

### 에고 목록
"생성 부위"는 [경로 1(바닥 무작위 생성)](#브랜드에고-아이템이-나오는-경로)에서 그 에고가 붙을 수 있는 장비다. 볼트 지정 아이템, 몬스터 장비, 아티팩트는 다를 수 있다.

#### 저항·방어
| 에고 | 효과 | 생성 부위 |
|---|---|---|
| Fire Resistance (rF+) | 화염 저항 +1 | 몸통(robe 포함), barding, 방패 |
| Cold Resistance (rC+) | 냉기 저항 +1 | 몸통(robe 포함), barding, 방패 |
| Resistance | rF+, rC+ 둘 다 | robe, scarf, buckler |
| Poison Resistance (rPois) | 독 저항 | 몸통(robe 제외), cloak, 방패 |
| Positive Energy (rN+) | 음에너지 저항 +1 | robe, leather·ring·scale mail, 방패 |
| Willpower (Will+) | Willpower +1단계(40) | 몸통, cloak, hat |
| Corrosion Resistance (rCorr) | 산·부식 저항 | cloak, kite shield, tower shield |
| Protection (AC+3) | AC +3 | 방패 |
| Reflection | 막아낸 투사체를 반사 | 방패 |
| Repulsion | 투사체에 대한 EV +15 | scarf |
| See Invisible (SInv) | 투명 감지 | hat |

#### 능력치·전투
| 에고 | 효과 | 생성 부위 |
|---|---|---|
| Strength / Dexterity / Intelligence | 해당 능력치 +3 | Str·Dex: gloves / Int: helmet, hat |
| Stealth | 은신 +1단계(50) | cloak, gloves, hat, boots, barding |
| Hurling | 투척 무기 Slaying +4 | gloves |
| Parrying | 직전 행동이 근접 공격이면 **SH +8**. 보조손에 무기가 아닌 것을 들고 있으면 절반 | gloves |
| Infusion | 근접 타격마다 MP 1을 써서 데미지 추가 | gloves |
| Archery | 원거리 공격 시 방해도 절반 | scale·chain·plate |
| Sniping | 무력화된 대상(수면·마비·석화·혼란·그물)에게 원거리·투척 데미지 +50% | helmet, hat |
| Rampaging | 적을 향해 이동할 때 한 칸 더 이동, 그 이동으로 공격하면 대상을 잠시 기절 | boots |
| Harm | **주는 데미지 +30%, 받는 데미지 +20%** (2개면 +45% / +30%) | scarf |

#### 이동·시야
| 에고 | 효과 | 생성 부위 |
|---|---|---|
| Flying | 비행 | boots, barding |
| Ponderousness | 이동이 느려짐(단점). 대신 인챈트가 +3~10 더 붙어 생성 | chain·plate, tower shield |
| Invisibility | 발동하면 일시 투명. 사용 시 최대 HP 감소 | scarf |
| Shadows | 시야 −1, 적에게 보이는 거리 감소 | scarf |
| Light | 주변을 밝혀 투명체를 드러내고, 범위 안의 대상(자신 제외)에 대한 명중 증가, 은신 감소 | helmet |

#### 마법 강화
| 에고 | 효과 | 생성 부위 |
|---|---|---|
| Fire | Fire 마법 강화 +1 | gloves |
| Ice | Ice 마법 강화 +1 | helmet, hat |
| Air | Air 마법 강화 +1 | cloak |
| Earth | Earth 마법 강화 +1 | boots, barding |
| Death | Necromancy 강화·실패율 감소, 다른 마법은 HP 소모 | scale·chain·plate |
| Command | Summoning 강화, Armour 스킬 비례 | scale·chain·plate |
| Resonance | Forgecraft 실패율 감소, Forgecraft 스킬 비례 근접 데미지 증가 | scale·chain·plate |
| Archmagi | 모든 마법 강화 +1 | **없음** (아래 참고) |

#### 오브(Orb) 전용
오브는 항상 에고가 붙는다.

| 에고 | 효과 |
|---|---|
| Energy | 주문 MP를 돌려받을 수 있지만 실패율 증가. Evocations 스킬로 확률 상승 |
| Attunement | 지팡이와 함께 쓰면 그 지팡이의 강화를 2배로, 그 지팡이로 근접 공격 시 MP 소량 회복 |
| Glass | 피해를 준 적을 Vitrify(유리화)해서 받는 피해를 늘림 |
| Guile | 자신과 내가 주술을 거는 대상 모두의 Willpower 감소 |
| Mayhem | 내가 적을 죽이는 걸 본 적들이 광란(frenzy) |
| Mesmerism | 근접 공격을 받으면 주변 적을 Daze, 이후 가만히 있으며 재충전 |
| Pyromania | Fire 마법 강화 +1, 공격 외의 방법으로 적을 죽이면 화염 폭발 |
| Stardust | 전투 중 처음 MP를 쓸 때 유성 공격, MP가 회복되고 적이 없을 때 재충전 |

(Orb의 Light 에고는 바닥 무작위 생성 가중치에 없다.)

### 바닥 무작위 생성으로는 나오지 않는 에고
- **Archmagi, Spirit Shield, Rage**: 방어구 종류별 에고 가중치 표에 없다.
- **Archmagi가 나오는 경로 (0.34.1 기준)**
  - 볼트 지정 아이템: Wizard's Laboratory, Trove, Necropolis 포털에 "robe ego:archmagi"가 지정된 경우가 있다.
  - 랜덤 아티팩트 로브의 Archmagi 속성 (가중치 40, 로브에만).
  - **몬스터 장비로는 나오지 않는다.** 몬스터에게 로브를 줄 때도 바닥 생성과 같은 에고 표를 쓰고, 몬스터 장비 코드에 Archmagi를 직접 지정하는 곳이 없다.
- Spirit Shield: 받는 데미지를 HP와 MP로 나눠 받는다.
- Rage: 근접 공격 시 20% 확률로 광폭화.

---

## 투척 브랜드

| 브랜드 | 대상 | 효과 | 생성 |
|---|---|---|---|
| Poisoned | Dart | 관통 데미지만큼 독 | Dart, 초반에 흔함 |
| Curare | Dart | 질식: 직접 데미지 + 독 + 감속. 맞으면 2배 확률로 부서짐 | Dart, 깊을수록 흔함 |
| Atropa (Blinding) | Dart | 실명(관통 데미지 턴) + 짧은 혼란 | Dart |
| Datura (Frenzy) | Dart | 대상이 광란해 아군·적을 가리지 않고 공격 | Dart |
| Disjunction | Dart | 3~4턴 동안 반복 블링크, 블링크마다 소량 데미지 | Dart |
| Silver | Javelin | 추가 데미지, 혼돈·변신 존재와 돌연변이 수에 비례해 더 큰 피해 | Javelin, 깊을수록 흔함 |
| Dispersal | Dart | 대상을 멀리 블링크 | 바닥 무작위 생성 없음 |
| Chaos | Boomerang·Javelin | 무작위 효과 | 바닥 무작위 생성 없음 |

- **Dart는 항상 브랜드가 붙어서 나온다.** Stone, Large Rock, Throwing Net은 브랜드가 없다.
- **Atropa·Datura의 성공 판정**: `2 + random2(4 + P)`가 대상 HD 이상이면 성공. P = (Throwing + Stealth 스킬) × 2/3.
  - HD 15 미만 대상에게는 별도로 약 3%의 자동 성공 확률이 있다.

> 출처: item-prop.cc, item-prop-enum.h, attack.cc, melee-attack.cc, fight.cc, monster.cc, mon-death.cc, mon-cast.cc, player.cc, player-reacts.cc, actor.cc, ouch.cc, spl-cast.cc, makeitem.cc, artefact.cc, ranged-attack.cc, zap-data.h, dat/descript/egos.txt (0.34.1)
