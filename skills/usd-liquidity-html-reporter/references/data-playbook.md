# Data Playbook

Use this reference when collecting and interpreting the liquidity data.

## Core frame
Build the report through six layers:
1. Fed balance sheet and policy implementation
2. Money markets and repo plumbing
3. Treasury cash and debt management
4. Bank and dealer balance-sheet constraints
5. Financial conditions
6. Global dollar liquidity

Always go in this order:
- accounting first
- market pricing second
- narrative last

## Non-negotiable rules
- Use official documents and official data first: Fed Board, New York Fed, U.S. Treasury, BIS, Chicago Fed, OFR, SEC, SF Fed when relevant.
- Never collapse the analysis into one meme like `순유동성`.
- Always separate stock from flow.
- Always show level, 1주 변화, 1개월 방향, 최근 분기 방향 when available.
- Separate accounting liquidity from felt market liquidity.
- Separate active drivers: Fed assets, ON RRP, TGA, bill issuance, dealer capacity, offshore dollar conditions.
- Do not assume reserve declines are automatically bearish for risk assets.
- Keep official-data dates distinct from newer market quotes.

## Data clock
Start every report with these clocks:
- latest daily market date
- latest H.4.1 date
- latest DTS date
- latest primary dealer date
- latest NFCI date
- latest MMF or SEC/OFR date
- latest BIS GLI quarter

If clocks differ, say so explicitly.

## Required pulls

### 1) Fed balance sheet
Required series:
- total factors supplying reserve funds / total assets proxy
- Treasury securities
- agency MBS
- reserve balances with Federal Reserve Banks
- reverse repurchase agreements
- repurchase agreements
- U.S. Treasury, General Account / Treasury deposits
- currency in circulation
- central bank liquidity swaps if non-zero

Use at least the latest release plus the prior 4 weekly observations.

Interpret reserves with the simplified bridge:
- ΔReserves ≈ ΔFed assets - ΔCurrency - ΔTGA - ΔONRRP - ΔOther non-reserve liabilities/capital

### 2) Money markets / repo
Required series where available:
- EFFR
- OBFR
- SOFR
- TGCR
- BGCR
- OFR repo rates and volumes

Key spreads:
- SOFR - IORB
- EFFR - IORB
- SOFR - EFFR
- TGCR/BGCR vs SOFR

Stable corridor behavior with low facility stress generally means plumbing is functioning.

### 3) Treasury cash & debt
Required series:
- TGA path from DTS
- recent deposits/withdrawals context if relevant
- recent bill auction sizes
- recent coupon auction sizes
- quarterly refunding / TBAC only when it matters for medium-term supply regime

Interpretation:
- TGA up = reserve/ON RRP drain from the private sector
- TGA down = private sector cash injection
- If bill issuance rises while ON RRP falls, test whether MMF cash is rotating into bills

### 4) Bank / dealer capacity
Use these when available:
- H.8 bank balance-sheet trends
- SFO survey / reserve preference clues
- NY Fed primary dealer statistics
- OFR repo volumes, collateral mix, rates

Signs of tighter capacity:
- repo volatility around supply events
- rising fails
- inventory strain
- stronger month-end/quarter-end dislocations

### 5) Financial conditions
Required market layer:
- 2Y and 10Y Treasury yields
- Chicago Fed NFCI / ANFCI
- broad dollar direction
- credit spreads (IG / HY) if accessible

Interpret direction jointly. High policy rates do not automatically mean tight felt conditions.

### 6) Global dollar liquidity
Prefer BIS GLI:
- USD credit to non-bank borrowers outside the U.S.
- cross-border bank credit
- international debt securities in dollars
- YoY and QoQ direction

Do not equate U.S. bank reserves with global dollar liquidity.

## Required questions
Answer these explicitly in the final report:
- 지금 준비금은 실제로 줄고 있는가, 아니면 다른 Fed liabilities와의 재배치가 더 큰가?
- ON RRP 변화는 유동성 공급인가, 단순한 자금 위치 이동인가?
- TGA 증감은 reserves를 얼마나 압박하거나 완화하는가?
- Treasury bill issuance가 MMF 자금을 ON RRP에서 국채로 이동시키고 있는가?
- repo 시장은 안정적인가, 아니면 balance-sheet stress 신호가 있는가?
- 은행과 dealers가 국채 및 자금시장 중개를 충분히 소화할 capacity가 있는가?
- broader financial conditions는 easing인가 tightening인가?
- 글로벌 달러 조달은 확장 중인가 수축 중인가?
- 위 요소들을 종합하면 위험자산, 특히 관심 자산에는 순풍인가 역풍인가?

## Analytical output rules
For each of the six layers, always include:
1. 최신 데이터 스냅샷
2. 최근 변화 방향
3. 왜 그런 변화가 생겼는지
4. 시장으로의 전달 경로
5. 점수 (-2 ~ +2)

Score guide:
- -2 = 강한 유동성 역풍
- -1 = 약한 역풍
- 0 = 중립/혼합
- +1 = 약한 순풍
- +2 = 강한 순풍

## Fallback
If a primary series is unavailable:
- say `확인 불가`
- list the missing series
- say which judgment depends most on them
- do not invent numbers or dates
