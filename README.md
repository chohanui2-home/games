# 미니게임 모음 (games hub)

가족·아이들이 한 페이지에서 4가지 미니게임을 골라 바로 시작하는 모바일·태블릿용 허브 페이지입니다.
빌드 도구 없이 **단일 `index.html`**(외부 리소스 0건)로 동작합니다.

- 배포 주소: <https://chohanui2-home.github.io/games/>
- 저장소: `chohanui2-home/games` (public, `main` / `(root)` GitHub Pages)
- 오프라인 사본: `dashboards/미니게임-모음.html` (`index.html`과 바이트·sha256 동일)

## 포함된 게임 (4가지)

| 아이콘 | 제목 | 게임 방식 | 주소 |
|---|---|---|---|
| ✏️ | 한붓그리기 | 점을 이어 모든 선을 중복 없이 한 번에 다 잇기 | https://chohanui2-home.github.io/one-stroke/ |
| 🧮 | ♡왕전초 연산왕!♡ | 1~6단계 사칙연산(+ − × ÷) 5문제 풀기 | https://chohanui2-home.github.io/wangjeon-math/ |
| ⏱️ | ♡왕전초 타이머왕!♡ | 눈짐작으로 목표 초에 딱 맞춰 멈추기 | https://chohanui2-home.github.io/wangjeon-timer/ |
| 🎨 | ♡왕전초 눈치왕!♡ | 적힌 글자·칠해진 색깔 헷갈리지 않고 고르기 | https://chohanui2-home.github.io/wangjeon-nunchi/ |

이 모음에는 위 4가지만 넣습니다(사용자 지정). 점프왕(`wangjeon-jump`), 내가 정육왕(`samgyeop-cut`),
내가 불판왕(`samgyeop-grill`)은 각자의 주소에서 따로 즐기고, `meat-cbt`(자격증 필기 공부용)도 제외합니다.

## 화면 규칙

- 상단 제목 `미니게임 모음` 한 줄 정중앙 + 부제 `하고 싶은 게임을 눌러 바로 시작해 보세요!`
- 카드 전체가 링크(`<a href="...">`) — 아이콘·게임 이름·짧은 게임 방식·`바로 시작 →` 배지
- 360~560px 1열, 600px 이상 2열 반응형 그리드 (아이콘 50~54px, 카드 전체가 터치 영역)
- 차분한 라이트 톤: 바탕 `#F4F6F9`, 카드 `#FFFFFF`, 카드별 은은한 파스텔 칩
- `env(safe-area-inset-*)` 적용, CSS에 `-webkit-text-stroke` 미사용
- 확인 뷰포트: `390×844`, `360×740`, `768×1024` — 가로 넘침 0

## 검증

```bash
python3 test_app.py
```

검사 항목: HTML 구조/태그 균형, 제목·부제, 4개 카드의 제목·URL·설명·배지, 카드 순서,
제외 게임(점프왕·정육왕·불판왕·meat-cbt) 링크 부재, `-webkit-text-stroke` 부재, safe-area 적용,
600px 2열 미디어쿼리, 외부 리소스·JS·인라인 핸들러 0건, `dashboards/미니게임-모음.html`과의 바이트 동일성.

## 배포 메모

`gh` 토큰이 없는 환경에서는 GitHub 웹 UI로 `index.html`·`README.md`를 업로드하고
Settings → Pages에서 `main` / `(root)`를 활성화합니다. 업로드 후 파일 목록에 반영된 것을 확인한 뒤
커밋해야 하며(너무 빨리 커밋하면 HTTP 400), 반영 후 실서버 본문의 sha256이 로컬과 같은지 확인합니다.
기존 파일을 덮어쓸 때는 웹 업로드가 막히면 해당 파일을 먼저 삭제한 뒤 다시 업로드합니다.
