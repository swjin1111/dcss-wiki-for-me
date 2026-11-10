# 아이템 (Items)

> 기준: DCSS 0.34.1

## 문서 목록

| 분류 | 문서 | 상태 |
|---|---|---|
| 브랜드·에고 (무기 브랜드, 방어구 에고, 투척 브랜드) | [brands-egos.md](brands-egos.md) | 작성 |
| 아티팩트 속성 (랜덤 아티팩트) | [artefact-properties.md](artefact-properties.md) | 작성 |
| 언랜드 아티팩트 — 무기 | [unrands-weapons.md](unrands-weapons.md) | 작성 |
| 언랜드 아티팩트 — 방어구 | [unrands-armour.md](unrands-armour.md) | 작성 |
| 언랜드 아티팩트 — 장신구 | [unrands-jewellery.md](unrands-jewellery.md) | 작성 |
| 무기 (근접·원거리·투척, 전투 공식) | [weapons.md](weapons.md) | 작성 |
| 방어구 (AC·EV·SH·방해도, 몬스터 공격과 방어) | [armour.md](armour.md) | 작성 |
| 포션 | [potions.md](potions.md) | 작성 |
| 스크롤 (아이템 세트, Acquirement 포함) | [scrolls.md](scrolls.md) | 작성 |
| 완드·발동 아이템 (Evoker) | [wands-evokers.md](wands-evokers.md) | 작성 |
| 반지·목걸이 (Jewellery) | [jewellery.md](jewellery.md) | 작성 |
| 지팡이 (Magical Staves) | [staves.md](staves.md) | 작성 |
| 탈리스만 | [talismans.md](talismans.md) | 작성 중 (공통 규칙, 1~3등급) |
| 특수 아이템 (룬, Gem, Orb of Zot, Gizmo, Bauble) | `special-items.md` | 예정 |

현재 버전에서 원거리 무기는 탄약을 쓰지 않는다. 화살·볼트·탄환 같은 탄약 아이템은 세이브 호환용으로만 남아 있고 생성되지 않는다.

---

## 감정 (Identification)
아이템 종류마다 감정되는 방식이 다르다.

| 분류 | 감정 방식 |
|---|---|
| 무기, 방어구, 반지·목걸이, 지팡이, Gizmo, 탈리스만, 완드 | **그 칸에 올라서기만 하면 자동 감정.** 인챈트 수치와 브랜드, 아티팩트 속성까지 전부 보인다. |
| 포션, 스크롤 | 사용하거나 Scroll of Identify로 감정. 같은 종류는 한 번 감정하면 이후 전부 알게 된다. |
| 투척 무기, 마법서, 발동 아이템(Evoker), 룬, Gem, 골드 등 | 처음부터 종류가 알려져 있다. |

- 아티팩트는 종류 지식이 공유되지 않는다. 아티팩트마다 따로 감정된다(올라서면 감정되는 것은 같다).
- Ashenzari 신자는 추가로 감정 관련 혜택이 있다(신 문서에서 다룰 예정).

## 인챈트 (Enchantment, +N)
무기와 방어구에는 `+N` 수치가 붙는다. Scroll of Enchant Weapon / Enchant Armour로 올릴 수 있다.

### 효과
- **무기**: +1당 명중 +1, 데미지는 최대 +1(평균 +0.5). 인챈트와 Slaying 합계만큼 `random(0 ~ 합계)`가 더해지기 때문이다. → [무기 문서](weapons.md#31-계산-순서)
- **방어구**: +1당 AC +1. **방패는 AC 대신 SH가 오른다.**

### 스크롤로 올릴 수 있는 상한
| 대상 | 상한 |
|---|---|
| 무기 | +9 |
| 몸통 방어구 (Barding 포함) | **기본 AC와 같은 값** (예: plate armour 기본 AC 10 → +10) |
| 방패 | `(기본 SH − 3)/2 + 3` → buckler +3, kite shield +5, tower shield +8 |
| 그 밖의 보조 장비 (투구·장갑·부츠·망토 등) | +2 |
| 인챈트 불가 | quicksilver dragon scales, scarf, orb |

- 상한은 스크롤로 올릴 수 있는 한계일 뿐이다. 생성될 때부터 상한을 넘는 아이템도 있다.
- **아티팩트는 인챈트할 수 없다.** 예외로 Mountain Dwarf는 랜덤 아티팩트(randart)를 인챈트할 수 있다. 언랜드 아티팩트는 Mountain Dwarf도 안 된다.

## 아이템 생성 (간략)
- **아이템 레벨**: 층에 떨어지는 아이템은 기본적으로 **절대 깊이**(D:1 = 0부터 1씩 증가)를 아이템 레벨로 쓴다.
  - Vaults는 ×1.5. Orcish Mines는 골드가 주로 나오고 레벨 ×2.
  - 볼트(vault)나 보상으로 지정된 "좋은 아이템"은 별도의 높은 레벨로 생성된다.
- **무기·방어구가 아티팩트가 될 확률**: `(101 + 아이템 레벨 × 3) / 4000`.
  - 아이템 레벨이 0이면(D:1) 확률 0. D:2에서 약 2.6%, 깊이 27에서 약 4.6%.
  - 그중 **1/20은 언랜드 아티팩트 시도**. 좋은 아이템으로 지정된 경우는 1/7.
- **일반 무기의 브랜드·인챈트**: `(51 + 레벨)/200` 확률로 "좋은 아이템" 판정을 받는다. 그 안에서 `(101 + 레벨)/300` 확률로 브랜드를 굴린다. 어떤 브랜드가 나오는지는 무기 계열별 가중치를 따른다([브랜드·에고](brands-egos.md) 참고).
- **일반 방어구의 에고**: `(51 + 레벨)/250` 확률로 "좋은 아이템" 판정을 받고, 그 안에서 `(31 + 레벨)/350` 확률로 에고가 붙는다. 보조 장비는 추가로 `(레벨×3 + 15)/200` 확률의 에고 판정이 한 번 더 있다.
- 전체적으로 **깊이 내려갈수록 아티팩트·브랜드·인챈트 확률이 오른다.**

## 아티팩트 개요
| | 랜덤 아티팩트 (Randart) | 언랜드 아티팩트 (Unrand) |
|---|---|---|
| 정의 | 무작위로 이름과 속성이 정해지는 아티팩트 | 이름·속성·고유 효과가 정해진 아티팩트 |
| 개수 | 무제한 | 무작위 생성 가능 **112개** (무기 51 / 방어구 47 / 장신구 14) + 특정 장소에서만 나오는 것 9개 |
| 속성 | [아티팩트 속성](artefact-properties.md) 참고 | [언랜드 무기](unrands-weapons.md), [언랜드 방어구](unrands-armour.md), [언랜드 장신구](unrands-jewellery.md) 참고 |

- **언랜드는 한 게임에 하나씩만** 나온다.
  - 초반용 언랜드는 지정된 깊이 이하에서 가중치 100, 그보다 깊으면 1. 일반 언랜드는 깊이와 무관하게 가중치 10.
  - Abyss에서 잃어버린 언랜드는 Abyss에서 다시 생성될 수 있다.
  - Pandemonium 바닥에서는 언랜드가 생성되지 않는다.
- Club은 아티팩트가 되지 않는다.

> 출처: item-name.cc, items.cc, item-prop.cc, item-prop.h, defines.h, player.cc, attack.cc, makeitem.cc, dungeon.cc, artefact.cc, art-data.txt (0.34.1)
