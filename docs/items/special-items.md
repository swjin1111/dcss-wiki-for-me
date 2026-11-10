# 특수 아이템 (Runes, Gems, Orb of Zot, Gizmos, Baubles 등)

> 기준: DCSS 0.34.1 · [아이템 목록으로](index.md)

장비·소모품 어디에도 속하지 않는 특수 아이템을 정리한다: 룬, Gem, Orb of Zot, Coglin의 Gizmo, flux bauble, ziggurat figurine, shop voucher, quad damage. 각 아이템이 놓이는 장소(브랜치 구조)의 상세는 던전 문서(예정)에서 다룬다.

---

## 1. 룬 (Runes of Zot)

- 룬은 무게가 없고, 주우면 **룬 목록에 기록**된다(`}` 키로 확인). 버리거나 잃어버릴 수 없다.
- **Realm of Zot 입구는 룬 3개 이상**이 있어야 들어갈 수 있다(`ZOT_ENTRY_RUNES`, Descent 모드 제외).
- **Vaults**: 룬 없이 Vaults에 들어가면 입구 문이 닫히고(`lock_vaults`), **룬이 1개 이상 있어야 Vaults를 나갈 수 있다.**
- 한 게임에서 얻을 수 있는 룬은 최대 **15개**(`MAX_RUNES`).

| 룬 | 얻는 곳 |
|---|---|
| decaying (Swamp), barnacled (Shoals), serpentine (Snake), gossamer (Spider) | Lair 하위 브랜치의 마지막 층. 게임마다 Swamp/Shoals 중 하나, Snake/Spider 중 하나만 생성되므로 이 중 2개 |
| slimy (Slime) | Slime Pits 마지막 층 |
| silver (Vaults) | Vaults 마지막 층 |
| golden (Tomb) | Tomb 마지막 층 |
| iron (Dis), obsidian (Gehenna), icy (Cocytus), bone (Tartarus) | 각 지옥의 마지막(7) 층 |
| abyssal | Abyss 3층 이상에서 생성될 수 있다. 층마다 생성 확률 가중치 3층 10, 4층 15, 5층 22, 6~7층 100(Lugonu 권능 5단계면 2배). 줍는 순간 Abyss 출구로 안내 |
| demonic ×1, glowing (Mnoleg), magical (Lom Lobon), fiery (Cerebov), dark (Gloorx Vloq) | Pandemonium |

- elven·mossy 룬(RUNE_ELF, RUNE_FOREST)은 Sprint 전용이다.
- 이름(색)은 `rune_type_name` 기준이며, 정확한 생성 위치·볼트는 던전 문서에서 다룬다.

---

## 2. Gem

Gem은 각 브랜치의 **마지막 층**에 놓이는 수집품이다(보통 브랜치 끝 볼트). **게임 플레이 효과는 없고**, 점수 기록(획득·보존한 gem 수, 마일스톤)에만 쓰인다.

### 2.1 Gem 시간 제한
- 각 gem에는 **그 브랜치 안에서 보낼 수 있는 시간**이 정해져 있다. 그 브랜치(어느 층이든)에 있는 동안 시간이 흐르고, 한도를 넘으면 **Zot의 힘이 gem을 부순다**.
  - 아직 줍지 않았으면 바닥의 gem이 부서진다. **이미 주운 gem도 부서진다**(gem은 "보존"되지 않음).
  - 한도 = **층당 시간 × 그 브랜치 층 수**.
- **Orb of Zot을 들고 있으면 gem 시간이 멈춘다.** Sprint·Descent 모드에서는 gem 시간이 없다.
- 남은 시간이 270턴, 100턴이 될 때 경고가 나온다(옵션 `more_gem_info`).

| Gem | 브랜치 | 층당 | 층 수 | 한도(턴) |
|---|---|---|---|---|
| smoky | Dungeon | 600 | 15 | 9000 |
| shimmering | Elven Halls | 600 | 3 | 1800 |
| earthy | Lair | 750 | 5 | 3750 |
| mossy | Swamp | 450 | 4 | 1800 |
| azure | Shoals | 450 | 4 | 1800 |
| jade | Snake Pit | 600 | 4 | 2400 |
| milky-white | Spider Nest | 600 | 4 | 2400 |
| starry | Slime Pits | 150 | 5 | 750 |
| shining | Vaults | 750 | 5 | 3750 |
| ivory | Crypt | 600 | 3 | 1800 |
| sanguine | Tomb | 600 | 3 | 1800 |
| midnight | Depths | 750 | 4 | 3000 |
| prismatic | Zot | 200 | 5 | 1000 |

- glittering gem(Orcish Mines)은 세이브 호환용으로만 남아 있고 생성되지 않는다.
- 이번 게임에 생성되지 않은 브랜치의 gem은 "모든 gem 수집" 판정에서 제외된다.

---

## 3. Orb of Zot

Zot:5에 있는 Orb of Zot을 주우면 **탈출(orb run)**이 시작된다. Orb을 가진 채로 D:1의 출구 계단으로 나가면 승리한다(Orb 없이 나가면 게임 종료).

### 3.1 줍는 순간
- **크기 30의 소음**(Silence 중이면 빛 효과만).
- "The lords of Pandemonium are not amused" 메시지와 함께 orb run 단계가 된다(Cheibriados 권능이 있으면 완화 메시지).

