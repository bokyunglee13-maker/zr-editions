# ZR Editions — ㅈㄹ막걸리 × POLYC

ㅈㄹ막걸리의 팝업/콜라보 행사를 **에디션(VOL.)** 단위로 누적하는 사이트.
두타몰 사이트(`../zr_makgeolli`)와 **별도 레포 / 별도 배포**다.

- 🔗 라이브: https://zr-editions.vercel.app
- 📦 GitHub: `bokyunglee13-maker/zr-editions`
- 📄 상세: [PRD.md](PRD.md) · [DESIGN.md](DESIGN.md)

## 폴더 관계 (중요)
```
claude_projects\
├── zr_makgeolli\   ← 두타몰 사이트(원본). github zr_makgeolli → zr-makgeolli.vercel.app  ※ 건드리지 말 것
└── zr-editions\    ← 이 프로젝트. github zr-editions → zr-editions.vercel.app
```
에디션 사이트 수정·배포는 **무조건 `zr-editions` 폴더에서**.

## 현재 — Phase 1 (VOL.02 POLYC 《비단일 非單一 Not Single》)
- `index.html` 단일 파일. 다국어 ko·en·ja·zh, 언어토글.
- 섹션: HERO(GLOBAL ARTIST POLYC EDITION) → ABOUT → MEANING(키네틱) → EXHIBITION → ARTIST → EDITIONS(학호도·서울의 조각들) → TASTE → NAME(초성 생성기) → MATCH(궁합, ko 전용) → VISIT → FOOTER(카카오채널).
- 전시: 2026.06.20–06.28 · 플라츠2(PLATZ 2) · 서울 성동구 뚝섬로17길 35 · 11:00–20:00.
- 행사 사실값은 `index.html` 상단 `EXHIBIT` 블록, 카피/번역은 `I18N` 사전.

## 기능
- **이름 초성 생성기**: `window.toChosung`(`/assets/chosung.js`) → 스토리 카드(호랑이/학 이름별 랜덤). 저장/공유(Web Share).
- **이름 궁합**: 한글 획수 알고리즘 → 스토리 카드(동물 일러스트). 한국어 전용.
- **공유**: 결과 생성 시 이미지 미리 굽기(`nameFile`/`matchFile`) → 공유 클릭 시 `navigator.share` 동기 호출(모바일 카톡·인스타 시트). 데스크톱은 저장 폴백.
- **로깅**: 두타몰과 동일 Apps Script `namegen` 시트(`EXHIBIT.webappUrl`), `page=polyc/match`로 구분 + Vercel Analytics.

## 이미지 자산 (`/assets/`)
`kv.png`(히어로) · `poster.png`(포스터) · `ed-hakhodo.png`/`tiger.png`(학호도) · `ed-seoul.png`(서울의 조각들) · `crane.png`(학) · `chosung.js`.

## 로컬 미리보기
상위 `../zr_makgeolli/.claude/serve-editions.cjs` (port 5520, root=../zr-editions) 정적 서빙.

## 배포
- `git push origin main` (소스 백업) → `vercel --prod` (라이브). **자동배포 연결 안 함** — 수정 후 명시적으로 배포.

## 미확정 / TODO
PRD.md §6 참고: 작가 협업 문구 확정, 포스터 주소 표기, 노리개 자산, OG 도메인.

## Phase 2 (예정)
홈을 RECENT EDITIONS 아카이브로. `edition{vol,title,venue,...,slug}` → `/editions/[slug]`. VOL.01 두타몰 → VOL.02 POLYC … 누적.
