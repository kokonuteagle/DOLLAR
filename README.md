# DOLLAR

OpenClaw용 **달러 유동성 HTML 보고서 스타터 리포지토리**.

이 리포는 OpenClaw가:
- 처음엔 **리포트 주기/시간만 물어보고**
- 그다음부터는 **공식 데이터 기반 달러 유동성 보고서를 HTML 완성형으로 생성**하고
- 필요하면 **크론으로 반복 실행**하게 만드는 용도다.

---

## 이 리포로 할 수 있는 것

- 달러 유동성 리포트 1회 실행
- 모바일에서 보기 쉬운 HTML 보고서 생성
- `index.html` 최신본 유지
- `reports/` 폴더에 날짜별 보고서 누적
- OpenClaw 크론으로 정기 보고서 자동화

리포트 프레임은 아래 6개 레이어를 기준으로 동작한다.

1. Fed balance sheet / policy implementation
2. money markets / repo plumbing
3. Treasury cash & debt management
4. bank & dealer balance-sheet constraints
5. financial conditions
6. global dollar liquidity

---

## 가장 쉬운 사용법

### 방법 1) 스킬 폴더 복붙

이 리포의 아래 폴더를 OpenClaw 워크스페이스의 `skills/` 아래에 넣으면 된다.

```text
skills/usd-liquidity-html-reporter/
```

그다음 OpenClaw에 이렇게 말하면 된다:

- `달러 유동성 HTML 리포트 세팅해줘`
- `달러 유동성 보고서 자동화해줘`
- `USD liquidity recurring HTML report setup`

### 방법 2) 패키지 파일 사용

아래 파일을 써도 된다.

```text
dist/usd-liquidity-html-reporter.skill
```

---

## 실제 동작 방식

이 스킬은 처음 세팅할 때 **주기/시간만 묻는 것**을 목표로 설계되어 있다.

예:
- 매일 07:00 KST
- 매주 일요일 19:00 KST
- 평일 08:00 KST

주기가 정해지면 그 뒤에는:
- 데이터 수집
- 리포트 생성
- HTML 렌더링
- `index.html` 업데이트
- `reports/YYYY-MM-DD_...html` 아카이브
- 필요 시 git commit / push

까지 이어지도록 설계되어 있다.

---

## 포함 파일

### 루트
- `index.html` — 최신 HTML 보고서
- `reports/` — 날짜별 보고서 보관
- `dist/usd-liquidity-html-reporter.skill` — 패키징된 skill 파일
- `skills/usd-liquidity-html-reporter/` — 실제 OpenClaw skill 디렉터리

### skill 내부
- `SKILL.md` — 스킬 본문. 세팅/실행 규칙
- `references/data-playbook.md` — 공식데이터 우선 수집·해석 규칙
- `references/html-report-spec.md` — 기관형 HTML 출력 스펙
- `references/cron-automation.md` — 정기 실행 자동화 규칙
- `assets/report-shell.html` — HTML 리포트 템플릿 뼈대

---

## 리포트 스타일

결과물은 다음 방향을 목표로 한다.

- 모바일 퍼스트
- 기관형(institutional) 톤
- 첫 화면에서 바로 이해 가능
- 차트 포함 가능
- OpenClaw 채팅 답변이 아니라 **완성된 HTML 문서**로 출력

즉, “설명문”이 아니라 **공유 가능한 보고서 파일**을 만드는 쪽이다.

---

## 데이터 원칙

가능하면 아래 1차 출처를 우선 사용한다.

- Federal Reserve
- New York Fed
- U.S. Treasury / DTS / Auctions
- Chicago Fed NFCI
- OFR
- BIS

필요할 때만 보조적으로 2차 배포 소스(FRED 등)를 쓴다.

---

## 권장 프롬프트 예시

- `달러 유동성 리포트 지금 한 번 만들어줘`
- `매일 아침 7시에 달러 유동성 HTML 보고서 자동으로 보내게 세팅해줘`
- `BTC 기준으로 달러 유동성 보고서 만들어줘`
- `나스닥 기준으로 recurring HTML liquidity report setup`

---

## 대상 사용자

이 리포는 이런 경우에 맞다.

- OpenClaw에서 정기 매크로/유동성 보고서를 돌리고 싶은 사람
- 텍스트 답변보다 HTML 리포트 파일이 필요한 사람
- 달러 유동성을 “순유동성 밈”이 아니라 **배관(plumbing) 관점**으로 보고 싶은 사람

---

## 메모

이 리포는 **OpenClaw용 워크플로 스타터**다.

즉 핵심은:
- 스킬 복붙
- 주기/시간 한 번 지정
- 이후 HTML 보고서 자동 생성

필요하면 이후에 BTC 전용 / Nasdaq 전용 / bond 전용 파생 버전으로 확장하면 된다.
