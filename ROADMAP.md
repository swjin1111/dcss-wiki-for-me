# 작업 계획

## 1단계: 카테고리별 코드 기반 작성 (진행 중)
README 목차의 각 카테고리를 0.34.1 소스코드 기준으로 작성한다. 이 단계에서는 플레이 팁을 쓰지 않는다.

- [x] 마법 — Alchemy
- [ ] 마법 — 나머지 학파
- [ ] 아이템 (아래 순서)
  1. [x] 공통 시스템: `index.md`(인챈트·감정·생성·아티팩트 개요), `brands-egos.md`, `artefact-properties.md`
  2. [x] 기본 장비: `weapons.md`(투척 포함, 전투 시스템 로직 상세), `armour.md`(AC·EV·SH·방해도 로직 상세)
  3. 언랜드의 기반이 되는 나머지 장비: [x] `jewellery.md`, [x] `staves.md`
  4. 언랜드 아티팩트: [x] `unrands-weapons.md`, [x] `unrands-armour.md`, [x] `unrands-jewellery.md` (기본 수치는 2~3단계 문서로 링크하고, 달라진 점과 고유 효과 위주로 작성)
     - `unrands-weapons.md` 진행: 무기 계열 단위로 나눠 작성. [x] Maces & Flails, [x] Short Blades, [x] Long Blades, [x] Axes, [x] Polearms, [x] Staves, [x] Ranged Weapons — **완료**
       (수치는 `art-data.txt`의 PLUS/BASE_* + `item-prop.cc` Weapon_prop로 계산, 고유 효과는 `art-func.h`와 `UNRAND_*` 검색)
     - `unrands-armour.md`: 51종(부위별: 몸통 18, 방패 5, 오브 5, 망토 6, 머리 7, 손 5, 발 5) **완료**
     - `unrands-jewellery.md`: 16종 **완료**
  5. 소모품·발동형: [x] `potions.md`, [x] `scrolls.md`, [x] `wands-evokers.md`
  6. 나머지: [x] `talismans.md`, [ ] `special-items.md`
- [ ] 종족, 직업, 신, 던전, 몬스터, 네임드, 적성, 능력치, 돌연변이 & 파멸
- [ ] 후순위: 능력, 상태이상, 보조 공격, 은신 & 암습

## 2단계: 교차 분석 업데이트 (주요 카테고리 완성 후)
여러 카테고리가 갖춰진 뒤, 카테고리끼리 엮어서 **전체 페이지를 다시 한 번 업데이트**한다.

- 카테고리 간 데이터를 결합한 분석을 추가한다.
  - 예: 브랜치별 출현 몬스터 × 저항 → "이 마법/브랜드가 어느 던전까지 통하는가"
  - 예: 몬스터 특성 × 마법 효과 → 특정 몬스터에 대한 유효/무효 수단
- 이 분석을 근거로 **플레이 팁** 섹션을 추가한다. 팁마다 근거가 된 데이터를 함께 적는다.
- 1단계에서 쓴 페이지 사이에 상호 링크를 보강한다(마법 ↔ 몬스터 ↔ 던전 ↔ 아이템).

## 보류 중인 항목
아직 반영 여부를 정하지 않은 것들.

- 나무위키 비교에서 찾은 Alchemy 보충 후보 (코드로 확인됨, 미반영)
  - Noxious Bog가 계단 칸도 늪으로 바꿈(지속 중 계단 사용 불가)
  - Sticky Flame에 맞은 대상이 빛남(backlit)
  - Walking Alembic 동시 유지 1마리
  - Leda's Liquefaction은 수중 종족·대형 몬스터에게도 적용
- 게임 실행을 통한 검증 (arena 모드, wizard mode fsim)
- 커뮤니티 자료(공략·경험담)를 출처와 함께 별도 섹션으로 넣을지 여부
- C++ 공부용 코드 해설 (장기 목표)

## 다른 문서를 쓸 때 반영할 발견
코드를 읽다가 찾았지만 아직 해당 문서가 없어서 적어두는 것.

