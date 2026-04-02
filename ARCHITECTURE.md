# alphareview-redirect - Architecture

## 시스템 개요

인앱 브라우저(카카오톡, 네이버 등)에서 Tally 프로모션 폼이 정상 동작하지 않는 문제를 해결하기 위한 리다이렉트 페이지. GitHub Pages로 정적 호스팅.

## 데이터 흐름

```
[일반 브라우저]
CRM 메시지 링크
  → index.html?t=<Tally폼URL>
  → window.location.replace(target)
  → Tally 폼 (즉시 이동)

[인앱 브라우저 - 카카오톡]
카카오톡 알림톡/LMS 링크
  → index.html?t=<Tally폼URL>
  → UA 감지: KAKAOTALK
  → kakaotalk://web/openExternal?url=<target>
  → 외부 브라우저 (Chrome/Safari)
  → Tally 폼

[인앱 브라우저 - Android]
인앱 링크
  → index.html?t=<Tally폼URL>
  → UA 감지: wv)
  → intent://<target>#Intent;scheme=https;package=com.android.chrome;end
  → Chrome
  → Tally 폼

[인앱 브라우저 - iOS / 기타]
인앱 링크
  → index.html?t=<Tally폼URL>
  → 폴백 UI 표시
  → "외부 브라우저에서 열기" 버튼
  → window.open(target, '_system') 또는 '_blank'
```

## 모듈 경계

| 모듈 | 위치 | 역할 |
|------|------|------|
| UA 감지 | index.html <script> | KAKAOTALK/NAVER/LINE/Instagram/FBAN/FBAV/Twitter/Snapchat/SamsungBrowser/wv 패턴 매칭 |
| 카카오톡 전용 | index.html <script> | `kakaotalk://web/openExternal` 스킴 사용 |
| Android intent | index.html <script> | `intent://` 스킴으로 Chrome 직접 호출 |
| 폴백 UI | index.html #fallback | 수동 "외부 브라우저에서 열기" 버튼 |
| 로딩 UI | index.html #loading | 스피너 + "이동 중" 메시지 |

## 제약사항

- iOS 인앱 브라우저에서 외부 브라우저로 자동 전환하는 보편적 방법이 없음 (폴백 버튼 필수)
- `?t=` 파라미터가 없으면 "잘못된 링크" 메시지 표시
- 카카오톡 스킴(`kakaotalk://web/openExternal`)은 카카오톡 앱 내에서만 동작
- promo_comparison.png는 Tally 폼의 EMBED 블록에서 참조하므로 URL 변경 시 폼도 수정 필요
