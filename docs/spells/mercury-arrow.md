# Mercury Arrow

> 기준: DCSS 0.34.1 · [Alchemy](alchemy.md) · [마법 목록](index.md)

| 항목 | 값 |
|---|---|
| 레벨 / MP | 2 / 2 |
| 학파 | Alchemy / Conjuration |
| Power cap | 50 |
| 사거리 | 4 |
| 수록 마법서 | Young Poisoner's Handbook, My Sojourn Through Swamps |

수은 화살을 날려 **Poison 데미지**를 주고, 맞은 적과 그 주변 적을 **Weak** 상태로 만들 수 있는 초반 공격 마법.

## 데미지
- **2개의 주사위, 최대 합계 `11 + Spell power/4`**
  - Spell power 0: 약 2d5
  - Spell power 50 (cap): 약 2d11 (평균 약 12)
- **명중**: 자동 명중이 아니다. 명중 수치는 `12 + Spell power/5` (cap에서 22). EV가 높은 적에게는 빗나갈 수 있다.

## rPois와의 관계
데미지의 **70%만 rPois로 줄어들고, 30%는 무조건 들어간다.**

| 대상 | 받는 데미지 (대략) |
|---|---|
| rPois 없음 | 100% |
| 몬스터, rPois 1단계 | 약 53% |
| 몬스터, Poison 면역 (rPois 3단계) | 30% |
| rPois− (취약) | 약 135% |

그래서 Poison 면역 몬스터에게도 조금은 데미지가 들어간다.

## Weak 효과
명중하면 대상에게 Weak를 걸 확률이 있다. **rPois와 무관하다.**

- **확률 = `100 − 12 × (대상 HD − 4)`%** (HD 4 이하는 100%)

| 대상 HD | ≤4 | 6 | 8 | 10 | 12 | 13+ |
|---|---|---|---|---|---|---|
| Weak 확률 | 100% | 76% | 52% | 28% | 4% | 0% |

- **Spell power와 무관하다.** Spell power를 올려도 확률은 그대로이고, HD만 본다.
- **Weak 효과**: 몬스터의 **melee 데미지가 2/3로 감소**한다. melee 공격이 없는 몬스터에게는 걸리지 않는다.
- **지속시간**: 약 5~12턴.
- 조준할 때 몬스터 정보에 `chance to weaken: N%`로 확률이 표시된다.

### Splash
맞은 대상의 **인접 8칸에 있는 다른 캐릭터들도 각자 Weak 판정**을 받는다(데미지는 없음).
- 시전자 본인은 제외된다.
- **아군도 Splash에 포함될 수 있다.** 아군 근처로 쏠 때는 주의.

## 플레이 팁
- 초반(D1~D4)의 melee형 적 대부분(HD 4 이하)에게 **Weak가 확정**으로 걸린다. 무리 지어 오는 적 사이에 쏘면 여러 마리를 한 번에 약화시킬 수 있다.
- 중반 이후 HD가 높은 적에게는 Weak가 거의 안 걸려서, 사실상 Poison 데미지 마법이 된다.
- 근접 캐릭터가 섞어 쓰는 견제기로도 쓸 만하다. 레벨 2라 실패율 부담이 적다.

> 출처: spl-data.h, zap-data.h, beam.cc, fight.cc, spl-damage.cc, monster.cc, melee-attack.cc (0.34.1)
