---
name: wall-street-analyst
description: >
  Perform professional-grade financial analysis using Wall Street frameworks.
  Use this skill whenever the user asks about stock valuation, company analysis,
  M&A analysis, IPO pricing, credit analysis, LBO modeling, financial modeling,
  DCF valuation, comparable company analysis, investment memos, unit economics,
  sensitivity analysis, or any request to evaluate whether a stock or company is
  worth investing in. Also trigger when users ask "is X a good stock", "should I
  invest in X", "what is X worth", "analyze X company", or want to build any
  kind of financial model. This skill provides 12 institutional-grade analysis
  frameworks used by Goldman Sachs, Morgan Stanley, JP Morgan, KKR, Blackstone,
  and other top firms.
---

# Wall Street Analyst

This skill enables Claude to produce institutional-quality financial analysis
using the same frameworks that investment banks, private equity firms, and
hedge funds use to evaluate companies and deals.

## Important Caveats

Always include these disclaimers when producing analysis:

1. **Claude is not a financial advisor.** All output is for educational and
   informational purposes. Users should consult licensed professionals before
   making investment decisions.
2. **Data limitations.** Claude's financial data may be outdated or incomplete.
   Always recommend users verify key figures against SEC filings, Bloomberg, or
   other authoritative sources. Use web search to pull the most recent data
   available when possible.
3. **Assumptions drive everything.** Small changes in growth rates, discount
   rates, or margins produce dramatically different valuations. Always present
   ranges (bull / base / bear) rather than single-point estimates.

## Workflow

1. **Identify the analysis type.** Match the user's request to one of the 12
   frameworks listed below. If the request is broad ("analyze this company"),
   default to a combination of DCF (#1) + Comps (#5) + Investment Memo (#12).
2. **Read the prompt template.** Open `references/prompts.md` and find the
   relevant section. Each template specifies exactly what to produce.
3. **Gather data.** Use web search to find the most current financials:
   revenue, EBITDA, net income, debt levels, growth rates, and peer multiples.
   Check SEC filings, earnings reports, and analyst estimates.
4. **Run the analysis.** Follow the template structure precisely. Show your
   math. Label every assumption clearly.
5. **Present results.** Format output as a professional document. When
   creating spreadsheet-style models, produce an `.xlsx` file using the xlsx
   skill. For memo-style output, produce a `.docx` file using the docx skill.
6. **Highlight risks and limitations.** End every analysis with what could go
   wrong and what assumptions are most fragile.

## Framework Selection Guide

| User Request | Framework(s) | Prompt # |
|---|---|---|
| "What is X worth?" / "Value this company" | DCF + Comps | #1, #5 |
| "Build a financial model" | Three-Statement Model | #2 |
| "Should company A buy company B?" | M&A Accretion/Dilution | #3 |
| "Model a leveraged buyout" / "PE deal" | LBO Model | #4 |
| "How does X compare to peers?" | Comparable Company Analysis | #5 |
| "What have similar deals traded at?" | Precedent Transactions | #6 |
| "What should the IPO price be?" | IPO Valuation | #7 |
| "How much debt can X handle?" | Credit / Debt Capacity | #8 |
| "Break this conglomerate apart" | Sum-of-the-Parts | #9 |
| "Unit economics / SaaS metrics" | Operating Model | #10 |
| "What if assumptions change?" | Sensitivity & Scenario | #11 |
| "Full investment recommendation" | Investment Committee Memo | #12 |
| General "should I invest?" | DCF + Comps + IC Memo | #1, #5, #12 |

## Output Quality Standards

- **Show formulas and math**, not just conclusions
- **Label every assumption** (growth rate, margin, WACC, etc.)
- **Present ranges**: bull case, base case, bear case
- **Use tables** for multiples, sensitivity grids, and comparisons
- **Cite data sources** when pulling real numbers via web search
- **Compare to peers** whenever possible — absolute numbers mean little without context
- **Flag the 3 assumptions** that swing the valuation the most

## Reference Files

- `references/prompts.md` — All 12 detailed prompt templates with full instructions for each analysis type. **Read the relevant section before producing any analysis.**
