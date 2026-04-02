# alphareview-redirect - Plans

> 최종 업데이트: 2026-04-02

## 현재 우선순위

1. **기본 기능 유지** (완료) - 카카오톡/Android/iOS 인앱 브라우저 감지 및 외부 전환
2. **GA4 이벤트 추적** (P1) - 리다이렉트 성공/실패/폴백 이벤트 수집
3. **promo_comparison.png 최신화** (필요 시) - 프로모션 조건 변경 시 이미지 재생성

## 로드맵

### Phase 1: 기본 기능 (완료)

- 카카오톡: `kakaotalk://web/openExternal` 스킴
- Android: `intent://` 스킴 (Chrome 직접 호출)
- iOS/기타: 폴백 버튼 UI
- GitHub Pages 배포

### Phase 2: 분석/추적

- GA4 이벤트 (page_view, redirect_success, redirect_fallback)
- UTM 파라미터 전달 (CRM 채널별 성과 분석)

## 기술적 의사결정

### 왜 GitHub Pages인가?

정적 HTML 1파일이므로 서버가 필요 없다. GitHub Pages는 무료, HTTPS 자동 지원, 배포가 git push만으로 완료된다.

### 왜 단일 HTML 파일인가?

외부 의존성이 없으면 CDN 장애, 버전 충돌 위험이 제로다. 인라인 CSS/JS로 HTTP 요청도 1회로 최소화.

## 기술 부채

| 항목 | 심각도 | 설명 | 해결 방안 |
|------|--------|------|-----------|
| UA 패턴 하드코딩 | 하 | 신규 인앱 브라우저 추가 시 코드 수정 필요 | UA 패턴을 배열로 분리 |
| 분석 부재 | 중 | 리다이렉트 성공률 측정 불가 | GA4 이벤트 추가 |
