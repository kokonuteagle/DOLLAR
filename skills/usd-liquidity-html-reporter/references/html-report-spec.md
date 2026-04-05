# HTML Report Spec

Use this reference when rendering the final report.

## Mandatory output mode
Return one complete HTML5 document that can be saved and opened directly in a mobile browser.
Do not return the final report as plain chat prose.

## Presentation rules
The visible report must read like an institutional macro note, not like an AI response.

Do not visibly include:
- setup chatter
- methodology narration
- assumptions as a standalone explainer unless unavoidable
- retrieval notes
- prompt or internal labels
- meta phrases like `다음은`, `아래는`, `요약해보면`, `AI`, `브라우징`

## Front-end stack
- Tailwind CSS via CDN
- Pretendard font via jsDelivr CDN
- Chart.js via CDN when charts are available
- If Chart.js is not used, render charts with inline SVG

## Visual tone
Target feel:
- institutional macro dashboard
- polished buy-side note
- premium fintech terminal on mobile
- serious, calm, high-trust

Required visual direction:
- page background: `bg-slate-100`
- main cards: `bg-white`
- hero card: also light, white or very light slate only
- headings: `text-slate-900`
- body text: `text-slate-600`
- secondary labels: `text-slate-500`
- separators: `border-slate-200`

Use:
- `rounded-2xl` or `rounded-3xl`
- `shadow-sm` with selective `shadow-md`
- strong spacing discipline
- compact mobile typography

Avoid:
- dark or near-black hero backgrounds by default
- heavy gradients
- neon accents
- decorative illustrations
- emojis in the report body

## First-screen requirements
The first screen must answer instantly:
1. 지금 위험자산에 순풍인가 역풍인가
2. 무엇이 가장 크게 작동 중인가
3. 자금이 어디로 이동 중인가
4. 지금 바로 체크할 숫자는 무엇인가

So the hero section must include:
- `[분석 기준일] 달러 유동성 분석 보고서`
- one regime badge
- one plain-language sentence
- 3 key driver chips
- 3 headline numbers

## Recommended page architecture
1. Hero section
2. Immediate market takeaway card
3. Dashboard chart section
4. Data clock card
5. Snapshot table card
6. Six-layer analysis cards
7. Integrated judgment section
8. Scenario section
9. Next checkpoints section
10. Sources footer

The dashboard chart section should appear as high as possible on mobile and must prioritize the most decision-useful visuals first:
- recent path / reserve bridge
- money-market implementation
- Treasury funding structure
- six-layer score comparison
- conditions panel

## Chart requirements
Charts are mandatory when data are available.
The chart section must feel information-dense enough that a user can understand the liquidity regime from the visuals alone.
Use at least **5 chart cards** when the data permit.

### Non-negotiable chart rule
A chart is not decoration.
Every chart must answer one concrete market question and must include:
- what changed
- over what time window
- why that matters

If a chart does not add information beyond a sentence, do not include it.

### Required dashboard chart set when data are available
1. **Recent path line chart**
   - reserves, ON RRP, TGA over at least the latest 4-5 observations
   - objective: show whether reserves are actually falling or whether the move is liability reallocation

2. **Reserve-bridge / contribution chart**
   - use waterfall, stacked bar, or grouped contribution bars
   - decompose reserve change into Fed assets, TGA, ON RRP, currency, and residual/other when available
   - objective: show what funded the move, not just that the move happened

3. **Money-market implementation chart**
   - show SOFR, EFFR, OBFR, IORB, and/or key spreads such as SOFR-IORB and EFFR-IORB
   - objective: show whether plumbing is orderly or whether corridor pressure is emerging

4. **Treasury funding structure chart**
   - show bill vs coupon issuance mix, recent auction sizing, or TGA direction with issuance context
   - objective: show how Treasury financing is interacting with private cash pools

5. **Six-layer score chart**
   - compare the six layers side by side
   - objective: show where the active support/headwind is actually coming from

### Strongly preferred additional charts
- **Financial conditions chart**
  - 2Y/10Y, IG/HY spreads, dollar direction, or a compact conditions dashboard
- **Scenario/risk-balance chart**
  - horizontal bars for base / improvement / deterioration transmission pressure
- **Per-layer mini sparklines or metric strips**
  - add inside six-layer cards when a clean recent trend exists

### Chart-type guidance
- line chart: recent multi-period path
- grouped bar chart: weekly vs monthly vs quarterly changes
- waterfall / contribution bars: reserve bridge or funding source decomposition
- donut chart: only for true composition views, such as bill/note/bond mix
- horizontal bars: scenario bias, pressure ranking, or score distribution
- sparkline / metric strip: compact trend cue inside a card

### Mobile chart rules
- charts must be readable without pinch-zoom
- on mobile, prefer slightly smaller fonts over cropped or clipped charts
- reduce legend, axis, and label font sizes as needed to keep the full chart visible
- every chart card should fit the full plot area within the viewport width
- avoid chart containers that force horizontal scrolling for the visual itself
- if a chart becomes cramped, reduce decorative padding first, then reduce text size, not plot visibility
- keep chart titles short
- annotate units clearly (`$bn`, `%`, `bp`, score)
- show source/date/frequency in or directly below the card
- if mixing official weekly data and daily market data, label the clocks clearly in the chart subtitle or footnote

### Six-layer visual rule
Each of the six-layer analysis cards should include a mini visual, compact metric strip, or explicit unavailable-state block when data are available or missing.
Examples:
- Fed balance sheet card: reserves / ON RRP / TGA mini trend or metric strip
- money markets card: SOFR-IORB / EFFR-IORB spread strip
- Treasury card: bill/coupon mix or TGA direction metrics
- dealer/bank card: inventory/capacity proxy or explicit missing-series block
- financial conditions card: yields/spreads mini metrics
- global dollar card: dollar / BIS direction cue or explicit `확인 불가`

If a layer lacks enough data for a chart, show a compact unavailable-state block that names the missing series and why they matter.

## Table rules
Wrap every table in:
- `<div class="overflow-x-auto">`

Style:
- minimal horizontal borders only
- compact rows
- clear numeric alignment
- keep source/date in the same row
- make the table readable on small screens

## Score badge mapping
- -2 → `bg-red-100 text-red-700` → `-2 강한 역풍`
- -1 → `bg-amber-100 text-amber-700` → `-1 약한 역풍`
- 0 → `bg-slate-100 text-slate-700` → `0 중립`
- +1 → `bg-emerald-100 text-emerald-700` → `+1 약한 순풍`
- +2 → `bg-teal-100 text-teal-700` → `+2 강한 순풍`

## Writing rules
Inside each analytical block, write in this order:
- what changed
- why it changed
- why markets should care

Every major card should include a plain-language market implication line.
Translate jargon into cash-flow meaning whenever possible.

Examples:
- `TGA 상승` → `재무부 현금잔고 증가, 민간 자금 흡수`
- `ON RRP 감소` → `연준 역레포 잔고 축소, 자금 위치 이동 가능성`
- `dealer capacity 제약` → `국채를 받아줄 중개 여력 부담`

## Source rendering
For every key quantitative item, show near the figure or in the same row:
- source institution
- series/report name when possible
- date
- frequency

At the bottom, include a compact primary-source footer.
If a market series came from a secondary distribution source, label it explicitly as secondary.
