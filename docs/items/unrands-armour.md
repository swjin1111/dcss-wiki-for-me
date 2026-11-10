# 언랜드 아티팩트 — 방어구 (Unrandart Armour)

> 기준: DCSS 0.34.1 · [아이템 목록으로](index.md)
>
> **작성 진행 상황**: 51종 전부 작성 완료.

이름·수치·고유 효과가 정해진 방어구 아티팩트를 정리한다. 원형 방어구의 기본 수치와 AC·EV·SH·방해도 공식은 [방어구 문서](armour.md), 에고 효과는 [브랜드·에고](brands-egos.md#방어구-에고), 아티팩트 속성(Str, rF, Will 등)의 의미는 [아티팩트 속성](artefact-properties.md) 참고. 이 문서는 **원형과 달라진 점과 고유 효과** 위주로 쓴다.

---

## 공통 규칙
- **한 게임에 하나씩만** 존재한다. 생성 가중치와 깊이 규칙은 [아이템 개요](index.md#아티팩트-개요) 참고.
- **인챈트(+N)는 고정**이다. 인챈트 스크롤로 올릴 수 없다(Mountain Dwarf도 불가). 예외적으로 인챈트가 스스로 변하는 것(Cigotuvi's embrace, toga "Victory")과 생성 때 무작위로 정해지는 것(faerie dragon scales)이 있다.
- 아래 수치표의 "AC"는 **원형의 기본 AC + 인챈트**다. 실제 몸통 방어구 AC는 Armour 스킬로 늘어난다. → [AC 계산](armour.md#21-계산)
  - 방패는 AC 대신 SH가 오르며, 인챈트 +1당 표시 SH +1이다. → [방패의 SH](armour.md#51-방패의-sh)
- 방해도(ER)·몸집 제한 등은 원형과 같다. → [전체 방어구 수치표](armour.md#8-전체-방어구-수치표)
- 그 칸에 올라서면 다른 방어구처럼 자동 감정된다.
- **볼트 지정 아이템**: 여러 언랜드에 그 언랜드를 지키는 전용 볼트(`guarded_unrand` 계열)나 상점 목록이 있다. 볼트가 지정한 언랜드가 이미 나왔으면 지정된 종류(`FALLBACK`)의 randart로 대신 만들어진다.
- 바닥에서 생성되지 않는 것(`nogen`): orb of Dispater, faerie dragon scales, dragonskin cloak, scarf of invisibility. 앞의 셋은 특정 네임드 몬스터가 들고 나온다.
- 고유 효과 중 "매 행동마다"라고 쓴 것은 플레이어가 행동할 때마다(행동에 걸린 시간과 무관하게) 한 번씩 판정한다. "시간 비례"라고 쓴 것은 10 aut(보통 속도 1턴)를 기준으로 행동 시간에 비례한다.
- **Regen(HP 재생) 속성은 regeneration 목걸이와 같은 동조(attunement) 규칙**을 따른다(HP가 가득 찬 적이 있어야 켜짐). → [동조](jewellery.md#41-regeneration--magic-regeneration)

## 전체 목록
바닥 무작위 생성 가능 47개 + `nogen` 4개 = 51개. (삭제된 언랜드 7개 — tower shield "Bullseye", cloak of Flash, boots of the spider, hat of the High Council, Maxwell's etheric cage, crown of Eternal Torment, armour of Talos — 는 제외)

| 부위 | 언랜드 | 원형 | 상세 |
|---|---|---|---|
| 몸통 | [robe of Augmentation](#robe-of-augmentation) | robe | 작성 |
| | [robe of Misfortune](#robe-of-misfortune) | robe | 작성 |
| | [Lear's hauberk](#lears-hauberk) | chain mail | 작성 |
| | [skin of Zhor](#skin-of-zhor) | animal skin | 작성 |
| | [salamander hide armour](#salamander-hide-armour) | leather armour | 작성 |
| | [robe of Folly](#robe-of-folly) | robe | 작성 |
| | [Maxwell's patent armour](#maxwells-patent-armour) | plate armour | 작성 |
| | [robe of Night](#robe-of-night) | robe | 작성 |
| | [scales of the Dragon King](#scales-of-the-dragon-king) | golden dragon scales | 작성 |
| | [robe of Clouds](#robe-of-clouds) | robe | 작성 |
| | [moon troll leather armour](#moon-troll-leather-armour) | troll leather armour | 작성 |
| | [orange crystal plate armour](#orange-crystal-plate-armour) | crystal plate armour | 작성 |
| | [robe of Vines](#robe-of-vines) | robe | 작성 |
| | [Kryia's mail coat](#kryias-mail-coat) | scale mail | 작성 |
| | [Cigotuvi's embrace](#cigotuvis-embrace) | leather armour | 작성 |
| | [toga "Victory"](#toga-victory) | robe | 작성 |
| | [justicar's regalia](#justicars-regalia) | scale mail | 작성 |
| | [faerie dragon scales](#faerie-dragon-scales) (nogen) | acid dragon scales | 작성 |
| 보조손 (방패·오브) | [tower shield of Ignorance](#tower-shield-of-ignorance) | tower shield | 작성 |
| | [shield of Resistance](#shield-of-resistance) | kite shield | 작성 |
| | [shield of the Gong](#shield-of-the-gong) | kite shield | 작성 |
| | [warlock's mirror](#warlocks-mirror) | buckler | 작성 |
| | [Storm Queen's Shield](#storm-queens-shield) | kite shield | 작성 |
| | [crystal ball of Wucad Mu](#crystal-ball-of-wucad-mu) | orb | 작성 |
| | [sphere of Battle](#sphere-of-battle) | orb | 작성 |
| | [Charlatan's Orb](#charlatans-orb) | orb | 작성 |
| | [skull of Zonguldrok](#skull-of-zonguldrok) | orb | 작성 |
| | [orb of Dispater](#orb-of-dispater) (nogen) | orb | 작성 |
| 망토 | [cloak of the Thief](#cloak-of-the-thief) | cloak | 작성 |
| | [cloak of Starlight](#cloak-of-starlight) | cloak | 작성 |
| | [ratskin cloak](#ratskin-cloak) | cloak | 작성 |
| | [fungal fisticloak](#fungal-fisticloak) | cloak | 작성 |
| | [dragonskin cloak](#dragonskin-cloak) (nogen) | cloak | 작성 |
| | [scarf of invisibility](#scarf-of-invisibility) (nogen) | scarf | 작성 |
| 머리 | [crown of Dyrovepreva](#crown-of-dyrovepreva) | hat | 작성 |
| | [hat of the Bear Spirit](#hat-of-the-bear-spirit) | hat | 작성 |
| | [hood of the Assassin](#hood-of-the-assassin) | hat | 작성 |
| | [mask of the Dragon](#mask-of-the-dragon) | hat | 작성 |
| | [hat of the Alchemist](#hat-of-the-alchemist) | hat | 작성 |
| | [hat of Pondering](#hat-of-pondering) | hat | 작성 |
| | [crown of vainglory](#crown-of-vainglory) | hat | 작성 |
| 손 | [gauntlets of War](#gauntlets-of-war) | gloves | 작성 |
| | [fencer's gloves](#fencers-gloves) | gloves | 작성 |
| | [Mad Mage's Maulers](#mad-mages-maulers) | gloves | 작성 |
| | [Delatra's gloves](#delatras-gloves) | gloves | 작성 |
| | [gloves of the gadgeteer](#gloves-of-the-gadgeteer) | gloves | 작성 |
| 발 | [seven-league boots](#seven-league-boots) | boots | 작성 |
| | [mountain boots](#mountain-boots) | boots | 작성 |
| | [slick slippers](#slick-slippers) | boots | 작성 |
| | [lightning scales](#lightning-scales) | barding | 작성 |
| | [Black Knight's barding](#black-knights-barding) | barding | 작성 |

---

## 몸통 방어구

### 수치표
| 언랜드 | 원형 (기본 AC) | 인챈트 | AC | 에고 | 속성 |
|---|---|---|---|---|---|
| robe of Augmentation | robe (2) | +4 | 6 | — | Str +4, Int +4, Dex +4 |
| robe of Misfortune | robe (2) | +5 | 7 | — | EV +5, Harm, \*Slow, \*Corrode |
| Lear's hauberk | chain mail (8) | +18 | **26** | — | (머리·손·발 슬롯 점유) |
| skin of Zhor | animal skin (2) | +4 | 6 | — | rC+++, SInv |
| salamander hide armour | leather armour (3) | +3 | 6 | — | rF++, rC−−, Fire 강화 |
| robe of Folly | robe (2) | +4 | 6 | — | Int +8, Will 0 |
| Maxwell's patent armour | plate armour (10) | +15 | **25** | — | Will+, rElec, rCorr, −Tele, \*Silence |
| robe of Night | robe (2) | +5 | 7 | — | Will+, SInv |
| scales of the Dragon King | golden dragon scales (12) | +9 | 21 | Command | (golden dragon scales 고유: rF+, rC+, rPois) |
| robe of Clouds | robe (2) | +3 | 5 | — | rElec |
| moon troll leather armour | troll leather armour (3) | +5 | 8 | Spirit Shield | MP +5, Regen +1 (원형의 Regen과 합쳐 2단계) |
| orange crystal plate armour | crystal plate armour (14) | +8 | 22 | Archmagi | Int +3, Clarity |
| robe of Vines | robe (2) | +1 | 3 | — | Regen +4 |
| Kryia's mail coat | scale mail (6) | +7 | 13 | — | rC+ |
| Cigotuvi's embrace | leather armour (3) | +4 (변동) | 7~ | — | rN+, Evil, ^Drain |
| toga "Victory" | robe (2) | +0 (변동, 최대 +7) | 2~9 | — | Clarity, Slay·Int (변동) |
| justicar's regalia | scale mail (6) | +5 | 11 | — | Str +4 |
| faerie dragon scales | acid dragon scales (6) | **+2~+8** | 8~14 | — | 무작위 randart 속성 + Hexes 강화 |

- 드래곤 비늘 원형의 고유 저항은 그대로 붙는다. → [특수 몸통 방어구](armour.md#6-특수-몸통-방어구)

### robe of Augmentation
- Str·Int·Dex 각각 **+4**. 고유 효과는 없다.
- 초반 언랜드(`MAX_LEVEL` 11): 깊이 11 이하에서 생성 가중치가 높다.

### robe of Misfortune
- EV +5와 함께 나쁜 속성 3개: **Harm**(주는 데미지 +30%, 받는 데미지 +20%), **\*Slow**, **\*Corrode**. → [나쁜 속성](artefact-properties.md#나쁜-속성)
- 초반 언랜드(`MAX_LEVEL` 11).

### Lear's hauberk
- chain mail +18, AC 26. ER은 chain mail과 같은 14.
- **몸통 + 머리 + 손 + 발 슬롯을 한꺼번에 차지한다.** 입으면 투구·장갑·부츠를 함께 쓸 수 없다.
  - 장착하려면 이 네 슬롯이 **모두 있어야** 한다. 예를 들어 부츠 슬롯이 없는 종족(barding을 입는 종족 등), 장갑을 낄 수 없는 종족은 입을 수 없다. chain mail 자체의 몸집 제한(Small~Medium)도 그대로다.
- 몬스터가 주울 수 없고 Tukima's Dance 같은 효과의 대상이 되지 않는다(`special`).
- 초반 언랜드(`MAX_LEVEL` 11).

### skin of Zhor
- animal skin(모든 몸집이 입을 수 있음) +4, **rC+++**, SInv.
- **Englaciate**: 위험한 몬스터가 근처에 있으면 매 행동마다 **1/7 확률**(행동 시간이 10 aut일 때. 더 긴 행동이면 확률이 오름)로 Englaciation(위력 30)이 발동한다.
  - **시야 안의 모든 대상**(아군 포함, 사용자 제외)에게 감속(Slow)을 건다. rC가 있는 대상은 면역.
  - 지속 = `round(3d31 / 6) − round((HD − 1) / 2)`턴. 0 이하이면 저항. 저항하지 않았으면 최소 2~5턴은 보장. 냉혈(cold-blooded) 몬스터는 2배.
  - 지속 기댓값이 약 8턴이므로, 대략 **HD 17 이상은 자주 저항하고 HD 32 이상은 항상 저항**한다.
  - Stasis가 있는 대상은 감속되지 않는다.

### salamander hide armour
- leather armour +3, **rF++, rC−−**, **Fire 마법 강화 +1단계**, **불 구름(flame cloud) 면역**.
- **Flames**: 입을 때와 매 행동마다, **사용자 주변 8칸에 불 구름**을 깐다(구름 지속 2~7). 사용자 칸에 불 구름이 있으면 지운다.
  - 같은 편 몬스터(아군)가 서 있는 칸은 건너뛴다. 중립 몬스터나 빈칸은 건너뛰지 않는다.
  - 몸에 붙은 얼음 효과를 매번 녹인다. 그래서 **Ozocubu's Armour를 쓸 수 없다**("your ring of flames would instantly melt the ice").
- 몬스터가 주울 수 없다(`special`).

### robe of Folly
- **Int +8.**
- **Brill(상시 Brilliance)**: 포션 of brilliance와 같은 효과가 항상 켜져 있다.
  - 모든 주문의 **마법 강화 +1단계**(Spell power ×1.5. 다른 강화와 합쳐 최대 3단계). → [마법 강화](brands-egos.md#공통-마법-강화enhancer)
  - 주문의 **MP 비용이 절반**(올림).
  - 입고 있는 동안 potion of brilliance를 마실 수 없다(효과가 겹치지 않음).
- **Will-∞: Willpower가 0이 된다.** 다른 Will 보너스와 무관하게 0이다. 몬스터가 입어도 그 몬스터의 Willpower가 0이 된다.

### Maxwell's patent armour
- plate armour +15, AC 25. **Will+, rElec, rCorr.**
- 나쁜 속성: **−Tele**(대부분의 순간이동 차단), **\*Silence**(피해를 받을 때 1% 확률로 4~10턴 침묵). → [나쁜 속성](artefact-properties.md#나쁜-속성)

### robe of Night
- Will+, SInv.
- **Dark**: **시야 반경 × 3/4** (기본 7 → 5). 시야는 대칭이라 그 밖의 몬스터도 사용자를 볼 수 없다. scarf of Shadows 등의 −1이 먼저 적용된 뒤 3/4이 곱해진다.

### scales of the Dragon King
- golden dragon scales +9. 에고 **Command**(Summoning 주문의 Spell power × `(270 + Armour 스킬×10) / 270`). → [마법 강화 에고](brands-egos.md#마법-강화)
- 몬스터 장비: Parghit이 입는 golden dragon scales가 1/100 확률로 이것이 된다.

### robe of Clouds
- rElec.
- **Thunder**: 반경 2 안(막힌 벽 너머 제외)의 **적대적이고 위협이 되는 몬스터 하나하나**에 대해, 시간 비례로 10 aut당 1/7 확률로 그 칸에 **storm cloud(4~8턴)** 를 만든다.
- **rCloud: 모든 구름에 면역.**

### moon troll leather armour
- troll leather armour +5. 에고 **Spirit Shield**(받는 데미지를 HP와 MP로 나눠 받음), **MP +5**, **Regen +1**.
- troll leather armour 자체의 HP 재생 증가와 합쳐 HP 재생 보너스가 2단계(+160, [재생량](jewellery.md#41-regeneration--magic-regeneration) 기준)다.

### orange crystal plate armour
- crystal plate armour +8, AC 22. 에고 **Archmagi**(모든 마법 강화 +1단계), **Int +3, Clarity**(혼란 면역).
- Archmagi는 원래 robe에만 붙는 에고인데(볼트 지정·randart 경로), 이것은 crystal plate armour에 붙어 있다. → [Archmagi가 나오는 경로](brands-egos.md#바닥-무작위-생성으로는-나오지-않는-에고)

### robe of Vines
- robe +1, **Regen +4**(HP 재생 보너스 +320, 즉 동조되면 턴당 3.2 HP 추가).
- **NoPotionHeal: 포션으로 HP가 회복되지 않는다**(heal wounds, curing의 HP 회복). potion of magic의 MP 회복은 그대로 된다.

### Kryia's mail coat
- scale mail +7, rC+.
- **PotionHeal\*2: 포션의 HP 회복량 2배**(heal wounds, curing, ambrosia. → [포션 회복 배율](potions.md#41-포션-회복-배율)), **potion of magic의 MP 회복량도 2배**.
  - 다른 감소 요인(돌연변이 등)이 있으면 그 감소를 먼저 적용한 뒤 2배를 곱한다.
- 초반 언랜드(`MAX_LEVEL` 11).

### Cigotuvi's embrace
- leather armour, 기본 +4. **rN+, rMiasma**(Miasma 면역), **Evil 아이템**, **^Drain**(벗을 때 Drain).
- 몬스터가 주울 수 없다(`special`).
- **Corpsefed**: 매 행동마다 **시야 안의 모든 시체(뼈가 아닌 온전한 시체)를 흡수**해서 일시적으로 인챈트가 오른다.
  - 시체 하나를 흡수할 때마다 Evil 행위 1회로 처리된다. Beogh 신자는 오크 시체를 흡수하지 않는다.
  - 내부 수치 `armour`: 시체 하나당 `10000 / (armour + 100)`만큼 증가(많이 모을수록 증가량이 줄어듦).
  - 인챈트 = `4 + 1 + (armour − 1) × 6 / 100` (armour가 0이면 기본 +4).
  - 시간 비례 감소: 10 aut당 `(armour + 400) / 400`씩 줄어든다.

  | 흡수한 시체 수 (한 번에) | armour | 인챈트 | AC (원형 3 포함) |
  |---|---|---|---|
  | 0 | 0 | +4 | 7 |
  | 1 | 100 | +10 | 13 |
  | 2 | 150 | +13 | 16 |
  | 3 | 190 | +16 | 19 |
  | 5 | 255 | +20 | 23 |
  | 10 | 379 | +27 | 30 |
  | 20 | 558 | +38 | 41 |

  - 추가 흡수 없이 0으로 돌아가기까지: armour 100에서 약 90턴, 200에서 약 160턴, 400에서 약 280턴.
- 벗으면 쌓인 수치가 바로 0이 된다.

### toga "Victory"
- robe, 기본 +0. **Clarity.**
- **Victory**: 사용자가 직접(근접·원거리·주문 포함) 경험치를 주는 몬스터를 죽이면 보너스 +1을 얻을 수 있다.
  - 그 몬스터의 위협도(threat)가 **Nasty면 항상, Tough면 1/4 확률**. 그보다 약하면 오르지 않는다. 아군·중립·소환물 처치는 해당 없음.
  - 보너스 1당 **AC +1(인챈트), Slaying +1, Int +1**. 최대 **+7**.
- **초기화 조건** (보너스가 0으로 돌아감):
  - **위험한 적대 몬스터가 보이는 상태에서 포션을 마시거나 스크롤을 읽으면** 다음 행동에 초기화된다. 보너스가 있을 때는 마시기·읽기 전에 확인 질문이 나온다.
  - 벗으면 초기화된다(변신으로 녹아든 것은 벗은 것이 아님).
- 초반 언랜드(`MAX_LEVEL` 11).

### justicar's regalia
- scale mail +5, **Str +4.**
- **Amulet+: 목걸이 슬롯 +1**(목걸이 2개 착용 가능).
- **Inspire**: 플레이어가 소환하거나 만들어 낸 몬스터는 생성될 때 **Regeneration 30~50턴**을 얻는다.

### faerie dragon scales
- **바닥에서 생성되지 않는다.** 네임드 Enchantress가 항상 입고 나온다.
- 원형 acid dragon scales(rCorr). 생성될 때 **무작위 randart 속성**을 굴린다(\*Silence가 붙으면 최대 100번까지 다시 굴림).
  - 추가로 각각 1/10 확률로 Clarity, MP +4~12, HP +4~12, +Inv가 붙는다.
  - **항상 Hexes 마법 강화 +1단계.**
- **인챈트는 `2 + random2(4) + random2(4)` = +2~+8**로 생성 때 정해진다(`art-data.txt`의 +3은 덮어씌워짐).

---

## 보조손: 방패

### 수치표
| 언랜드 | 원형 (기본 SH) | 인챈트 | SH | 에고 | 속성 |
|---|---|---|---|---|---|
| tower shield of Ignorance | tower shield (13) | +10 | 23 | — | Int −4, rN+ |
| shield of Resistance | kite shield (8) | +2 | 10 | — | rF++, rC++, Will++ |
| shield of the Gong | kite shield (8) | **+18** | **26** | — | EV −5, Will+, rN+, rCorr |
| warlock's mirror | buckler (3) | +3 | 6 | Reflection | Omnireflect |
| Storm Queen's Shield | kite shield (8) | +5 | 13 | — | rElec, Fly |

- SH 열은 기본 SH + 인챈트다. 실제 SH는 Shields 스킬 등으로 늘어난다. → [방패의 SH](armour.md#51-방패의-sh)
- **방패 언랜드의 "막았을 때" 효과는 근접 공격뿐 아니라 투사체·주문 볼트를 막았을 때도 발동한다**(막기에 성공하면 공통으로 실행되는 처리에 붙어 있음).

### tower shield of Ignorance
- Int −4, rN+. 고유 효과는 없다.

### shield of Resistance
- rF++, rC++, Will++. 고유 효과는 없다.

### shield of the Gong
- kite shield +18. EV −5, Will+, rN+, rCorr.
- **Loud: 막을 때마다 소음 40**(매우 큼). 사용자 칸이 침묵 상태면 소리가 나지 않는다.

### warlock's mirror
- buckler +3, 에고 **Reflection**(막은 것을 반사). → [저항·방어 에고](brands-egos.md#저항방어)
- **Omnireflect**: 원래 방패로 막을 수 없는 공격도 막고 반사할 수 있다.
  - **관통(piercing) 볼트, 전기 볼트**: 보통 볼트처럼 명중치 대 SH로 막기 판정. → [막기 판정](armour.md#52-막기-판정)
  - **반드시 명중하는(Willpower로 저항하는) 주술 등**: 확률 **`표시 SH / (표시 SH + 10)`** 로 막는다. 예: SH 10이면 50%, SH 20이면 67%.
  - 관통 투척 무기·투사체(javelin 등)도 막을 수 있다.
  - 폭발(explosion), Glaciate, Vampiric Draining은 막을 수 없다.
- 일반 방패처럼 턴당 막기 횟수 제한을 따른다.

### Storm Queen's Shield
- kite shield +5, **rElec, 비행(Fly).**
- **Shock**: 막을 때마다 **1/3 확률**로 공격자에게 전기 방전. **3d8 전기 데미지**(rElec로 감소, AC 절반 적용).
  - 공격자가 **3칸 이내**이고 시야가 통하면 원거리 공격자에게도 발동한다.
  - (코드 주석에는 3d7이라고 적혀 있지만 실제 계산식 `3d(4 + 3×3/2)`은 3d8이다.)

---

## 보조손: 오브

### 수치표
| 언랜드 | 에고 | 속성 |
|---|---|---|
| crystal ball of Wucad Mu | Energy | Mindtap |
| sphere of Battle | — | Battlesphere 자동 소환, 파괴 마법 강화 |
| Charlatan's Orb | — | 가짜 Orb 효과, 스킬 증가 |
| skull of Zonguldrok | — | Int +4, rN+, Evil, 머리 슬롯 +1 |
| orb of Dispater | — | AC +5, Evil, \*Corrode, 발동: Hurl Damnation |

- orb는 기본 AC·SH가 0이고 방해도가 없다. 모든 몸집이 쓸 수 있다.

### crystal ball of Wucad Mu
- 에고 **Energy**: 주문 실패율이 오르는 대신, 주문을 쓴 뒤 그 MP를 돌려받을 수 있다. → [오브 에고](brands-egos.md#오브orb-전용)
  - 돌려받을 확률 = `15 + Evocations 스킬 × 30/27` % (스킬 0: 15%, 27: 45%). **주문이 실패(miscast)하면 항상** 돌려받는다.
  - HP로 주문을 쓰는 캐릭터(Djinni)에게는 효과가 없다.
- **Mindtap**: 주문이 **성공했고** MP를 돌려받는 경우, 추가로
  - 시야 안의 **주문을 쓰는 적대 몬스터**(Antimagic이 통하고 아직 Antimagic 상태가 아닌 것) 하나하나가 **(주문 MP 비용)/9 확률**로 **Antimagic 2~5턴**에 걸린다.
  - 걸린 몬스터가 있으면 MP를 `1~3 + (걸린 수)/2`만큼 더 얻는다.
- MP를 돌려받을 때마다 "wizardly item" 사용으로 처리된다(Trog가 싫어함).

### sphere of Battle
- **Battle**: Battlesphere가 없고, 보이는 위험한 몬스터가 근처에 있고, 사용자 주변 2칸 안에 비행체가 설 수 있는 빈칸이 있으면 **매 행동마다 자동으로 Battlesphere를 소환**한다(MP 소모 없음).
  - 위력 = `round((15 + Conjurations 스킬 × 15) / 3)` = 약 `5 + Conjurations × 5`.
  - Battlesphere의 동작은 Conjurations 학파 문서(예정)에서 다룬다.
  - 소환할 때마다 "wizardly item" 사용으로 처리된다. 벗으면 Battlesphere가 사라진다.
- **Destructive**: **Conjurations 주문과 파괴(destructive) 플래그가 붙은 주문은 강화 +1단계, 그 밖의 모든 주문은 −1단계**(Spell power ÷2). Vehumet이 지원하는 주문과 같은 기준이다.

### Charlatan's Orb
- 진짜 Orb of Zot을 든 것과 같은 불이익을 준다.
  - **Stealth ÷3.**
  - **순간이동 방해**: Teleport는 지연이 5~9턴 늘어나고(보통 3~5턴 → 8~14턴), scroll of blinking은 지정할 수 있는 거리가 줄고 도착 지점이 흔들린다(상태 표시 "Orb?").
  - 사용자 주변 반경 2에 Orb의 빛이 보인다(표시 효과).
- **Charlatan**: **Evocations를 제외한 모든 스킬에 `기본 Evocations 스킬 × 20%`를 더한다.** 기본 스킬(다른 보정 전 실제로 올린 수치)을 기준으로 한다.
  - HP·MP가 스킬에 따라 달라지므로 끼고 벗을 때 다시 계산된다.

### skull of Zonguldrok
- Int +4, rN+, **Evil 아이템.**
- **Hat+: 머리 슬롯 +1.** hat뿐 아니라 helmet도 끼울 수 있다(종족의 helmet 제한은 그대로). 머리 장비를 끼우면 해골이 말을 한다(효과 없음).
- **Reaping**: 사용자가 **공격(근접·원거리 무기·투척 등 attack 처리)** 으로 준 데미지가 대상에 기록된다. 그 몬스터가 죽으면 **`기록된 데미지 / (그 몬스터가 받은 총 데미지 × 1.5)`** 확률로 영혼이 뜯겨 **아군 spectral thing**이 된다.
  - 혼자 다 깎았으면 확률 2/3. 주문 데미지는 기록되지 않는다.
  - Yredelemnul 신자이거나 Death Channel이 켜져 있으면 발동하지 않는다. 아군을 둘 수 없는 상태에서도 발동하지 않는다.
  - 공격이 맞을 때마다 Evil 행위로 처리된다.

### orb of Dispater
- **바닥에서 생성되지 않는다.** Dis의 Dispater가 들고 있고, 처치하면 얻을 수 있다(Dispater는 이 오브 외의 방패·오브를 들지 않는다).
- **AC +5**, **Evil 아이템**, **\*Corrode.**
- **발동(Evoke Damnation)**: MP 4, **HP 최대치의 10%** 를 소모해서 **Hurl Damnation**을 쏜다.
  - 위력 = `Evocations 스킬 × 8` (주문 위력 상한 200이 적용되지 않아 스킬 27에서 216).
  - 데미지 `3dN`, `N = (8 + 위력×3/5) / 3`. 스킬 10에서 3d18, 스킬 27에서 3d45. 사거리 6, 맞은 곳에서 폭발.
  - damnation 저항이 있는 몬스터는 피해가 없다. 쏠 때 Evil 행위로 처리된다.
  - Artifice를 희생한 경우(`MUT_NO_ARTIFICE`) 쓸 수 없다.

---

## 망토

### 수치표
| 언랜드 | 원형 (기본 AC) | 인챈트 | AC | 속성 |
|---|---|---|---|---|
| cloak of the Thief | cloak (1) | +0 | 1 | Stealth +1단계, SInv |
| cloak of Starlight | cloak (1) | +1 | 2 | EV +4, Stealth −2단계 |
| ratskin cloak | cloak (1) | +2 | 3 | Str −1, Int −1, Dex +1, rN+, rPois |
| fungal fisticloak | cloak (1) | +3 | 4 | HP −10, Int −2, Str −2 |
| dragonskin cloak | cloak (1) | +4 | 5 | Avatar's Aegis |
| scarf of invisibility | scarf (0) | +0 | 0 | +Inv |

### cloak of the Thief
- Stealth +1단계, SInv.
- **Quiet**: **사용자가 볼 수 있는 칸에서 나는 모든 소음의 크기가 절반**이 된다(몬스터가 내는 소리 포함). Dithmenos의 같은 권능과 겹치면 다시 절반.

### cloak of Starlight
- EV +4, **Stealth −2단계.**
- **Dazzle**: 인접한 몬스터의 근접 공격을 **회피했을 때**(막기는 해당 없음) 그 몬스터를 **4~8턴 실명(Blind)** 시킬 수 있다. 실명 저항이 강한 몬스터(res_blind 2 이상)와 이미 실명 중인 몬스터는 제외.
  - 확률 = `min(50, (95 − HD × 4) / 5) / 50`.
  - **코드에서 찾은 점**: 이 HD가 공격한 몬스터가 아니라 **방어하는 쪽, 즉 망토를 입은 플레이어의 경험 레벨(XL)** 이다(`melee-attack.cc`의 `do_starlight`에서 `defender->get_hit_dice()`). 비슷한 공식을 쓰는 Gloom 등은 대상의 HD를 쓴다. 그 결과 확률이 몬스터와 무관하게 **XL에 따라 줄어든다**: XL 1은 36%, XL 10은 22%, XL 20은 6%, **XL 23 이상은 0%**(0.34.1).

### ratskin cloak
- Str −1, Int −1, Dex +1, rN+, rPois.
- **Rats**: 피해를 받을 때(독 피해 제외) 확률 **`3 × min(데미지, 최대HP/2) / (2 × 최대HP)`** 로 **아군 쥐**가 나온다(최대HP의 절반 이상을 한 번에 받으면 75%).
  - hell rat 또는 river rat 중 하나(신이 싫어하는 종류는 제외. 둘 다 안 되면 나오지 않음). 소환 지속은 약 30턴(무작위 변동).
- 초반 언랜드(`MAX_LEVEL` 11).

### fungal fisticloak
- HP −10, Int −2, Str −2.
- **망토 슬롯과 함께 머리 슬롯도 차지한다**(머리 장비와 같이 쓸 수 없음). 게임 내 설명에는 이 점이 적혀 있지 않다.
- **Gloves+: 장갑 슬롯 +1.**
  - **코드에서 찾은 점**: 이 추가 슬롯은 "장갑을 낄 수 없는 종족" 판정보다 먼저 더해진다(`player-equip.cc`). 그래서 원래 장갑을 낄 수 없는 경우(몸집 Large 이상·Little 이하, Claws 3단계, Demonic Touch 3단계 등)에도 장갑 1개를 낄 수 있다. 장갑에는 별도의 몸집 검사가 없다(0.34.1, 실제 착용 미확인).
- **Shroompunch**: 매 행동마다 **1/4 확률**로, 인접한 보이는 적대 몬스터 중 무작위 하나에게 **보조 공격(aux attack) "shroompunch"**(기본 데미지 9)를 한다.
  - 맞은 대상이 숨을 쉬는 몬스터면 **1/3 확률로 혼란**.
- Fedhas 신자가 입으면 Fedhas가 기뻐하는 메시지가 나온다(효과 없음).

### dragonskin cloak
- **바닥에서 생성되지 않는다.** Tiamat이 항상 입고 나온다.
- **Avatar's Aegis**: rF, rC, rElec, rPois, rCorr, rN을 **판정할 때마다 각각 50% 확률로 +1.** 화면에 표시되는 저항에는 포함되지 않는다.

### scarf of invisibility
- **일반 게임에서는 나오지 않는다.** Sprint 맵 한 곳에서만 지정된다.
- +Inv(발동형 투명). 이 스카프로 투명해지면 **최대 HP가 줄지 않는다**(보통 발동형 투명은 최대 HP 감소가 있음).

---

## 머리

### 수치표
| 언랜드 | 인챈트 (= AC) | 에고 | 속성 |
|---|---|---|---|
| crown of Dyrovepreva | +3 | — | Int +2, rElec, SInv |
| hat of the Bear Spirit | +2 | Spirit Shield | Will++, \*Rage 20% |
| hood of the Assassin | +2 | — | Stealth +2단계 |
| mask of the Dragon | +2 | — | SInv |
| hat of the Alchemist | **−2** | — | rF+, rC+, Will+, rN+, rElec, rPois, rMut, rCorr |
| hat of Pondering | +3 | Ponderousness | Int +5, MP +10, Will+ |
| crown of vainglory | +3 | — | Will+, ^Fragile |

- 모두 원형은 hat(기본 AC 0)이다.

### crown of Dyrovepreva
- Int +2, rElec, SInv. 고유 효과는 없다.

### hat of the Bear Spirit
- 에고 **Spirit Shield**(받는 데미지를 HP와 MP로 나눠 받음), **Will++**, **\*Rage**: 적대 대상에게 근접 공격할 때 **20% 확률로 광폭화(Berserk)**.
- **Bear**: 광폭화 중 HP 배율이 **×1.5 대신 ×2**. 광폭화가 끝난 뒤 걸리는 감속 지속이 **2/3**로 줄어든다. 상태 표시가 "Bearserk"로 바뀐다.

### hood of the Assassin
- Stealth +2단계.
- **Detect**: **반경 4 안의 몬스터를 감지**한다(Antennae 돌연변이와 같은 방식, 둘 중 큰 반경 적용).
- **Stab+**: **모든 근접 무기와 맨손 공격이 Short Blades처럼 "좋은 암습"** 보너스를 받는다. 원거리 공격에는 해당 없음. dagger의 추가 보너스는 여전히 dagger에만 붙는다.
  - 암습 공식은 은신 & 암습 문서(예정)에서 다룬다.

### mask of the Dragon
- SInv.
- **Dragonpray**: 비용이 있는 신의 권능(Invocation)을 쓸 때, 보이는 위험한 적대 몬스터가 근처에 있으면 **`10% + 피에티 비용 평균 × 2%`** 확률로 **아군 드래곤**을 소환한다. 소환 지속은 약 10~30턴.
  - 드래곤 종류는 **경험 레벨(XL)** 에 따라 정해진다(신이 싫어하는 종류는 제외):

  | XL 범위 | 후보 |
  |---|---|
  | 0~13 | steam dragon |
  | 0~15 | acid dragon, swamp drake |
  | 9~18 | wind drake, death drake, rime drake |
  | 9~20 | lindwurm |
  | 15~22 | swamp dragon |
  | 17~24 | fire dragon, ice dragon |
  | 21~27 | iron dragon, storm dragon, shadow dragon |
  | 24~30 | quicksilver dragon, golden dragon |

- 신의 선물: Okawaru는 이 가면을 선물하지 않는다. Love를 희생한 상태에서 획득(acquirement)으로 나오면 파괴된다.

### hat of the Alchemist
- 인챈트 **−2**(AC −2). 대신 **rF+, rC+, Will+, rN+, rElec, rPois, rMut, rCorr**.

### hat of Pondering
- 에고 **Ponderousness**(이동 속도 +1 aut, 10 → 11), **Int +5, MP +10, Will+.**
- 몬스터 장비: Gastronok이 1/10 확률로 쓰고 나온다.

### crown of vainglory
- Will+, **^Fragile(벗으면 파괴).**
- **Ring++: 반지 슬롯 +2.**
- **Majesty**:
  - **반경 0의 후광(Halo)** 이 생긴다. 사용자 칸이 빛나므로 **투명해질 수 없고**, 빛에 드러난(backlit) 상태가 되어 **Stealth ×2/5**가 된다.
  - **층에 도착할 때마다**(층 이동 시) 시야 안에 아군이 아닌 몬스터가 있으면, 그 몬스터들을 모두 깨우고 자극하며 **12~22턴 동안 계단으로 층을 떠날 수 없고 왕관을 벗을 수도 없다.** Passage of Golubria와 transporter는 쓸 수 있다.

---

## 손

### 수치표
| 언랜드 | 인챈트 | AC | 속성 |
|---|---|---|---|
| gauntlets of War | +3 | 4 | Slay +5 |
| fencer's gloves | +0 | 1 | Dex +3 |
| Mad Mage's Maulers | +3 | 4 | −Cast |
| Delatra's gloves | +1 | 2 | — |
| gloves of the gadgeteer | +0 | 1 | ^Fragile |

- 모두 원형은 gloves(기본 AC 1)이다.

### gauntlets of War
- **Slaying +5.** 고유 효과는 없다.

### fencer's gloves
- Dex +3.
- **Riposte**: 몬스터의 근접 공격을 **회피하거나 막았을 때**, **1/3 확률로 즉시 반격**한다.
  - 근접 무기를 들었거나 맨손이어야 한다. 공격한 몬스터가 사용자의 공격 사거리(reach 포함) 안에 있어야 한다.
  - **같은 몬스터에게는 플레이어 행동 한 번 사이에 한 번만** 반격한다.
  - 회피 쪽은 사용자가 공격자를 볼 수 있고 행동 가능하며 혼란 상태가 아닐 때만 판정된다.

### Mad Mage's Maulers
- **−Cast: 주문을 쓸 수 없다.**
- **Infuse+∞**: 근접 공격이 명중할 때마다 **현재 MP를 전부 소모**하고, 소모한 MP 1당 **Slaying +4**를 그 공격에 더한다. → [Infusion 에고](brands-egos.md#능력치전투) (일반 Infusion은 타격당 MP 1)
  - Slaying은 `random(0 ~ 합계)`로 더해지므로 MP 1당 평균 데미지 +2. → [데미지 계산](weapons.md#31-계산-순서)
- **VampMP**: 근접 공격으로 데미지를 주면 **데미지 / 8**만큼 MP를 회복한다.
- HP로 주문을 쓰는 캐릭터(Djinni)에게는 Infuse가 작동하지 않는다.

### Delatra's gloves
- **ID++**: **처음 보는(미감정) 포션을 마시면** heal wounds 효과(HP `10 + random2avg(28, 3)` = 10~37 회복), **처음 보는 스크롤을 읽으면** potion of magic 효과(MP `10 + random2avg(28, 3)` 회복).
  - 이 회복은 [포션 회복 배율](potions.md#41-포션-회복-배율)의 영향을 받지 않는다. robe of Vines나 포션 회복 불가 상태에서도 HP가 회복되고, Kryia's mail coat로 2배가 되지도 않는다.
- 초반 언랜드(`MAX_LEVEL` **6**).

### gloves of the gadgeteer
- **^Fragile(벗으면 파괴).**
- **Gadgeteer**:
  - **완드 위력 ×1.3**(완드 주문의 위력 상한은 그대로).
  - 완드를 쓸 때 **30% 확률로 충전을 소모하지 않는다.**
  - 발동 아이템(Evoker)의 재충전 속도(경험치에 따른 충전) ×1.3.
- Coglin의 gizmo "Gadgeteer"도 충전 보존·재충전은 같지만, **완드 위력 ×1.3은 이 장갑에만** 있다.

---

## 발

### 수치표
| 언랜드 | 원형 (기본 AC) | 인챈트 | AC | 에고 | 속성 |
|---|---|---|---|---|---|
| seven-league boots | boots (1) | +3 | 4 | — | Rampage+∞ |
| mountain boots | boots (1) | +3 | 4 | — | rC+ |
| slick slippers | boots (**0**) | +2 | 2 | — | EV +4 |
| lightning scales | barding (4) | +6 | 10 | — | rElec |
| Black Knight's barding | barding (4) | +10 | 14 | Ponderousness | rN+, rPois, Evil |

- barding은 barding을 입는 종족만 쓸 수 있다. → [슬롯과 착용 제한](armour.md#1-슬롯과-착용-제한)

### seven-league boots
- **Rampage+∞**: Rampaging 에고처럼 적을 향해 이동하면 여러 칸을 한 번에 이동하는데, **이동 칸 수가 시야 반경만큼**(보통 7)이다(일반 Rampaging은 최대 3).
  - 여러 칸을 이동해도 걸리는 시간은 **한 칸 이동의 평균 시간**이다.
  - **대상 몬스터는 경계 상태가 된다**(시야 끝에서 달려가 잠든 적을 암습하는 것을 막기 위함).
  - 도착해서 공격하는 규칙(대상을 비틀거리게 함, 공격이 이동보다 느리면 데미지 감소)은 일반 Rampaging과 같다. → [능력치·전투 에고](brands-egos.md#능력치전투)
- 여러 칸 이동은 Cheibriados가 싫어하는 서두름(hasty) 행위로 처리된다.

### mountain boots
- rC+.
- **Steadfast**: **강제 이동을 막는다** — 넉백, 짓밟기(trample), 끌어당기기(촉수·주문), 노래에 끌려가기, vortex, 함정 샤프트로 떨어지기 등. 블링크·순간이동·추방(banishment)은 막지 않는다.
- 몬스터가 주울 수 없다(`special`).

### slick slippers
- **원형 boots의 기본 AC 1이 0으로 바뀐다**(AC = 인챈트 +2). EV +4.
- **Slick**: **조이기(constrict), 그물, 거미줄, binding sigil, bolas, Grave Claw의 꿰뚫기**에 걸리지 않는다.
- **Slippery**: 인접한 몬스터의 근접 공격에 **맞아서 데미지를 받으면 항상 1칸 뒤로 미끄러진다.** 공격한 몬스터는 이동할 수 있으면 그 칸으로 따라온다.
  - 뒤 칸이 막혀 있거나 다른 대상이 있으면 미끄러지지 않는다. 계단을 오르내리는 중에는 발동하지 않는다. 끌어당기기(AF_DRAG) 공격에는 발동하지 않는다.

### lightning scales
- barding +6, rElec.
- **Swift**: **이동 속도 −1 aut**(10 → 9).
- 이동할 때마다 Cheibriados가 싫어하는 서두름 행위로 처리되고, 서두름 아이템으로 취급된다.

### Black Knight's barding
- barding +10. 에고 **Ponderousness**(이동 속도 +1 aut), **rN+, rPois, Evil 아이템.**
- 입고 있으면 시간 비례로 10턴당 평균 1회 Evil 행위로 처리된다(선한 신이 싫어함).

> 출처: art-data.txt, art-func.h, artefact.cc, item-prop.cc, player.cc, player-equip.cc, player-act.cc, player-reacts.cc, melee-attack.cc, attack.cc, ranged-attack.cc, fight.cc, actor.cc, beam.cc, fineff.cc, spl-cast.cc, spl-util.cc, spl-monench.cc, spl-transloc.cc, ability.cc, acquire.cc, item-use.cc, potion.cc, evoke.cc, movement.cc, stairs.cc, areas.cc, cloud.cc, shout.cc, ouch.cc, traps.cc, mon-death.cc, mon-place.cc, mon-gear.cc, mon-ench.cc, monster.cc, orb.cc, god-abil.cc, zap-data.h (0.34.1)
