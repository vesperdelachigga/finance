# Wall Street Analyst — Prompt Templates

This file contains 12 institutional-grade financial analysis frameworks.
Each section is a complete template. Replace bracketed placeholders with
real data gathered via web search and user input.

## 常用术语解释

- **NTM (Next Twelve Months)**: 未来12个月财务预测
- **LTM (Last Twelve Months)**: 过去12个月实际数据
- **EV/EBITDA**: 企业价值倍数（企业价值/息税折旧摊销前利润）
- **FCF**: 自由现金流（Free Cash Flow）
- **WACC**: 加权平均资本成本（Weighted Average Cost of Capital）
- **DCF**: 折现现金流（Discounted Cash Flow）
- **CAGR**: 复合年增长率（Compound Annual Growth Rate）
- **ROE**: 净资产收益率（Return on Equity）
- **MOIC**: 现金-on-cash倍数（Multiple on Invested Capital）
- **IRR**: 内部收益率（Internal Rate of Return）
- **EBITDA**: 息税折旧摊销前利润
- **LBO**: 杠杆收购（Leveraged Buyout）
- **SOTP**: 分部估值法（Sum-of-the-Parts）
- **Comps**: 可比公司分析（Comparable Company Analysis）

## 风险提示

1. **数据时效性风险**: 财务数据可能已过时，需验证最新财报
2. **假设敏感性风险**: 小幅假设变动可能导致估值大幅变化
3. **行业差异风险**: 不同行业适用不同的估值倍数标准
4. **市场条件风险**: 宏观经济环境影响估值结果
5. **模型局限性**: 模型假设可能不适用于所有情况

## 使用示例

### 示例1: DCF估值
用户问: "腾讯控股值多少钱？"
触发条件: 询问公司价值/估值
框架选择: #1 (DCF) + #5 (Comps)
执行步骤:
1. 读取 prompts.md 的 DCF 模板部分
2. 获取腾讯最新财务数据
3. 建立模型并计算
4. 输出专业估值报告

### 示例2: 股票比较
用户问: "茅台和五粮液哪个更好？"
触发条件: 比较两只股票
框架选择: #5 (Comps)
执行步骤:
1. 收集两家公司最近3年数据
2. 计算关键指标对比
3. 分析差异
4. 给出结论

## Table of Contents

