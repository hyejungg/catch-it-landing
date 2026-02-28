# CatchIt Landing Page 작업 계획

## 1) 목표
- `catch-it` 확장 프로그램의 핵심 가치를 소개하는 랜딩 페이지를 만든다.
- 기본 진입 페이지는 `docs/mockup.html`의 메인 톤/핵심 메시지를 반영한다.
- 메인 페이지에서 확장 프로그램 설치 페이지로 자연스럽게 이동하는 CTA 버튼을 제공한다.

## 2) 참고 문서 (source of truth)
- `catch-it/README.md`
- `catch-it/docs/mockup.html`
- `catch-it/docs/plan.md`
- `catch-it/docs/qa/1-mvp-qa-checklist.md`
- `catch-it/docs/progress/1-mvp-implementation-order.md`

## 3) 랜딩 범위 정의
- 포함:
  - 메인 랜딩 페이지 1개 (목업 기반)
  - 확장 설치 안내 페이지 1개
  - 메인 -> 설치 페이지 CTA 동선
- 제외:
  - 확장 기능 자체 구현(content-script/background/dashboard/settings)
  - Notion 연동 로직 구현

## 4) 페이지 구조

### 4.1 메인 페이지 (`/`)
- Hero 섹션:
  - 제품 한 줄 정의: 드래그 기반 텍스트 수집 + Notion 동기화
  - 주요 CTA: `확장 프로그램 설치하기` (설치 페이지 이동)
  - 보조 CTA: `기능 살펴보기` (페이지 내 기능 섹션 스크롤)
- 핵심 기능 섹션:
  - 드래그 저장
  - Dashboard 검색/관리
  - Notion Push Sync
- 사용 흐름 섹션:
  - `드래그 -> 저장 -> Dashboard 확인 -> Notion 동기화`
- 신뢰/안내 섹션:
  - 로컬 저장 기반, Notion 연동은 옵션임을 명시

### 4.2 설치 페이지 (`/install` 또는 `/extension-install`)
- 설치 CTA 섹션:
  - Chrome Web Store 링크 버튼 (배포 전이면 임시 문구/비활성 처리)
- 수동 설치 가이드 섹션 (`README.md` 기준):
  - `npm run build`
  - `chrome://extensions` -> 개발자 모드 ON
  - `dist` 폴더 로드
- 설치 후 확인 섹션:
  - 텍스트 드래그 -> 저장 -> Dashboard 확인
- Notion 연동 시작 섹션(요약):
  - Token / Database ID 설정 위치와 개념 안내

## 5) 상세 작업 항목

### 5.1 콘텐츠/카피 정리
- README 기반으로 랜딩 카피 초안 작성
- 한국어 우선 카피 기준 확정
- 용어 통일: `sync`, `ready`, `failed`, `Auto Sync`, `Sync Now`

### 5.2 UI 구현
- 목업 스타일을 랜딩 섹션형 레이아웃으로 변환
- 반응형 대응(모바일/태블릿/데스크톱)
- CTA 버튼 시각적 우선순위 부여(메인 버튼 1순위)

### 5.3 라우팅/동선
- 메인 페이지에서 설치 페이지로 이동하는 CTA 연결
- 헤더/푸터에도 설치 페이지 진입 경로 1개 이상 추가
- 설치 페이지에서 다시 메인 또는 기능 섹션으로 돌아오는 링크 제공

### 5.4 설치 안내 정확성 검수
- 설치 절차가 README와 일치하는지 검수
- 배포 채널 상태(스토어 링크 유무)에 따라 문구 분기

### 5.5 기본 품질 점검
- 브라우저 기본 동작 확인 (최신 Chrome)
- 주요 섹션 가독성/오탈자 점검
- CTA 클릭 경로 및 깨진 링크 점검

## 6) 완료 기준 (Definition of Done)
- 메인 페이지가 목업 기반 메시지/비주얼 톤을 반영한다.
- 메인 페이지에 설치 페이지 이동 CTA가 명확히 존재한다.
- 설치 페이지에서 설치 방법(스토어 또는 수동 설치)이 이해 가능하게 제공된다.
- README 기반 핵심 기능/설치 안내와 충돌되는 문구가 없다.

## 7) 후속 작업 (권장)
- 실제 Chrome Web Store 배포 후 설치 버튼을 실 링크로 교체
- 간단한 사용 영상/GIF 추가
- FAQ 섹션에 Notion 연동 트러블슈팅 추가
