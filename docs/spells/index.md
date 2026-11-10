# 마법 (Spells)

> 기준: DCSS 0.34.1

플레이어 마법의 공통 규칙(위력·실패율·MP·사거리·소음·기억)과 학파별 문서 목록. 개별 마법은 학파 페이지에 있다. 완드에 들어 있는 주문의 상세는 [완드 문서](../items/wands-evokers.md#23-완드-목록)에 있다.

---

## 학파 (Schools)

0.34.1의 학파는 11개이고, 각각 같은 이름의 마법 스킬을 쓴다(`spl-util.h` spschool).

| 학파 | 스킬 | 문서 |
|---|---|---|
| Conjuration | Conjurations | 예정 |
| Hexes | Hexes | 예정 |
| Fire | Fire Magic | 예정 |
| Ice | Ice Magic | 예정 |
| Air | Air Magic | 예정 |
| Earth | Earth Magic | 예정 |
| Necromancy | Necromancy | 예정 |
| Summoning | Summonings | 예정 |
| Translocation | Translocations | 예정 |
| Alchemy | Alchemy | [alchemy.md](alchemy.md) |
| Forgecraft | Forgecraft | 예정 |

- 마법 하나가 여러 학파에 속하면 **위력·실패율에는 그 학파 스킬들의 평균**이 쓰인다. 각 학파 페이지에는 모든 소속 마법이 목록에 나오지만, 상세 설명은 한 페이지에만 있다.
- **Spellcasting** 스킬은 모든 마법의 위력·실패율·기억 가능량에 관여한다.

---

## 1. 시전 조건과 MP

### 1.1 시전할 수 없는 경우
- 주문을 시전할 수 없는 변신 형태(bat swarm 등). → [탈리스만](../items/talismans.md)
- `DUR_NO_CAST`(마법 봉인) 상태, 시전 금지 아티팩트(−Cast) 착용.
- **Berserk, Confusion, Silence**(Flooded 포함).
- MP 부족. Djinni는 MP 대신 HP로 시전한다.

### 1.2 MP 비용
- 기본 **MP 비용 = 마법 레벨.**
- 감소 요인(이 순서로 적용, 최소 1):
  1. Coglin의 Spellmotor gizmo: −회전 단계 → [gizmo](../items/special-items.md#4-gizmo-coglin-전용)
  2. Efficient Magic 돌연변이: −단계
  3. **Brilliance**(potion of brilliance, robe of Folly): **절반, 올림** → [brilliance](../items/potions.md#33-brilliance)
- 시전을 시작하면 MP를 먼저 낸다. **취소(abort)하면 돌려받지만, 실패(miscast)해도 MP와 턴은 소모된다**(Energy 에고 방어구는 일정 확률로 환급).

---

## 2. Spell power (마법 위력)

### 2.1 계산 순서 (`spl-cast.cc` calc_spell_power)
1. **스킬 위력** = `2 × (학파 스킬 평균) + 0.5 × Spellcasting`
   - (Divine Exegesis 중이면 `+ 3 × Invocations`)
2. **× Intelligence / 10**
3. **마법 강화(enhancer)**: 강화 1단계당 **×1.5**, 약화 1단계당 **÷2**. 합계는 −3 ~ +3단계로 제한. → [마법 강화](../items/brands-egos.md#공통-마법-강화enhancer), [지팡이](../items/staves.md)
4. 돌연변이·상태 배율: Wild Magic `×(10 + 3×단계)/10`, Subdued Magic `÷(10 + 3×단계)/10`, Augmentation(HP가 높을 때), Horror(단계당 약 −10%), Enkindled(Revenant), Command 에고(Summoning).
5. **Stepdown(체감)**: 위 값을 `raw`라 하면
   - `raw < 50`이면 그대로
   - `raw ≥ 50`이면 **`50 × log2(1 + raw/50)`**, 최대 200
6. **Power cap**(마법마다 다름)으로 자른다.
7. 그 뒤에 Diminished Spells 상태면 절반, Claustrophobia bane이면 주변 벽 1개당 −5%.

| raw | 50 | 100 | 150 | 250 | 350 | 750 이상 |
|---|---|---|---|---|---|---|
| 최종 위력(상한 전) | 50 | 79 | 100 | 129 | 150 | 200 |

### 2.2 예시 (단일 학파, 강화 없음 / 강화 1단계)
| 학파 스킬 | Spellcasting | Int | 위력 | 강화 +1 |
|---|---|---|---|---|
| 5 | 5 | 10 | 12 | 18 |
| 10 | 10 | 15 | 37 | 54 |
| 10 | 10 | 20 | 50 | 66 |
| 15 | 12 | 20 | 64 | 82 |
| 20 | 15 | 25 | 87 | 109 |
| 27 | 27 | 30 | 116 | 141 |

- **Power cap**: 위력이 이 값을 넘어도 효과는 더 오르지 않는다. 마법별 값은 학파 페이지 목록에 있다.
- 실패율 계산에는 Power cap이 적용되지 않은 스킬 위력이 쓰인다(아래).

---

## 3. 실패율

### 3.1 계산 순서 (`spl-cast.cc` raw_spell_fail)
1. `x = 60 − 6 × (스킬 위력) − 2 × Int + 방어구·방패 페널티 + 레벨 난이도`
   - 스킬 위력은 2.1의 1단계 값(`2 × 학파 평균 + 0.5 × Spellcasting`). 즉 학파 스킬 1당 −12, Spellcasting 1당 −3.
   - 방어구·방패 페널티 = `19 × (Armour 스킬로 줄어든 몸통 방어구 페널티) + 19 × (Shields 스킬로 줄어든 방패 페널티)`. Runic Magic 돌연변이는 몸통 부분을 1/4로. → [방해도](../items/armour.md)
   - 레벨 난이도:

| 레벨 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 |
|---|---|---|---|---|---|---|---|---|---|
| 난이도 | 3 | 15 | 35 | 70 | 100 | 150 | 200 | 260 | 340 |

2. `x`는 최대 400.
3. **`raw = (x³ + 426x² + 82670x + 7245398) / 262144`**(0 미만이면 0). 이 다항식은 `x`가 약 −190 이하면 0, 약 125면 100이 된다.
4. 가산: Wild Magic 단계당 +4, Anti-Wizardry 단계당 +4, Subdued Magic 단계당 −2, **Energy 에고 +10**, **Vertigo +7**.
5. 배율(곱해짐):
   - Vehumet 권능(Vehumet이 지원하는 주문, 주로 파괴 마법) ×2/3
   - 변신 형태: Rime Yak(Ice), Sun Scarab(Fire), Sphinx(Hexes) 각 ×2/3
   - 에고: Command(Summoning) `×180/(180 + Armour×10)`, Death(Necromancy) ×1/2, Resonance(Forgecraft) ×2/3
   - **Wizardry**: `×6/(7 + n)` (n = Wizardry 개수) → [ring of wizardry](../items/jewellery.md#31-ring-of-wizardry)
6. Enkindled(Revenant)면 `×3/4 − 5`(이 경우 방어구 페널티도 무시).
7. 0~100으로 자른다.

### 3.2 실제 실패 확률
시전할 때 `random2avg(100, 3)`(0~99, 세 난수의 평균)을 굴려 **raw보다 작으면 실패**한다. 그래서 게임에 표시되는 실패율은 raw가 아니라 이 확률이다(세 난수 합이 `3 × raw` 미만일 확률, 표시는 소수점 버림·최소 1%).

| raw | 10 | 20 | 25 | 30 | 40 | 50 | 60 | 70 |
|---|---|---|---|---|---|---|---|---|
| 실제 실패 확률 | 0.5% | 3.7% | 7.2% | 12.3% | 28.5% | 50% | 71.5% | 87.7% |

### 3.3 예시 (단일 학파, 방어구 없음)
| 레벨 | 학파 | Spellcasting | Int | raw | 실패율 |
|---|---|---|---|---|---|
| 1 | 0 | 0 | 10 | 44 | 36.8% |
| 1 | 3 | 3 | 12 | 25 | 7.2% |
| 3 | 5 | 5 | 15 | 24 | 6.4% |
| 5 | 8 | 6 | 12 | 35 | 19.5% |
| 5 | 10 | 8 | 18 | 21 | 4.3% |
| 7 | 15 | 12 | 20 | 28 | 10.0% |
| 9 | 20 | 15 | 25 | 56 | 63.2% |
| 9 | 27 | 27 | 30 | 12 | 0.8% |

### 3.4 실패 (Miscast)
실패하면 MP와 턴을 쓰고 마법 효과는 없으며, 다음이 일어난다(`spl-miscast.cc`).
- `실패 정도 = raw − 굴린 값`. **마법 오염 `0.4 × (레벨² × 실패 정도 + 250)`**(1000 = 오염 1단계).
- `레벨² × 실패 정도`가 150 이하면 오염만 받는다.
- 그보다 크면 마법의 학파 중 하나를 골라 부작용. 세기 `d = (레벨)d(raw + 레벨) / 9`:

| 학파 | 부작용 |
|---|---|
| Conjuration | 마법 피해 d (저항 불가) |
| Hexes | Slow (d) |
| Summoning | 적대 nameless horror 소환 (HD ≈ 2d/3) |
| Necromancy | 음에너지 피해 d (rN 적용). Kikubaaqudgha 신자는 piety에 비례해 막음 |
| Translocation | Dimension Anchor + 이동 불가 d/2턴 |
| Fire / Ice / Air | 화염 / 냉기 / 전기 피해 d (각 저항 적용) |
| Earth | 파편 피해 d (AC 3배 적용) |
| Alchemy | 중독 (d × 2.5) |
| Forgecraft | 부식 |

---

## 4. 사거리
- 마법마다 최소·최대 사거리가 있다. 둘이 다르면 위력에 비례해 늘어난다: `최소 + 위력 × (최대 − 최소) / Power cap`(반올림), Power cap에서 최대.
- 현재 시야 반경을 넘지 않는다.
- **Vehumet** 권능: Vehumet이 지원하는 주문의 사거리 +1(최대 사거리 2 이상인 주문).

## 5. 소음
- **시전 소음 = 마법 레벨**(조용한 주문 제외). 이와 별도로 효과 자체의 소음(폭발 등)이 있는 마법이 있다. 소음 규칙은 은신 문서에서 다룰 예정이다.

## 6. 주문 기억 (Memorisation)
- **기억 가능한 주문 레벨 합 = `XL − 1 + 2 × Spellcasting`**(부스트 제외 실제 스킬, 최대 99). 기억한 주문의 레벨 합이 이를 넘을 수 없다.
- 동시에 기억할 수 있는 주문은 **최대 21개.**
- **XL이 주문 레벨보다 낮으면 기억할 수 없다.**
- 마법서를 주우면 주문이 **라이브러리**에 등록되고, 라이브러리에서 기억한다(Vehumet 선물 포함). Confusion·Berserk 중에는 기억할 수 없다.
- 주문을 잊는 방법은 scroll of amnesia다. → [amnesia](../items/scrolls.md#213-amnesia)

## 7. 스킬 훈련
- 시전할 때마다 각 학파 스킬에 `random2(1 + 레벨) / 학파 수`(4/5 확률로 +1) 만큼, Spellcasting에 `1 + random2(1 + 레벨) / 학파 수` 만큼 경험치가 들어간다(실제 증가는 스킬 훈련 규칙을 따름).
- 실패하면 학파 수에 4~13을 더해 나누므로 훈련량이 크게 준다.
- **Conjuration이 포함된 주문**은 `학파 수 / 4` 확률로만 훈련된다(학파 1개면 1/4).

> 출처: spl-cast.cc, spl-util.cc, spl-util.h, spl-miscast.cc, spl-book.cc, player.cc, exercise.cc, stepdown.cc, spl-data.h, book-data.h (0.34.1)
