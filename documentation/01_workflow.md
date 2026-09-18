# Project 3 — Workflow

## 1. Source ingestion

Imported a largely clean 100k+ row CSV into Power BI.

## 2. Light Power Query cleanup

Only minor source-value corrections were required. The dataset did not require a large-scale cleaning workflow like Project 1 or Project 2.

## 3. Dimensional modeling

The flat source was separated into dimensions and a fact table:

- ChannelDim
- CostTypeDim
- CustomerDim
- DataTypeDim
- PaymentDim
- ProductDim
- RegionDim
- ScenarioDim
- DateDim
- DateTableDim
- SalesFactTable

## 4. Semantic layer

Measures were centralized in a dedicated measure table. Core measures cover revenue, units, ASP, COGS, gross profit, EBITDA, EBIT, EBT, net profit, margins, operating expenses, variable costs, CAC, marketing ROI, AR, AP, inventory, working capital and CapEx.

## 5. Reporting

The report contains four pages:

1. Revenue Performance Overview
2. Revenue & Profit Decomposition
3. Cash Flow / Working Capital Analysis
4. Actions & Profit Forecast

## 6. Storytelling approach

Each page follows a management-oriented structure: headline → KPIs → key takeaway → diagnostic visuals → implication/action.
