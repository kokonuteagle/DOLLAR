# Source Map

Use this reference as the canonical source map for the report.
Do not paraphrase it away. Keep these URLs visible and available to the skill.

## 1) Fed balance sheet and implementation

### Federal Reserve H.4.1 current release and DDP
- https://www.federalreserve.gov/releases/h41/current/
- https://www.federalreserve.gov/datadownload/choose.aspx?rel=h41

Pull at least the latest release plus the previous 4 weekly observations.
Required fields:
- total assets
- Treasury securities
- agency MBS
- reserve balances with Federal Reserve Banks
- reverse repurchase agreements
- repurchase agreements
- U.S. Treasury General Account / Treasury deposits
- other deposits if relevant
- currency in circulation
- central bank liquidity swaps or loans and credit extensions if non-zero

### Federal Reserve reserve balances / IORB / implementation note
- https://www.federalreserve.gov/monetarypolicy/reserve-balances.htm
- latest FOMC implementation note page

Pull:
- IORB rate
- SRF rate
- ON RRP offering rate
- any reinvestment or bill-purchase instructions

### New York Fed SOMA holdings
- https://www.newyorkfed.org/markets/soma-holdings

Pull:
- total Treasury SOMA holdings
- total agency MBS holdings
- weekly or monthly changes
- maturity composition if relevant

### New York Fed repo / reverse repo / standing repo
- https://www.newyorkfed.org/markets/desk-operations/repo
- https://www.newyorkfed.org/markets/desk-operations/reverse-repo
- https://www.newyorkfed.org/markets/repo-agreement-ops-faq
- https://www.newyorkfed.org/markets/rrp_faq.html

Pull:
- daily SRF usage
- daily ON RRP take-up
- counterparty-type data when available

## 2) Money markets and repo plumbing

### New York Fed reference rates and methodology
- https://www.newyorkfed.org/markets/reference-rates
- https://www.newyorkfed.org/markets/reference-rates/sofr
- https://www.newyorkfed.org/markets/reference-rates/obfr
- https://www.newyorkfed.org/markets/reference-rates/additional-information-about-reference-rates

Pull:
- EFFR
- OBFR
- SOFR
- TGCR
- BGCR

### Office of Financial Research Short-term Funding Monitor
- https://www.financialresearch.gov/short-term-funding-monitor/
- https://www.financialresearch.gov/short-term-funding-monitor/datasets/repo/
- https://www.financialresearch.gov/short-term-funding-monitor/documentation/

Pull:
- centrally cleared repo rates and volumes
- tri-party repo rates and volumes
- collateral and tenor breakdowns

### New York Fed tri-party/GCF repo statistics
- https://www.newyorkfed.org/research/tri-party-repo

Pull:
- snapshot volumes
- collateral mix
- haircuts if relevant

### SEC/OFR money market fund data when MMF allocation matters
- https://www.sec.gov/data-research/statistics-data-visualizations/money-market-fund-statistics
- https://www.financialresearch.gov/money-market-funds/

Pull:
- government MMF asset levels
- repo holdings vs Treasury bill holdings if needed

## 3) Treasury cash and debt management

### Treasury Fiscal Data API / Daily Treasury Statement
- https://fiscaldata.treasury.gov/datasets/daily-treasury-statement/
- API base: https://api.fiscaldata.treasury.gov/services/api/fiscal_service/

Key endpoints:
- /v1/accounting/dts/operating_cash_balance
- /v1/accounting/dts/deposits_withdrawals_operating_cash
- /v1/accounting/dts/debt_subject_to_limit
- /v1/accounting/dts/public_debt_transactions

Pull:
- TGA closing balance
- daily deposit and withdrawal drivers
- debt subject to limit if debt ceiling is live
- security issuance and redemption cash flows if relevant

### Treasury auction and issuance sources
- https://fiscaldata.treasury.gov/datasets/treasury-securities-auctions-data/
- https://www.treasurydirect.gov/auctions/announcements-data-results/
- https://www.treasurydirect.gov/auctions/upcoming/