### 3.2 Orb을 가지고 있는 동안
- **Stealth ÷3.** → 은신 문서(예정)
- **순간이동 제한**: Teleport 지연 +5~9턴, scroll of blinking·controlled blink는 사거리 감소와 도착점 흔들림. → [teleportation](scrolls.md#22-teleportation), [blinking](scrolls.md#25-blinking)
- **Zot 시계와 gem 시간이 멈춘다.**
- **orb run 중 몬스터 추가 생성**: Abyss가 아니면 플레이어 근처에 몬스터가 계속 생성된다(생성 주기 기본 18, Cheibriados 권능 36). 상세는 던전 문서에서 다룬다.
- Charlatan's Orb(언랜드)는 Stealth÷3과 순간이동 제한만 같다. → [Charlatan's Orb](unrands-armour.md)

---

## 4. Gizmo (Coglin 전용)

- **Coglin**은 **XL 14**에 능력 **Invent Gizmo**를 얻는다. 사용하면 **3개의 gizmo 중 하나를 골라 조립**하고 전용 gizmo 슬롯에 바로 장착한다(한 번만). 그 전에도 레벨업 중에 앞으로 만들 gizmo의 이름이 미리 공개된다.
- 각 gizmo는 **희귀 속성 1개 + 일반 속성 2개**를 가진다. 세 gizmo의 속성은 서로 겹치지 않게 섞어서 배분된다(일반 속성 6종은 세 gizmo에 전부 한 번씩 나타남).

| 분류 | 속성 | 효과 |
|---|---|---|
| 일반 | rF | rF+ |
| 일반 | rC | rC+ |
| 일반 | rElec | rElec |
| 일반 | rPois | rPois + rCorr |
| 일반 | Slay | Slaying +3 |
| 일반 | Wiz | Wizardry + 최대 MP +4 |
| 희귀 | Regen | HP 재생 + MP 재생 |
| 희귀 | Repel | RMsl(투사체 회피) + Clarity |
| 희귀 | Rampage | Rampage + Acrobat (Cheibriados 신자에게는 나오지 않음) |
| 희귀 | **Gadgeteer** | 완드 충전 30% 보존, 발동 아이템 재충전 경험치 ×1.3 → [완드](wands-evokers.md#22-충전-charges) |
| 희귀 | **RevGuard** | 회전(rev) 단계에 따라 **AC +2/+4/+5**. 회전 최고 상태에서 근접 공격 시 낮은 확률로 상대 무기를 떨어뜨림 |
| 희귀 | **Spellmotor** | 주문 MP 비용 −회전 단계(최소 1). 주문을 시전하면 추가 공격이 발동 |
| 희귀 | **Autodazzle** | 공격받을 때 1/20 확률로 공격자에게 dazzle 투사체(위력 = XL) |

- 회전(rev) 단계는 Coglin의 종족 특성이다(종족 문서에서 다룰 예정).

---

## 5. flux bauble

- **사용하면 부서지면서 flux form으로 변신**한다. 탈리스만 형태 중에도 쓸 수 있고, 끝나면 원래 형태로 돌아간다.
- flux form (Shapeshifting 5~14, 스킬 부족 시 HP 페널티가 **2배**(레벨당 −20%)):
  - 녹아듦: 무기·방패, 몸통, 장갑. EV +6 ~ +16.
  - **빛남(backlit)**: 투명해질 수 없고 쉽게 보인다.
  - **근접 데미지 절반.**
  - **Contaminating**: 근접 공격이 명중할 때마다 대상의 오염 단계가 오르고, 이미 2단계인 대상을 치면 **`2d(5 + 2s)`** 피해(스킬 5 → 2d15, 14 → 2d33)와 함께 **malmutate**를 일으키고 오염을 지운다(즉 같은 대상을 세 번째 칠 때 터짐).
  - **에너지 45**로 시작하고 명중할 때마다(폭발을 일으킨 타격은 제외) 1~2씩 줄어 **0이 되면 형태가 끝난다**(10 미만이 되면 경고).
- 생성: 무작위 아이템이 `1/275 × (1 − 아이템 레벨/35)` 확률로 bauble이 된다(얕은 곳일수록 잘 나옴).

---

## 6. 그 밖의 특수 아이템

### ziggurat figurine
- Ziggurat **마지막(27) 층의 출구**에 놓인다.
- 사용하면 그 자리에 **Ziggurat 입구**가 생긴다. 계단 등 중요한 지형 위, Arena, 임시 지형 위, 이미 진행 중인 Ziggurat가 있을 때는 쓸 수 없다.
- Sacrifice Artifice의 영향을 받지 않는다(Berserk·Confusion 중에는 다른 발동 아이템처럼 쓸 수 없다).
- 참고: **Ziggurat를 한 번이라도 완주하면(`zigs_completed`) Zot 시계가 영구히 멈춘다**(`zot.cc` zot_immune). → 던전 문서

### shop voucher
- **Descent 모드에서만** 쓰이는 아이템. 주우면 바우처 수가 늘고, **상점에서 아이템 하나를 금화 없이 살 수 있다**(1장 소모). Descent 모드는 시작할 때 1장을 받는다.

### quad damage
- **Sprint 전용.** 사용하면 30턴 동안 Quad Damage 상태가 된다: **플레이어가 주는 피해 ×4**(Torment 피해 제외), 몸이 빛나서(backlit) 투명해질 수 없다.

### horn of Geryon
- 발동 아이템이다. → [완드·발동 아이템](wands-evokers.md#horn-of-geryon)

> 출처: item-prop-enum.h, item-prop.cc, items.cc, zot.cc, zot.h, orb.cc, main.cc, stairs.cc, abyss.cc, abyss.h, mon-place.cc, player.cc, acquire.cc, acquire.h, artefact.cc, attack.cc, melee-attack.cc, spl-cast.cc, spl-util.cc, evoke.cc, transform.cc, transform.h, dat/forms/flux.yaml, makeitem.cc, shopping.cc, ng-setup.cc, dat/dlua/ziggurat.lua, branch-data.h, defines.h (0.34.1)
