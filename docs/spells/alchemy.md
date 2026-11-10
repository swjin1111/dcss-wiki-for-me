# Alchemy

> 기준: DCSS 0.34.1 · [마법 목록으로](index.md)

Poison(독)과 물질 변환을 다루는 학파. 예전의 Poison Magic과 Transmutation 일부가 합쳐진 학파로, Poison 데미지 외에도 Petrify(석화), Liquefaction(액화), Irradiate(방사능), 연금 폭탄 같은 다양한 효과를 가진다.

## 목록

- Power cap(위력 상한): Spell power(마법 위력)가 이 값을 넘어도 효과가 더 오르지 않는다.
- 사거리 `—`는 대상을 지정하지 않는 마법(자신 중심, 지속 효과 등). `시야`는 시야 전체.
- MP 소모 = 마법 레벨.

| Lv | 마법 | 학파 | Power cap | 사거리 | 수록 마법서 |
|---|---|---|---|---|---|
| 1 | [Poisonous Vapours](#poisonous-vapours) | Alchemy / Air | 25 | 3 | Young Poisoner's Handbook, Book of Cantrips |
| 2 | [Mercury Arrow](#mercury-arrow) | Alchemy / Conjuration | 50 | 4 | Young Poisoner's Handbook, My Sojourn Through Swamps |
| 3 | [Mephitic Cloud](#mephitic-cloud) | Conjuration / Alchemy / Air | 100 | 4 | Book of the Senses, Trismegistus Codex |
| 4 | [Fulminant Prism](#fulminant-prism) | Conjuration / Alchemy | 200 | 4 | Book of Conjurations, Book of Blasting |
| 4 | [Ignite Poison](#ignite-poison) | Fire / Alchemy | 100 | — | Everburning Encyclopedia, Book of Blood |
| 4 | [Leda's Liquefaction](#ledas-liquefaction) | Earth / Alchemy | 200 | — | Book of Earth, Book of Sloth |
| 4 | [Olgreb's Toxic Radiance](#olgrebs-toxic-radiance) | Alchemy | 100 | — | Young Poisoner's Handbook, Unrestrained Analects |
| 4 | [Petrify](#petrify) | Alchemy / Earth | 200 | 6 | Book of Transmutation, Book of Sloth |
| 4 | [Sticky Flame](#sticky-flame) | Alchemy / Fire | 100 | 1 | Book of Flames, Everburning Encyclopedia |
| 5 | [Alistair's Intoxication](#alistairs-intoxication) | Alchemy | 150 | — | Book of Party Tricks, Great Wizards, Vol. II |
| 5 | [Alistair's Walking Alembic](#alistairs-walking-alembic) | Forgecraft / Alchemy | 100 | — | Book of Metalworking, Book of Contraptions |
| 5 | [Detonation Catalyst](#detonation-catalyst) | Fire / Alchemy | 100 | — | Book of Spontaneous Combustion, Book of Battle |
| 5 | [Irradiate](#irradiate) | Conjuration / Alchemy | 200 | 1 | Book of Spontaneous Combustion, Book of Transmutation |
| 5 | [Yara's Violent Unravelling](#yaras-violent-unravelling) | Hexes / Alchemy | 200 | 시야 | Book of Misfortune, Great Wizards, Vol. VII |
| 6 | [Eringya's Noxious Bog](#eringyas-noxious-bog) | Alchemy | 200 | 4 | Fen Folio, Great Wizards, Vol. II |
| 6 | [Sculpt Simulacrum](#sculpt-simulacrum) | Ice / Alchemy | 200 | 1 | Book of Wicked Creation, Book of Cryoformation |
| 8 | [Fulsome Fusillade](#fulsome-fusillade) | Alchemy / Conjuration | 200 | 시야 | Book of Transmutation, Book of Spectacle |

(몬스터 전용 마법은 제외하고, 고정 마법서에 수록된 마법만 담았다. 랜덤 마법서에는 다른 조합으로 나올 수 있다.)

### 공통: rPois와 Poison 데미지
이 페이지의 많은 마법이 Poison 데미지를 쓰는데, 종류에 따라 rPois(독 저항)에 막히는 비율이 다르다.
- **일반 Poison**: 전부 rPois의 영향을 받는다. 몬스터 rPois 3단계(면역)는 0.
- **70%만 저항 가능한 Poison** (Mercury Arrow, Fulsome Fusillade의 Poison 폭발, Noxious Bog): 데미지의 30%는 무조건 들어간다.

| 대상 | 일반 Poison | 70% 저항형 |
|---|---|---|
| rPois 없음 | 100% | 100% |
| 몬스터 rPois 1단계 | 약 33% | 약 53% |
| 몬스터 rPois 3단계 (면역) | 0% | 30% |
| rPois− (취약) | 150% | 약 135% |

---

## Poisonous Vapours
`Lv 1 · MP 1 · Alchemy / Air · Power cap 25 · 사거리 3`

지정한 칸의 대상 하나에게 Poison 데미지와 독을 건다.

- **조준**: 지정 칸에 바로 걸리는 방식이라 사이에 다른 몬스터가 있어도 상관없다.
- **데미지**: `1d(1 + Spell power/8)`. Power cap에서 1d4.
- **독**: 맞은 몬스터에게 독 1단계를 건다.
- **rPois가 조금이라도 있으면 완전히 무효**다. rPois 몬스터는 조준 대상으로 지정할 수도 없다.
- 지정한 칸에만 작용하고, 구름이 남지 않는다.

## Mercury Arrow
`Lv 2 · MP 2 · Alchemy / Conjuration · Power cap 50 · 사거리 4`

수은 화살을 날려 Poison 데미지를 주고, 맞은 적과 그 주변 적을 Weak(약화) 상태로 만들 수 있다.

### 데미지
- **2개의 주사위, 최대 합계 `11 + Spell power/4`**
  - Spell power 0: 약 2d5
  - Spell power 50 (cap): 약 2d11 (평균 약 12)
- **명중**: 자동 명중이 아니다. 명중 수치는 `12 + Spell power/5` (cap에서 22). EV(회피)가 높은 적에게는 빗나갈 수 있다.
- **70% 저항형 Poison**이라 Poison 면역 몬스터에게도 30%는 들어간다. ([공통](#공통-rpois와-poison-데미지) 참고)

### Weak 효과
명중하면 대상에게 Weak를 걸 확률이 있다. **rPois와 무관하다.**

- **확률 = `100 − 12 × (대상 HD − 4)`%** (HD 4 이하는 100%). HD는 Hit Dice(몬스터 레벨).

| 대상 HD | ≤4 | 6 | 8 | 10 | 12 | 13+ |
|---|---|---|---|---|---|---|
| Weak 확률 | 100% | 76% | 52% | 28% | 4% | 0% |

- **Spell power와 무관하다.** Spell power를 올려도 확률은 그대로이고, HD만 본다.
- **효과**: 몬스터의 **melee(근접 공격) 데미지가 2/3로 감소**한다. melee 공격이 없는 몬스터에게는 걸리지 않는다.
- **지속시간**: 약 5~12턴.
- 조준할 때 몬스터 정보에 `chance to weaken: N%`로 확률이 표시된다.

### Splash
맞은 대상의 **인접 8칸에 있는 다른 캐릭터들도 각자 Weak 판정**을 받는다. 이 Splash(튀김)에는 데미지가 없다.
- 시전자 본인은 제외된다.
- **아군도 Splash에 포함될 수 있다.**

## Mephitic Cloud
`Lv 3 · MP 3 · Conjuration / Alchemy / Air · Power cap 100 · 사거리 4`

플라스크를 던져 3×3 범위에 독가스 구름을 만든다. 구름 안의 몬스터는 Confusion(혼란)에 걸릴 수 있다.

- **명중**: 자동 명중. 사거리 끝이나 처음 맞은 대상에서 터진다.
- **구름 범위**: 중심 칸에는 항상, 주변 8칸에는 각각 `(125 + Spell power)/225` 확률로 생긴다.
  - Spell power 0: 주변 칸마다 약 56%
  - Spell power 100 (cap): **3×3 전부**
- **구름 지속**: `2d(8 + Spell power/20)`턴. cap에서 2d13턴.
- **데미지는 없다.** 효과는 Confusion뿐이다.
- **Confusion 확률** (구름 안에 있는 매 턴):
  - 몬스터: `1 − HD/21`. HD 21 이상은 2%.
  - **rPois가 있거나 Clarity가 있으면 면역.**
  - 조준할 때 `chance to affect: N%`로 표시된다.
- **플레이어도 구름에 들어가면 혼란에 걸릴 수 있다.** 확률은 매 턴 약 `(28 − XL)/27` (XL은 경험치 레벨)로, XL 27에서도 약 4%. rPois나 Clarity가 있으면 면역.

## Fulminant Prism
`Lv 4 · MP 4 · Conjuration / Alchemy · Power cap 200 · 사거리 4`

지정한 빈 칸에 폭발하는 프리즘을 만든다.

- **설치**: 사거리 안의 빈 칸에만 설치할 수 있다. 벽이나 보이는 몬스터 위에는 안 된다.
  - 보이지 않는 몬스터가 있는 칸을 지정하면 실패하지만 MP는 소모된다.
- **프리즘의 HD = `Spell power/10`** (cap에서 20).
- **폭발 타이밍**: 프리즘은 자기 차례마다 충전된다. **두 번째 차례에 스스로 폭발**한다. 일반 속도 기준으로 설치 후 약 2턴이다.
- **폭발 데미지** (`HD`는 프리즘 HD):

| 상태 | 범위 | 데미지 | cap 기준 |
|---|---|---|---|
| 완전 충전 (스스로 폭발) | 반경 2 (5×5) | `3d(5 + HD×7/4)` | 3d40 |
| 1회 충전 후 파괴됨 | 반경 1 (3×3) | `2d(5 + HD×7/4)` | 2d40 |
| 충전 전에 파괴됨 | — | 폭발 없음 | — |

- 데미지는 저항할 수 없는 마법 데미지다.
- **플레이어 자신과 아군도 폭발 범위에 있으면 맞는다.**
- 프리즘은 날아다니고 움직이지 않으며, Fire·Cold·Elec 저항이 있다.

## Ignite Poison
`Lv 4 · MP 4 · Fire / Alchemy · Power cap 100 · 사거리 —`

시야 안의 모든 독을 불로 바꾼다.

- **독에 걸린 몬스터**: 독 단계(degree)에 비례한 Fire 데미지를 받는다.
  - **데미지 = `(독 단계 × 2)d(12 + Spell power × 6/100)`**. cap에서 주사위 크기 18.
  - 예: 독 3단계인 몬스터는 cap에서 6d18.
  - **Fire 저항의 영향을 받는다.**
  - 살아남으면 **독이 사라진다.**
- **독 구름**: Poison 구름과 Mephitic 구름이 **Fire 구름으로 바뀐다.** 지속은 약 3~5턴에서 Spell power에 따라 최대 약 15턴.
- **Toxic bog 지형**: 칸마다 25% 확률로 짧은 Fire 구름이 생긴다.
- **시전자는 직접 피해를 받지 않는다.** 하지만 바뀐 Fire 구름은 시전자가 서 있는 칸이나 주변에도 생길 수 있다.
- **독에 걸린 아군도 데미지를 받는다.**

## Leda's Liquefaction
`Lv 4 · MP 4 · Earth / Alchemy · Power cap 200 · 사거리 —`

시전자 주변 땅을 액화해서, 그 위의 몬스터를 느리게 하고 공격을 방해한다. 범위는 시간이 지나면서 줄어든다.

- **지속시간**: `15 + random2avg(Spell power, 2)`턴, 최대 100턴. 다시 시전하면 지속시간이 더해진다(최대 100).
- **반경**: 남은 지속시간에 따라 줄어든다.

| 남은 턴 | 39+ | 27~38 | 17~26 | 11~16 | 7~10 | 1~6 |
|---|---|---|---|---|---|---|
| 반경 | 5 | 4 | 3 | 2 | 1 | 0 (시전자 칸만) |

- **액화된 땅 위의 몬스터** (날지 않는 몬스터):
  - **이동 비용 +6** (일반 속도 몬스터는 이동이 약 1.6배 느려진다).
  - **공격 시 25% 확률로 헛디뎌서 공격이 실패**한다.
- **날고 있는 몬스터는 영향을 받지 않는다.** 게임 내 설명에는 "날 수 없게 된다"고 되어 있지만, 0.34.1 코드에서는 날고 있는 몬스터를 땅으로 끌어내리는 처리가 없다. 비행 몬스터는 그냥 영향을 받지 않는다.
- **시전자**:
  - 유지하는 동안 **이동 비용 +3** (날고 있어도 적용).
  - 시전자는 액화된 땅에서 헛디디지 않는다.
- 물·용암 칸은 액화되지 않는다.

## Olgreb's Toxic Radiance
`Lv 4 · MP 4 · Alchemy · Power cap 100 · 사거리 —`

시전자가 독 기운을 내뿜어, 시야 안의 모든 대상에게 매 턴 Poison 데미지와 독을 건다.

- **지속시간**: `2 + random2(1 + Spell power/25)`턴. cap에서 2~6턴. 다시 시전하면 더해진다(최대 15턴).
- **매 턴 효과** (시간 10 aut당):
  - 데미지 `1d(1 + Spell power/20)`. cap에서 1d6.
  - 독: 50% 확률로 1단계 추가. **독에 안 걸린 대상은 항상 1단계 이상** 걸린다.
- **rPois가 조금이라도 있는 몬스터는 완전 면역.**
- **시야 안의 아군도 맞는다.** 반투명 벽 너머는 영향을 받지 않는다.
- 시전자 본인은 맞지 않는다.

## Petrify
`Lv 4 · MP 4 · Alchemy / Earth · Power cap 200 · 사거리 6`

대상을 석화하고, 주변 적 최대 2명에게 연쇄된다.

- **Willpower(의지력) 판정**이 있다. 막히면 효과 없음.
- **연쇄**: 맞은 대상에 인접한 적대 몬스터(없으면 그 다음 칸까지) 중 **최대 2명**에게 추가로 걸린다.
  - 연쇄 대상에게는 **Spell power의 2/3**로 판정한다.
  - 아군, firewood(식물 같은 장애물형 몬스터)는 연쇄되지 않는다.
- **진행 단계**:
  1. **Petrifying**(석화 중): 잠시 느려진다. 받는 데미지 **×2/3**.
  2. **Petrified**(석화): 행동할 수 없다. 받는 데미지 **×1/2**. 지속시간은 몬스터 속도에 따라 다르다.
- 석화된 대상에게는 암습(stab)이 가능하다.
- 석화 면역 몬스터에게는 통하지 않는다.

## Sticky Flame
`Lv 4 · MP 4 · Alchemy / Fire · Power cap 100 · 사거리 1`

인접한 적에게 끈적한 불을 붙여 여러 턴 동안 태운다.

- **명중 데미지**: `2d(4 + Spell power/9)` Fire. 자동 명중. cap에서 2d15.
- **연소 지속**: `3 + (Spell power/20 ~ Spell power/10)`턴. cap에서 8~13턴.
- **연소 데미지**: 매 턴 `2d7` Fire. Fire 저항의 영향을 받는다.
- **꺼지는 조건**:
  - 몬스터가 **이동할 때마다 남은 시간이 5턴씩 줄어든다.**
  - 날지 않는 몬스터가 물에 들어가면 꺼진다. Water 공격을 맞아도 꺼진다.
- Insubstantial 몬스터에게는 붙지 않는다. 조준할 때 `unstickable`로 표시된다.

## Alistair's Intoxication
`Lv 5 · MP 5 · Alchemy · Power cap 150 · 사거리 —`

시야 안의 지능 있는 생물들을 Confusion에 걸리게 한다. 성공하면 시전자는 Vertigo(어지러움)에 걸린다.

- **대상**: 시야 안의 **지능이 Human 이상인 모든 몬스터**.
  - 제외: Clarity가 있는 몬스터, rPois 3단계 몬스터.
  - **rPois 1단계 몬스터는 2/3 확률로 저항**한다.
- **확률**: `40 + Spell power/3`%. cap에서 90%.
- **Willpower 판정이 없다.**
- **아군도 대상이 된다.** 시야 안에 있는 지능 있는 아군이 혼란에 걸릴 수 있다.
- **시전자 Vertigo**: 한 명이라도 혼란에 걸리면, 걸린 수를 N이라 할 때 `4 + N + random(0~N)`턴 동안 Vertigo.
  - Vertigo 중: **EV −5, 명중 −5** (근접·원거리 모두), **마법 실패율 증가**.

## Alistair's Walking Alembic
`Lv 5 · MP 5 · Forgecraft / Alchemy · Power cap 100 · 사거리 —`

싸우면서 포션을 만드는 연금 골렘을 소환한다. 일정 횟수 때리면 주변 아군에게 포션을 나눠주고 사라진다.

- **HD**: `7 + Spell power/16`. cap에서 13.
- **지속**: 약 30턴 (변동 있음).
- **기본 능력치** (몬스터 데이터 기준): melee 1회(펀치, 데미지 19), AC 9, EV 8, Fire·Cold·Elec 저항.
- **펀치 효과**:
  - 맞은 대상 칸에 Poison 구름(3~7턴)을 만든다.
  - 50% 확률로 주변에 Poison 구름 3~4개를 더 만든다. 아군이 있는 칸은 피한다.
- **포션 제조**: 소환 시 **4~6회**의 카운트를 가진다. 적을 때릴 때마다 1씩 줄고, 0이 되면 포션을 분배하고 사라진다.
  - firewood를 때리면 카운트가 줄지 않는다.
- **플레이어가 받는 포션**: 알렘빅에서 **3칸 이내**에 있고 시야가 통하면 받는다. 상황에 맞는 것 중 무작위로 하나.

| 포션 | 가중치 | 조건 |
|---|---|---|
| Haste | 50 | 마실 수 있을 때 |
| Heal Wounds | 50 | HP가 가득 차지 않았을 때 |
| Might | 50 | 마실 수 있을 때 |
| Magic | 30 | MP가 가득 차지 않았을 때 |
| Invisibility | 30 | 마실 수 있을 때 |

  - 효과 지속은 직접 마실 때보다 약간 짧다.
  - Cocytus에서는 포션이 얼어서 효과가 없다.
- **아군 몬스터**: 3칸 이내 아군 최대 5명에게 Haste, Might, Brilliance(이미 걸려 있지 않은 것), Heal Wounds 중 무작위로 하나씩 준다.

## Detonation Catalyst
`Lv 5 · MP 5 · Fire / Alchemy · Power cap 100 · 사거리 —`

근접 공격이 맞을 때마다 대상 위치에서 Fire 폭발이 일어나게 한다.

- **지속시간**: 3~5턴. 단, **공격을 시도한 턴에는 줄어들지 않는다.** 계속 공격하는 동안에는 무한히 유지되고, 다른 행동을 하면 빠르게 끝난다.
- **폭발**: 근접 공격의 주 대상 중심 **3×3**, Fire 데미지, 자동 명중.
  - **플레이어와 아군 칸은 폭발에서 제외된다.**
  - 대상이 공격으로 죽어도 폭발한다.
  - 휩쓸기(cleave)로 맞은 추가 대상에게는 폭발이 일어나지 않는다.
- **데미지**: 2개의 주사위, 최대 합계 `무기 위력 − (8 − Spell power/10)` (최소 1).
  - **무기 위력 = 무기의 기본 데미지 × 9/5.** 맨손이면 맨손 기본 데미지(+보너스)를 쓴다.
  - Spell power가 낮으면 감점이고, cap(100)에서 **+2 보너스**가 된다.
  - 예: 기본 데미지 10인 무기 → 무기 위력 18. Spell power 0에서 2d5, cap에서 2d10.
- 무기를 쓸 때는 무기의 기본 데미지만 본다. 인챈트, 무기 스킬, Str은 반영되지 않는다.

## Irradiate
`Lv 5 · MP 5 · Conjuration / Alchemy · Power cap 200 · 사거리 1`

시전자 주변 8칸 전체에 마법 방사선을 터뜨린다. 시전할 때마다 Contamination(마법 오염)이 쌓인다.

- **범위**: 시전자 인접 8칸 전부. **아군도 맞는다.**
- **데미지**: 3개의 주사위, 최대 합계 `35 + Spell power/2`. Spell power 0에서 약 3d11, cap에서 **약 3d45**. **AC(방어)가 적용된다.**
- **추가 효과**: 살아남은 몬스터는 50% 확률로 Malmutate(일시적 돌연변이)에 걸려 **Wretched** 상태가 된다.
  - Wretched: **AC −8**, **유효 HD ×3/4**. 지속은 약 23~50턴(몬스터 속도에 따라 다름).
  - 돌연변이할 수 없는 몬스터에게는 걸리지 않는다.
- **시전자 Contamination**: 1회당 **185~400**. 합계가 1000 이상이면 위험(dangerous) 단계가 된다.
  - 오염이 0인 상태에서 2회 연속 시전까지는 1000을 넘지 않는다. 3회째부터 위험해질 수 있다.
  - 합계가 1000을 넘을 것 같으면 경고가 뜬다.

## Yara's Violent Unravelling
`Lv 5 · MP 5 · Hexes / Alchemy · Power cap 200 · 사거리 시야`

버프가 걸려 있거나 소환된 대상의 마법을 해체해서 폭발시킨다.

- **대상 조건**: 마법 효과(버프)가 걸려 있는 대상, 또는 **소환된 몬스터**만 가능하다. 아니면 시전이 거부된다.
- **Willpower 판정이 없다.**
- **효과**:
  - **소환수는 즉시 소멸**한다.
  - 소환수가 아니면 버프가 전부 제거된다.
  - 그 다음 대상 위치에서 **3×3 폭발**이 일어난다.
- **폭발**: `3d(3 + Spell power/6)` 데미지(cap에서 3d36). 범위 안의 모두에게 Malmutate(→ Wretched)를 건다.
- **플레이어도 폭발 범위에 있으면 맞고, 돌연변이를 얻는다.** 범위에 들어갈 것 같으면 경고가 뜬다.

## Eringya's Noxious Bog
`Lv 6 · MP 6 · Alchemy · Power cap 200 · 사거리 4`

시전자 주변 땅을 일시적으로 Toxic bog(독 늪)로 바꾼다. 늪 위의 몬스터는 매 턴 Poison 데미지와 독을 받는다.

- **범위**: 시전자 중심 반경 4 안의 시야 내 칸.
  - **바닥이 단단한 칸만 가능** (깊은 물, 용암 등은 불가).
  - **인접 8칸 중 벽(또는 보이지 않는 칸)이 3개 이상인 칸은 늪이 되지 않는다.** 좁은 복도에서는 거의 안 생긴다.
- **지속**: `4 + random2(2 + Spell power/10)`턴. cap에서 4~25턴.
  - **시야 밖으로 벗어난 늪 칸은 즉시 사라진다.**
  - 층을 이동하면 끝난다.
  - 지속 중에는 다시 시전할 수 없다.
- **늪 위의 대상** (날지 않는 대상, 매 턴):
  - 데미지 `4d6`, **70% 저항형 Poison**. rPois가 있어도 30%는 들어간다.
  - 독: 저항이 없으면 강하게, 일부 저항하면 약하게 건다.
  - 늪은 얕은 물 취급이라 몬스터가 허우적댄다: **이동 비용 +6**, **공격 25% 실패**.
- **시전자는 지속 중 늪의 영향을 받지 않는다.**
- **아군도 늪 위에 있으면 데미지를 받는다.**

## Sculpt Simulacrum
`Lv 6 · MP 6 · Ice / Alchemy · Power cap 200 · 사거리 1`

인접한 생물의 얼음 복제품(simulacrum)을 만든다.

- **대상 조건**: 인접한 **Natural, Demonic, Holy** 몬스터. 공격 수단이 있어야 한다.
  - 소환된 몬스터, 촉수류, Pandemonium lord는 불가.
- **대상은 피해를 받지 않는다.** 복제품만 만든다.
- **개수**: 기본 2개. `Spell power/200` 확률로 3개. **cap(200)에서 항상 3개.**
- **생성 과정**:
  1. 먼저 Block of ice(얼음 덩어리)가 나타난다(HD 8).
  2. 약 3~5턴 뒤 첫 번째가 simulacrum으로 바뀐다. 나머지는 1~3턴 간격으로 차례로 바뀐다.
  3. **바뀌기 전에 얼음 덩어리가 부서지면 그 복제품은 생기지 않는다.**
- **Simulacrum**: 원본 몬스터 종류를 따르는 아군. HD는 그 몬스터 종류의 기본 HD. 지속 약 30턴.
- **동시 유지 최대 5개.**
- **선한 신(Good god)이 싫어하는 마법**이다(unholy).

## Fulsome Fusillade
`Lv 8 · MP 8 (+ 추가 volley마다 2) · Alchemy / Conjuration · Power cap 200 · 사거리 시야`

시전 후 몇 턴 동안 시야 내 적들에게 원소 폭탄이 자동으로 쏟아지는 지속형 광역 마법. 폭발이 겹치는 칸에서는 더 강력한 Unstable reaction(불안정 반응)이 일어난다.

### 진행 방식
- **총 5회 volley(일제 사격).**
  - 시전한 행동에서 1회, 이후 시간이 걸리는 행동을 할 때마다 1회씩, 4회 더.
  - 게임 시간 기준이 아니라 **플레이어 행동 횟수 기준**이다.
- **MP**: 첫 volley는 시전 비용(8 MP)에 포함된다. 2~5번째 volley는 **각 2 MP**를 따로 소모한다(최대 8 MP 추가).
  - volley 시점에 MP가 2 미만이면 즉시 종료된다.
- 지속 중에는 다시 시전할 수 없다.

### volley 1회의 동작
1. 표적 선정: 시야 안에서 보이는 **적대 몬스터 중 플레이어와 인접하지 않은(거리 2 이상) 대상** 중 무작위로 **최대 3마리**를 고른다.
   - 아군, firewood, 투사체 몬스터는 표적에서 빠진다.
   - 표적이 3마리보다 적으면, 남은 폭탄은 시야 안의 **빈 칸(플레이어와 인접하지 않은 곳)에 무작위로** 떨어진다.
2. 각 폭탄은 표적 중심 **3×3 범위**로 폭발한다.
   - 원소는 Fire, Cold, Poison, Electricity 중 **서로 다른 3개**가 무작위로 배정된다.
   - 폭발 하나마다 Noise(소음) 15가 발생한다.

### 데미지
- **원소 폭발**: `3d(5 + Spell power/8)`. cap(200)에서 **3d30**, 자동 명중.
  - 해당 원소 저항의 영향을 받는다. Poison 폭발은 70% 저항형이다.
- **Unstable reaction**: 두 개 이상의 폭발이 **겹친 칸**에서는 원소 데미지 대신 `5d(5 + Spell power/8)`, cap에서 **5d30**. **저항할 수 없는 데미지**다.
  - 칸 하나는 volley 한 번에 한 번만 판정된다. 폭발이 3개 겹쳐도 데미지는 Unstable reaction 1회분이다.
  - 표적끼리 가까이(2칸 이내) 붙어 있을수록 겹치는 칸이 생긴다. **뭉쳐 있는 무리에게 강하다.**
- 게임 내에는 데미지가 `(3-5)dN`으로 표시된다.

### Unstable reaction의 추가 상태이상
Unstable reaction에 맞고 살아남은 몬스터에게 아래 중 하나가 무작위로 적용된다.

| 결과 | 확률 |
|---|---|
| 효과 없음 | 약 59% |
| Malmutate | 약 9% |
| Slow | 약 9% |
| Weakness | 약 9% |
| Confusion | 약 6% |
| Ensnare (실제로는 효과 없음) | 약 6% |
| Petrify | 약 3% |

- 상태이상의 power는 `Spell power/20`(cap에서 10)이다. 코드상 **Willpower 판정을 거치지 않는 경로**로 적용된다. 다만 Clarity가 있으면 Confusion이, 석화 면역이면 Petrify가 막힌다.
- **Ensnare는 확률표에는 있지만, 0.34.1 코드에서는 실제로 발동하지 않는다.** 결과를 고르는 `switch`가 뽑힌 효과 대신 폭발 원소를 검사하는 버그 때문에, Ensnare 처리로 가지 않고 아무 효과도 없이 끝난다.

### 아군·자신에 대한 피해
- **플레이어 자신은 절대 맞지 않는다.**
- **아군과 중립 몬스터는 폭발 범위에 있으면 맞는다.** 표적으로 고르지는 않지만, 근처 적을 노린 폭발에 휘말린다.

---

> 출처: spl-data.h, book-data.h, zap-data.h, beam.cc, fight.cc, cloud.cc, spl-damage.cc, spl-selfench.cc, spl-summoning.cc, spl-other.cc, spl-cast.cc, spl-util.cc, mon-explode.cc, mon-act.cc, mon-ench.cc, monster.cc, melee-attack.cc, player.cc, player-reacts.cc, areas.cc, mon-death.cc, timed-effects.cc (0.34.1)