Pull:
- recent bill auction sizes
- recent coupon auction sizes
- changes versus prior month or prior quarter
- bid-to-cover and tails only if directly relevant

### Quarterly refunding / TBAC
- https://home.treasury.gov/policy-issues/financing-the-government/quarterly-refunding
- https://home.treasury.gov/policy-issues/financing-the-government/quarterly-refunding/most-recent-quarterly-refunding-documents
- https://home.treasury.gov/policy-issues/financing-the-government/quarterly-refunding/treasury-borrowing-advisory-committee-tbac

Pull:
- financing estimates
- policy statement
- TBAC report
- recommended financing tables
- auction schedule XML/PDF
- explicit language on bill/coupon mix and buybacks

### Debt limit / extraordinary measures
- https://home.treasury.gov/policy-issues/financial-markets-financial-institutions-and-fiscal-service/debt-limit

Pull:
- debt ceiling status
- extraordinary measures usage
- implications for TGA path and bill supply

## 4) Bank and dealer balance-sheet constraints

### H.8 weekly bank balance sheets
- https://www.federalreserve.gov/releases/h8/

Pull:
- large-bank reserve/cash proxies if visible
- securities holdings
- deposits and borrowings trends

### Senior Financial Officer Survey
- latest survey page and PDF

Pull:
- lowest comfortable level of reserves (LCLOR)
- qualitative reserve preference changes

### New York Fed Primary Dealer Statistics
- https://www.newyorkfed.org/markets/counterparties/primary-dealers-statistics

Pull relevant series on:
- positions in Treasuries
- financing/repo volumes
- fails to deliver / fails to receive
- marketable debt inventories if useful

### OFR STFM / NY Fed repo sources
Use repo volumes, funding rates, and collateral mix as indirect capacity signals.

## 5) Financial conditions

### Treasury yields
- https://home.treasury.gov/policy-issues/financing-the-government/interest-rate-statistics
- https://home.treasury.gov/treasury-daily-interest-rate-xml-feed

Pull:
- 2Y and 10Y yields
- curve changes over 1주 / 1개월 / 1분기

### Chicago Fed NFCI / ANFCI
- https://www.chicagofed.org/research/data/nfci/current-data

Pull:
- latest NFCI
- weekly change
- whether conditions are looser or tighter than average

### Dollar index / exchange-rate backdrop
- https://www.federalreserve.gov/releases/h10/current/

Pull:
- broad dollar index or major-currency subindex
- recent direction

### Mortgage rates
- https://www.freddiemac.com/pmms

Pull:
- latest 30Y and 15Y mortgage rates
- weekly change

### Credit spreads and equities
Prefer Fed sources when possible.
Use FRED if no direct primary source exists:
- IG OAS: BAMLC0A0CM
- HY OAS: BAMLH0A0HYM2
- S&P 500 or relevant index series

If the user specifies Nasdaq, long bonds, BTC, or another asset, use the most authoritative directly accessible market or index source available and explicitly label it as secondary if it is not a primary public-sector source.

## 6) Global dollar liquidity

### BIS Global Liquidity Indicators
- https://data.bis.org/topics/GLI
- https://www.bis.org/statistics/dataportal/gli.htm

Pull:
- USD credit to non-bank borrowers outside the U.S.
- cross-border bank credit
- international debt securities in dollars
- latest quarterly year-over-year and quarter-over-quarter direction

### BIS statistical commentary / release
- latest GLI commentary page

### Optional supporting context
- Federal Reserve notes on the international role of the dollar

## Machine-readable retrieval snippets

Treasury Fiscal Data API base
- https://api.fiscaldata.treasury.gov/services/api/fiscal_service/

Daily Treasury Statement
- /v1/accounting/dts/operating_cash_balance
- /v1/accounting/dts/deposits_withdrawals_operating_cash
- /v1/accounting/dts/debt_subject_to_limit
- /v1/accounting/dts/public_debt_transactions

Treasury auctions
- /v1/accounting/od/auctions_query
