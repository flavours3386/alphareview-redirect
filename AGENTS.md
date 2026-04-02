# alphareview-redirect - 인앱 브라우저 리다이렉트 - Agent Guide

> 이 파일은 목차다. 상세 내용은 각 링크를 따라가라.

## Quick Start

1. `index.html` 단일 파일로 구성
2. GitHub Pages로 배포: https://flavours3386.github.io/alphareview-redirect/
3. 사용법: `?t=<대상URL>` 쿼리 파라미터로 리다이렉트 대상 지정
4. 예시: `https://flavours3386.github.io/alphareview-redirect/?t=https://tally.so/r/rjlOP2`

## Golden Principles

1. **단일 파일 유지**: index.html 하나에 HTML/CSS/JS 모두 포함. 빌드 도구 사용 금지
2. **인앱 브라우저 우선 감지**: 카카오톡, 네이버, LINE, Instagram 등 주요 인앱 브라우저 커버
3. **즉시 리다이렉트**: 일반 브라우저는 1초 이내 자동 리다이렉트, 인앱은 외부 브라우저 전환 시도
4. **폴백 필수**: 외부 브라우저 전환 실패 시 수동 버튼 표시
5. **이미지 에셋 동시 관리**: promo_comparison.png도 이 레포에서 호스팅

## Key Files

```
alphareview-redirect/
├── CLAUDE.md                # 프로젝트 문서
├── AGENTS.md                # 이 파일
├── ARCHITECTURE.md          # 시스템 아키텍처
├── index.html               # 리다이렉트 페이지 (단일 파일)
├── promo_comparison.png     # 프로모션 비교표 이미지 (Tally 폼에서 참조)
├── docs/
│   ├── PRODUCT_SENSE.md     # 제품 방향
│   ├── PLANS.md             # 우선순위/로드맵
│   ├── design-docs/         # 설계 문서
│   └── exec-plans/          # 실행 계획
```

## Docs Map

| 문서 | 용도 | 변경 빈도 |
|------|------|-----------|
| CLAUDE.md | 프로젝트 개요, 배포 정보 | 기능 변경 시 |
| AGENTS.md | 문서 목차 및 핵심 원칙 | 구조 변경 시 |
| ARCHITECTURE.md | 인앱 감지 로직, 분기 처리 | 로직 변경 시 |
| docs/PRODUCT_SENSE.md | 제품 방향 | 분기별 |
| docs/PLANS.md | 우선순위 | 기능 추가 시 |
