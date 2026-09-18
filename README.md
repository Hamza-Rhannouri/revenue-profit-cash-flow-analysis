# Project 3 — Revenue, Profit & Cash Flow Analysis (Power BI)

## Purpose

A Power BI FP&A-style analysis of revenue performance, profitability, operating costs, working capital and forward-looking profit risk.

## Tools

- Power BI Desktop
- Power Query
- DAX
- CSV source data

## Project scope

The source dataset contains 100,500 rows and 58 columns covering orders, customers, products, geography, channels, payments, costs, working capital, capital expenditure, depreciation, taxes, interest, planning fields and operational metrics.

The report was designed around four questions:

1. What is happening to revenue and profit?
2. What is driving the profitability change?
3. What is happening to working capital / cash-flow-related drivers?
4. What actions should management consider?

## Model

The report uses a star-schema approach with a central `SalesFactTable` and dimensions for Date, Customer, Product, Region, Channel, Payment, Cost Type, Data Type and Scenario. A dedicated `DateTableDim` is used for time intelligence.

## Important portfolio note

This is an AI-generated/synthetic dataset. No confidential or real company data is represented.

## Evidence included

- Original source CSV
- Original PBIX report
- Four report-page screenshots
- Model documentation
- DAX inventory
- Technical audit and portfolio recommendations

## Reproduction

Open the PBIX file in Power BI Desktop. The source CSV is included for reference. Because the PBIX preserves the original Power BI model/report state, a reviewer should treat the PBIX as the primary executable artifact and the documentation as the explanation of the analytical design.
