# 완드·발동 아이템 (Wands & Evokers)

> 기준: DCSS 0.34.1 · [아이템 목록으로](index.md)

완드(wand)와 경험치로 재충전되는 발동 아이템(XP evoker, miscellaneous)의 효과·수치, 위력 공식, 충전 규칙, 생성 규칙을 정리한다. 둘 다 Evocations 스킬을 쓰고 `V`(evoke)로 사용한다. 지속 시간은 **턴**(10 aut = 1턴) 단위다.

ziggurat figurine, shop voucher, flux bauble, gizmo는 [특수 아이템](special-items.md)에서 다룬다.

---

## 1. 공통 규칙

### 1.1 사용할 수 없는 경우
- **Berserk, Confusion** 상태에서는 완드·발동 아이템을 쓸 수 없다.
- Ru의 Sacrifice Artifice(`MUT_NO_ARTIFICE`)를 하면 쓸 수 없다(ziggurat figurine, flux bauble 제외).
- 아군을 가질 수 없는 경우(`allies_forbidden`)에는 아군을 만드는 아이템(wand of charming, phantom mirror, horn of Geryon, box of beasts, sack of spiders)을 쓸 수 없다.
- 사용은 행동 1회. 대상 선택을 취소하면 턴과 충전이 소모되지 않는다.

### 1.2 Evocations 스킬 훈련
- 완드를 한 번 쓰면 Evocations 연습 1, 발동 아이템은 아이템에 따라 1 또는 3(phial of floods, gravitambourine, horn of Geryon은 3).

---

## 2. 완드 (Wands)

### 2.1 위력 공식
완드는 지정된 주문을 다음 위력으로 시전한다(`evoke.cc` `wand_power`).

**위력 = (15 + Evocations × 3.5) × (MP 소모 + 9) / 9**, 그다음 gloves of the gadgeteer ×1.3, 마지막으로 그 주문의 **Power cap(위력 상한)** 적용.

| Evocations | 0 | 5 | 10 | 15 | 20 | 27 |
|---|---|---|---|---|---|---|
| 위력 | 15 | 32 | 50 | 67 | 85 | 109 |
| gadgeteer 착용 | 19 | 41 | 65 | 87 | 110 | 141 |

- **MP 소모**: `MUT_MP_WANDS`(좋은 돌연변이) 1단계당 3 MP를 써서 위력 ×(3+9)/9 = **×4/3**. MP가 부족하면 가진 만큼만 쓴다. Djinni는 MP 대신 HP를 쓴다(HP 1은 남김). 취소·실패하면 MP를 돌려받는다.
- 위력은 Spell power처럼 실패율이 없다. 완드는 항상 발동한다.
- 완드에 담긴 주문은 위 위력만 쓰고, 플레이어의 마법 스킬·Intelligence·마법 강화(enhancer)는 반영되지 않는다.

### 2.2 충전 (Charges)
- 완드는 충전 수만큼 쓸 수 있고, **0이 되면 부서진다.** 재충전 수단은 없다(scroll of recharging은 삭제됨).
- **같은 종류의 완드를 주우면 충전이 합쳐진다**(상한 없음).
- **충전 보존**: gloves of the gadgeteer나 Coglin의 gadgeteer gizmo가 있으면 사용할 때 **30% 확률로 충전이 줄지 않는다.**
- 생성 시 충전 = `1 + random2avg(최대값, 2)`. 최대값은 종류와 깊이에 따라 다르다(깊을수록 적다):

| 완드 | 아이템 레벨 7 이하 | 아이템 레벨 8 이상 |
|---|---|---|
| flame | 32 | 16 |
| mindburst | 24 | 12 |
| digging | 9 | 9 |
| 그 밖의 완드 | 15 | 8 |

### 2.3 완드 목록

