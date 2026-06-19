# ZR Editions — ㅈㄹ막걸리 팝업 아카이브

ㅈㄹ막걸리의 팝업/콜라보 행사를 **에디션(VOL.)** 단위로 누적하는 사이트.
두타몰 사이트(`zr-makgeolli`)와 **별도 레포 / 별도 배포**로 운영한다.

## 톤
- **Pastel Lilac** 디자인 시스템 — POLYC 콜라보 막걸리 라벨에서 추출한 파스텔 보라.
- 두타몰의 "Kinetic Pink"(브루탈/핑크)와 의도적으로 분리. 갤러리·에디토리얼 무드.
- 컬러 토큰: `--lav-bg #F3EEFB` · `--wisteria #B9A7E6` · `--violet #7A5CD0` · `--peri #5C7CDA` · `--cobalt #2E3192` · 포인트 `--magenta/#pink/#teal/#marigold`.

## 현재 단계 — Phase 1
- `index.html` — **VOL.02 POLYC 성수 개인전 콜라보** 랜딩 1장.
  - HERO / 전시 정보 / 콜라보 스토리 / 라벨 갤러리 / 현장 체험 / **이름 초성 생성기**(보라 리스킨) / 방문 / 푸터.
  - 두타몰의 초성 생성기(`/assets/chosung.js`, `window.toChosung`)를 보라 카드(1080×1920 Canvas)로 재사용.
- 행사 정보는 `index.html` 상단 **`EXHIBIT` CONFIG 블록**에서만 수정 (TODO 항목 = 실제 정보로 교체 필요).

### 채워야 할 TODO (행사 확정 정보)
- `EXHIBIT.title` — 개인전 제목
- `EXHIBIT.artist` — 작가 이름
- `EXHIBIT.address` — POLYC 성수 정확한 주소
- `EXHIBIT.hours` — 운영시간 확인
- 포스터/라벨 추가 컷 이미지 (`/assets/`) — 현재 `label.jpg`로 임시 대체

## 다음 단계 — Phase 2 (아카이브 홈)
- 홈(`/`)을 **RECENT EDITIONS** 아카이브로 전환 (레퍼런스: WOOMUL 스타일 VOL 카드).
- 데이터 모델: `edition { vol, title, venue, dateStart, dateEnd, partner, posterImg, accentColor, slug }`.
- 각 행사 = `/editions/[slug]`. VOL.01 두타몰 → VOL.02 POLYC … 누적.
- "다음 에디션 알림 신청" CTA (현재 푸터에 자리만 잡아둠).
- 이름 궁합(`match`)·인스타 공유 카드 추가 리스킨도 이 단계에서.

## 로컬 미리보기
상위 `zr_makgeolli/.claude/serve-editions.cjs` (port 5520)로 정적 서빙.

## 배포
- Vercel 새 프로젝트로 이 폴더 연결. `vercel.json`에 `/polyc`, `/name` rewrite.
- OG 메타의 도메인(`zr-editions.vercel.app`)은 실제 배포 도메인으로 교체.