- **Quill form 반격 AC 이중 적용**: `melee-attack.cc` do_spines에서 quill 반격 데미지에 `apply_ac`를 두 번 호출한다(spiny 돌연변이는 한 번). [talismans.md](docs/items/talismans.md#quill-talisman)에 기록. → 2단계 검증 대상
- **Zin과 탈리스만**: Zin 신자가 어떤 탈리스만이든 사용하면 즉시 파문(`god-item.cc` god_despises_item). 선한 신은 sanguine·death 탈리스만도 파문. → 신(Zin, 선한 신) 문서
- **Shapeshifter 직업은 quill talisman 형태로 시작**(`ng-setup.cc`). → 직업 문서
- **변신 상태와 입교**: Zin은 어떤 형태든 변신 중인 플레이어를, 선한 신은 death form을, Okawaru는 hive form을 신자로 받지 않는다(`religion.cc` _transformed_player_can_join_god). → 신 문서
- **Sphinx form의 Willpower 우회**는 Hexes만이 아니라 플레이어가 거는 모든 Willpower 판정에 적용된다(`actor.cc`→`apply_willpower_bypass`). 게임 내 설명은 "Hexes are ... harder to resist". → 2단계 검증 대상
- **완드 주문의 상세는 [wands-evokers.md](docs/items/wands-evokers.md#23-완드-목록)에 있다**: Throw Flame, Paralyse, Charm, Iceblast, Fastroot, Warp Space, Corrosive Bolt, Bolt of Light, Quicksilver Bolt, Polymorph, Mindburst, Dig. 마법 학파 페이지에서 이 주문들이 플레이어 주문으로 있으면 피해 공식은 같으므로 링크로 연결하고, 주문 고유 정보(레벨·책·실패율)만 쓴다. Thunderbolt(lightning rod), Primal Wave(phial), Gell's Gravitas(gravitambourine)도 같음.
- **Inner Flame 상세**(폭발 피해 3d15/3d20/3d25, 피격 시 불 구름)는 [scrolls.md](docs/items/scrolls.md#29-immolation)에 요약. → 마법(Inner Flame) 문서에서 상세화하고 링크
- **아이템 세트와 소거법 자동 감정**: 게임마다 세트당 한 종류만 생성(summoning/butterflies, 완드 3세트, 발동 아이템 3세트)되고, 미감정 종류가 1개만 남으면 자동 감정된다(`items.cc` maybe_identify_base_type). [scrolls.md](docs/items/scrolls.md#11-아이템-세트-item-set)에 정리함. → 2단계에서 아이템 개요(index.md) 감정 절에 링크 추가
- **브랜치별 아이템 사용 금지**: Gehenna에서는 스크롤을 읽을 수 없고, Cocytus에서는 포션을 마실 수 없다. Tartarus에서는 플레이어 Willpower가 항상 절반(`player.cc` player_willpower). Abyss는 revelation 불가(no_map). → 던전 문서
- **`DUR_NO_SCROLLS`는 0.34.1에서 거는 곳이 없다**(정의·표시 코드만 있음). → 상태이상 문서
- **Enlightenment 지속 단위 불일치**: `potion.cc`의 PotionEnlightenment가 `max(비행 지속(aut), Enlightened 지속(aut), 25+random2(pow)(턴 숫자))`로 지속을 정해서, 비행이 불가능한 형태(tree form 등)에서 마시면 Will+ 효과가 2.5~6.4턴만 유지된다(0.34.1). Efficient Metabolism 2배도 사실상 무효. → 상태이상 문서 ([potions.md](docs/items/potions.md#34-enlightenment))
- **Ru의 Sacrifice Drink/Words 조건 차이**: 포션은 HP가 최대의 1/2 **미만**, 스크롤은 1/2 **이하**일 때 적이 있어도 사용 가능(`player-reacts.cc` `_handle_hoarding`). 적이 사라진 뒤 6턴 동안 계속 금지. → 신(Ru) 문서
- **Berserk 상세**(사용 제한 목록, 종료 후 Slow/재광폭화 불가 기간 공식)는 [potions.md](docs/items/potions.md#311-berserk-rage)에 요약. → 상태이상 문서에서 상세화
- **은신·소음 관련 방어구 언랜드**: cloak of the Thief(보이는 칸의 소음 절반, Dithmenos 권능과 중첩), robe of Night(시야 ×3/4), crown of vainglory(반경 0 후광 → backlit, Stealth ×2/5), Charlatan's Orb(Stealth ÷3), hood of the Assassin(모든 근접 무기·맨손에 좋은 암습, 감지 반경 4). → 은신 & 암습 문서 ([unrands-armour.md](docs/items/unrands-armour.md)로 링크)
- **장비 슬롯 예외**: fungal fisticloak의 추가 장갑 슬롯은 종족 제한 검사 전에 더해져서 Large·Little 종족도 장갑 1개를 낄 수 있다(코드상, 미확인). Lear's hauberk는 몸통·머리·손·발 슬롯이 모두 있어야 입을 수 있다. → 종족 문서(장비 제한 정리 시)
- **Coglin의 Warmup Strikes**(`MUT_WARMUP_STRIKES`): 회전 수치가 낮을 때의 데미지 감소(0일 때 2/3)가 **원거리 공격에만 적용되고 근접 공격에는 적용되지 않는다.** `melee-attack.cc`의 `player_apply_final_multipliers`에서 `apply_rev_penalty(damage);`의 반환값을 버리기 때문(0.34.1). → 종족 문서
- **Sticky Flame 종료 판정 버그**: `player.cc`의 `dec_sticky_flame_player`에서 `you.duration[DUR_STICKY_FLAME == 0]`로 잘못 쓰여 있어, 실제로는 `you.duration[0]`(= `DUR_INVIS`, 투명 상태)를 검사한다. 그 결과 (1) 지속 시간이 자연히 끝날 때는 종료 메시지와 정리(`end_sticky_flame_player`)가 실행되지 않고, (2) **플레이어가 투명 상태이면 Sticky Flame이 다음 틱에 바로 꺼진다**(0.34.1). → 상태이상 문서, Alchemy의 Sticky Flame 항목(2단계)
- **주문 볼트에 대한 플레이어의 막기 공식**은 근접·투사체 공격과 다르다: `beam.cc`에서 `random2(명중 × 1.3) < shield_bonus()`로 판정(몬스터 HD가 아니라 볼트의 명중치 사용). 방어구 문서 5.2절은 근접·투사체 기준. → 상태이상 또는 2단계에서 방어구 문서 보충 검토
- **무작위 아이템 종류 가중치 합**: `makeitem.cc` 주석은 "Total weight: 1660"이지만 실제 합은 1661(사소함). → 아이템 개요 보충 시
- **staff of necromancy 설명문 불일치**: 설명문(`dat/descript/items.txt`)은 근접 추가 데미지가 "방어구를 무시한다"고 하지만 `Staff_prop`은 `ac_type::normal`이라 AC가 그대로 적용된다(0.34.1). → 2단계(마법 Necromancy 학파 페이지에서 지팡이 언급 시 링크)
- **은신 보정(언랜드)**: morningstar "Eos" 사용자는 자기 후광 때문에 backlit 상태가 되어 Stealth ×2/5, eveningstar "Brilliance"/ring of Shadows의 Umbra 안에서는 Stealth ×1.5(`player.cc` stealth 계산). Spriggan's Knife는 암습 가능한 대상을 1/2 확률로 잠든 대상처럼 취급. → 은신 & 암습 문서 (언랜드 문서로 링크)
- **Death Curse 가중치 버그**: `death-curse.cc`의 주석은 세기 15 초과 시 "메시지" 가중치를 0으로 유지한다고 하지만 코드는 음수가 되도록 둔다. 음수 가중치가 목록 맨 앞이라 Smite(그다음 Doom)의 몫이 깎인다(세기 21 이상이면 Smite 0%). 세기는 scythe of Curses = 공격 데미지(최대 27), **미라 = HD(guardian mummy 7, mummy priest 10, greater mummy 15, Khufu 18)**, Kiku 징벌 = XL. → 몬스터(미라)·네임드(Khufu)·신(Kikubaaqudgha) 문서. 세기별 확률표는 [unrands-weapons.md](docs/items/unrands-weapons.md#scythe-of-curses)
- **Polearms reach 막힘 판정**: 사이에 몬스터가 있으면 50% 확률로 막히고, 막히면 그 몬스터가 적대적일 때 그 몬스터를 공격한다(`quiver.cc`). 무기 문서 5절은 "사이에 막는 것이 없어야 한다"로만 적혀 있음. 지형은 두 중간 칸이 모두 막혀 있을 때만 불가. → 2단계에서 무기 문서 보충
- **Majin-Bo + Death 에고 HP 환불 중복**: `spl-cast.cc`에서 주문이 비용 지불 후 취소되면 `_majin_charge_hp()`와 `_death_ego_charge_hp()` 각각에 대해 합산된 `hp_cost`를 `refund_hp`로 돌려준다. 둘 다 해당하면 2배 환불, `refund_hp`는 최대 HP 상한 검사가 없음(재현 미확인). → 방어구 에고(Death) 보충 시, 마법 공통 시스템 문서