| 완드 | 주문 | Power cap | 사거리 | 생성 가중치 |
|---|---|---|---|---|
| [flame](#flame) | Throw Flame | **50** | 7 | 14 (20%) |
| [paralysis](#paralysis--charming) / [charming](#paralysis--charming) | Paralyse / Charm | 200 | 7 | 14 (hex 세트) |
| [iceblast](#iceblast) / [roots](#roots) / [warping](#warping) | Iceblast / Fastroot / Warp Space | 200 | 5 | 14 (blast 세트) |
| [acid](#acid--light) / [light](#acid--light) / [quicksilver](#quicksilver) | Corrosive Bolt / Bolt of Light / Quicksilver Bolt | 200 | 5 / 5 / 7 | 9 (beam 세트) |
| [polymorph](#polymorph) | Polymorph | 200 | 7 | 7 (10%) |
| [mindburst](#mindburst) | Mindburst | 200 | 7 | 7 (10%) |
| [digging](#digging) | Dig | 200 | 7 | 5 (7%) |

- 같은 칸의 완드들은 [아이템 세트](scrolls.md#11-아이템-세트-item-set)로 묶여 있어서 **한 게임에 세트당 한 종류만** 생성된다(hex: paralysis/charming, beam: acid/light/quicksilver, blast: iceblast/roots/warping).
- 아래 피해 공식에서 `p`는 위력. "AdB 합계 최대 N"은 N을 A개의 주사위로 나눈 것(`calc_dice`)이다.
- 삭제된 완드(생성 안 됨): frost, slowing, hasting, magic darts, heal wounds, fire, cold, confusion, invisibility, teleportation, lightning, random effects, clouds, scattershot.

#### flame
- **Throw Flame**: 화염 볼트 1발, 피해 **2d(4 + p/10)**, 명중 `8 + p/10`. 관통하지 않는다.
- **Power cap 50**: Evocations 10 이상이면 더 강해지지 않는다(최대 2d9).

#### paralysis / charming
- Willpower 판정(위력 = 완드 위력)에 실패하면 효과.
- **Paralyse**: 마비 지속 `stepdown(p×10, 70)`의 0.5~1.5배(aut). 평균 약 위력 15 → 11.6턴, 50 → 21턴, 109 → 28턴. 이미 마비됐거나 Stasis인 몬스터는 무효.
- **Charm**: 몬스터를 일시적으로 아군으로 만든다. 지속은 보통 속도 몬스터 기준 약 `500 / (HD + 10)`턴(무작위 보정). 아군·이미 같은 편인 몬스터에게는 무효.

#### iceblast
- **얼음 폭발**: 목표 지점에서 반경 1 폭발, 피해 **3d, 합계 최대 `14 + 3p/5`**(위력 50 → 44, 200 → 134). 폭발이라 명중 판정이 사실상 없다(명중 40).
- 피해의 **50%만 rC로 저항**된다(나머지는 물리 충격, AC 적용).

#### roots
- **Fastroot**: 목표 지점 반경 1 폭발 범위의 적을 **뿌리로 조인다(constriction)**. Willpower 판정 없음. 아군, 이미 조여진 대상, 조임 면역(`res_constrict`), 단단한 바닥이 아닌 칸(깊은 물·용암 등)에 있는 대상은 무효.
  - 지속 `3 + random_range(p/22, p/16 + 1)`턴.
  - 조이는 동안 매 턴 피해 **2d((25 + p)/7)**(위력 15 → 2d6, 200 → 2d32).
  - 몬스터가 벗어나기: 시도마다 `(5 + HD + 시도횟수² × 5) / (50 + p/2)` 확률.

#### warping
- **Warp Space**: 목표 지점 반경 1 폭발, 피해 **3d, 합계 최대 `12 + 3p/5`**. 맞은 몬스터는 **`min(90, 35 + p)`% 확률로 무작위 근거리 Blink**된다.

#### acid / light
둘 다 **관통하는 볼트**(경로상의 모든 대상), 피해 **4d, 합계 최대 `13 + 3p/5`**, 명중 `10 + p/25`.
- **Corrosive Bolt (acid)**: 맞은 몬스터는 2/3 확률로 Corrosion(부식)에 걸린다. 산성 저항으로 피해가 줄어든다.
- **Bolt of Light (light)**: Blind 저항이 1단계 이하이고 이미 실명이 아닌 몬스터를 **실명**시킨다. 실명 지속 `max(1, 54/HD)`턴의 1~2배.

#### quicksilver
- **Quicksilver Bolt**: 관통 볼트, 피해 **6d, 합계 최대 `15 + 2p/3`**, 명중 `10 + p/25`. 피해 종류는 저항 불가 마법 피해.
- **맞은 몬스터의 해제 가능한 마법 효과를 모두 없앤다**(debuff: haste, might, 투명 등).

#### polymorph
- Willpower 판정에 실패하면 몬스터를 **무작위 다른 몬스터로 변신**시킨다.
- Zin이 싫어하는 chaotic 행위다(DID_DELIBERATE_MUTATING conduct). 완드 자체가 Zin이 싫어하는 아이템이다.

#### mindburst
- 보이지 않는 정신 공격 빔. **Willpower 판정**에 쓰는 위력은 **완드 위력 × 2.5**(위력 50 → 125)라 통하기 쉽다.
- 판정에 실패하면 피해 **3d, 합계 최대 `15 + 3p/4`**(위력 50 → 52, 200 → 165). 피해 종류는 저항 불가.
- **지능이 없는(brainless) 몬스터에게는 무효.**
- 소음 6.

#### digging
- 직선 경로상의 **파낼 수 있는 벽**을 사거리 7까지 없앤다. 파낼 수 있는 것: rock wall, clear rock wall, slimy wall, frigid wall, iron grate, orcish idol, granite statue, petrified tree. 돌벽(stone)·금속벽·영구벽 등은 파낼 수 없다.
- 위력은 효과와 무관하다. 소음 4.

### 2.4 몬스터와 완드
- 몬스터도 완드를 주워서 쓴다(digging은 공격용이 아니지만 사용함).
- 아이템 레벨 2 미만(D:1~2)에서 생성된 고급 완드(charming, paralysis, acid, light, quicksilver, iceblast, roots, mindburst)는 몬스터가 줍지 않는다.

---

## 3. 발동 아이템 (XP Evokers)

### 3.1 충전 규칙
발동 아이템은 소모되지 않고, **쓸 때마다 "경험치 빚(debt)"이 쌓이며 경험치를 얻으면 빚이 줄어 다시 충전된다.**

| 아이템 | 최대 충전 | 1회 사용당 빚 |
|---|---|---|
| phial of floods | 1 | 10 |
| horn of Geryon | 1 | 10 |
| **lightning rod** | **4** | **3** |
| tin of tremorstones | 2 | 10 |
| phantom mirror | 1 | 10 |
| box of beasts | 1 | 10 |
| sack of spiders | 1 | 10 |
| condenser vane | 1 | 10 |
| gravitambourine | 2 | 10 |

- **남은 충전 = 최대 충전 − ⌈빚 / 1회 빚⌉.**
- 경험치 `E`를 얻을 때마다 빚이 `E / plus_factor`만큼 줄어든다(인벤토리에 있는 것만).
  - `xp_factor = max(현재 레벨→다음 레벨 필요 경험치 / 5, 100) / (3 + Evocations/9)`
  - `plus_factor = 5 × xp_factor / (5 + 아이템 강화 수치)`
  - gloves of the gadgeteer·gadgeteer gizmo가 있으면 얻는 경험치 ×1.3으로 계산.
- 풀어 쓰면, 충전 1회(빚 10)에 필요한 경험치는 **다음 레벨까지 필요량의 약 `10 / ((3 + Evo/9) × (5 + 강화))`배**다(필요량/5가 100보다 큰 구간 기준).

| | Evocations 0 | Evocations 27 |
|---|---|---|
| 강화 +0 | 레벨의 약 2/3 | 약 1/3 |
| 강화 +5 | 약 1/3 | 약 1/6 |

  lightning rod는 빚이 3이라 위 값의 0.3배다.
- 빚과 강화 수치는 **아이템 개체가 아니라 종류별로 플레이어에게 저장된다.** 같은 종류를 버렸다가 다시 주워도 빚은 그대로다.

### 3.2 강화 수치 (+N)
- **이미 가진 발동 아이템과 같은 종류를 주우면 합쳐지면서 강화 수치 +1**(최대 **+5**). 강화 수치는 재충전 속도만 올린다(위 표). 효과의 위력은 바뀌지 않는다.
- +5가 되면 그 종류는 자동 줍기가 꺼진다. +5에서 같은 종류를 주우면 "더 이상 강화할 수 없다"는 메시지와 함께 흡수된다.

### 3.3 아이템별 효과

#### phial of floods
- **Primal Wave**: 위력 **`10 + Evocations × 4`**, 사거리 5. 물줄기 볼트 피해 **4d, 합계 최대 `10 + p/5`**, 명중 `10 + p/25`. 맞은 대상을 밀쳐낼 수 있다.
- 착탄 지점 주변(반경 2)에 **얕은 물 웅덩이** `3p/20 + 3 + random2(7)`칸을 만들고, `(4p/3 + 66)` aut 동안 유지된다.
- 웅덩이 칸의 몬스터(물에서 숨 쉬는 몬스터 제외)는 **Flooded** 상태가 된다: `p + 20` ~ 1.5배 aut 동안 **Silence와 같은 상태(주문 시전 불가 등)**, 매 턴 3d2 피해.
- [아이템 세트](scrolls.md#11-아이템-세트-item-set) "control": gravitambourine과 둘 중 하나만 생성.

#### gravitambourine
- **Gell's Gravitas**를 위력 **`15 + Evocations × 3.5`**(상한 100)로 시전한다. 효과 상세는 마법 Translocations 문서에서 다룰 예정.
- 최대 충전 2. 아이템 세트 "control": phial of floods와 둘 중 하나.

#### lightning rod
- **Thunderbolt**를 위력 **`5 + Evocations × 3`**으로 시전한다. 사거리 5.
- 바로 직전 턴에도 lightning rod를 썼으면 앞의 목표와 이번 목표 사이 **호(arc)** 전체를 맞히고, 연속 사용할수록 강해진다(누적 충전 최대 4).
  - 피해: 주사위 `2 + 연속 누적`개(최대 6개), 각 `(45 + p/4) / (호 길이 + 2)`. 호가 길수록 한 칸당 피해가 작다.
- 소음 15. 전기 피해(rElec로 저항).
- **최대 충전 4, 1회 빚 3**이라 다른 발동 아이템보다 훨씬 자주 쓸 수 있다.

#### tin of tremorstones
- 위력 `15 + Evocations`. **폭발 횟수 = `1 + stepdown((위력 − 15)/3, 2)`** → Evocations 0에서 1번, 27에서 6번.
- 목표 지점: 시야 안 몬스터들의 무게중심에 가장 가까운, **플레이어에게서 3칸 떨어진** 칸. 각 폭발은 그 칸 또는 인접 칸에서 반경 2로 터진다.
- 폭발마다 **6d6 파편 피해**(AC 적용). 고정물(firewood)은 표적 계산에서 제외.
- 폭발 중심이 플레이어와 2칸까지 가까워질 수 있으므로 플레이어가 휘말릴 가능성이 있다(미확인).
- 최대 충전 2. 아이템 세트 "area": condenser vane과 둘 중 하나.

#### condenser vane
- 위력 `15 + Evocations × 3.5`. 시야 안의 **위협적인 적대 몬스터 주변 칸**(벽·구름·아군이 있는 칸 제외)에 구름을 만든다.
  - 첫 칸은 반드시, 이후 각 칸은 `(50 + p)/160` 확률로 구름이 생긴다.
  - 구름 종류는 위력에 따라 고른다: 낮을 때는 mephitic이 많고, 위력이 오를수록 fire·cold·poison, 높으면 misery·storm·acid가 나온다. 선한 신 신자는 misery가 나오지 않는다.
  - 구름 지속 `5 + random2avg(12 + 3p/4, 3)`턴.
- **Still Winds** 상태의 층에서는 쓸 수 없다.
- 아이템 세트 "area": tin of tremorstones와 둘 중 하나.

#### phantom mirror
- 보이는 몬스터 하나를 골라 **아군 복제(illusion)**를 만든다. 고정물(firewood 등 peripheral), boundless tesseract, 이미 환영인 몬스터, 복제가 이미 존재하는 몬스터는 안 된다(다른 phantom mirror 복제는 다시 복제 가능).
- 지속 등급 `min(6, max(1, (Evocations/4 + 1) × (100 − 저항 차이) / 100))`. 저항 차이는 위력 `5 + Evocations × 3`의 Willpower 판정 결과다(대상의 Willpower가 높을수록 짧다).
- 복제는 **HD/3만큼 Drain**된 상태로 나온다.

#### box of beasts
- **mutant beast** 1마리를 아군으로 소환한다. 지속 등급 3~5(약 30~90턴, 무작위 보정).
- 등급 결정: `min(27, Evocations + random2(7) − random2(7))`을 넘지 않는 첫 단계 → larval(HD 3), juvenile(9), mature(15), elder(21), primal(27).
- Zin이 싫어하는 chaotic 행위다(DID_CHAOS).
- 아이템 세트 "ally": sack of spiders와 둘 중 하나.

#### sack of spiders
- 거미류 아군 `2 + 2E/27` ~ `2 + 4E/27`마리(E = Evocations; 최소 2, Evocations 27에서 4~6)를 소환한다. 종류는 Evocations에 따라: 낮으면 scorpion, redback, culicivora, 중간에 jumping spider, tarantella, 이후 wolf spider, steelbarb worm, 높으면 demonic crawler, broodmother. 신이 싫어하는 몬스터는 제외.
- 추가로, 반경 5 안의 아군이 아닌 몬스터마다 **`36 + 2 × Evocations`% 확률로 거미줄**을 씌운다(바닥 칸이거나 이미 거미줄인 칸에 있고, 이미 붙잡히지 않은 몬스터).
- 아이템 세트 "ally": box of beasts와 둘 중 하나.

#### horn of Geryon
- **sin beast**를 소환한다. 마릿수 1 + (`Evo×10 + random2(90)`이 130, 180, 230을 넘을 때마다 +1, 최대 4).
- 각 sin beast는 `random2(Evo × 10) > 7`일 때 아군, 아니면 **적대**로 나온다(Evocations 0이면 항상 적대, 1이면 20%만 아군, 5면 84% 아군).
- 소음 15. 선한 신이 싫어하는 evil 행위(DID_EVIL). Silence 상태에서는 쓸 수 없다.
- 네임드 Geryon이 가지고 있다(네임드 문서에서 다룰 예정).

### 3.4 생성 (발동 아이템)
- **바닥 무작위 생성**: 아이템 레벨 8 이상에서 `(11 + 아이템 레벨)/9000` 확률로 무작위 아이템이 발동 아이템으로 바뀐다. 종류는 5개 후보에서 균등: control 세트 선택분(phial/gravitambourine), lightning rod, ally 세트 선택분(box/sack), phantom mirror, area 세트 선택분(condenser/tin).
- horn of Geryon은 무작위 생성되지 않는다.

---

## 4. 생성 (완드)
- **바닥 무작위 생성**: 무작위 아이템 종류 중 완드의 가중치는 70 / 1661(약 4.2%). **아이템 레벨 7 미만에서는 `(7 − 레벨)/7` 확률로 포션이나 스크롤로 바뀐다**(D:1에서는 완드가 거의 나오지 않음).
- 종류별 가중치 합 70: flame 14, blast 세트 14, hex 세트 14, beam 세트 9, polymorph 7, mindburst 7, digging 5.
- Acquirement 계열(신의 선물 등)의 완드 선택은 미감정 종류를 2배로 우대한다. 스크롤 of acquirement 선택지에는 완드·발동 아이템이 나오지 않는다. → [acquirement](scrolls.md#3-acquirement)

> 출처: evoke.cc, xp-evoker-data.h, item-prop.cc, makeitem.cc, items.cc, player.cc, spl-book.cc, spl-data.h, zap-data.h, beam.cc, spl-damage.cc, spl-monench.cc, monster.cc, mon-ench.cc, actor.cc, terrain.cc, mutant-beast.h, mutation-data.h, acquire.cc (0.34.1)
