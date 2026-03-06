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
   - **数据获取优先级**: AkShare（首选）→ 东方财富/同花顺 → 巨潮资讯（A股）→ Bloomberg（国际）
4. **Run the analysis.** Follow the template structure precisely. Show your
   math. Label every assumption clearly.
5. **Present results.** Format output as a professional document. When
   creating spreadsheet-style models, provide CSV format and structured data tables.
   For memo-style output, use Markdown formatting with clear sections. All outputs
   should include data sources and calculation references.
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
- **Provide CSV exports** for tabular data when needed
- **Include formulas in code blocks** for easy replication

## 常见错误处理

1. **数据获取失败**
   - 检查网络连接
   - 尝试不同数据源
   - 明确告知数据限制

2. **指标缺失**
   - 使用相关指标替代
   - 解释替代原因
   - 保持透明度

3. **估值异常**
   - 检查输入数据准确性
   - 分析异常原因
   - 提供合理区间

4. **模型计算错误**
   - 验证关键公式
   - 检查单位一致性
   - 确保逻辑合理性

## Output Formats (推荐使用 .xlsx/.docx)

### 数据表格式
使用 Markdown 表格输出结构化数据：

| 指标 | 数值 | 说明 |
|------|------|------|
| 营业收入 | 100亿元 | 2025年预计 |
| 净利润 | 15亿元 | 增长率15% |
| PE | 25x | 行业平均 |

### 格式转换建议
- **Excel**: 直接生成 .xlsx 格式文件
- **Word**: 生成 .docx 格式报告
- **CSV**: 作为数据导出选项

### 数据导出方法
为需要表格输出的分析，提供多种格式导出功能：
```python
# 示例：数据导出
import pandas as pd

# 生成 Excel 文件
df.to_excel('analysis_data.xlsx', index=False)

# 生成 Word 报告
# 需要额外库支持，如 python-docx
# from docx import Document
# document = Document()
# document.add_table(df.shape[0]+1, df.shape[1])
# ...

# 生成 CSV 文件（备用）
df.to_csv('analysis_data.csv', index=False)
```

## 技术实现细节

### 数据处理
- 使用 pandas 处理表格数据
- 标准化日期格式：YYYY-MM-DD
- 货币单位统一：亿元
- 保留4位小数精度

### 模型构建
- DCF 使用 WACC = 10% 作为默认值
- EBITDA 倍数范围：6-12倍（消费），8-15倍（科技）
- 股票风险溢价：6-8%
- 终端增长率：2-3%

### AkShare 集成
- 优先使用 AkShare 获取真实数据
- 提供数据获取的常见 API 列表
- 错误处理示例

### 多语言支持
- 根据用户语言自动切换模板语言
- 保持专业术语的准确性

### 版本控制
- 增加模板版本号
- 记录每次更新的内容

## 技能兼容性说明

由于 Claude Code 环境缺少以下技能，将采用替代方案：

| 缺失技能 | 替代方案 | 说明 |
|---------|---------|------|
| `.xlsx` | CSV + Markdown | 数据以 CSV 和 Markdown 表格形式输出 |
| `.docx` | Markdown 格式 | 报告以 Markdown 格式呈现，可轻松复制到 Word |

## Reference Files

- `references/prompts.md` — All 12 detailed prompt templates with full instructions for each analysis type. **Read the relevant section before producing any analysis.**

## AkShare 使用指南

### 数据获取优先级
1. AkShare（首选）- 提供中国股市实时数据
2. 东方财富/同花顺 - 中文金融数据平台
3. 巨潮资讯（A股公告）- 官方披露平台
4. Bloomberg（国际数据）- 全球金融数据

### 常用 API 列表
- `ak.stock_zh_a_hist()` - 获取A股历史数据
- `ak.stock_financial_analysis()` - 财务分析数据
- `ak.stock_board_industry_name_em()` - 行业分类
- `ak.stock_board_industry_cons()` - 行业成分股

### 错误处理示例
```python
try:
    data = ak.stock_zh_a_hist(symbol="000001", period="daily", start_date="20200101", end_date="20240101")
except Exception as e:
    print(f"数据获取失败: {e}")
    # 尝试备用数据源或使用估计值
```
