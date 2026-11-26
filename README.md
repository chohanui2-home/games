# ♡왕전초 창의수학 놀이터!♡

왕전초 친구들이 태블릿·스마트폰으로 바로 여는 창의수학 놀이 5가지와, 놀이가 끝나면 남기는 **학년·번호 기록장**입니다.

- 놀이터(모음): <https://chohanui2-home.github.io/games/>
- 기록장: <https://chohanui2-home.github.io/games/records.html>
- QR카드: `downloads/qr-changui-math.png` (놀이터), `downloads/qr-timer.png` (도전!! 타이머왕♡ · 단독)

## 놀이 5가지

| 놀이 | 주소 | 끝났을 때 남는 기록 |
| --- | --- | --- |
| 🧮 ♡왕전초 연산왕!♡ | <https://chohanui2-home.github.io/wangjeon-math/> | 점수 · 맞힌 문제 수 · 걸린 시간 |
| 🌈 ♡왕전초 길찾기왕!♡ | <https://chohanui2-home.github.io/wangjeon-connect/> | 완료한 문제 수 (단계별) |
| 🎨 ♡왕전초 눈치왕!♡ | <https://chohanui2-home.github.io/wangjeon-nunchi/> | 점수 · 정답 수 · 반응 시간 |
| 🍎 ♡왕전초 사과게임왕!♡ | <https://chohanui2-home.github.io/apple-game/> | 점수 · 터뜨린 사과 · 120초 |
| ✏️ ♡왕전초 한붓그리기왕!♡ | <https://chohanui2-home.github.io/one-stroke/> | 완료한 문제 수 (단계별) |

별도 놀이: ⏱️ **도전!! 타이머왕♡** — <https://chohanui2-home.github.io/wangjeon-timer/> (5종 모음에는 넣지 않고 단독 QR로 씁니다. 기록은 같은 기록장에 모입니다.)

## 기록 남기기 (게임 화면)

- 한 판이 끝나거나 한 단계를 다 풀면 결과 화면(길찾기왕·한붓그리기왕은 `🏆 기록` 버튼/단계 완성 알림)에 **🏆 기록 남기기** 칸이 나옵니다.
- 입력은 **학년 · 번호**(필수)와 **이름**(선택, 비워도 등록됩니다). 반(class)은 쓰지 않습니다.
- `등록`을 누르면 Supabase `game_records` 로 바로 보내고, 화면에 등록 완료가 뜹니다. 연습만 할 때는 등록하지 않고 `다시 하기`를 누르면 됩니다.
- 공용 태블릿 원칙: 게임은 `localStorage`/`sessionStorage` 를 쓰지 않습니다. 새로고침하면 처음 상태로 돌아갑니다.

## 기록장 (선생님)

- 게임별·학년별 필터, 게임별 최고 기록 순위(학생별 최고 1건), 전체 기록 목록.
- **엑셀(CSV) 저장** — UTF-8 BOM 을 붙여 한글이 깨지지 않습니다.
- **선생님 모드**(PIN `2026`): 기록 한 건씩 삭제, 전체 비우기.

## 구조

- `index.html` — 놀이터 모음 페이지
- `records.html` — 기록장
- `schema.sql` — Supabase 스키마(테이블 + RPC 4개). 이미 적용되어 있습니다.
- `record-panel.css`, `record-panel.js` — 6개 게임에 똑같이 들어가는 기록 패널(원본)
- `inject_record.py`, `patch_games.py`, `patch_builds.py` — 각 게임 템플릿/build.py 에 패널을 넣은 1회용 스크립트
- `make_qr.py` — QR카드 2장 생성 + OpenCV 디코딩 검증

## 데이터

- Supabase 프로젝트 `family-dashboard`(`hlqyzstixodeqywgfmvg`) · 테이블 `game_records`
- 컬럼: `id, created_at, game_id, game_title, grade, student_num, student_name, score, detail, duration_sec`
- RPC: `game_record_submit`(anon), `game_record_list`(anon), `game_record_delete`(PIN), `game_record_clear`(PIN)
- 테이블은 RLS 로 직접 읽기/쓰기를 막고, RPC 만 열어 두었습니다.
