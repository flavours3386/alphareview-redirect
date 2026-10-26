# alphareview-redirect

## 프로젝트 개요
카카오톡, 네이버, LINE 등 인앱 브라우저 환경에서 Tally 프로모션 신청 폼이 정상 동작하지 않는 문제를 해결하기 위해, 외부 브라우저로 자동 전환하거나 폴백 UI를 제공하는 단일 HTML 리다이렉트 페이지.

## 기술 스택
- 정적 HTML (순수 JavaScript, CSS)
- 인앱 브라우저 감지: User-Agent 파싱
- 외부 브라우저 전환: 카카오톡 커스텀 스킴, Android Intent URL

## 주요 명령어
해당 없음 (정적 HTML 파일로, 별도 빌드 없이 GitHub Pages 등 정적 호스팅에 배포)

## 폴더 구조
```
alphareview-redirect/
├── index.html          # 리다이렉트 로직 포함 메인 페이지 (인앱 브라우저 감지 및 외부 브라우저 전환)
└── promo_comparison.png # 프로모션 혜택 비교표 이미지
```

## 사용 방법
쿼리스트링 `t` 파라미터에 URL 인코딩된 이동 대상 URL을 전달한다.
```
https://{배포도메인}/?t={URL_ENCODED_TALLY_LINK}
```

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
├── AGENTS.md                # 프로젝트 문서 (CLAUDE.md는 이 파일의 심볼릭 링크)
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
| AGENTS.md | 프로젝트 개요, 배포 정보, 핵심 원칙 | 기능·구조 변경 시 |
| ARCHITECTURE.md | 인앱 감지 로직, 분기 처리 | 로직 변경 시 |
| docs/PRODUCT_SENSE.md | 제품 방향 | 분기별 |
| docs/PLANS.md | 우선순위 | 기능 추가 시 |
