# 언랜드 아티팩트 — 무기 (Unrandart Weapons)

> 기준: DCSS 0.34.1 · [아이템 목록으로](index.md)
>
> **작성 진행 상황**: Maces & Flails, Short Blades, Long Blades, Axes 작성 완료. Polearms, Staves, Ranged Weapons는 다음 실행에서 이어서 작성한다(아래 [전체 목록](#전체-목록)의 "상세" 칸 참고).

이름·수치·고유 효과가 정해진 무기 아티팩트를 정리한다. 원형 무기의 기본 수치와 전투 공식은 [무기 문서](weapons.md), 브랜드 효과는 [브랜드·에고](brands-egos.md#무기-브랜드), 아티팩트 속성(Str, rF 등)의 의미는 [아티팩트 속성](artefact-properties.md) 참고. 이 문서는 **원형과 달라진 점과 고유 효과** 위주로 쓴다.

---

## 공통 규칙
- **한 게임에 하나씩만** 존재한다. 생성 가중치와 깊이 규칙은 [아이템 개요](index.md#아티팩트-개요) 참고.
- **인챈트(+N)는 고정**이다. 인챈트 스크롤로 올릴 수 없다(Mountain Dwarf도 불가).
- 일부 언랜드는 원형 무기의 기본 데미지·명중·딜레이를 바꾼다(`BASE_DAM`, `BASE_ACC`, `BASE_DELAY`). 아래 수치표의 괄호가 원형 대비 변화량이다.
- 그 칸에 올라서면 다른 무기처럼 자동 감정된다.
- **대체 생성(fallback)**: 볼트가 특정 언랜드를 지정했는데 그 언랜드가 이미 나온 경우, 대신 지정된 종류(`FALLBACK`)의 randart가 지정된 브랜드(`FB_BRAND`)로 만들어진다. 플레이어가 직접 신경 쓸 일은 거의 없다.
- 바닥에서 생성되지 않는 것(`nogen`): sword of Cerebov, sceptre of Asmodeus, Axe of Woe. 각각 특정 몬스터·장소에서만 나온다.
- 언랜드 무기 효과 중 "명중했을 때"라고 쓴 것은 근접 공격이 맞았을 때마다 판정한다(브랜드 판정과 별개).

## 전체 목록
바닥 무작위 생성 가능 51개 + `nogen` 3개 = 54개. (삭제된 언랜드는 제외)

| 계열 | 언랜드 | 원형 | 상세 |
|---|---|---|---|
| Maces & Flails | [mace of Variability](#mace-of-variability) | great mace | 작성 |
| | [sceptre of Torment](#sceptre-of-torment) | eveningstar | 작성 |
| | [eveningstar "Brilliance"](#eveningstar-brilliance) | eveningstar | 작성 |
| | [giant club "Skullcrusher"](#giant-club-skullcrusher) | giant club | 작성 |
| | [morningstar "Eos"](#morningstar-eos) | morningstar | 작성 |
| | [great mace "Undeadhunter"](#great-mace-undeadhunter) | great mace | 작성 |
| | [whip "Snakebite"](#whip-snakebite) | whip | 작성 |
| | [shillelagh "Devastator"](#shillelagh-devastator) | club | 작성 |
| | [dark maul](#dark-maul) | great mace | 작성 |
| | [demon whip "Spellbinder"](#demon-whip-spellbinder) | demon whip | 작성 |
| | [great mace "Firestarter"](#great-mace-firestarter) | great mace | 작성 |
| | [sceptre of Asmodeus](#sceptre-of-asmodeus) (nogen) | eveningstar | 작성 |
| Short Blades | [Vampire's Tooth](#vampires-tooth) | quick blade | 작성 |
| | [Spriggan's Knife](#spriggans-knife) | dagger | 작성 |
| | [captain's cutlass](#captains-cutlass) | rapier | 작성 |
| | [arc blade](#arc-blade) | rapier | 작성 |
| | [pair of quick blades "Gyre" and "Gimble"](#pair-of-quick-blades-gyre-and-gimble) | quick blade | 작성 |
| Long Blades | [Singing Sword](#singing-sword) | double sword | 작성 |
| | [demon blade "Leech"](#demon-blade-leech) | demon blade | 작성 |
| | [zealot's sword](#zealots-sword) | eudemon blade | 작성 |
| | [sword of the Dread Knight](#sword-of-the-dread-knight) | great sword | 작성 |
| | [plutonium sword](#plutonium-sword) | triple sword | 작성 |
| | [autumn katana](#autumn-katana) | long sword | 작성 |
| | [Maxwell's thermic engine](#maxwells-thermic-engine) | double sword | 작성 |
| | [Throatcutter](#throatcutter) | long sword | 작성 |
| | [sword of Cerebov](#sword-of-cerebov) (nogen) | great sword | 작성 |
| Axes | [Wrath of Trog](#wrath-of-trog) | battleaxe | 작성 |
| | [mithril axe "Arga"](#mithril-axe-arga) | broad axe | 작성 |
| | [obsidian axe](#obsidian-axe) | broad axe | 작성 |
| | [frozen axe "Frostbite"](#frozen-axe-frostbite) | executioner's axe | 작성 |
| | [woodcutter's axe](#woodcutters-axe) | battleaxe | 작성 |
| | [consecrated labrys](#consecrated-labrys) | broad axe | 작성 |
| | [Axe of Woe](#axe-of-woe) (nogen) | executioner's axe | 작성 |
| Polearms | glaive of Prune | glaive | 예정 |
| | scythe of Curses | halberd | 예정 |
| | scythe "Finisher" | halberd | 예정 |
| | glaive of the Guard | glaive | 예정 |
| | trident of the Octopus King | trident | 예정 |
| | lance "Wyrmbane" | spear | 예정 |
| | demon trident "Rift" | demon trident | 예정 |
| | trishula "Condemnation" | trishula | 예정 |
| | Lochaber axe | bardiche | 예정 |
| | Force Lance | spear | 예정 |
| Staves | staff of Olgreb | (magical staff) | 예정 |
| | Elemental Staff | (magical staff) | 예정 |
| | Majin-Bo | (magical staff) | 예정 |
| | lajatang of Order | lajatang | 예정 |
| | staff of the Meek | quarterstaff | 예정 |
| Ranged Weapons | greatsling "Punk" | sling | 예정 |
| | longbow "Zephyr" | longbow | 예정 |
| | storm bow | longbow | 예정 |
| | arbalest "Damnation" | arbalest | 예정 |
| | heavy crossbow "Sniper" | triple crossbow | 예정 |
| | hand cannon "Mule" | hand cannon | 예정 |

---

## Maces & Flails

### 수치표
| 언랜드 | 인챈트 | 데미지 | 명중 | 딜레이 | 최소 딜레이 (필요 스킬) | 브랜드 |
|---|---|---|---|---|---|---|
| mace of Variability | +7 | 17 | −4 | 1.7 | 0.7 (20) | Chaos |
| sceptre of Torment | +7 | 15 | −1 | 1.5 | 0.7 (16) | Pain |
| eveningstar "Brilliance" | +1 | 15 | −1 | 1.5 | 0.7 (16) | Foul Flame |
| giant club "Skullcrusher" | +3 | 20 | −6 | 1.6 | 0.7 (18) | Speed |
| morningstar "Eos" | +10 | 13 | −2 | 1.5 | 0.7 (16) | Electrocution |
| great mace "Undeadhunter" | +7 | 17 | −4 | 1.7 | 0.7 (20) | 없음 |
| whip "Snakebite" | +8 | 6 | +2 | 1.1 | 0.5 (12) | Venom |
| shillelagh "Devastator" | +6 | **8 (+3)** | +3 | 1.3 | 0.6 (14) | 없음 |
| dark maul | +10 | **37 (+20)** | **−2 (+2)** | **2.4 (+0.7)** | 1.0 (28)\* | Heavy |
| demon whip "Spellbinder" | +5 | 11 | +1 | 1.1 | 0.5 (12) | Antimagic |
| great mace "Firestarter" | +7 | 17 | −4 | 1.7 | 0.7 (20) | Flaming |
| sceptre of Asmodeus | +13 | 15 | −1 | 1.5 | 0.7 (16) | 없음 |

- 딜레이는 브랜드(Speed ×2/3, Heavy ×1.5) 적용 전 값이다. → [공격 속도](weapons.md#4-공격-속도)
- \* dark maul은 최소 딜레이까지 스킬 28이 필요해서, 최대 스킬 27에서는 1.0~1.1턴(평균 1.05)이다. 여기에 Heavy ×1.5가 곱해진다.
- 손·최소 몸집은 원형과 같다. → [무기 수치표](weapons.md#maces--flails)

### mace of Variability
- 브랜드 Chaos.
- **명중할 때 1/5 확률로 Chain of Chaos 발동** (위력 `75 + random2avg(75, 2)`, 즉 75~149).
  - 무기를 든 사람에게서 시작한 혼돈의 호(arc)가 가까운 대상으로 옮겨 다닌다. 호 하나마다 **Chaos 데미지 `3d(5 + 위력/6)`**, 한 번 옮겨갈 때마다 위력이 8~20씩 줄어들고 0이 되면 끝난다(대략 5~12번).
  - **아군도 맞는다.** 사용자에게 돌아온 호는 데미지 없이 지나간다.
- 시야 안에 아군 등 공격하면 안 되는 대상이 있으면 공격할 때 경고가 나온다.

### sceptre of Torment
- 브랜드 Pain.
- **명중할 때 1/5 확률로 Torment.** 사용자를 중심으로 **시야 안의 모든 대상**(아군 포함)이 현재 HP의 `(50 − rN×5)% − 1`만큼 피해를 입는다. 사용자 자신은 영향받지 않는다.
  - Torment 저항(언데드 등)이 있는 대상은 피해가 없다. 플레이어가 맞는 경우 Torment 저항 돌연변이, 일부 변신 형태, Kikubaaqudgha의 보호가 피해를 줄인다.
  - 이 Torment로는 대상이 죽지 않는다(현재 HP의 절반 미만만 깎음).
- 시야 안에 Torment에 취약한 아군 등이 있으면 공격할 때 경고가 나온다.

### eveningstar "Brilliance"
- 브랜드 **Foul Flame**(언랜드 전용 브랜드). → [그 밖의 브랜드](brands-egos.md#그-밖의-브랜드)
- **Umbra(그림자 오라), 반경 3**:
  - 사용자는 nightvision(어둠 시야)을 얻는다.
  - **오라 안에 있는 대상을 공격하는 쪽**은, nightvision이 없으면 근접·원거리 명중 −3(볼트 등 빔 공격은 명중치 −6). 사용자 자신의 공격은 영향이 없다.
  - 사용자가 오라 안에 있고 빛(halo 등)에 드러나 있지 않으면 **Stealth ×1.5**.
- 몬스터가 들어도 같은 반경 3의 Umbra가 생긴다.

### giant club "Skullcrusher"
- 브랜드 Speed, **Str +7**. 고유 효과는 없다.
- giant club이므로 Large 이상만 들 수 있다.

### morningstar "Eos"
- 브랜드 Electrocution, **rElec**.
- **Halo(후광), 반경 3**:
  - 후광 안의 **다른 대상**은 빛에 드러난다(backlit): 투명 상태가 소용없어지고, 그 대상을 공격하는 쪽은 명중 +5(빔 공격은 명중치 +10).
  - **사용자 자신도 빛에 드러난 상태**가 된다: **Stealth ×2/5**, 투명화 불가. 다만 사용자를 공격하는 쪽이 명중 보너스를 얻지는 않는다.
- 몬스터가 들어도 같은 반경 3의 Halo가 생긴다.

### great mace "Undeadhunter"
- 브랜드 없음, **rN +1**.
- **언데드에게 명중하고 데미지가 들어가면 2/3 확률로 추가 데미지 `random2avg(1 + 데미지×3, 3)`** (평균 약 데미지 ×1.5). 그 공격으로 대상이 죽었으면 발동하지 않는다.

### whip "Snakebite"
- 브랜드 Venom, **rPois**.
- **명중할 때 2/5 확률로 Curare**(대상이 그 공격으로 죽지 않았을 때):
  - rPois가 있는 대상에게는 효과 없음.
  - 중독 2단계(강제 적용), **Poison 데미지 2d6**, **Slow**(Stasis가 있으면 Slow 제외).
- 몬스터 장비: Amaemon이 1/100 확률로 들고 나온다.

### shillelagh "Devastator"
- 브랜드 없음. 원형 club보다 기본 데미지 +3. **club 계열이지만 언랜드다**(일반 club은 아티팩트가 되지 않음).
- **명중하고 데미지가 들어가면 Shatter 폭발**: 대상 칸과 그 주변 8칸의 몬스터(사용자 제외)에게 `XdY − random2(1 + AC)` 데미지.
  - Y = `5 + 이번 공격 데미지/2`
  - X = 기본 3. 돌·금속·수정 계열 몬스터, 석화 중·석화된 대상, 해골·얼음 몬스터는 6. 날고 있거나 형체가 없는(amorphous) 대상은 1. 실체가 없는(insubstantial) 대상은 1.
  - **아군도 맞는다.** 플레이어가 사용자이면 플레이어는 맞지 않는다. 몬스터가 들고 있으면 그 몬스터에게 인접한 플레이어가 맞는다.
  - 소음 7.
- 몬스터가 주울 수 없고 Tukima's Dance의 대상이 되지 않는다(`special`).
- 초반 언랜드(`MAX_LEVEL` 11): 깊이 11 이하에서 생성 가중치가 높다.

### dark maul
- 브랜드 Heavy. **기본 데미지 +20, 명중 +2, 딜레이 +0.7**. 고유 효과는 없다.
- 데미지 37은 모든 근접 무기 중 최고 수준이지만, Heavy까지 더하면 공격 하나가 매우 느리다.

### demon whip "Spellbinder"
- 브랜드 Antimagic, **Willpower +1단계**.
- **마법을 쓰는 대상**(Antimagic이 통하는 몬스터)에게 명중하면, 그 공격으로 죽지 않은 경우 **매번 무작위 학파의 Miscast(마법 실패 효과)** 를 대상에게 일으킨다. 실패 레벨은 1~9 무작위, 세기는 그 공격의 데미지에 비례.
  - Miscast의 구체적인 효과는 학파마다 다르다(마법 문서에서 다룰 예정).

### great mace "Firestarter"
- 브랜드 Flaming, **rF++**, **불 구름(fire cloud) 면역**.
- **명중하고 데미지가 들어가면 대상에게 Inner Flame**을 건다(몬스터만, 이미 걸려 있지 않을 때). 지속 `3 + random2(데미지)` 턴. Inner Flame이 걸린 몬스터는 죽을 때 폭발한다.

### sceptre of Asmodeus
- **바닥에서 생성되지 않는다.** Gehenna의 Asmodeus가 들고 있고, 처치하면 얻을 수 있다.
- 브랜드 없음, 인챈트 +13. **Evil 아이템**(선한 신이 싫어함).
- **플레이어가 명중할 때 1/10 확률로 악마 소환**(소환물이나 주변부(peripheral) 몬스터를 때릴 때는 발동하지 않음):
  - Balrug 3 : Hellion 2 : Brimstone Fiend 1 비율로 하나, **아군**으로 소환. 지속은 약 40턴(무작위 변동).
  - 소환할 때마다 Evil 행위로 처리된다.
  - 아군을 둘 수 없는 상태(`allies_forbidden`, 예: 일부 신앙)에서는 발동하지 않는다.
- 몬스터는 Asmodeus 본인만 이 무기를 든다.

---

## Short Blades

### 수치표
| 언랜드 | 인챈트 | 데미지 | 명중 | 딜레이 | 최소 딜레이 (필요 스킬) | 브랜드 |
|---|---|---|---|---|---|---|
| Vampire's Tooth | +8 | 4 | +6 | 1.5 | 0.5 (20) | Vampirism |
| Spriggan's Knife | +7 | 4 | +6 | 1.0 | 0.5 (10) | 없음 |
| captain's cutlass | +7 | 7 | +4 | 1.2 | 0.5 (14) | Speed |
| arc blade | +8 | 7 | +4 | 1.2 | 0.5 (14) | 없음 |
| pair of quick blades "Gyre" and "Gimble" | +8 | 4 | +6 | 1.5 | 0.5 (20) | Protection |

→ [무기 수치표](weapons.md#short-blades)

### Vampire's Tooth
- 원형 quick blade: **한 번 휘두를 때 2회 타격.** → [무기 계열 특성](weapons.md#5-무기-계열별-특성)
- 브랜드 Vampirism이지만 **회복량이 다르다**: 일반 Vampirism은 발동 시 `1 ~ 데미지` 회복인데, Vampire's Tooth는 **들어간 데미지 전부**를 회복한다(대상의 rN으로 감소).
  - 발동 확률은 일반 Vampirism과 같다(3/5). 살아 있는(vampirism이 통하는) 대상에게만, 사용자 HP가 가득 차 있지 않을 때만, Death's Door 중이 아닐 때만 발동한다. → [Vampirism](brands-egos.md#vampirism)

### Spriggan's Knife
- 원형 dagger(이름 표기는 "knife"). 브랜드 없음, **EV +4, Stealth +1단계**.
- **암습(stab) 강화**: 암습이 가능한 상태의 대상(혼란, 다른 대상에 정신 팔림 등)을 칠 때, **1/2 확률로 잠든 대상처럼 취급**해서 가장 큰 암습 배율을 적용한다. 암습 자체는 [은신 & 암습](../stealth) 문서(예정)에서 다룬다.

### captain's cutlass
- 원형 rapier(이름 표기는 "cutlass"). 브랜드 Speed.
- **무장해제(Disarm)**: 플레이어가 무기를 든 몬스터에게 명중할 때, 아래를 모두 만족하면 **몬스터의 무기를 바닥에 떨어뜨리고 추가 데미지 18~35**.
  1. 1/2 확률
  2. 이번 공격 데미지 ≥ `3 + random2(대상 HD)`
  3. `대상 HD / (random2(20) + 데미지×4)` 확률의 저항 판정에 실패
  4. 그 공격으로 대상이 죽지 않음
- 몬스터가 들면 이 효과가 없다.

### arc blade
- 브랜드 없음, **rElec**.
- **명중할 때 1/3 확률로 Static Discharge 발동** (위력 `100 + random2avg(100, 2)`, 즉 100~199).
  - 대상이 인접해 있으면 **사용자 주변 칸**으로, 떨어져 있으면(reach 등) **대상 위치**에서 번개가 튄다.
  - 첫 번개 수: `1 + random2(2 + 위력/25)`. 각 번개는 맞은 대상에서 다시 주변으로 `1 + random2(2 + 위력/25)`번 연쇄된다.
  - 번개 하나의 데미지: `3 + random2(3 + 위력/12)` (위력 100에서 3~13, 199에서 3~21). **AC는 절반만 적용**, rElec로 감소. rElec 면역(3단계)인 대상에서는 연쇄가 끊긴다.
  - **아군과 사용자 자신도 맞을 수 있다.** 사용자에게 튄 번개는 데미지 절반.
- 공격하기 전에 번개가 아군에게 튈 수 있으면 경고가 나온다.
- 몬스터 장비: Nikola가 1/100 확률로 들고 나온다.

### pair of quick blades "Gyre" and "Gimble"
- quick blade 두 자루 한 쌍. **양손 무기로 취급**된다(방패·오브와 같이 쓸 수 없음).
- **한 번 휘두를 때 4회 타격**(일반 quick blade는 2회). 타격마다 "Gyre"와 "Gimble"이 번갈아 표시된다.
- 브랜드 Protection(적을 맞히면 일시적으로 AC +7). → [Protection](brands-egos.md#protection)

---

## Long Blades

### 수치표
| 언랜드 | 인챈트 | 데미지 | 명중 | 딜레이 | 최소 딜레이 (필요 스킬) | 브랜드 |
|---|---|---|---|---|---|---|
| Singing Sword | +11 | 15 | −1 | 1.5 | 0.7 (16) | 없음 |
| demon blade "Leech" | +8 | 13 | −1 | 1.3 | 0.6 (14) | Vampirism |
| zealot's sword | +10 | 14 | −2 | 1.2 | 0.6 (12) | Holy Wrath |
| sword of the Dread Knight | +13 | 17 | −3 | 1.7 | 0.7 (20) | 없음 |
| plutonium sword | +11 | 19 | −4 | 1.8 | 0.7 (22) | 없음 |
| autumn katana | +8 | **14 (+4)** | **+3 (+2)** | **1.2 (−0.2)** | 0.6 (12) | 없음 |
| Maxwell's thermic engine | +2 ~ +14 (변동) | 15 | −1 | 1.5 | 0.7 (16) | Flaming |
| Throatcutter | +7 | 10 | +1 | 1.4 | 0.7 (14) | Draining |
| sword of Cerebov | +6 | **18 (+1)** | **−2 (+1)** | 1.7 | 0.7 (20) | Flaming |

→ [무기 수치표](weapons.md#long-blades)

### Singing Sword
- 브랜드 없음, 인챈트 +11.
- **명중할 때 일정 확률로 Sonic Wave 발동**: 사용자를 중심으로 **시야 안의 모든 대상**(아군 포함, 사용자 제외)에게 데미지. 데미지는 주사위 2개로 합계 최대 `5 + 위력/5`, 대상의 AC가 적용된다.
- 발동 확률과 위력은 **전투의 긴장도(tension)** 단계에 따라 달라진다. 단계 = `1 + 긴장도/20` (1~4). 긴장도는 주변 적의 위협 정도로 게임이 내부적으로 계산하는 값이다.

| 단계 | 이름 표시 | 발동 확률 | 위력 | 최대 데미지 | 소음 |
|---|---|---|---|---|---|
| 0 (사용자가 Silence 안) | Sulking Sword | (대사만, 발동 없음) | — | — | 0 |
| 1 | Singing Sword | 6/24 = 25% | 100 | 25 | 0 |
| 2 | Singing Sword | 6/16 = 37.5% | 113 | 27 | 20 |
| 3 | Singing Sword | 6/12 = 50% | 126 | 30 | 30 |
| 4 | **Screaming Sword** | 6/12 = 50% | 175 | 40 | 40 |

- 발동할 때마다 대사를 말하며, 단계 2 이상이면 그만큼 소음을 낸다.
- 몬스터가 들면 항상 단계 1로 취급한다.
- Silence 상태가 아니고 시야 안에 공격하면 안 되는 대상이 있으면 공격할 때 경고가 나온다.

### demon blade "Leech"
- 브랜드 Vampirism, **rN +1**, **Harm**(주는 데미지와 받는 데미지 증가), **^Drain**(해제 시 최대 HP Drain). → [아티팩트 속성](artefact-properties.md)
- **Vampirism이 매번 발동한다**: 일반 Vampirism의 2/5 실패 판정이 없다. 회복량은 일반과 같은 `1 ~ 데미지`. 그 밖의 조건(살아 있는 대상, HP가 가득 차 있지 않음 등)은 같다. → [Vampirism](brands-egos.md#vampirism)
- 플레이어가 피가 있는 대상을 죽이면 `데미지/729` 확률로 대상이 피 구름으로 터진다(연출).

### zealot's sword
- 원형 eudemon blade(설명에서도 원형 이름이 드러나지 않는다). 브랜드 Holy Wrath, **EV +3, rN +1, \*Rage 20%**(근접 공격 시 20% 확률로 광폭화).
- **Zealotry**: 사용자가 광폭화(Berserk)하면 **시야 안의 모든 아군도 같이 광폭화**한다. 몬스터가 들고 있으면 그 몬스터 편의 대상이 같이 광폭화한다.

### sword of the Dread Knight
- 브랜드 없음, 인챈트 +13, **Willpower +1단계**, **\*Silence**(피해를 받을 때 확률적으로 침묵), **Evil 아이템**, **^Drain**.
- **Decimate**: 명중할 때마다(대상이 죽지 않았으면) 추가 데미지 `random2avg(1 + 대상 최대HP/10, 3)` (평균 약 대상 최대 HP의 5%). AC를 무시한다.

### plutonium sword
- 브랜드 없음, 인챈트 +11, **Stealth −1단계**, **^Contam**(해제 시 마법 오염), **Chaotic 아이템**(Zin이 싫어함).
- **명중할 때 1/5 확률로 변이 에너지**(대상이 그 공격으로 죽지 않았고 돌연변이가 가능한 대상일 때):
  - 그중 1/10: 대상을 **Polymorph**(다른 몬스터로 변신). 플레이어가 맞으면 7~14턴의 짧은 변이.
  - 나머지: 몬스터에게 **나쁜 돌연변이(malmutate) + 데미지 5~25**. 플레이어가 맞으면 마법 오염 700~1350 + 데미지 5~25.
  - 플레이어가 사용자이면 발동할 때마다 Chaos 행위로 처리된다.

### autumn katana
- 원형 long sword(이름 표기는 "katana"). 브랜드 없음. **기본 데미지 +4, 명중 +2, 딜레이 −0.2.**
- **명중할 때 1/8 확률로 Manifold Assault**: 시야 안의 보이는 **적대 대상** 중 원래 대상을 뺀 최대 8명에게 이 카타나로 근접 공격을 한 번씩 한다(순서 무작위). 아군과 중립 몬스터는 대상에서 빠진다.
  - 이 연쇄 공격에서 다시 Manifold Assault가 발동하지는 않는다.

### Maxwell's thermic engine
- 브랜드 Flaming. 인챈트가 **+2에서 시작해 전투 중에 변한다.**
  - **명중할 때마다 인챈트 +2**, 최대 +14.
  - **턴마다 인챈트 −1**씩 +2까지 돌아간다.
  - 장착하거나 해제하면 +2로 초기화된다.
- **Freeze**: 명중할 때마다(대상이 죽지 않았으면) 추가 Cold 데미지 `random2(데미지)/2 + 1` (평균 약 데미지의 1/4, rC로 감소). 냉기에 노출시키므로 냉혈 몬스터를 느리게 할 수 있다.

### Throatcutter
- 브랜드 Draining.
- **Coup de Grace**: 몬스터에게 명중한 뒤 대상의 **남은 HP가 20 이하**이면 **1/3 확률로 즉사**. 머리가 여럿인 히드라도 한 번에 죽는다. 플레이어에게는 발동하지 않는다.
- 초반 언랜드(`MAX_LEVEL` 9).
- 몬스터 장비: Terence가 1/100 확률로 들고 나온다.

### sword of Cerebov
- **바닥에서 생성되지 않는다.** Pandemonium의 Cerebov가 들고 있다.
- 원형 great sword(이름 표기는 "flamberge"). 기본 데미지 +1, 명중 +1. 브랜드 Flaming, **Evil 아이템**.
- **Hellfire**: 데미지가 들어가면 대상에게 **Fire Vulnerability**(rF −1)를 건다. 지속 `3 + random2(데미지)` 턴. 이미 걸려 있으면 새로 걸지 않는다. 플레이어가 맞아도 걸린다.
- 몬스터는 Cerebov 본인만 이 무기를 든다.

## Axes

### 수치표
| 언랜드 | 인챈트 | 데미지 | 명중 | 딜레이 | 최소 딜레이 (필요 스킬) | 브랜드 |
|---|---|---|---|---|---|---|
| Wrath of Trog | +8 | 15 | −4 | 1.7 | 0.7 (20) | Antimagic |
| mithril axe "Arga" | +8 | 13 | −2 | 1.6 | 0.7 (18) | Speed |
| obsidian axe | +16 | 13 | −2 | 1.6 | 0.7 (18) | Draining |
| frozen axe "Frostbite" | +8 | 18 | −6 | 1.9 | 0.7 (24) | Freezing |
| woodcutter's axe | +5 | 15 | −4 | **1.0 (−0.7) 고정** | 1.0 (—) | 없음 |
| consecrated labrys | +4 ~ +16 (변동) | **14 (+1)** | −2 | 1.6 | 0.7 (18) | Holy Wrath |
| Axe of Woe | — | 18 | (항상 명중) | 1.9 | 0.7 (24) | 없음 |

- Axes 계열이므로 모두 **휩쓸기(cleave)**를 한다. → [무기 계열 특성](weapons.md#5-무기-계열별-특성)
- → [무기 수치표](weapons.md#axes)

### Wrath of Trog
- 브랜드 Antimagic, **\*Rage 50%**(근접 공격 시 50% 확률로 광폭화), **Rampage**.
- **장착하는 순간 광폭화가 끝난 직후와 같은 대가를 받는다**: 광폭화 중이 아니어도 Slow `12 + 2d12`턴, 광폭화 재사용 대기(exhaustion) 그 2배.
- **광폭화 중에 적을 죽이면 1/2 확률로 광폭화 지속 1~2턴 연장.** (Trog 신자의 신앙 효과로 연장이 먼저 발동한 경우에는 이 효과가 발동하지 않는다.)
- **Trog은 이 무기를 선물하지 않는다**(Trog 선물로 나오면 파괴된다).

### mithril axe "Arga"
- 브랜드 Speed, **Willpower +1단계**. 고유 효과는 없다.

### obsidian axe
- 브랜드 Draining, 인챈트 +16, **SInv, 비행, ^Drain**.
- **명중할 때 1/10 확률로 악마 소환**(주변부(peripheral) 몬스터를 때릴 때는 제외):
  - 플레이어: 1/3 확률로 3등급 악마(sun demon, soul eater, smoke demon, neqoxec, ynoxinul, sixfirhy 중 하나), 2/3 확률로 4등급 악마(ice devil, rust devil, orange demon, red devil, chaos spawn, hellwing 중 하나)를 **아군**으로 소환. 아군을 둘 수 없는 상태면 발동하지 않는다.
  - 몬스터가 들고 있으면 같은 편의 일반 악마를 소환한다.
  - 소환 지속은 약 190턴(무작위 변동).
- **Mesmerise(매혹)**: 매 턴, 보이는 위협적인 적 중 가장 가까운 하나에게 **매혹**된다(그 적에게서 멀어지는 이동 불가). 새 대상에게 매혹될 때는 다른 매혹 출처가 모두 지워진다.
  - 매혹된 동안에는 **이 무기를 해제할 수 없다.**
  - 대신 **Confusion이 매 턴 풀린다.**
  - 매혹 중에도 광폭화할 수 있다(일반적으로는 매혹 중 광폭화 불가).
  - 해제하면 매혹이 모두 풀린다.
- 설명에서 원형 이름(broad axe)이 드러나지 않는다.

### frozen axe "Frostbite"
- 브랜드 Freezing, **rC +1, 비행**, 말을 한다(`noises`, 소음 발생).
- **명중할 때 1/5 확률로 대상 칸에 freezing cloud**(지속 4~8).
- **freezing cloud 면역.**

### woodcutter's axe
- 브랜드 없음. 원형 battleaxe(1.7)보다 딜레이 −0.7.
- **공격 딜레이가 항상 정확히 1.0턴**이다. 스킬로 줄어들지 않고, 방패 페널티, Finesse, Haste·Slow 같은 속도 보정도 적용되지 않는다(`player-act.cc`에서 다른 계산 전에 바로 반환).
- 초반 언랜드(`MAX_LEVEL` 9).

### consecrated labrys
- 원형 broad axe(이름 표기는 "labrys"). 기본 데미지 +1. 브랜드 Holy Wrath, **비행, SInv, ^Fragile**(해제하면 파괴).
- **Valiant**: 인챈트가 시야 안의 위협에 따라 매 턴 바뀐다.
  - 인챈트 = `min(4 + 3 × 공포 수치, 16)`
  - 공포 수치(horror level): 시야 안의 적대적이고 위협적인 몬스터마다, 위협도 **nasty(빨강) +3, tough(노랑) +1**. 그 밖은 0.
  - 예: 위협 없음 +4, tough 2마리 +10, nasty 1마리 +13, nasty 2마리 이상 +16.

### Axe of Woe
- **일반 게임에서는 생성되지 않는다**(`nogen`). Sprint 모드의 맵(`sprint/meat.des`)에 배치된다.
- 원형 executioner's axe. 들 수 없는 종족이면 broad axe로 바뀌어 생성된다(항상 들 수 있게).
- **항상 명중한다.** 명중한 대상은 **남은 HP만큼 피해를 받아 즉사**한다(휩쓸기 대상 포함). 데미지 표시는 "∞"로 나온다.

## Polearms
(다음 실행에서 작성)

## Staves
(다음 실행에서 작성)

## Ranged Weapons
(다음 실행에서 작성)

> 출처: art-data.txt, art-func.h, item-prop.cc, fight.cc, attack.cc, melee-attack.cc, areas.cc, player.cc, monster.cc, spl-damage.cc, spl-goditem.cc, beam.cc, cloud.cc, mon-gear.cc, mon-ench.cc, makeitem.cc, artefact.cc (0.34.1)
