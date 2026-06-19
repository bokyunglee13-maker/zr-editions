# PRD — ㅈㄹ막걸리 × POLYC 에디션 사이트 (zr-editions)

> 두타몰 사이트(`zr_makgeolli`)와 **별도 레포 / 별도 Vercel 배포**. 팝업·콜라보를 에디션(VOL.) 단위로 누적하는 사이트의 첫 에디션.

## 1. 개요
- **무엇**: POLYC 개인전 《비단일 非單一 · Not Single》 × ㅈㄹ막걸리 콜라보 한정 에디션 소개 원페이지 (다국어 ko·en·ja·zh).
- **누구**: 전시 방문객(내·외국인).
- **톤**: Pastel Lilac (파스텔 보라). 갤러리·에디토리얼 무드. (`DESIGN.md`)
- **기간/장소**: 2026.06.20 – 06.28 · 플라츠2(PLATZ 2) · 서울 성동구 뚝섬로17길 35 · 11:00–20:00.
- **슬로건**: `DRINK HAPPY, NOT HEAVY`
- **배포**: https://zr-editions.vercel.app · GitHub `bokyunglee13-maker/zr-editions`

## 2. 라우트 (Vercel)
| 페이지 | 파일 | 라우트 |
|---|---|---|
| 랜딩 | `index.html` | `/`, `/polyc` |

- 언어: `?lang=ko/en/ja/zh` > localStorage > 기본 ko. (URL 경로 라우트는 미사용)

## 3. 섹션 구조 (스크롤 순)
1. **네비** — 로고 · ABOUT/MEANING/EDITIONS/NAME/MATCH/VISIT · 언어토글(국기 4) · **스마트 숨김**(아래로 숨김/위로·상단 등장)
2. **HERO** — `비단일 非單一` / NOT SINGLE / **GLOBAL ARTIST POLYC EDITION** + 아트에디션 소개 + 기부 문구(작게) + 키비주얼(`kv.png`, 학+호)
3. **ABOUT** — ㅈㄹ막걸리 브랜드 소개
4. **MEANING** — `ㅈㄹ, 무슨 뜻일까요?` 키네틱 워드(ko: ㅈㄹ + 의미 단어 10 / en·ja·zh: WTF + 확장어구). 비단일 컨셉과 연결
5. **EXHIBITION** — 전시 정보 카드(포스터 `poster.png`)
6. **ARTIST** — POLYC 글로벌 아티스트 + 협업 칩(BTS·권은비·타투이스트·글로벌 협업·전통 재해석·끊임없는 변화)
7. **EDITIONS** — 학호도(鶴虎圖, Tiger and Crane through Cubism) · 서울의 조각들(Pieces of Seoul)
8. **TASTE** — 맛 설명 + 스펙칩(당일도정 춘천쌀 100%·첨가물 0%·50일 저온숙성·잘 익은 참외·생크림 질감)
9. **NAME** — 이름 초성 생성기 → 스토리 카드
10. **MATCH** — 이름 궁합(한글 획수) → 스토리 카드 **(한국어 전용; en/ja/zh 숨김)**
11. **VISIT** — 장소·기간·시간·네이버 지도(주소 검색)
12. **FOOTER** — 다음 에디션 알림(**카카오채널** `pf.kakao.com/_sxnQXX`) + 인스타

## 4. 핵심 기능
### 4-1. 이름 초성 생성기
- 입력 이름 → 한글 초성(`/assets/chosung.js`, `window.toChosung(name, lang)`; 두타몰과 동일 엔진).
- 결과 → **스토리 카드(1080×1920 Canvas)**: 상단 브랜드 + @핸들·날짜 / 가운데 이름·초성·슬로건·일러스트. 일러스트는 **이름별 호랑이/학 랜덤**(deterministic), 한글 이름 Paperlogy.
- 저장(다운로드) / **공유(Web Share)** — 결과 생성 시 이미지를 미리 구워(`nameFile`) 공유 클릭 시 `navigator.share` 동기 호출 → 모바일 카톡·인스타 공유시트.

### 4-2. 이름 궁합 (한국어 전용)
- 두 한글 이름 → 한글 획수 궁합(초/중/종성 자소 획수 합 → 교차 인접합 mod 10 반복 → 2자리 점수). 양방향(`getScore(A,B)`/`(B,A)`) 평균.
- 키치 연출(획수 카운트업·게이지·점수대 이모지/멘트 6단계). 스토리 카드 + 호랑이/학 일러스트.
- **랜덤 버튼 없음**(제거됨). 획수 궁합은 한글 전용 → ko UI에서만 노출.

## 5. 데이터/분석
- **구글시트 로깅**: 두타몰과 동일한 Apps Script 엔드포인트(`EXHIBIT.webappUrl`)의 `namegen` 시트에 적재. event=`generate/save/share`(이름) · `match_generate/save/share`(궁합). `page=polyc`(이름)·`match`(궁합)로 두타 데이터와 구분.
- **Vercel Web Analytics**: 커스텀 이벤트 `name_*` / `match_*`.

## 6. 미확정 / TODO
- [ ] **작가 협업 문구**: BTS·타투이스트 권은비 구체 표현은 사실 확인 전 일반 표현 → 확정 시 `#artist` 교체.
- [ ] **포스터 주소 표기**: 포스터 이미지에 "연무장길 126"이 보이나 본문은 확정 주소 "뚝섬로17길 35". 포스터 원본 정정 필요 시 새 이미지 교체.
- [ ] **노리개 자산**: 궁합/이름 카드에 노리개(매듭) 누끼 PNG 추가 요청 → 자산 확보 시 반영.
- [ ] **OG 도메인**: 실제 배포 도메인 확정(현재 `zr-editions.vercel.app` 하드코딩).

## 7. Phase 2 (예정)
- 홈(`/`)을 **RECENT EDITIONS** 아카이브로 전환. 데이터 모델 `edition{vol,title,venue,dateStart,dateEnd,partner,posterImg,accentColor,slug}`, 각 행사 `/editions/[slug]`. VOL.01 두타몰 → VOL.02 POLYC … 누적. "다음 에디션 알림" 카카오채널 연동.
