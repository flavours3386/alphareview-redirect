# alphareview-redirect - 인앱 브라우저 리다이렉트

> 문서 목차 및 핵심 원칙: [AGENTS.md](AGENTS.md)

## 프로젝트 개요

카카오톡/네이버 등 인앱 브라우저에서 Tally 프로모션 폼이 정상 동작하지 않는 문제를 해결하기 위한 리다이렉트 페이지. GitHub Pages로 정적 호스팅.

## 기술 스택

- HTML/CSS/JS (단일 파일, 빌드 도구 없음)
- GitHub Pages (정적 호스팅)

## 배포 정보

- URL: https://flavours3386.github.io/alphareview-redirect/
- 레포: https://github.com/flavours3386/alphareview-redirect (public)
- 배포: `git push origin main` → GitHub Pages 자동 배포

## 사용법

```
https://flavours3386.github.io/alphareview-redirect/?t=<대상URL>
```

예시:
- VIP 폼: `?t=https://tally.so/r/rjlOP2`
- 통합 폼: `?t=https://tally.so/r/4427rA`

## 폴더 구조

```
alphareview-redirect/
├── CLAUDE.md                # 이 파일
├── AGENTS.md                # 문서 목차 및 핵심 원칙
├── ARCHITECTURE.md          # 인앱 감지 로직
├── index.html               # 리다이렉트 페이지 (단일 파일)
├── promo_comparison.png     # 프로모션 비교표 이미지
└── docs/
    ├── PRODUCT_SENSE.md     # 제품 방향
    ├── PLANS.md             # 우선순위/로드맵
    ├── design-docs/         # 설계 문서
    └── exec-plans/          # 실행 계획
```

## 최근 변경사항

### 2026-03-30: 독립 레포 구성
- IMWEB 프로젝트에서 redirect.html + promo_comparison.png 분리
- GitHub Pages 배포 설정
