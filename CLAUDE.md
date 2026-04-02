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
