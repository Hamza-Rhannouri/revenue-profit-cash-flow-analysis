# Source → Report Lineage

`project3_source.csv`

→ Power BI / Power Query ingestion

→ light source-value cleanup

→ dimensional model + `SalesFactTable`

→ dedicated `DateTableDim`

→ centralized DAX measures

→ four-page executive/FP&A report

→ management takeaways and action recommendations

For a production-quality version, add an explicit validation layer between source ingestion and the semantic model, including duplicate-key checks, null checks, referential-integrity checks and reconciliation of major financial totals.
