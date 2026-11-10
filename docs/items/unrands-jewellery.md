# 언랜드 아티팩트 — 장신구 (Unrandart Jewellery)

> 기준: DCSS 0.34.1 · [아이템 목록으로](index.md)
>
> **작성 진행 상황**: 16종 전부 작성 완료.

이름·속성·고유 효과가 정해진 반지·목걸이 아티팩트를 정리한다. 원형 장신구의 효과와 슬롯 규칙은 [반지·목걸이 문서](jewellery.md), 아티팩트 속성(rF, Will, Slay 등)의 의미는 [아티팩트 속성](artefact-properties.md) 참고. 이 문서는 **원형과 달라진 점과 고유 효과** 위주로 쓴다.

---

## 공통 규칙
- **한 게임에 하나씩만** 존재한다(예외: ring of the Octopus King은 종류를 바꿔 최대 8개). 생성 가중치와 깊이 규칙은 [아이템 개요](index.md#아티팩트-개요) 참고.
- **원형 장신구의 기본 효과는 그대로 유지된다.** 예: ring of the Mage는 ring of wizardry의 실패율 감소를 그대로 가진다.
- 원형이 **amulet of nothing**(효과 없는 목걸이)인 것은 아래 속성과 고유 효과만 가진다. amulet of nothing은 언랜드의 기반으로만 쓰이고 그 자체로는 생성되지 않는다.
- 반지의 수치(+N)는 언랜드에 정해진 값이 일반 반지의 고정 수치를 대신한다(ring of the Hare, ring of the Tortoise).
- 그 칸에 올라서면 자동 감정된다.
- **Regen·RegenMP 속성은 regeneration 목걸이와 같은 동조(attunement) 규칙**을 따른다. → [동조](jewellery.md#41-regeneration--magic-regeneration)
- 바닥에서 생성되지 않는 것: amulet of invisibility(일반 게임에서는 나오지 않음), dreamdust necklace(dreamshard necklace가 깨져서 생기는 것).

## 전체 목록
바닥 무작위 생성 가능 14개 + 생성되지 않는 것 2개 = 16개. (삭제된 amulet of Cekugob은 제외)

| 종류 | 언랜드 | 원형 | 속성 | 고유 효과 |
|---|---|---|---|---|
| 반지 | [ring of Shadows](#ring-of-shadows) | ring of stealth | Stealth +1단계, +Inv | Umbra |
| | [ring of the Hare](#ring-of-the-hare) | ring of evasion | **EV +10** | — |
| | [ring of the Tortoise](#ring-of-the-tortoise) | ring of protection | **AC +8** | — |
| | [ring of the Mage](#ring-of-the-mage) | ring of wizardry | Archmagi | — |
| | [ring of the Octopus King](#ring-of-the-octopus-king) | 8종 중 하나 | AC +2, EV +2, SH +2, HP +2 | 종류별로 하나씩 최대 8개 |
| 목걸이 | [amulet of the Air](#amulet-of-the-air) | nothing | Air 강화, rElec, Fly, RMsl | Inacc |
| | [amulet of the Four Winds](#amulet-of-the-four-winds) | nothing | rN+, Will+++, Clarity | — |
| | [necklace of Bloodlust](#necklace-of-bloodlust) | nothing | Int −3, Will++, \*Rage 50%, Slay +6 | Fury |
| | [brooch of Shielding](#brooch-of-shielding) | guardian spirit | **SH +8** | — |
| | [amulet of Vitality](#amulet-of-vitality) | nothing | Regen +2, RegenMP +2 | — |
| | [macabre finger necklace](#macabre-finger-necklace) | nothing | rN+, HP +7, Evil | 반지 슬롯 +1 |
| | [dreamshard necklace](#dreamshard-necklace) | the acrobat | — | 치명상 1회 무효 |
| | [amulet of Elemental Vulnerability](#amulet-of-elemental-vulnerability) | nothing | **AC +8**, rPois, rF−−, rC−− | — |
| | [Hermit's Pendant](#hermits-pendant) | faith | MP +5 | Invocations 14, Evocations 0 |
| | [amulet of invisibility](#amulet-of-invisibility) (생성 안 됨) | nothing | +Inv | — |
| | [dreamdust necklace](#dreamdust-necklace) (생성 안 됨) | the acrobat | — | — |

---

## 반지

### ring of Shadows
- 원형 ring of stealth(일반 생성에서는 삭제된 반지)지만 **Stealth +1단계 효과는 그대로 있다.** 여기에 +Inv(발동형 투명, 보통처럼 최대 HP 감소가 따름).
- **Umbra(그림자 오라), 반경 3**: eveningstar "Brilliance"와 같은 효과다. → [eveningstar "Brilliance"](unrands-weapons.md#eveningstar-brilliance)
  - 사용자는 nightvision을 얻는다.
  - 오라 안의 대상을 공격하는 쪽은 nightvision이 없으면 명중이 깎인다.
  - 사용자가 오라 안에 있고 빛에 드러나 있지 않으면 Stealth ×1.5.
- 몬스터가 껴도 같은 반경 3의 Umbra가 생긴다.

### ring of the Hare
- ring of evasion이지만 수치가 **+10**(일반 +5). → [수치가 있는 반지](jewellery.md#2-수치n가-있는-반지)

### ring of the Tortoise
- ring of protection이지만 수치가 **+8**(일반 +4). Armour 스킬 배율을 받지 않는 고정 AC다.

### ring of the Mage
- ring of wizardry(마법 실패율 감소 → [ring of wizardry](jewellery.md#31-ring-of-wizardry)) + **Archmagi**(모든 마법 강화 +1단계, Spell power ×1.5).
- randart에서 Archmagi는 robe에만 붙지만, 이 반지에는 붙어 있다.
- "wizardly item"으로 취급된다(Trog가 싫어함).

### ring of the Octopus King
- **한 게임에 최대 8개**가 나올 수 있다. 하나가 생성될 때마다 아래 8종 중 **아직 나오지 않은 종류** 하나로 정해진다. 8종이 다 나오기 전까지는 "이미 존재함" 표시가 다시 풀려서 또 생성될 수 있다.

  | 원형 반지 (8종) |
  |---|
  | see invisible, protection from fire, protection from cold, resist corrosion, flight, wizardry, magical power, positive energy |

- 모든 반지에 **AC +2, EV +2, SH +2, HP +2**가 붙는다. 원형 반지의 효과도 그대로 있다.
- 장착한 개수만큼 trident of the Octopus King의 인챈트가 오른다(+8 + 2×개수). → [trident of the Octopus King](unrands-weapons.md#trident-of-the-octopus-king)
- 반지 8개를 동시에 끼려면 반지 슬롯이 8개 필요하다(Octopode). → [슬롯](jewellery.md#1-슬롯)
- Abyss에서 마지막 하나(8번째 종류)를 잃어버린 경우에는 다시 생성되지 않는다.
- 이름에 다른 아티팩트처럼 "the"가 붙지 않는다(여러 개가 있으므로).

---

## 목걸이

### amulet of the Air
- **Air 마법 강화 +1단계, rElec, 비행(Fly), RMsl**(투사체에 대한 EV +15).
- **Inacc(부정확)**: 사용자의 **근접·원거리 공격 명중 −5**, 사용자가 쏘는 **볼트형 주문·완드의 명중치 −5**(반드시 명중하는 효과는 영향 없음).
  - 같은 페널티를 주는 `MUT_MISSING_EYE`와 합산된다(1단계당 −5).

### amulet of the Four Winds
- **rN+, Will+++, Clarity**(혼란 면역). 고유 효과는 없다.

### necklace of Bloodlust
- **Int −3, Will++, Slay +6, \*Rage 50%**(적대 대상에게 근접 공격할 때 50% 확률로 광폭화).
- **Fury**: **광폭화 중에 적을 직접 죽이면(처치 판정 `KILL_YOU`. 원거리 무기·볼트형 주문 처치는 해당 없음) 1/2 확률로 광폭화 지속 1~2턴 연장.** Wrath of Trog의 효과와 같은 크기다.
  - Trog 신자의 신앙 효과로 연장이 먼저 발동했으면 발동하지 않는다. Wrath of Trog와 함께 쓰면 이 목걸이 쪽만 판정한다(중복 연장 없음).

### brooch of Shielding
- 원형 guardian spirit(받는 데미지를 HP와 MP로 나눠 받음 → [guardian spirit](jewellery.md#42-guardian-spirit)) + **표시 SH +8**.
- SH +8은 Shields 스킬·Dex와 무관한 고정값이며 방패 SH에 더해진다. **방패가 없어도 이 SH로 막기 판정을 한다**(amulet of reflection과 같은 방식). → [SH와 막기](armour.md#5-sh와-막기-shields--blocking)

### amulet of Vitality
- **Regen +2, RegenMP +2**(HP 재생 +160, MP 재생 +80, [재생량](jewellery.md#41-regeneration--magic-regeneration) 기준). 고유 효과는 없다.
- HP와 MP 재생을 둘 다 주므로 **HP와 MP가 둘 다 가득 차야** 동조된다.

### macabre finger necklace
- **rN+, HP +7, Evil 아이템.**
- **Ring+: 반지 슬롯 +1.** → [슬롯](jewellery.md#1-슬롯)
- **매 행동마다 Evil 행위 1회**로 처리된다(선한 신이 싫어함).

### dreamshard necklace
- 원형 the acrobat(이동·대기 직후 EV +15 → [the acrobat](jewellery.md#45-the-acrobat)). 몬스터가 주울 수 없다(`special`).
- **Dream: 치명적인 피해를 한 번 막아 준다.** 받은 피해가 현재 HP 이상이면:
  - 그 피해를 무시하고 **HP가 1**이 되며, 중독이 사라진다.
  - **다음 턴이 시작될 때까지** 어떤 피해로도 죽지 않는다(Death's Door와 같은 보호 범위).
  - 아군을 둘 수 있는 상태면 **그 층에 맞는 무작위 아군 몬스터 2~5마리**를 소환한다(소환 지속 약 40턴).
  - Still Winds 상태가 아니면 사용자 주변에 **fluffy cloud**(시야를 가리는 무해한 구름)를 크게 퍼뜨린다.
  - 자고 있었다면 깨어난다.
  - 목걸이는 **dreamdust necklace**로 바뀐다(벗겨지지 않고 그대로 착용 상태).
- 막지 못하는 경우: 용암·물에 빠지는 등 지형에 의한 사망, Zot에 의한 사망, 던전을 떠나는 것 등 Death's Door로도 막을 수 없는 죽음.

### amulet of Elemental Vulnerability
- **AC +8, rPois**, 그리고 **rF−−, rC−−.** 고유 효과는 없다.
- 초반 언랜드(`MAX_LEVEL` 11): 깊이 11 이하에서 생성 가중치가 높다.

### Hermit's Pendant
- 원형 faith(Piety 획득·손실 ×1.25, 빼면 Piety 1/3 손실 → [faith](jewellery.md#43-faith)) + **MP +5**.
- **Invo=14: Invocations 스킬이 정확히 14가 된다.** 실제 스킬이 14보다 높아도 14로 고정된다(이 경우 오히려 손해).
- **Evo=0: Evocations 스킬이 0이 된다.**
- 이 고정값은 다른 스킬 보정(Ashenzari, Heroism, Charlatan's Orb 등)보다 먼저 적용되고 그 보정을 무시한다. 스킬 화면에서도 보너스(14 미만일 때)·페널티로 표시된다.
- 초반 언랜드(`MAX_LEVEL` 9).

### amulet of invisibility
- **일반 게임에서는 나오지 않는다.** Sprint 맵 한 곳에서만 지정된다.
- +Inv(발동형 투명). 이 목걸이로 투명해지면 **최대 HP가 줄지 않는다.**

### dreamdust necklace
- dreamshard necklace가 효과를 쓰고 바뀐 것. 원형 the acrobat의 효과만 남는다. 몬스터가 주울 수 없다.

> 출처: art-data.txt, art-func.h, artefact.cc, item-name.cc, player.cc, player-equip.cc, actor.cc, attack.cc, beam.cc, areas.cc, mon-death.cc, ouch.cc, spl-goditem.cc, skill-menu.cc, ability.cc, god-item.cc, dat/des (0.34.1)
