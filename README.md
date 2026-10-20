# Investment Deal Spend & Budget Tracking Dashboard
A two-page Power BI dashboard that tracks transaction advisory spend against a board-approved investment budget across a portfolio of 29 deals, built on a Star Schema data model.

> **Data disclaimer:** All data in this repository is **synthetic / sample data** created for demonstration purposes. It does not represent real financial figures, deals, or suppliers. Company names and logos (if shown) are used only for visual-identity demonstration.

---

## Dashboard Preview

| Page 1: Executive Overview | Page 2: Spend Breakdown |
|---|---|
| ![Page 1](<img width="880" height="492" alt="1" src="https://github.com/user-attachments/assets/790b414a-bdaa-44a4-99ae-5ec8c08d3951" />
) | ![Page 2](<img width="897" height="512" alt="2" src="https://github.com/user-attachments/assets/67c56920-e960-4286-a758-fa14cc10857e" />
) |

---

## Business Problem

Investment teams spend heavily on advisors, due diligence, and success fees across many deals. Management needs a single view to answer:

- How much of the approved budget has actually been spent?
- Where is the money going: which business unit, activity type, deal, and supplier?
- How is spend split between upfront fees and success fees?
- Which suppliers concentrate the largest share of spend?

## Key Features

- **Executive KPIs:** board-approved budget, MIC/IC allocation, total actual spend, total commitment, and average spend per activity.
- **Deal portfolio status:** total deals with an active vs. aborted split.
- **Spend analysis by:** business unit, activity type, deal name, and supplier.
- **Fee structure:** upfront fees vs. success fees for both actual spend and commitments.
- **Top 10 suppliers** ranking with a detailed supplier table.
- **Interactive slicers:** year, business unit, deal, activity type, deal stage, supplier, and deal status.

## Tools & Skills

| Area | Tools |
|---|---|
| Visualization & BI | Power BI Desktop |
| Data preparation | Power Query |
| Calculations | DAX |
| Data modeling | Star Schema |

## Data Model

The report is built on a **Star Schema**: central fact tables surrounded by descriptive dimensions.

```
            DimDate
               |
DimSupplier -- FactSpend -- DimDeal
               |
        DimActivityType -- DimBusinessUnit
```

> Replace the diagram and table names above with the exact tables used in your model.

| Table | Type | Description |
|---|---|---|
| `FactSpend` | Fact | Actual spend and commitments per deal, activity, and supplier |
| `DimDeal` | Dimension | Deal name, stage, status |
| `DimSupplier` | Dimension | Supplier names |
| `DimActivityType` | Dimension | Due diligence, advisory, success fees, etc. |
| `DimBusinessUnit` | Dimension | Business unit of each deal |
| `DimDate` | Dimension | Calendar table for year-based analysis |

## Main DAX Measures

```DAX
-- Add your real measures here, for example:
Total Actual Spend = SUM ( FactSpend[ActualSpend] )

Avg Spend per Activity =
DIVIDE ( [Total Actual Spend], DISTINCTCOUNT ( FactSpend[ActivityID] ) )

Budget Utilization % =
DIVIDE ( [Total Actual Spend], [Board Approved Budget] )
```

## Repository Structure

```
.
├── README.md
├── ALAT_Spend_Dashboard.pbix
├── data/
│   └── sample_data.xlsx
├── images/
│   ├── page1_overview.png
│   ├── page2_breakdown.png
│   └── data_model.png
└── docs/
    └── Dashboard.pdf
```

## How to Use

1. Download `ALAT_Spend_Dashboard.pbix`.
2. Open it in **Power BI Desktop**.
3. If prompted, update the data source path to point to `data/sample_data.xlsx` (Transform data → Data source settings).
4. Refresh and explore using the slicers.

## Key Insights (from the sample data)

- Three suppliers account for roughly 60% of total spend.
- AI & Digital Hardware is the largest business unit by spend (about half of the total).
- Actual spend represents about a third of the approved investment budget.

> These insights reflect the sample data only.

## Author

**Mostafa Hamed** | Data Analyst
[LinkedIn](https://www.linkedin.com/in/mostafa-hamed-4aa035273/) | mostafa.hamed1499@gmail.com
