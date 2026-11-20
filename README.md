# 미니게임 모음 (games hub)

가족·아이들이 한 페이지에서 7가지 미니게임을 골라 바로 시작하는 모바일·태블릿용 허브 페이지입니다.
빌드 도구 없이 **단일 `index.html`**(외부 리소스 0건)로 동작합니다.

- 배포 주소: <https://chohanui2-home.github.io/games/>
- 저장소: `chohanui2-home/games` (public, `main` / `(root)` GitHub Pages)
- 오프라인 사본: `dashboards/미니게임-모음.html` (`index.html`과 바이트·sha256 동일)

## 포함된 게임

| 아이콘 | 제목 | 게임 방식 | 주소 |
|---|---|---|---|
| 🧮 | ♡왕전초 연산왕!♡ | 1~6단계 사칙연산(+ − × ÷) 5문제 풀기 | https://chohanui2-home.github.io/wangjeon-math/ |
| ⏱️ | ♡왕전초 타이머왕!♡ | 눈짐작으로 목표 초에 딱 맞춰 멈추기 | https://chohanui2-home.github.io/wangjeon-timer/ |
| 🎨 | ♡왕전초 눈치왕!♡ | 적힌 글자·칠해진 색깔 헷갈리지 않고 고르기 | https://chohanui2-home.github.io/wangjeon-nunchi/ |
| ⚡ | ♡왕전초 점프왕!♡ | 2단 회오리 점프로 바닥 레이저·회오리벽 넘기 | https://chohanui2-home.github.io/wangjeon-jump/ |
| 🥩 | 내가 정육왕 | 통삼겹을 목표 무게에 딱 맞게 똑같이 자르기 | https://chohanui2-home.github.io/samgyeop-cut/ |
| 🔥 | 내가 불판왕 | 불판 위 삼겹살을 타이밍 맞춰 노릇하게 굽기 | https://chohanui2-home.github.io/samgyeop-grill/ |
| ✏️ | 한붓그리기 | 점을 이어 모든 선을 중복 없이 한 번에 다 잇기 | https://chohanui2-home.github.io/one-stroke/ |

`meat-cbt`(자격증 필기 공부용)는 게임이 아니므로 이 모음에 넣지 않습니다.

## 화면 규칙

- 상단 제목 `미니게임 모음` 한 줄 정중앙 + 부제 `하고 싶은 게임을 눌러 바로 시작해 보세요!`
- 카드 전체가 링크(`<a href="...">`) — 아이콘·게임 이름·짧은 게임 방식·`바로 시작 →` 배지
- 360~560px 1열, 600px 이상 2열 반응형 그리드 (터치 영역 최소 50px 아이콘 + 카드 전체 클릭)
- 차분한 라이트 톤: 바탕 `#F4F6F9`, 카드 `#FFFFFF`, 카드별 은은한 파스텔 칩
- `env(safe-area-inset-*)` 적용, CSS에 `-webkit-text-stroke` 미사용
- 확인 뷰포트: `390×844`, `360×740`, `768×1024` — 가로 넘침 0

## 검증

```bash
python3 test_app.py
```

검사 항목: HTML 구조/태그 균형, 제목·부제, 7개 카드의 제목·URL·설명·배지, 중복/예상 밖 링크,
`-webkit-text-stroke` 부재, safe-area 적용, 600px 2열 미디어쿼리, 외부 리소스·인라인 핸들러 0건,
`dashboards/미니게임-모음.html`과의 바이트 동일성.

## 배포 메모

`gh` 토큰이 없는 환경에서는 GitHub 웹 UI로 `index.html`·`README.md`를 업로드하고
Settings → Pages에서 `main` / `(root)`를 활성화합니다. 업로드 후 파일 목록에 반영된 것을 확인한 뒤
커밋해야 하며(너무 빨리 커밋하면 HTTP 400), 반영 후 실서버 본문의 sha256이 로컬과 같은지 확인합니다.