1. [DCF Valuation Model](#1-dcf-valuation-model)
2. [Three-Statement Financial Model](#2-three-statement-financial-model)
3. [M&A Accretion/Dilution Analysis](#3-ma-accretiondilution-analysis)
4. [LBO (Leveraged Buyout) Model](#4-lbo-leveraged-buyout-model)
5. [Comparable Company Analysis (Comps)](#5-comparable-company-analysis-comps)
6. [Precedent Transaction Analysis](#6-precedent-transaction-analysis)
7. [IPO Valuation & Pricing Analysis](#7-ipo-valuation--pricing-analysis)
8. [Credit Analysis & Debt Capacity Model](#8-credit-analysis--debt-capacity-model)
9. [Sum-of-the-Parts (SOTP) Valuation](#9-sum-of-the-parts-sotp-valuation)
10. [Operating Model & Unit Economics](#10-operating-model--unit-economics)
11. [Sensitivity & Scenario Analysis](#11-sensitivity--scenario-analysis)
12. [Investment Committee Memo](#12-investment-committee-memo)

---

## 1. DCF Valuation Model

**Role context:** Senior Analyst, Investment Banking Division

**Produce a complete DCF (Discounted Cash Flow) valuation model containing:**

- **Free cash flow projections:** Next 5 years with explicit growth assumptions.
  Build from revenue → EBITDA → EBIT → NOPAT → FCF. State each assumption.
- **WACC calculation:** Cost of equity (CAPM: risk-free rate + beta × equity
  risk premium) + cost of debt (after tax). Weight by target capital structure.
- **Terminal value:** Calculate using BOTH the perpetuity growth method
  (Gordon Growth: FCF × (1+g) / (WACC−g)) AND exit multiple method
  (terminal EBITDA × exit multiple). Compare results.
- **Sensitivity analysis:** Two-way table varying WACC (rows) and terminal
  growth rate (columns). Show implied share price at each intersection.
- **Discount rate justification:** Explain beta source, risk-free rate
  selection, and equity risk premium used.
- **Key drivers:** Identify the 3–5 variables that move the valuation most.
- **Comparable companies:** Show how growth, margin, and risk assumptions
  compare to public peers.
- **Valuation range:** Bull case, base case, bear case with clear
  assumptions for each.

**Format:**
- **Primary output**: Markdown formatted analysis with tables and clear formulas
- **Data file**: `DCF_projections.csv` containing all calculations and projections
- **Visual elements**: ASCII sensitivity tables and scenario comparisons
- **Formulas**: Provided in code blocks for Excel replication

**Example structure:**
```
# DCF Valuation Analysis

## Summary Tables
| Metric | Value | Source |
|--------|-------|--------|
| WACC | 10.5% | Market data |
| Terminal Value | $1,000M | Perpetuity growth |
| Implied Share Price | $50 | Base case |

## Detailed Calculations
[CSV file available: DCF_projections.csv]

## 风险提示
- 数据基于2024年财报，需验证2025年最新数据
- 终端增长率假设为3%，±1%变动导致估值±15%变化
- WACC计算基于CAPM模型，beta值敏感性高
```

---

## 2. Three-Statement Financial Model

**Role context:** VP, Financial Modeling Group

**Produce a complete three-statement model containing:**

- **Income statement:** Revenue, COGS, gross profit, SG&A, EBITDA, D&A, EBIT,
  interest, taxes, net income — projected 5 years.
- **Balance sheet:** Current assets (cash, AR, inventory), fixed assets, total
  assets; current liabilities (AP, accrued), long-term debt, equity — 5 years.
- **Cash flow statement:** Operating (net income + add-backs + working capital
  changes), investing (capex, acquisitions), financing (debt, dividends,
  buybacks) — 5 years.
- **Link formulas:** Explain how net income flows to cash flow statement, how
  cash flow ending balance ties to balance sheet cash, how retained earnings
  link statements together.
- **Working capital model:** Days sales outstanding (DSO), days inventory
  outstanding (DIO), days payable outstanding (DPO) driving AR, inventory, AP.
- **Debt schedule:** Outstanding principal, interest rate, mandatory
  amortization, optional prepayment, interest expense calculation.
- **Key assumptions:** Revenue growth rate, gross margin, opex as % of
  revenue, capex as % of revenue, tax rate, working capital days.
- **Error checks:** Balance sheet balances (A = L + E), cash flow ties to
  balance sheet, no circular references without iteration.

**Format:**
- **Primary output**: Excel-style model in Markdown format with formulas explained
- **Data file**: `Three_Statements_Model.csv` containing all projections
- **Formulas**: Plain English explanations with code block examples
- **Linkages**: Diagram showing how statements connect

**Example:**
```
# Income Statement (Year 1-5)

| Item | Year 1 | Year 2 | ... | Formula |
|------|--------|--------|-----|--------|
| Revenue | $100M | $110M | | Prev × 1.1 |
| COGS | $60M | $66M | | Revenue × 0.6 |

## 风险提示
- 模型假设收入增长率为10%，实际可能波动
- 营运资本模型基于行业平均DSO/DIO/DPO
- 需验证实际财务数据与模型假设的一致性
```
```

---

## 3. M&A Accretion/Dilution Analysis

**Role context:** Managing Director, M&A Advisory

**Produce an accretion/dilution analysis containing:**

- **Deal structure:** Cash vs. stock consideration mix, total enterprise value,
  equity value, per-share price, premium to current trading price.
- **Pro forma income statement:** Combined revenue, EBITDA, net income for
  acquirer + target post-deal.
- **EPS impact:** Standalone acquirer EPS vs. pro forma EPS. Calculate
  accretion or dilution in dollars and percentage.
- **Synergies:** Itemize cost synergies (headcount, facilities, systems) and
  revenue synergies (cross-sell, pricing) with dollar amounts and timing
  (when they phase in).
- **Funding sources:** How the deal is paid for — cash on hand, revolver
  draw, new term loan, bond issuance, stock issuance. Show interest cost of
  each debt tranche.
- **Credit impact:** Pro forma net debt/EBITDA, interest coverage ratio,
  credit rating implications.
- **Break-even synergies:** Minimum synergies required for deal to be EPS
  accretive in year 1.
- **Sensitivity table:** EPS accretion/dilution at different purchase prices
  and synergy levels.

**Format:**
- **Primary output**: M&A analysis memo in Markdown format
- **Data file**: `Accretion_Dilution_Analysis.csv` with detailed calculations
- **Visuals**: Combined income statement comparison table
- **Recommendation**: Clear buy/sell/hold recommendation with rationale

**Example structure:**
```
# M&A Accretion/Dilution Analysis

## Deal Summary
| Metric | Value |
|--------|-------|
| Purchase Price | $50/share |
| Premium | 25% |
| Synergies | $200M/year |

## EPS Impact
- Acquirer standalone: $2.00
- Pro forma: $2.15
- Accretion: $0.15 (7.5%)

## 风险提示
- 协同效应实现时间假设为2年，提前或延迟影响EPS
- 融资成本基于当前利率，利率变动影响债务成本
- 模型假设交易立即完成，实际整合时间可能影响结果
```
```

---

## 4. LBO (Leveraged Buyout) Model

**Role context:** Associate, Private Equity

**Produce a complete LBO model containing:**

- **Sources and uses:** Sources (senior debt, mezzanine, sponsor equity,
  rollover equity, cash on B/S). Uses (equity purchase price, transaction
  fees, debt repayment, cash to balance sheet).
- **Debt structure:** Senior secured (term loan A, term loan B), second lien,
  mezzanine/sub debt, revolver. For each: amount, interest rate (fixed vs.
  floating), amortization schedule, maturity, covenants.
- **Cash flow sweep:** How excess free cash flow is applied to mandatory
  debt repayment vs. optional prepayment. Sweep percentage by year.
- **Exit scenarios:** Strategic sale and IPO at years 3, 4, and 5. Apply
  exit EBITDA multiples ranging from current to +1x expansion.
- **IRR calculation:** Equity IRR for each exit year and multiple
  combination. Show the formula.
- **Cash-on-cash multiple (MOIC):** Total equity proceeds ÷ initial equity
  invested for each scenario.
- **Debt paydown schedule:** Year-by-year beginning balance, mandatory
  amort, optional prepay, ending balance for each tranche.
- **Management assumptions:** Revenue CAGR, EBITDA margin trajectory,
  capex as % of revenue, working capital changes.

**Format:**
- **Primary output**: PE investment committee memo in Markdown
- **Data file**: `LBO_Model_Analysis.csv` with cash flow and returns
- **Returns table**: IRR and MOIC for each exit scenario
- **Visuals**: Cash flow sweep schedule and debt paydown timeline

**Example:**
```
# LBO Returns Analysis

| Exit Year | IRR | MOIC | EV Multiple |
|-----------|-----|------|-------------|
| Year 3 | 18% | 1.8x | 8x |
| Year 4 | 25% | 2.2x | 9x |
| Year 5 | 30% | 2.5x | 10x |

## 风险提示
- 退出倍数假设基于行业平均，实际可能波动
- 利率变动影响债务成本和IRR计算
- 经营假设敏感性高，收入增长±5%影响IRR±8%
```
```

---

## 5. Comparable Company Analysis (Comps)

**Role context:** Equity Research Analyst

**Produce a trading comps analysis containing:**

- **Peer group:** 10–15 public companies in the same industry. Justify
  inclusion/exclusion criteria (size, geography, business model, growth).
- **Trading multiples:** For each peer: EV/Revenue (NTM), EV/EBITDA (NTM),
  P/E (NTM), EV/FCF. Use next-twelve-months consensus estimates.
- **Financial metrics:** Revenue, revenue growth, EBITDA, EBITDA margin,
  net income, FCF margin for each peer.
- **Valuation range:** 25th percentile, median, mean, 75th percentile of
  each multiple across the peer set.
- **Implied valuation:** Apply 25th/median/75th multiples to the target
  company's financials to get an implied equity value range.
- **Premium/discount adjustments:** Explain why the target deserves to
  trade at a premium (superior growth, margins) or discount (smaller scale,
  higher risk) vs. peers.
- **Growth comparison:** Revenue growth, EBITDA growth, margin trend vs.
  peer median.
- **Quality screen:** Rank peers by comparability. Flag the 5 closest comps.

**Format:**
- **Primary output**: Trading comps analysis with peer comparison tables
- **Data file**: `Comparable_Companies_Analysis.csv` with all peer data
- **Valuation ranges**: Percentile distribution table for each multiple
- **Premium/discount**: Clear justification for target's premium/discount

**Example:**
```
# Peer Multiples Analysis

| Company | EV/Rev | EV/EBITDA | P/E |
|---------|--------|-----------|-----|
| Target | 2.5x | 15x | 25x |
| Peer A | 2.2x | 12x | 20x |
| Peer B | 2.8x | 18x | 30x |
| Median | 2.5x | 15x | 25x |

## 风险提示
- 可比公司选择基于行业和规模，可能存在差异
- 市场情绪影响倍数波动
- 财务数据基于不同会计准则，需调整可比性
```
```

---

## 6. Precedent Transaction Analysis

**Role context:** M&A Banker

**Produce a precedent transaction analysis containing:**

- **Transaction universe:** 15–20 relevant M&A deals in the past 5 years in
  the same or adjacent industry.
- **Deal multiples:** EV/EBITDA, EV/Revenue paid in each transaction.
- **Deal characteristics:** Acquirer name, target name, deal size (EV),
  announcement date, deal rationale (strategic, financial, consolidation).
- **Premium analysis:** Control premium paid over the target's unaffected
  trading price (1-day, 30-day, 90-day prior).
- **Valuation range:** 25th percentile, median, 75th percentile of deal
  multiples.
- **Adjustments:** Flag differences between strategic vs. financial buyers,
  high-synergy vs. low-synergy deals, contested vs. friendly transactions.
- **Market conditions:** Note how M&A volumes, credit availability, and
  sector sentiment evolved over the period.
- **Implied valuation:** Apply 25th/median/75th deal multiples to the target
  company's financials.

**Format:**
- **Primary output**: Precedent transaction analysis with deal summaries
- **Data file**: `Precedent_Transactions_Analysis.csv` with all deal data
- **Multiple ranges**: EV/EBITDA and EV/Revenue distribution analysis
- **Market conditions**: Timeline showing deal activity and pricing trends

**Example:**
```
# Transaction Multiples Analysis

| Deal Date | Buyer | Seller | EV/EBITDA | Premium |
|-----------|-------|--------|-----------|---------|
| 2024-Q1 | Corp A | Target X | 12x | 30% |
| 2024-Q2 | Corp B | Target Y | 15x | 25% |
| 2024-Q3 | Corp C | Target Z | 18x | 40% |
| Median | | | 15x | 30% |

## 风险提示
- 交易背景差异（战略vs财务买家）影响倍数可比性
- 市场条件变化影响交易价格
- 控制溢价可能不适用于所有交易场景
```
```

---

## 7. IPO Valuation & Pricing Analysis

**Role context:** Capital Markets Banker

**Produce an IPO pricing analysis containing:**

- **Offering structure:** Primary shares (new capital raised) vs. secondary
  shares (insider selling), total shares offered, over-allotment (greenshoe).
- **Pre-money valuation:** Implied company value before IPO proceeds.
- **Post-money valuation:** Pre-money + primary proceeds.
- **Comparable IPOs:** 5–10 recent IPOs in the same sector with pricing
  multiples (EV/Revenue, EV/EBITDA, P/E at IPO price), first-day return,
  and current trading vs. IPO price.
- **Valuation range:** Low, mid, high price per share with implied
  EV/Revenue and EV/EBITDA at each price.
- **Dilution analysis:** Existing shareholder ownership before and after IPO,
  including ESOP pool expansion.
- **Float analysis:** Shares trading publicly as % of total shares
  outstanding. Compare to sector median float.
- **First-day pop expectation:** Typical underpricing in the sector based on
  recent IPO data.

**Format:**
- **Primary output**: IPO pricing memo with valuation analysis
- **Data file**: `IPO_Pricing_Analysis.csv` with comps and valuation ranges
- **Price range**: Low/mid/high share price with implied multiples
- **Float analysis**: Ownership structure and dilution impact

**Example:**
```
# IPO Pricing Analysis

| Price Range | EV/Revenue | EV/EBITDA | P/E |
|-------------|------------|-----------|-----|
| Low: $15 | 3x | 20x | 18x |
| Mid: $20 | 4x | 25x | 24x |
| High: $25 | 5x | 30x | 30x |

**Recommended Range: $18-22**

## 风险提示
- 首日表现受市场情绪影响，可能偏离估值
- 稀释效应需考虑ESOP池和现有股东
- 定价基于可比IPO，实际可能因市场条件调整
```
```

---

## 8. Credit Analysis & Debt Capacity Model

**Role context:** Leveraged Finance Banker

**Produce a debt capacity analysis containing:**

- **EBITDA analysis:** Historical (3 years) and projected (3 years). Note any
  add-backs or adjustments to arrive at "adjusted EBITDA."
- **Leverage ratios:** Total Debt / EBITDA, Senior Debt / EBITDA, Net Debt /
  EBITDA. Compare to industry standards and rating agency thresholds.
- **Interest coverage:** EBITDA / Interest Expense, (EBITDA − Capex) /
  Interest Expense. State minimum acceptable thresholds.
- **Debt structure:** Senior secured (1st lien), senior unsecured, subordinated,
  mezzanine layers. Amount, rate, maturity for each.
- **Covenants:** Maximum leverage ratio, minimum interest coverage, minimum
  liquidity, restricted payments basket.
- **Maximum debt capacity:** How much the company can borrow while staying
  within investment-grade (or specified) credit metrics.
- **Pricing grid:** Expected interest rate at different leverage levels
  (e.g., 2.0x = L+175, 3.0x = L+250, 4.0x = L+350).
- **Refinancing analysis:** Existing debt maturity profile and when each
  tranche needs to be rolled or refinanced.

**Format:** Credit memo with debt capacity recommendation.

## 风险提示
- 信用评级变化影响债务成本
- 行业标准可能随时间变化
- 模型假设基于当前市场条件

---

## 9. Sum-of-the-Parts (SOTP) Valuation

**Role context:** Restructuring / Strategic Advisor

**Produce a sum-of-the-parts valuation containing:**

- **Business segments:** Break the company into distinct operating divisions.
  Name each segment and describe what it does.
- **Segment financials:** Revenue, EBITDA, EBITDA margin, revenue growth for
  each segment.
- **Valuation methodology:** Select the best approach for each segment — DCF,
  public comps, or precedent transactions. Justify the choice.
- **Segment values:** Individual enterprise value for each segment using the
  chosen methodology.
- **Corporate costs:** Identify unallocated overhead. Decide whether to
  capitalize as a negative value or allocate to segments.
- **Debt allocation:** Total consolidated debt, cash, and other
  enterprise-to-equity bridge items.
- **Total value:** Sum of segment EVs − corporate costs − net debt + cash +
  non-operating assets.
- **Value per share:** Total equity value ÷ diluted shares outstanding.
  Compare to current trading price to find discount/premium.

**Format:** Restructuring analysis with breakup valuation scenarios.

## 风险提示
- 分部估值假设各业务独立运营
- 协同效应可能被低估或高估
- 市场对分拆的估值可能不同于整体

---

## 10. Operating Model & Unit Economics

**Role context:** Growth Equity Investor

**Produce a detailed operating model containing:**

- **Revenue build:** Bottom-up forecast. For SaaS: customers × ARPU × retention.
  For e-commerce: orders × AOV × purchase frequency. For marketplaces:
  GMV × take rate. State the driver model explicitly.
- **Unit economics:** Customer acquisition cost (CAC), lifetime value (LTV),
  LTV/CAC ratio, payback period in months, gross margin per unit or per
  customer.
- **Cohort analysis:** Show how retention, revenue, and margin evolve for
  customer cohorts acquired in different periods.
- **Key drivers:** The 5 inputs that move revenue and costs the most. Show
  impact of ±10% change in each.
- **Scenario planning:** Upside (strong retention, expanding ARPU, lower CAC),
  base (management plan), downside (churn increases, CAC rises, growth
  slows). State assumptions for each.
- **Burn rate:** Monthly cash consumption. Cash runway at current burn. Months
  to zero.
- **Breakeven analysis:** When does the company reach cash-flow breakeven?
  What metrics must hit for that to happen?
- **Scaling assumptions:** How do unit economics improve (or degrade) as the
  company scales? Economies of scale vs. diminishing returns.

**Format:** Operating model with monthly projections for year 1, quarterly
for years 2–3.

## 风险提示
- 用户获取成本和生命周期价值假设敏感性高
- 规模效应可能延迟实现
- 市场竞争影响增长假设

---

## 11. Sensitivity & Scenario Analysis

**Role context:** Risk Management / Valuation Quality Control

**Produce a sensitivity and scenario analysis containing:**

- **One-way sensitivity:** For each key variable (revenue growth, EBITDA
  margin, WACC, terminal growth, exit multiple), show how the valuation
  changes as that single variable moves ±20% from base case.
- **Two-way sensitivity:** Pair the two most impactful variables. Create a
  matrix showing valuation at each combination.
- **Scenario builder:**
  - *Bull case:* All key assumptions at optimistic end simultaneously.
  - *Base case:* Management plan / consensus estimates.
  - *Bear case:* All key assumptions at pessimistic end simultaneously.
  State the specific assumptions for each scenario.
- **Monte Carlo inputs (conceptual):** For each key assumption, define the
  probability distribution (normal, triangular, uniform) and parameters
  (mean, std dev, min, max). Describe the simulation approach.
- **Breakeven analysis:** What minimum revenue growth, margin, or synergy
  level is required for the investment to generate a positive return?
- **Downside protection:** At what valuation does the equity get wiped out?
  What margin of safety exists?
- **Risk factors:** Rank the top 5 assumptions by impact on valuation. For
  each, state the base case value, plausible downside, and valuation impact.
- **Hedging strategies:** For each major risk, suggest a financial or
  operational hedge.

**Format:** Risk analysis memo with sensitivity tables and scenario outcomes.

## 风险提示
- 情景分析基于历史数据，未来可能不同
- 变量相关性可能影响结果
- 极端情景概率难以准确估计

---

## 12. Investment Committee Memo

**Role context:** Partner / Portfolio Manager, Investment Committee

**Produce an investment committee memo containing:**

- **Executive summary:** Three paragraphs: (1) what the opportunity is and why
  now, (2) expected returns and structure, (3) key risks and mitigants.
- **Deal overview:** Transaction structure, total size, use of proceeds,
  expected timeline, key parties involved.
- **Company analysis:** Business model, products/services, customer base,
  competitive positioning (moats), management team assessment, financial
  performance summary (3-year history + projections).
- **Industry analysis:** Total addressable market (TAM), market growth rate,
  secular trends, competitive landscape, regulatory environment.
- **Investment thesis:** 3–5 specific reasons this investment will generate
  returns. Each point should be a testable hypothesis with supporting
  evidence.
- **Valuation summary:** Present results from multiple methodologies (DCF,
  comps, precedent transactions). Describe the "football field" chart showing
  ranges from each method.
- **Returns analysis:** Expected IRR, cash-on-cash multiple (MOIC), payback
  period. Show returns under base, upside, and downside scenarios.
- **Risk assessment:** Top 5 risks ranked by probability × impact. For each:
  description, likelihood, severity, and specific mitigation strategy.
- **Recommendation:** Clear invest or pass recommendation with reasoning. If
  invest, state the maximum price / terms acceptable.

**Format:** Investment committee presentation deck outline.

## 风险提示
- 投资决策基于多种假设，实际结果可能不同
- 市场条件变化影响投资回报
- 模型假设需定期更新和验证
