# 포션 (Potions)

> 기준: DCSS 0.34.1 · [아이템 목록으로](index.md)

포션의 종류별 효과·수치, 마시는 규칙, 포션 효과를 바꾸는 요인, 생성 규칙을 정리한다. 포션은 마시거나 Scroll of Identify로 감정한다. → [감정](index.md#감정-identification)

지속 시간은 모두 **턴**(10 aut = 1턴, 기본 행동 1회) 단위다. `random2(n)`은 0~n−1의 균등 난수다.

---

## 1. 목록

| 포션 | 효과 요약 | 지속 | 생성 가중치 |
|---|---|---|---|
| [curing](#21-curing) | HP 5~11 회복, Poison(중독)·Confusion(혼란) 해제 | 즉시 | 192 (18.4%) |
| [heal wounds](#22-heal-wounds) | HP 10~37 회복 (평균 23.5) | 즉시 | 105 (10.0%) |
| [haste](#31-haste) | Haste(가속): 모든 행동 시간 ×2/3 | 26~40 (합계 상한 80) | 67 (6.4%) |
| [might](#32-might) | 근접 공격 데미지 +1~10 | 35~74 | 67 |
| [brilliance](#33-brilliance) | 모든 주문 강화 +1단계, MP 비용 절반 | 35~74 | 67 |
| [enlightenment](#34-enlightenment) | 비행 + Willpower +1단계 | 비행과 같음 (25~64, 상한 100) | 67 |
| [attraction](#35-attraction) | 시야 안의 적을 매 턴 3칸씩 끌어당김 | 20~39 | 67 |
| [lignification](#36-lignification) | 나무 형태로 변신 | 15~58 | 67 |
| [moonshine](#37-moonshine) | Vertigo(현기증): 명중 −5, EV −5, 주문 실패율 +7 | 10~24 (상한 50) | 67 |
| [mutation](#38-mutation) | 돌연변이 2~3개 제거 후 1~3개(+50% 확률로 좋은 것 1개) 추가 | 영구 | 67 |
| [invisibility](#39-invisibility) | 투명 | 15~54 (상한 100) | 35 (3.3%) |
| [resistance](#310-resistance) | rF+, rC+, rElec, rPois, rCorr | 35~74 | 35 |
| [magic](#23-magic) | MP 10~37 회복 (평균 23.5) | 즉시 | 35 |
| [berserk rage](#311-berserk-rage) | Berserk(광폭화) | 10~19 | 35 |
| [cancellation](#312-cancellation) | 해제 가능한 마법 효과 전부 종료, 마법 오염 감소 | 즉시 | 35 |
| [ambrosia](#24-ambrosia) | 혼란에 걸리는 대신 매 턴 HP·MP 3~5 회복 | 3~10 | 35 |
| [experience](#313-experience) | 경험 레벨 +1, 스킬 경험치 획득 | 즉시 | 2 (0.2%) |

- 가중치 합 1045. 괄호 안은 바닥 무작위 생성 시 포션 중 해당 종류가 나올 확률.
- **지속 시간은 기존 지속에 더해진다**(같은 포션을 겹쳐 마시면 늘어남). 상한이 적힌 것만 상한에서 멈춘다.
- 아래 포션은 세이브 호환용으로 코드에만 남아 있고 **0.34.1에서는 생성되지 않는다**(`removed_items`): gain strength / dexterity / intelligence, poison, strong poison, slowing, porridge, decay, water, restore abilities, cure mutation, beneficial mutation, blood, coagulated blood.

---

## 2. 회복 포션

### 2.1 curing
- **HP `5 + random2(7)` = 5~11 회복.** [포션 회복 배율](#41-포션-회복-배율) 적용.
- **Poison과 Confusion을 없앤다.** (Confusion이 끝나므로 [ambrosia](#24-ambrosia) 효과도 함께 끝난다.)
- Death's Door 상태에서는 HP가 회복되지 않는다("You feel queasy."). Poison·Confusion 해제는 된다.
- HP가 가득 차 있고 Poison·Confusion도 없으면 감정된 curing은 마실 수 없다(아래 Oni 예외).

### 2.2 heal wounds
- **HP `10 + random2avg(28, 3)` = 10~37 회복**(평균 23.5). 포션 회복 배율 적용.
  - `random2avg(28, 3)`은 난수 3개의 평균이라 가운데 값이 잘 나온다.
- 최대 HP를 넘겨 회복하지는 않는다.
- Death's Door 상태이거나 포션 회복 배율이 0이면 효과가 없다. 감정된 상태에서는 이 경우와 HP가 가득 찬 경우 마실 수 없다.

### 2.3 magic
- **MP `10 + random2avg(28, 3)` = 10~37 회복**(평균 23.5).
- MP 회복 배율은 HP와 다르다: robe of Vines와 `MUT_NO_POTION_HEAL`(Vine Stalker)의 감소를 **받지 않고**, Kryia's mail coat ×2와 `MUT_DOUBLE_POTION_HEAL`(Oni) ×2만 적용된다.
- Djinni(`MUT_HP_CASTING`)와 최대 MP가 0인 캐릭터는 마실 수 없다. MP가 가득 차 있으면 감정된 상태로는 마실 수 없다.

### 2.4 ambrosia
- **Confusion `3 + random2(8)` = 3~10턴**을 걸고, 같은 길이의 Ambrosia 상태를 얻는다.
  - 이 Confusion은 강제로 걸린다(Clarity나 Divine Stamina로 막히지 않음). Confusion 지속 합계 상한은 40턴.
- Ambrosia 동안 **매 턴 HP 3~5, MP 3~5 회복**(행동 시간에 비례).
  - HP 회복에는 포션 회복 배율이, MP 회복에는 MP 회복 배율이 적용된다. Death's Door 중에는 HP가 회복되지 않는다.
- **Confusion이 끝나면 Ambrosia도 즉시 끝난다.** curing을 마시거나 다른 방법으로 Confusion이 풀리면 회복도 멈춘다.
- Ambrosia 자체는 cancellation으로 해제할 수 있는 효과다.

---

## 3. 강화·기타 포션

### 3.1 haste
- **Haste `random_range(26, 40)`턴.** 이미 Haste 중이면 더해지지만 **합계 80턴을 넘지 않는다.**
- Haste 중에는 **모든 행동의 소요 시간이 ×2/3**(이동·공격·주문 모두, `player_speed`). Slow와 동시에 걸리면 ×3/2 와 ×2/3가 곱해져 상쇄된다.
- **Stasis**(정지) 상태이거나 Cheibriados 신자는 마실 수 없다(감정된 경우). 모르고 마셔도 효과가 없다.
- Cheibriados가 싫어하는 아이템(hasty)이다.

### 3.2 might
- **Might `35 + random2(40)` = 35~74턴.**
- **근접 공격 데미지 +`1 + random2(10)`** (1~10, 평균 5.5). 무기 공격과 맨손 공격, **보조 공격(aux attack)** 모두에 적용되고, 원거리·투척에는 적용되지 않는다. → [데미지 계산 순서](weapons.md#31-계산-순서)
  - 이 보너스는 Berserk의 보너스와 **같은 것**이라 Might와 Berserk가 함께 있어도 한 번만 더해진다.
- **Str은 오르지 않는다.**

### 3.3 brilliance
- **Brilliance `35 + random2(40)` = 35~74턴.**
- **모든 주문의 마법 강화(enhancer) +1단계**: Spell power ×1.5. 다른 강화와 합쳐 최대 +3단계. → [마법 강화](brands-egos.md#공통-마법-강화enhancer)
- **주문의 MP 비용이 절반**(올림). 예: 5레벨 주문 → 3 MP.
- Trog 신자는 마실 수 없다(감정된 경우). robe of Folly를 입고 있으면 같은 효과가 이미 있어서 마실 수 없다. → [robe of Folly](unrands-armour.md#robe-of-folly)

### 3.4 enlightenment
- **비행**: 비행 지속에 `25 + random2(40)` = 25~64턴을 더한다(비행 지속 합계 상한 100턴).
- **Enlightened(깨달음)**: **Willpower +1단계**(내부값 +40). 지속 시간은 아래 규칙 때문에 사실상 **비행 지속 시간과 같다.**
  - 코드는 Enlightened 지속을 `max(현재 비행 지속, 현재 Enlightened 지속, 25 + random2(40))`로 정한다. 그런데 앞의 두 값은 내부 단위(aut, 1턴 = 10)이고 마지막 값은 턴 단위 숫자 그대로라서, 비행이 걸리면 항상 비행 지속이 선택된다.
  - **비행할 수 없는 형태**(tree form 등 `forbids_flight`)에서 마시면 비행이 걸리지 않아서, Enlightened 지속이 `25~64 aut` = **2.5~6.4턴**밖에 되지 않는다(0.34.1, 단위 불일치).
  - 같은 이유로 `MUT_EFFICIENT_METABOLISM`의 2배도 Enlightened에는 사실상 적용되지 않는다(비행 지속은 2배가 되지 않음).
- 이미 비행 중이면 지속만 늘어난다.

### 3.5 attraction
- **Attractive `20 + random2(40)/2` = 20~39턴.**
- 매 턴, **시야 안(투명한 벽 너머 제외)의 우호적이지 않은 몬스터**를 가까운 순서대로 **최대 3칸**(행동 시간에 비례) 플레이어 쪽으로 끌어당긴다.
  - 플레이어 바로 옆(1칸)에 있는 몬스터는 끌리지 않는다. 끌린 몬스터는 플레이어와 인접한 칸까지만 온다.
  - 직선 경로가 있어야 하며, 이동할 수 없는 칸이면 그 앞에서 멈춘다. 끌리기 전후 칸에 translocation energy 구름(1~3턴)이 생긴다.
  - 순간이동이 불가능한 몬스터(`no_tele`)는 끌리지 않는다.
  - 몬스터를 **깨우지는 않는다**. 잠든 몬스터도 잠든 채로 끌려온다.
- 감정된 상태로 마실 때 항상 확인을 묻는다(위험 아이템).

### 3.6 lignification
- **Tree form(나무 형태)으로 변신**, 지속 `15 + random2(30) + random2(15)` = **15~58턴.**
- **스스로 변신을 풀 수 없다**(`transform_uncancellable`). cancellation으로는 풀 수 있다.
- Tree form의 주요 특성(`dat/forms/tree.yaml`):

| 항목 | 값 |
|---|---|
| 최대 HP | ×1.5 |
| AC | `+20 + 14 × XL / 27` (XL 27에서 +34) |
| EV | **`2 + 몸집 보정/2`로 상한** (거의 0) |
| 맨손 공격 | 기본 데미지 12(Branches) |
| 저항 | rPois, Torment 면역 |
| 이동 | **불가**(제자리 고정). 순간이동 불가(진행 중인 Teleport도 취소) |
| 비행·수영 | 불가. 변신할 때 비행이 즉시 끝난다 |
| 장비 | 몸통 방어구와 보조 공격 부위가 녹아든다(meld). 무기는 들 수 있다 |

- 형태 일반(장비 녹아듦, 형태별 수치)은 탈리스만 문서에서 다룰 예정이다.
- 해로운 구름 위에 서 있으면 감정된 상태로 마실 때 확인을 묻는다(Tree form이 면역인 mephitic·poison 구름 제외).
- Zin이 싫어하는 chaotic 아이템이다(마시면 Zin conduct 위반).
- Death form 중에는 효과가 없다.

### 3.7 moonshine
- **Vertigo `random_range(10, 25)`턴**, 합계 상한 50턴. 효과:
  - 근접·원거리·보조 공격 **명중 −5**
  - **EV −5**
  - **주문 실패율 +7%p**(Wizardry 등 실패율 배율 적용 전에 더해짐)
- **감정된 moonshine은 마실 수 없다**("is_bad_item": 해로운 효과만 있는 아이템). 모르고 마실 때만 효과가 난다.
- 같은 Vertigo는 alcohol 구름(1/2 확률, 7~11턴), 몬스터의 plum 파이 등에서도 걸린다.

### 3.8 mutation
1. 무작위 돌연변이를 **2~3번 제거** 시도한다.
2. 무작위 돌연변이를 **1~3번 추가** 시도한다.
3. **1/2 확률로 좋은 돌연변이 1번**을 추가 시도한다.

- 각 시도는 일반적인 돌연변이 규칙(rMut 저항, 이미 많이 돌연변이된 경우의 제거 전환 등)을 따른다. 상세는 돌연변이 문서에서 다룰 예정이다.
  - 예: 아이템으로 얻은 rMut이 있으면 각 추가 시도가 2/3 확률로 막힌다(좋은 돌연변이 시도도 포함).
- **Zin 신자**: Zin의 권능(`cleanse_mut_potions`)이 있으면 **1단계(제거)만 일어나고 추가는 없다.** 권능이 없는 Zin 신자가 감정된 상태로 마시면 확인을 묻고 conduct 위반이 된다.
- 돌연변이할 수 없는 상태(일부 언데드 등)에서는 마실 수 없다(감정된 경우).
- 설명문은 추가되는 돌연변이가 "유익할 가능성이 높다"고 하지만, 코드상 확실히 좋은 쪽으로 굴리는 것은 3단계의 1/2 확률 1회뿐이다.

### 3.9 invisibility
- **Invisible(투명) `15 + random2(40)` = 15~54턴**, 합계 상한 100턴.
- **빛나는 상태(backlit)이면 완전히 투명해지지 않는다**: 마법 오염(1단계 이상), Corona, Sticky Flame, 후광(halo), flux form 등.
  - 감정된 상태에서 마실 때: 자기 후광(언랜드 Eos·Vainglory, Light 에고 방어구, The Shining One 신자 등) 때문이면 마실 수 없다. 그 밖의 backlit이면 경고 후 마실 수 있다.
- 투명 상태가 몬스터에게 미치는 영향(명중 페널티, 추적)은 상태이상 문서에서 다룰 예정이다.

### 3.10 resistance
- **Resistance `35 + random2(40)` = 35~74턴.** 효과:
  - **rF +1, rC +1, rElec +1**: 다른 저항에 1단계씩 더해진다.
  - **rPois +1**: rPois는 최대 1단계라 이미 있으면 의미 없음(Virulence 등 감소에는 반영).
  - **rCorr**
- cancellation으로 해제된다.

### 3.11 berserk rage
- **Berserk 지속 `(20 + random2avg(19, 2)) / 2` = 10~19턴**(평균 약 14).
- Berserk 효과(요약):
  - **최대·현재 HP ×1.5**(hat of the Bear Spirit는 ×2)
  - 모든 행동 시간 ×2/3 (Haste와 같은 크기. Cheibriados 신자는 속도 증가 없음)
  - 근접 데미지 +1~10 (Might와 같은 보너스, 중첩 안 됨)
  - 걸리는 순간 Fear(공포)와 Finesse가 해제된다
  - 주문·스크롤·포션 등 사용 제한, Stealth 0 등의 제약이 있다(상태이상 문서에서 다룰 예정)
- **공격하지 않으면 빨리 끝난다**: 공격(시도 포함)하지 않은 행동이 이어질 때마다 추가로 깎이는 지속이 1, 2, 3…턴씩 늘어난다(삼각수: 연속 8번이면 추가 감소 누적 36턴). 공격하면 이 누적이 0으로 돌아간다.
- **종료 후**:
  - **Slow `(12 + 2d12) × 1.5`턴**(hat of the Bear Spirit는 2/3로 감소). Stasis면 걸리지 않는다.
  - **재광폭화 불가 기간**: `(12 + 2d12) × 2`턴(위 Slow와 같은 주사위 값). Haste 중에는 1.5배 빨리 줄어든다.
- 마실 수 없는 경우(감정된 경우 확인 단계에서 거부):
  - 이미 Berserk 중이거나 재광폭화 불가 기간
  - Death's Door
  - Mesmerised(매혹) 상태 (Obsidian Axe 장착 시 예외)
  - 완전한 언데드(Poltergeist·Revenant 같은 `undead` 종족, Death form 중. 모르고 마셔도 "slightly irritated"만 출력하고 효과 없음)
  - Stasis
- 아이템 레벨 2 미만(D:1~2)에서 생성된 berserk rage는 몬스터가 줍지 않는다.

### 3.12 cancellation
- **해제 가능한(`D_DISPELLABLE`) 모든 지속 효과를 끝낸다.** 좋은 효과와 나쁜 효과를 가리지 않는다.
  - 대부분은 지속이 1 aut로 줄어 다음 순간 끝난다. Teleport 대기, Petrifying, Flayed, Sticky Flame, fortress blast 충전은 즉시 제거.
  - 해제되는 예: Haste, Might, Brilliance, Resistance, Enlightened, Invisible, Ambrosia, 비행(일시적), 변신(탈리스만 기본 형태 제외), Confusion, Slow, Corrosion, Vertigo, Attractive, Weak, Blind, Silence, Mesmerised, Petrified, Paralysis, Sleep, Fear 등 61종.
  - **해제되지 않는 것**: Poison, Berserk와 재광폭화 불가 기간, Death's Door, 영구 비행, 탈리스만으로 바꾼 기본 형태, slaughter form.
- **마법 오염 `250~1000` 감소**(오염 1단계 = 1000, 최대 3000).
- `MUT_INVIOLATE_MAGIC`이 있어도 포션은 무시하고 해제한다.
- 해제할 효과도 오염도 없으면 감정된 상태로는 마실 수 없다.

### 3.13 experience
- **경험 레벨(XL) +1.** 현재 레벨 안에서의 진행도(%)는 유지된다. 최대 레벨이면 레벨은 오르지 않는다.
- **스킬 경험치 `7500 × XL`**(마시기 전의 XL)을 받는다. 마시면 스킬 메뉴가 열려서 어느 스킬에 쓸지 고를 수 있다.
  - Gnoll(`MUT_DISTRIBUTED_TRAINING`)은 메뉴 없이 평소 훈련 방식대로 분배된다.
- **Hepliaklqana의 징벌(penance) 중이면** 위 효과 대신 징벌이 `750 × XL`만큼 줄어든다.

---

## 4. 포션 효과를 바꾸는 요인

### 4.1 포션 회복 배율
curing·heal wounds의 HP 회복과 ambrosia의 HP 회복에 적용된다(`_get_potion_heal_factor`).

1. 기본 2(= ×1)
2. 감소: robe of Vines −2, `MUT_NO_POTION_HEAL` 단계당 −1 (Vine Stalker는 2단계 → 0)
3. 증가: Kryia's mail coat ×2, `MUT_DOUBLE_POTION_HEAL`(Oni) ×2
4. 최종 회복량 = 기본 회복량 × 배율 / 2. 배율이 0이면 회복 없음.

| 조건 | 배율 |
|---|---|
| 기본 | ×1 |
| Kryia's mail coat 또는 Oni | ×2 |
| Oni + Kryia's mail coat | ×4 |
| `MUT_NO_POTION_HEAL` 1단계 | ×1/2 |
| Vine Stalker(2단계) 또는 robe of Vines | ×0 |

- **MP 회복**(magic, ambrosia)은 감소 요인을 무시하고 Kryia's mail coat ×2, `MUT_DOUBLE_POTION_HEAL` ×2만 적용된다. 그래서 Vine Stalker도 potion of magic의 효과를 그대로 받는다.
- Delatra's gloves의 회복은 포션 경로가 아니라 배율과 무관하다. → [언랜드 방어구](unrands-armour.md#delatras-gloves), [Kryia's mail coat](unrands-armour.md#kryias-mail-coat), [robe of Vines](unrands-armour.md#robe-of-vines)

### 4.2 Efficient Metabolism (`MUT_EFFICIENT_METABOLISM`)
돌연변이(좋은 쪽, 1단계). **포션으로 얻는 상태 효과의 지속이 2배.**
- 적용: haste, might, brilliance, attraction, lignification, moonshine, invisibility, resistance, ambrosia(혼란·회복 지속 모두), berserk rage, enlightenment(위 3.4의 이유로 사실상 무효).
- 지속 합계 상한(haste 80, invisibility 100 등)은 그대로다.
- 포션을 직접 마셨을 때만 적용된다. 신의 능력 등으로 포션 효과를 받는 경우(아래 4.5)는 2배가 되지 않는다.

### 4.3 Oni의 Drunken Brawling (`MUT_DRUNKEN_BRAWLING`)
- **curing, heal wounds, magic, ambrosia를 마시면, 마시기 전에 인접한 모든 적에게 근접 공격**을 한 번씩 한다(cleave와 같은 대상 선택, 공격 자체는 cleave하지 않음).
- 이 공격이 일어나면 **HP·MP가 가득 차 있어도 그 포션을 마실 수 있다**(평소에는 "이미 가득 참"으로 거부됨).
- Oni는 `MUT_DOUBLE_POTION_HEAL`도 있어서 위 회복 배율 ×2를 받는다.

### 4.4 그 밖의 요인
- **amulet of chemistry**: 포션 효과가 발동하면 MP 5~9 회복(MP가 가득 차 있지 않을 때). → [chemistry](jewellery.md#47-chemistry)
- **Potion Fungus** (`MUT_POTION_FUNGUS`, 나쁜 돌연변이): 포션을 마실 때 1/3 확률로, 시야 안에서 그 효과를 받을 수 있는 몬스터의 40~90%(최소 1마리)에게 같은 포션의 효과가 퍼진다. **적대 몬스터도 대상**이다.
  - 대상 포션과 몬스터 효과: haste·might·invisibility·resistance·berserk(해당 상태 부여), brilliance(주문 강화), heal wounds(HP 30~50), curing(HP 10~20, 중독·혼란 해제), enlightenment(비행·의지 강화 30~45턴), magic(Antimagic 해제).
- **toga "Victory"**: 적대 몬스터가 보이는 상태에서 마시면 축적된 능력치가 초기화된다(확인 질문 있음). → [toga "Victory"](unrands-armour.md#toga-victory)
- **Xom**: 모르는 포션을 위험한 상황에서 마시면 Xom이 즐거워한다.

### 4.5 포션 효과를 빌려 쓰는 다른 경로
다음은 포션을 마신 것이 아니라 효과만 적용된다. 그래서 **포션 회복 배율, Efficient Metabolism, chemistry MP 회복이 적용되지 않는다.**
- Delatra's gloves(미감정 포션·스크롤 사용 시 heal wounds·magic 효과)
- Gozag의 포션 청원(Potion Petition)
- 그 밖의 일부 능력·빔 효과(아군 강화 빔의 heal wounds·might·invisibility·resistance 등)

---

## 5. 마실 수 없는 경우

| 조건 | 내용 |
|---|---|
| Mummy (`MUT_NO_DRINK`) | 포션을 전혀 마실 수 없다 |
| Death form | 변신 중 마실 수 없다 |
| lemon 파이 등 (`DUR_NO_POTIONS`) | 지속 동안 불가 (10~20턴, 상한 50) |
| Berserk 중 | 불가 |
| **Cocytus** | **이 브랜치 안에서는 포션을 마실 수 없다**("everything's frozen solid") |
| Ru의 Sacrifice Drink (`MUT_RENOUNCE_POTIONS`) | 적대 몬스터가 근처에 보이는 동안과 그 뒤 6턴은 불가. **HP가 최대의 1/2 미만이면 가능**(스크롤 희생은 1/2 이하) |
| Gozag 징벌 중 | 마실 때 1/3 확률로 실패하고 턴만 소모 |

- **감정된 포션**은 효과가 없을 상황이면 마시기 전에 거부된다(각 포션 항목 참고). 미감정 포션은 그런 검사 없이 마신다.
- 감정된 attraction·lignification·mutation(Zin 권능 없는 경우)은 위험 아이템이라 확인을 묻는다. 신이 싫어하는 포션(Zin: mutation·lignification, Cheibriados: haste)은 징벌 경고와 함께 묻는다.

---

## 6. 생성 (간략)
- **바닥 무작위 생성**: 무작위 아이템 종류 중 포션의 가중치는 176 / 1661(약 10.6%). 아이템 레벨 7 미만에서는 완드로 정해진 아이템이 일정 확률로 포션 또는 스크롤로 바뀌어 포션이 조금 더 나온다.
  - 수량: 1개, 1/18 확률로 +1, 1/25 확률로 +1(최대 3개).
  - 종류별 확률은 [1. 목록](#1-목록)의 생성 가중치. 아이템 레벨(깊이)과 무관하다.
- 볼트 지정 아이템(`.des`), 상점, 신의 선물 등 다른 경로는 각 문서에서 다룬다.
- 몬스터는 0.34.1에서 포션을 마시지 않는다.

> 출처: potion.cc, potion-type.h, item-use.cc, item-name.cc, item-prop.cc, makeitem.cc, player.cc, player-act.cc, player-reacts.cc, main.cc, spl-goditem.cc, spl-transloc.cc, spl-cast.cc, spl-util.cc, melee-attack.cc, attack.cc, mutation.cc, mutation-data.h, transform.cc, dat/forms/tree.yaml, duration-data.h (0.34.1)
