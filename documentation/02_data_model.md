# Data Model

## Fact table

`SalesFactTable` contains the transaction-level numeric measures and foreign keys.

Key measures/fields include:

- Order_ID
- Units
- Unit_Price
- Discount_Pct
- Unit_Material_Cost
- Unit_Labor_Cost
- Unit_Overhead_Cost
- Marketing_Expense
- Logistics_Expense
- Support_Expense
- Administrative_Expense
- Accounts_Receivable_Amount
- Accounts_Payable_Amount
- Inventory_Value
- CapEx
- Depreciation
- Taxes
- Interest_Expense
- Planned_Units
- Planned_Price
- Return_Amount
- Shipping_Time_Days

## Dimensions

### CustomerDim
Customer identity, type, segment, geography, signup date, new-customer flag and churn flag.

### ProductDim
Product, category, subcategory, type, supplier and launch date.

### RegionDim
Region, country and city.

### ChannelDim
Acquisition channel and sales channel.

### PaymentDim
Payment method and payment status.

### CostTypeDim
Cost type classification.

### DataTypeDim
Data type classification.

### ScenarioDim
Scenario classification.

### DateTableDim
A dedicated calendar from 2021-01-01 through 2025-12-31 with year, quarter, month, week, day, weekday and weekend attributes.

## Modeling principle

Dimensions should filter the fact table through one-to-many relationships with single-direction filtering. The dedicated calendar should be marked as the model's date table and used for time-intelligence calculations.
