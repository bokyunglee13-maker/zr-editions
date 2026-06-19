# DESIGN.md — "Pastel Lilac" 디자인 시스템 (zr-editions)

POLYC 콜라보 막걸리 라벨에서 추출한 **파스텔 보라** 시스템. 두타몰의 "Kinetic Pink"(브루탈/핑크)와 의도적으로 분리 — 갤러리·에디토리얼 무드.

## 1. 컬러 토큰 (`:root`)
| 토큰 | 값 | 용도 |
|---|---|---|
| `--lav-bg` | `#F3EEFB` | 페이지 배경 |
| `--lilac` | `#E4DAF6` | 카드/섹션 면 |
| `--wisteria` | `#B9A7E6` | 히어로 면, 카드 그라데이션 |
| `--violet` | `#7A5CD0` | 메인 포인트/버튼 |
| `--peri` | `#5C7CDA` | CTA(이미지2 톤) |
| `--cobalt` | `#2E3192` | 딥 섹션 배경, 텍스트 강조 |
| `--magenta` | `#D46AAE` | 라벨 포인트(×, 점수) |
| `--pink`/`--teal`/`--marigold` | `#EBB3D4`/`#2FA7A0`/`#F2C24A` | 소량 포인트(라벨에서) |
| `--ink` | `#2A2350` | 본문 텍스트(소프트 플럼) |

- 선택 영역: `::selection{ background:var(--violet); color:#fff; }`
- 딥 섹션(MEANING/ARTIST): 코발트 배경 + 보라/흰 포인트.

## 2. 타이포그래피
| 토큰 | 폰트 | 용도 |
|---|---|---|
| `--display` | `'Archivo','Paperlogy'` | 라틴 디스플레이(900) |
| `--mono` | `'Space Mono','Paperlogy'` | eyebrow/라벨/메타(대문자) |
| `--body` | `'Inter','Paperlogy'` | 본문·폼 |
| `.kr-head` | `'Paperlogy' 900` | 한글 헤드라인 |

- 한글 = Paperlogy(jsDelivr, 400/500/700/900). Archivo Black 미사용(부드러운 Archivo로 교체).
- ⚠️ Space Mono는 한글 글리프 없음 → 한글이 들어가는 캔버스 텍스트(이름·"비단일" 등)는 **Paperlogy**로 렌더.

## 3. 핵심 컴포넌트
- **버튼** `.btn`: pill, `--violet`(보라필)/`--peri`(페리필)/`--ghost`(보라 보더). hover `translateY(-2px)`.
- **네비**: 고정 + blur, **스마트 숨김**(`.nav-hidden{ translateY(-105%) }`, 아래로 숨김/위로·상단 등장). 모바일은 가운데 메뉴 숨김, 언어토글 유지.
- **언어토글** `.lang`: 국기 4(flagcdn kr/us/jp/cn), 활성 = 보라 링.
- **키네틱 워드** `.mstage`: 코발트 면 위 대형 글자(`.kw-big`, ko ㅈㄹ / 그외 WTF) + 떠다니는 의미 단어(`.kw`, float 애니메이션, `KIN_SLOTS` 좌표).
- **에디션 카드** `.ed`: 흰 카드 + 라일락 이미지면(`object-fit` 미고정 → 병 **전체 노출**), 한글명 + 한자 + 영문 부제 + 설명 + 스펙칩.
- **궁합 결과**: 획수 칩(보라 보더)·태그 pill·게이지(`linear-gradient(wisteria→magenta)`)·대형 점수(마젠타)·양방향.
- **스토리 카드**(1080×1920 Canvas): 파스텔 보라 그라데이션 배경. 이름 카드 = 상단 브랜드/@핸들·날짜 + 가운데 이름·초성·슬로건·**호랑이/학 일러스트**(이름별 랜덤). 궁합 카드 = A♥B·점수%·게이지·양방향 + 동물 일러스트. 한글은 Paperlogy.

## 4. 폰트 사용 원칙
- 큰 제목·한글 헤드 = Paperlogy 900 / 라틴 디스플레이 = Archivo 900.
- eyebrow/짧은 메타 = Space Mono(대문자).
- 본문·폼·설명 = Inter/Paperlogy.

## 5. 금지/주의
- 그라데이션은 히어로 면·스토리 카드 배경·게이지에만(브랜드 톤 유지). 드롭섀도우는 카드 깊이용만.
- 한글 캔버스 텍스트에 Space Mono 금지(글리프 없음) → Paperlogy.
- 둥근 모서리: pill 버튼·태그·카드·칩.

## 6. 반응형
- 모바일: 네비 가운데 메뉴 숨김(언어토글 유지), 에디션/방문 1열, 클램프 폰트.
- 폭 기준: `.wrap max-width:1080px`, 폰트 `clamp()`.
