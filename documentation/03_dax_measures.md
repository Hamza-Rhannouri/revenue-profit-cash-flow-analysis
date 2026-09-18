# DAX Measure Inventory

The original measure logic supplied for the project is documented below. This is an inventory/reference file; the PBIX remains the source of truth.

## Revenue and volume

```DAX
Revenue =
SUMX(
    SalesFactTable,
    SalesFactTable[Units]
        * SalesFactTable[Unit_Price]
        * (1 - SalesFactTable[Discount_Pct])
)

UNITS = SUM(SalesFactTable[Units])

ASP = DIVIDE([Revenue], [Units])

Revenue Per Customer = DIVIDE([Revenue], [Customer Count])

Customer Count = DISTINCTCOUNT(CustomDim[Customer_ID])
```

## Cost and profitability

```DAX
COGS =
SUMX(
    SalesFactTable,
    SalesFactTable[Units]
        * (
            SalesFactTable[Unit_Material_Cost]
            + SalesFactTable[Unit_Labor_Cost]
            + SalesFactTable[Unit_Overhead_Cost]
        )
)

Gross Profit = [Revenue] - [COGS]

Gross Margin % = DIVIDE([Gross Profit], [Revenue])

Variable Material Cost =
SUMX(
    SalesFactTable,
    SalesFactTable[Units] * SalesFactTable[Unit_Material_Cost]
)

Variable Labor Cost =
SUMX(
    SalesFactTable,
    SalesFactTable[Units] * SalesFactTable[Unit_Labor_Cost]
)

Variable Logistics Cost = SUM(SalesFactTable[Logistics_Expense])

Variable Costs =
[Variable Material Cost]
+ [Variable Labor Cost]
+ [Variable Logistics Cost]

Contribution Margin = [Revenue] - [Variable Costs]

Contribution Margin % = DIVIDE([Contribution Margin], [Revenue])

Operating Expenses =
SUM(SalesFactTable[Marketing_Expense])
+ SUM(SalesFactTable[Logistics_Expense])
+ SUM(SalesFactTable[Support_Expense])
+ SUM(SalesFactTable[Administrative_Expense])
+ SUM(SalesFactTable[Depreciation])

EBIT = [Gross Profit] - [Operating Expenses]

EBITDA = [EBIT] + SUM(SalesFactTable[Depreciation])

EBT = [EBIT] - SUM(SalesFactTable[Interest_Expense])

NET PROFIT = [EBT] - SUM(SalesFactTable[Taxes])

Net Margin% = DIVIDE([NET PROFIT], [Revenue])
```

## Working capital and growth

```DAX
AR = SUM(SalesFactTable[Accounts_Receivable_Amount])
AP = SUM(SalesFactTable[Accounts_Payable_Amount])
Inventory = SUM(SalesFactTable[Inventory_Value])
Working Capital = [AR] + [Inventory] - [AP]

Avg Customer Days = AVERAGE(SalesFactTable[Customer_Payment_Days])
Avg Supplier Days = AVERAGE(SalesFactTable[Supplier_Payment_Days])

CapEx = SUM(SalesFactTable[CapEx])

New Customers =
CALCULATE(
    DISTINCTCOUNT(CustomDim[Customer_ID]),
    CustomDim[New_Customer_Flag] = 1
)

CAC = DIVIDE([Marketing Expense], [New Customers])

Marketing ROI = DIVIDE([Revenue], [Marketing Expense])
```

## Time intelligence

The project uses a dedicated `DateTableDim` and year-over-year comparison patterns using `DATEADD` for KPI cards.
