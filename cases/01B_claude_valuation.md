# Mini-Case 1B: Build a Valuation Model with Claude

## Background

CP3 Pharmaceuticals (from the chapter) is evaluating a $547,000 materials-handling system. The capital expenditure request form shows:

- **Annual benefits:** $300,000 scrap revenue + $35,000 labor savings + $8,800 reduced recycling costs = $343,800 total
- **Investment:** $547,000, depreciated straight-line over 5 years (zero salvage value)
- **Tax rate:** 40%
- **Project life:** 5 years
- **Reported metrics:** NPV = $200,773; IRR = 35.8%; Payback = 2.19 years

The strategic planning committee wants to understand how sensitive the NPV is to the key assumptions before approving the project.

## Your Task

Use Claude (via claude.ai chat, Claude Code, or the Claude Excel add-in) to build an Excel workbook that:

1. **Inputs sheet** — clearly labeled input cells for: initial investment, annual benefits (broken out by category), tax rate, depreciation life, and discount rate

2. **Cash flow sheet** — annual free cash flows for Years 0–5, showing EBIT, taxes, NOPAT, depreciation add-back, and FCF

3. **Results sheet** — NPV, IRR, and payback period, computed from the cash flows

4. **Sensitivity table** — a two-way table showing NPV across a range of discount rates (8%–20%) and annual benefit totals (±30% around the base case)

## Suggested Prompt for Claude

> I need an Excel workbook to evaluate a capital expenditure proposal. The investment is $547,000 in a materials-handling system with a 5-year life, straight-line depreciation to zero salvage value, and a 40% tax rate. Annual pre-tax benefits are $343,800. Create: (1) an Inputs sheet with clearly labeled yellow input cells, (2) a Cash Flows sheet showing NOPAT, depreciation add-back, and free cash flow for each year, (3) a Results sheet with NPV, IRR, and payback period using a 12% discount rate, and (4) a Sensitivity table showing NPV for discount rates from 8% to 20% in 2% steps and annual benefits ranging from $240,000 to $450,000 in $30,000 steps. Use professional formatting with a dark navy header row.

## Discussion Questions

1. At what discount rate does the project become NPV-negative? Does this change your view of the investment?

2. The annual benefit estimate ($343,800) is based on projected scrap prices and labor savings. If actual benefits come in 20% below projection, is the project still attractive?

3. The strategic planning committee suspects the analyst is overconfident. What discount rate adjustment might the committee apply to account for optimistic bias, and how does this affect the decision?

4. What does the sensitivity table tell you about which input the NPV is most sensitive to?

## Key Concepts

- Excel models make sensitivity analysis fast and transparent
- The NPV profile (NPV vs. discount rate) shows how much margin of safety exists
- Sensitivity analysis is a key tool for Phase II managerial review — it exposes how fragile the investment thesis is
- Claude can build professional financial models from plain-English descriptions in seconds
