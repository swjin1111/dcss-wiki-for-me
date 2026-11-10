# 스크롤 (Scrolls)

> 기준: DCSS 0.34.1 · [아이템 목록으로](index.md)

스크롤의 종류별 효과·수치, 읽는 규칙, 생성 규칙을 정리한다. 스크롤은 읽거나 Scroll of Identify로 감정한다. → [감정](index.md#감정-identification)

지속 시간은 **턴**(10 aut = 1턴) 단위다. 스크롤을 읽는 데는 행동 1회가 든다.

---

## 1. 목록

| 스크롤 | 효과 요약 | 생성 가중치 |
|---|---|---|
| [identify](#21-identify) | 미감정 아이템 1개 감정 | 200 (26.1%) |
| [teleportation](#22-teleportation) | 3~5턴 뒤 같은 층의 무작위 위치로 순간이동 | 100 (13.1%) |
| [enchant weapon](#23-enchant-weapon) | 무기 인챈트 +1 (최대 +9) | 36 (4.7%) |
| [enchant armour](#24-enchant-armour) | 방어구 인챈트 +1 | 36 |
| [blinking](#25-blinking) | 시야 안의 원하는 칸으로 즉시 이동 | 36 |
| [fear](#26-fear) | 시야 안의 적에게 Fear(공포) | 36 |
| [fog](#27-fog) | 주변에 연기 구름 | 36 |
| [revelation](#28-revelation) | 층 전체 지형 지도 + 1턴 동안 주변 투시 | 36 |
| [immolation](#29-immolation) | 시야 안의 몬스터에게 Inner Flame | 36 |
| [poison](#210-poison) | 시야 안의 빈칸 전부에 독 구름 | 36 |
| [vulnerability](#211-vulnerability) | 자신과 시야 안 몬스터의 Willpower 절반 | 36 |
| [noise](#212-noise) | 큰 소음 | 36 |
| [amnesia](#213-amnesia) | 기억한 주문 1개 잊기 | 36 |
| [summoning](#214-summoning) 또는 [butterflies](#215-butterflies) | 아군 소환 (게임마다 둘 중 하나만 생성) | 15 (2.0%) |
| [silence](#216-silence) | 자신 주변 Silence(침묵) | 15 |
| [brand weapon](#217-brand-weapon) | 무기 브랜드를 무작위로 교체 | 15 |
| [torment](#218-torment) | 자신 포함 시야 안 전체에 Torment | 15 |
| [acquirement](#3-acquirement) | 고른 아이템 1개 획득 | 9 (1.2%) |

- 가중치 합 765(summoning·butterflies 중 하나만 포함). 괄호 안은 바닥 무작위 생성 시 스크롤 중 해당 종류가 나올 확률. `makeitem.cc`의 주석은 합계를 750으로 적고 있지만 실제 가중치 합은 765다(0.34.1).
- 아래 스크롤은 세이브 호환용으로 코드에만 남아 있고 **생성되지 않는다**(`removed_items`): remove curse, random uselessness, curse weapon / armour / jewellery, enchant weapon II / III, recharging, holy word. 읽으면 "This item has been removed"가 출력되고 소모되지 않는다.

### 1.1 아이템 세트 (Item Set)
일부 아이템은 **세트로 묶여 있어서, 게임을 시작할 때 세트마다 한 종류만 골라 그 게임에서 생성된다**(`item-prop.cc` `item_sets`).

| 세트 | 후보 (게임마다 1개) |
|---|---|
| ally scroll | scroll of **summoning** / scroll of **butterflies** |
| hex wand | wand of charming / paralysis |
| beam wand | wand of acid / light / quicksilver |
| blast wand | wand of iceblast / roots / warping |
| area misc | condenser vane / tin of tremorstones |
| ally misc | box of beasts / sack of spiders |
| control misc | phial of floods / gravitambourine |

- 바닥 무작위 생성과 볼트 지정 아이템(`.des`)은 이 선택을 따른다(볼트가 예외 플래그를 단 경우 제외). 시작 아이템은 예외라서, 시작 인벤토리에 있는 종류는 그 게임의 선택을 알려주지 않는다.
- 선택된 종류를 한 번 보면, 같은 세트의 나머지 종류는 "이번 게임에 없음"으로 취급되어 감정 목록에서 빠진다.

---

## 2. 종류별 효과

### 2.1 identify
- **미감정 아이템 1개를 고른다**(인벤토리 또는 발밑). 책은 대상이 아니다. 대부분의 장비는 올라서면 자동 감정되므로, 실제 대상은 주로 미감정 포션·스크롤이다.
- 모르고 읽었을 때 선택을 취소하면 "스크롤을 버리겠느냐"고 묻는다(취소해도 소모).
- **소거법 자동 감정**: 어떤 종류(포션 또는 스크롤)에서 미감정 종류가 1개만 남으면, 그 종류는 볼 때 자동으로 감정된다. 위 아이템 세트에서 이번 게임에 없는 종류는 감정된 것으로 친다.
  - 그래서 포션·스크롤 각각 미감정 종류가 1개 이하이면 감정된 identify를 읽을 수 없다("There is nothing left to identify"). Mummy는 포션을 세지 않는다.
- **Ashenzari** 신자(권능 1단계 이상)는 읽을 수 없다("no need of identification").

### 2.2 teleportation
- **`3 + random2(3)` = 3~5턴 뒤 순간이동**한다. 대기 중에는 상태 표시 "Tele".
  - **Abyss**: 지연 +5~14턴. 순간이동하면 Abyss의 새 구역으로 간다.
  - **Zot, Orb of Zot 소지, Charlatan's Orb 착용**: 지연 +5~9턴.
- **대기 중에 다시 읽으면 순간이동이 취소된다.**
- 도착 위치: 같은 층의 무작위 칸. 몬스터·구름·벽·위험 지형(용암, 깊은 물 등)이 있는 칸과 순간이동 금지 구역은 제외한다.
- **읽을 수 없거나 효과가 없는 경우**: Stasis, −Tele(순간이동 금지) 장비, Dimension Anchor, tree form, **Gauntlet**, Dungeon Sprint. 감정된 스크롤은 거부되고, 모르고 읽으면 효과 없이 소모된다.
- cancellation으로 대기 중인 순간이동을 취소할 수 있다. → [cancellation](potions.md#312-cancellation)

### 2.3 enchant weapon
- 고른 무기의 **인챈트 +1**. 상한 **+9**. 무기 인챈트의 효과는 → [인챈트](index.md#인챈트-enchantment-n)
- 대상: 일반 무기(원거리 무기 포함). **아티팩트는 안 된다**(Mountain Dwarf는 언랜드가 아닌 randart 가능). magical staff(지팡이)와 투척 무기는 대상이 아니다.
- 손이 없는 종족(`MUT_NO_GRASPING`, Felid 등)은 읽을 수 없다(감정된 경우).

### 2.4 enchant armour
- 고른 방어구의 **인챈트 +1**(방패는 SH). 상한은 부위마다 다르다. → [스크롤로 올릴 수 있는 상한](index.md#스크롤로-올릴-수-있는-상한)
- 아티팩트 불가(Mountain Dwarf 예외는 enchant weapon과 같음). quicksilver dragon scales, scarf, orb는 인챈트할 수 없다.

### 2.5 blinking
- **시야 안의 원하는 칸으로 즉시 이동**한다(Blink 주문과 달리 위치를 고를 수 있다). 출발 칸에 translocation energy 구름이 남는다.
  - 보이지 않는 칸, 투명한 벽 너머, 벽, 보이는 몬스터가 있는 칸, 위험 지형은 고를 수 없다.
  - Mesmerised면 매혹한 몬스터에게서 멀어지는 칸, Fear면 공포를 준 몬스터에게 가까워지는 칸은 고를 수 없다.
  - 고른 칸에 **보이지 않는 몬스터가 있으면** 무작위 근거리 Blink로 바뀐다.
- **Zot, Orb 소지, Charlatan's Orb**: 사거리가 **시야 반경 −2**로 줄고, 도착점이 **고른 칸 주변 반경 2 안의 무작위 칸**으로 흔들린다.
- 감정된 상태로 위치 선택을 취소하면 소모되지 않는다. **모르고 읽었을 때는 취소할 수 없다**(반드시 위치를 골라야 함).
- Constriction(조임)에서 벗어난다.
- Stasis, −Tele 장비, Dimension Anchor, tree form에서는 쓸 수 없다. **Gauntlet과 Sprint의 금지는 blinking에는 적용되지 않는다.**

### 2.6 fear
- **시야 안(투명한 벽 너머 제외)의 모든 적대 몬스터**에게 Fear를 건다. Spell power 1000 → mass enchantment 배율 ×1.5 후 **상한 200**으로 Willpower 판정.
- 면역: 아군, 이미 Fear인 몬스터, natural·demonic·holy가 아닌 몬스터(언데드, nonliving, 식물 등), Berserk·Frenzy 상태, Clarity, firewood(식물·버섯 등 고정물), Willpower ∞(`WILL_INVULN`).
- 지속: 보통 속도 몬스터 기준 약 `150 / (HD + 6)`턴에 무작위 보정(−60%~+40%). HD가 높을수록 짧다.
- 시야 안에 영향을 받을 적이 보이지 않으면 감정된 상태에서 확인을 묻는다.

### 2.7 fog
- 자신을 중심으로 **8~15칸**에 연기 구름(grey / blue / black / purple smoke 중 무작위 1종)을 만든다.
- 각 구름의 지속: `3 + random2(12) + random2(12) + random2(12)` = **3~36턴**(평균 19.5).
- 연기는 시야를 가리고 피해는 없다.
- **Still Winds 상태의 층**에서는 감정된 상태로 읽을 수 없다(poison도 같음).

### 2.8 revelation
- **현재 층 전체의 지형을 지도에 기록**한다(magic mapping, 반경 제한 없음, 거리 감쇠 없음). 아이템·몬스터는 표시되지 않는다.
- 추가로 **읽은 그 턴 동안**:
  - 시야 반경 안의 모든 칸을 **벽과 무관하게** 본다.
  - **투명한 몬스터도 보인다**(See Invisible).
- 지도가 유지되지 않는 곳(`no_map` 플래그가 있는 **Abyss**)에서는 감정된 상태로 읽을 수 없다.

### 2.9 immolation
- 시야 안의 **모든 몬스터(아군 포함)**에게 **Inner Flame**을 건다. **Willpower 판정이 없다.** 면역은 Willpower ∞ 몬스터뿐이다(Jiyva 신자일 때 슬라임 제외).
- Inner Flame(지속 25~35턴):
  - 공격자에게 피해를 받을 때마다 그 칸에 불 구름이 생긴다.
  - **죽으면 폭발**: 화염 피해, 몸집 Tiny 이하 3d15 / 그 위 3d20 / Large 초과 3d25. 폭발 반경 1(Large 초과는 2). 폭발 범위 안의 다른 대상이 맞는지는 일반 폭발 규칙을 따른다(플레이어 피격 여부 미확인).
  - 남은 HP가 −15 이하로 크게 죽거나, 추방(banish)·리셋으로 사라지면 폭발하지 않는다.
- 시야 안에 영향받을 적이 없으면 감정된 상태에서 확인을 묻는다(위험 아이템).

### 2.10 poison
- **시야 안의 빈칸(누군가 서 있지 않은 칸) 전부**에 **독 구름**(지속 10~20턴)을 만든다. 플레이어가 서 있는 칸은 비어 있지 않으므로 제외되지만, 움직이면 구름에 들어가게 된다.
- 감정된 상태에서 구름을 만들 빈칸이 없으면 소모되지 않는다.
- rPois가 없고 구름 면역이 아니면 위험 아이템으로 취급되어 확인을 묻는다.

### 2.11 vulnerability
- **자신과 시야 안의 모든 몬스터(아군 포함)**의 **Willpower를 절반**으로 만든다. 지속 `30 + random2(20)` = **30~49턴**(플레이어는 합계 상한 40턴).
- Willpower 판정 없이 걸린다. Willpower ∞ 몬스터만 면역이다.
- 적대 몬스터는 이 스크롤로 플레이어에게 적대적 반응(annoy)을 보인다. 아군은 적대로 바뀌지 않는다.
- 참고: **Tartarus** 안에서는 플레이어의 Willpower가 항상 절반이다(같은 계산 위치).

### 2.12 noise
- 읽은 위치에 **크기 25의 소음**을 낸다. 소음이 몬스터를 깨우고 끌어들이는 규칙은 은신 문서에서 다룰 예정이다.

### 2.13 amnesia
- **기억한 주문 1개를 골라 잊는다.** 잊은 주문의 레벨만큼 주문 슬롯이 돌아온다. 주문은 라이브러리에 남아 있어 다시 배울 수 있다.
- 기억한 주문이 없으면 감정된 상태로는 읽을 수 없다(모르고 읽으면 "forgetful for a moment"만 출력).
- **Djinni**(`MUT_INNATE_CASTER`)와 **Trog 신자**는 읽을 수 없다.

### 2.14 summoning
- **2~4마리**(2d2)의 아군 몬스터를 소환한다. 종류는 **현재 층에서 생성될 수 있는 몬스터** 중 무작위(정지형 몬스터와 신앙에 맞지 않는 몬스터 제외, 깊이보다 강한 몬스터 제외). 무리(band)로 나오는 몬스터는 무리째 소환된다.
  - 신이 싫어하는 무리 구성원은 제거된다.
- 지속은 몬스터 HD에 따라 다르다: `min(4, 1 + 17/max(HD−3, 1))` 등급 → 등급당 약 10턴(−60%~+40% 보정). HD 8 이하는 약 40턴, HD 20이면 약 20턴.
- 무리 구성원은 리더와 소환 수 제한을 공유한다.
- 주변에 소환할 공간이 없으면 감정된 상태에서는 소모되지 않는다.
- 아군을 가질 수 없는 경우(Ru의 Sacrifice Love 등 `allies_forbidden`)에는 감정된 상태로 읽을 수 없다.
- [아이템 세트](#11-아이템-세트-item-set): butterflies와 둘 중 하나만 그 게임에서 생성된다.

### 2.15 butterflies
1. 먼저 **반경 2 안의 모든 몬스터를 2~4칸 밀어낸다**(먼 것부터). 밀려난 몬스터는 플레이어를 인지한다.
2. **아군 butterfly** 16~22마리를 주변 반경 2에, 다시 12~28마리를 반경 5 안에 배치한다. 지속 약 30턴(소환 등급 3).
- 아군을 가질 수 없으면 아무 일도 일어나지 않는다(감정된 상태로는 읽을 수 없음).
- [아이템 세트](#11-아이템-세트-item-set): summoning과 둘 중 하나만 생성된다.

### 2.16 silence
- 플레이어를 중심으로 **Silence**. 지속 `20 + 6 + random2avg(15, 2)` = **26~40턴**(Silence 주문 위력 30과 같음, 합계 상한 100).
- 반경은 남은 지속에 따라 줄어든다: `√(min(3 × (남은 턴 − 5) / 4, 25))` → 처음 3~5칸, 끝날 무렵 0(자기 칸만).
- 범위 안에서는 **스크롤 읽기, 주문 시전, 신의 권능 사용, 외치기가 불가능**하다(플레이어와 몬스터 모두). 일부 몬스터의 고유 능력은 쓸 수 있다.
- 위험 아이템으로 취급되어 감정된 상태에서 확인을 묻는다.

### 2.17 brand weapon
- 고른 무기의 브랜드를 **기존과 다른 무작위 브랜드로 교체**한다. 신이 금지하는 브랜드가 나오면 다시 굴린다.
- **아티팩트와 축복받은 무기(blessed)는 대상이 아니다.** 원거리 무기도 된다.
- 근접 무기의 브랜드 가중치(합 17):

| 브랜드 | 가중치 |
|---|---|
| flaming, freezing, heavy, venom, protection | 각 2 |
| **무기 계열 전용 브랜드** | 2 |
| draining, electrocution, spectral, vampirism, chaos | 각 1 |

  - 계열 전용 브랜드: Short Blades → devious, Long Blades → valour, Maces & Flails → concussion, Axes → sundering, Polearms → entangling, Staves → rebuke. → [브랜드·에고](brands-egos.md)
- 원거리 무기의 브랜드 가중치(합 14): flaming·freezing·draining·heavy 각 3, electrocution·chaos 각 1.
- 기존 브랜드와 같은 것이 나오면 다시 굴리므로, 실제 확률은 위 가중치에서 기존 브랜드를 뺀 비율이다.
- spectral 브랜드였던 무기를 바꾸면 소환된 spectral weapon이 사라진다.

### 2.18 torment
- **자신을 포함해 시야 안(투명한 벽 너머 제외)의 모든 생물**에게 Torment.
- 피해: **현재 HP × (50 − rN × 5)% − 1** (rN 0단계면 현재 HP의 절반). 현재 HP 기준이라 **이 피해로 직접 죽지는 않는다.**
  - 플레이어: statue form·vampire form·bat swarm form이면 절반, `MUT_TORMENT_RESISTANCE`이면 다시 절반. Torment 면역(언데드 등)이면 피해 없음. Kikubaaqudgha 신자는 확률적으로 막거나 줄인다.
  - 몬스터: Torment 면역(언데드, 데몬 등)이면 피해 없음.
- 감정된 상태로 읽으면 DID_EVIL conduct(선한 신이 싫어함). 감정된 torment는 선한 신 신자에게 징벌 경고와 함께 확인을 묻는다.
- 모르고 읽은 경우 아군은 적대 반응을 보이지 않는다.

---

## 3. acquirement
**고를 수 있는 아이템 목록을 보여주고, 그중 하나를 발밑에 만든다.** 감정 여부와 무관하게 읽으면 곧바로 acquirement임을 알려준다.

### 3.1 선택지 구성
1. 다음 분류 중 사용 가능한 것을 섞어서 **앞에서부터 최대 3개 분류**의 아이템을 하나씩 만든다.

| 분류 | 포함 조건 |
|---|---|
| 방어구 | 방어구를 입을 수 있음 |
| 무기 | 손이 있음(`MUT_NO_GRASPING` 아님) |
| magical staff | 손이 있고, **1/3 확률**로만 후보에 들어감 |
| 장신구 | Coglin이 아님 |
| 책 | 항상 |
| 탈리스만 | Zin 신자가 아니고 변신 불가 종족이 아니며, **45% 확률**로만 후보에 들어감 |

2. 여기에 **골드(200~1400, 두 난수의 평균)**가 항상 추가된다.
- 선택지는 처음 읽을 때 정해져 저장된다. **목록을 닫으면(감정 여부와 무관) 스크롤이 소모되지 않고, 다음에 읽을 때 같은 목록이 나온다.**
- 아이템이 사라지는 지형(깊은 물(수중 종족 제외), 용암 등) 위에서는 읽어도 취소된다.
- 선택하지 않은 목록의 언랜드는 다시 생성될 수 있는 상태로 돌아간다.

### 3.2 분류별 규칙 (요약)
모든 아이템은 "좋은 아이템"(`ISPEC_GOOD_ITEM`) 품질로 만들어지고, 쓸 수 없는 아이템·신이 싫어하는 아이템은 다시 만든다(최대 40회).

- **무기**: 무기 스킬을 무작위로 고른다. 스킬 가중치 `(s + 2)(s + 3)`(s = 그 스킬 레벨)이라 많이 올린 스킬이 크게 유리하다. 그 스킬의 무기 중 획득 가중치(`acq_weight`)로 고르며, **아직 본 적 없는 무기 종류는 ×5**. 양손 무기는 Shields 스킬이 높을수록 덜 나온다.
  - 브랜드가 없거나 흔한 브랜드(flaming, freezing, draining, heavy, venom, protection, electrocution)이면 높은 확률로 다시 굴린다(브랜드 없음은 1/10, 흔한 브랜드는 1/3 확률로만 유지).
  - 인챈트는 0 미만이 되지 않는다. 브랜드 없는 giant club류는 24/25 확률로 randart가 된다.
- **방어구**: 부위 가중치 몸통 2, 방패 1, 망토·투구·장갑·부츠·바딩은 그 부위를 본 적이 없으면 3, 있으면 1(Naga·Armataur는 바딩 우선). 몸통 방어구는 Armour 스킬이 높을수록 무거운 것이 잘 나오고, 방패는 Shields 스킬이 높을수록 tower shield가 잘 나온다.
  - **아티팩트가 아닌 방어구는 12/13 확률로 다시 만든다** → 획득한 방어구는 대부분 아티팩트다.
- **장신구**: 반지와 목걸이 비율은 반지 슬롯 수 : 1. 아직 감정하지 않은 종류를 최대 10번까지 우선 시도한다. 수치 반지는 고정값(능력치 +6, protection·slaying +4, evasion +5). 언랜드가 아니면 **1/2 확률로 randart**.
- **magical staff**: 해당 학파 스킬 레벨을 가중치로 고르고(무작위 가중치 5 추가), 이미 감정한 지팡이 종류는 제외. 언랜드가 아니면 **4/5 확률로 randart**.
- **책**: 마법 스킬과 그 밖 스킬의 비율에 따라 **스킬 교본(manual)**이 나올 수 있다(스킬 경험치 2000~3000, 27레벨 스킬·쓸모없는 스킬 제외). 아니면 모르는 주문이 많은 책, 테마 randart 책, 레벨 randart 책 중 하나.
- **탈리스만**: 아직 본 적 없는 종류 ×10, Shapeshifting 스킬로 정한 목표 등급(3~6)에 가까울수록 가중치가 크다. 1/4 확률로 randart. 스크롤로는 protean talisman이 나오지 않는다.

신의 선물(Okawaru, Trog 등)도 같은 함수를 쓰지만 부위 가중치·품질이 다르다(신 문서에서 다룰 예정).

---

## 4. 읽을 수 없는 경우

| 조건 | 내용 |
|---|---|
| **Gehenna** | 이 브랜치 안에서는 스크롤을 읽을 수 없다("smoke and ash is too thick") |
| Berserk | 불가 |
| **Confusion** | 불가 |
| **Silence 범위 안, Flooded 상태** | 불가 |
| Ru의 Sacrifice Words (`MUT_RENOUNCE_SCROLLS`) | 적대 몬스터가 근처에 보이는 동안과 그 뒤 6턴 불가. **HP가 최대의 1/2 이하이면 가능**(포션 희생은 1/2 미만) |

- 그 밖에 종류별 조건(위 각 항목)에 해당하면 감정된 스크롤은 거부된다. 미감정 스크롤은 그런 검사 없이 읽힌다.
- 코드에는 스크롤 사용 금지 상태(`DUR_NO_SCROLLS`)가 정의되어 있지만, 0.34.1에서 이 상태를 거는 곳은 없다.
- **위험 아이템**(immolation, vulnerability, noise, silence, torment(면역이 아닐 때), poison(rPois 없을 때))은 감정된 상태로 읽을 때 확인을 묻는다. 시야 안에 영향받을 적이 없으면 그 사실도 함께 알려준다.

## 5. 스크롤에 영향을 주는 요인
- **Booming Voice** (`MUT_BOOMING_VOICE`, 나쁜 돌연변이): 적이 보이는 상태에서 스크롤을 읽으면 그 자리에 **크기 40의 소음**이 추가로 난다.
- **Delatra's gloves**: 미감정 스크롤을 읽으면 potion of magic 효과(MP 10~37). → [Delatra's gloves](unrands-armour.md#delatras-gloves)
- **toga "Victory"**: 적대 몬스터가 보이는 상태에서 읽으면 축적 능력치가 초기화된다. → [toga "Victory"](unrands-armour.md#toga-victory)
- **Xom**: 위험한 상황에서 미감정 스크롤을 읽으면 즐거워한다. Xom이 주는 스크롤에는 identify·revelation이 나오지 않는다.
- 몬스터는 0.34.1에서 스크롤을 읽지 않는다.

---

## 6. 생성 (간략)
- **바닥 무작위 생성**: 무작위 아이템 종류 중 스크롤의 가중치는 270 / 1661(약 16.3%). 아이템 레벨 7 미만에서는 완드로 정해진 아이템이 일정 확률로 포션 또는 스크롤로 바뀐다.
  - 수량: 46/48 확률로 1장, 1/48 확률로 2장, 1/48 확률로 3장.
  - 종류별 확률은 [1. 목록](#1-목록)의 생성 가중치. 아이템 레벨(깊이)과 무관하다. [아이템 세트](#11-아이템-세트-item-set)에서 빠진 종류는 나오지 않는다.
  - Dungeon Sprint에서는 teleportation과 noise가 생성되지 않는다.
- 볼트 지정 아이템, 상점, 신의 선물 등 다른 경로는 각 문서에서 다룬다.

> 출처: item-use.cc, item-name.cc, item-prop.cc, item-prop-enum.h, makeitem.cc, items.cc, acquire.cc, spl-transloc.cc, spl-summoning.cc, spl-clouds.cc, spl-selfench.cc, spl-goditem.cc, beam.cc, mon-explode.cc, mon-ench.cc, monster.cc, player.cc, player-reacts.cc, areas.cc, cloud.cc, map-knowledge.cc, actor-los.cc, dat/descript/items.txt (0.34.1)
