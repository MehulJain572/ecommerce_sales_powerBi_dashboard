# E-Commerce Sales Dashboard (Power BI)

An interactive Power BI dashboard that analyses sales, profit and demand for an e-commerce company using ~500 orders from 2018. It tracks four headline KPIs and breaks performance down by state, product category, sub-category, customer, payment mode and month.

![E-Commerce Sales Dashboard](photos/dashboard.png)

## Business Questions Answered

- Which states and customers drive the most sales?
- Which product categories account for most of the units sold?
- Which payment modes do customers prefer?
- Which months and sub-categories are profitable, and which make a loss?

## Key Metrics

| KPI | Value |
|---|---|
| Total Sales Amount | 438K |
| Total Quantity Sold | 6K units |
| Total Profit | 37K (overall margin ≈ 8%) |
| Average Order Value (AOV) | 876 |

## Dashboard Features

- 4 KPI cards: Sum of Amount, Sum of Quantity, Sum of Profit and AOV
- Quarter slicer (Qtr 1 to Qtr 4) and dropdown filter that update every visual
- Bar charts: sales by state, sales by customer, profit by sub-category
- Donut charts: quantity share by category and by payment mode
- Column chart: monthly profit, with loss-making months highlighted in red
- Custom dark theme and consistent colour palette

## Key Insights

- **Regional concentration:** Maharashtra (102K) and Madhya Pradesh (87K) are the top two states, together contributing about 43% of total sales.
- **Category mix:** Clothing makes up 63% of units sold, followed by Electronics (21%) and Furniture (17%).
- **Payment preference:** Cash on Delivery is the largest payment mode at 44% of units sold. The rest is split across UPI (21%), debit card (13%), credit card (12%) and EMI (10%).
- **Seasonality in profit:** Most months are profitable, but May, June, July and December show net losses. July is the weakest month.
- **Sub-category profitability:** Printers is the most profitable sub-category (~8.6K), followed by Bookcases (~6.5K).
- **Top customer:** Harivansh is the highest-spending customer (9.9K), followed by Madhav (9.4K).

## Data Model

The model uses two tables linked on `Order ID`:

- **Orders:** Order ID, Order Date, CustomerName, City, State
- **Details:** Order ID, Amount, Profit, Quantity, Category, Sub-Category, PaymentMode

### DAX Measure

AOV is a measure rather than a calculated column, so it is computed once at the total level (total sales ÷ number of unique orders) and responds correctly to every slicer and filter.

```DAX
AOV = DIVIDE(SUM(Details[Amount]), DISTINCTCOUNT(Orders[Order ID]))
```

## Repository Structure

```
├── data/
│   ├── Orders1.csv
│   └── Details1.csv
├── dashboard/
│   └── E_Commerce_Dashboard.pbix
└── photos/
    └── dashboard.png
```

## How to Open

1. Download `E_Commerce_Dashboard.pbix` from the `dashboard/` folder.
2. Open it in [Power BI Desktop](https://powerbi.microsoft.com/desktop/) (free, Windows only).
3. Use the quarter slicer and dropdown to explore the data. If Power BI asks for the data source, point it to the CSV files in the `data/` folder.

## Tools Used

Power BI Desktop, DAX, Data Modelling, CSV

## Credits

Built as a learning project while following a Power BI beginner tutorial on YouTube ("Power BI Dashboard Project in Hindi | Power BI Course 2023"). The dataset is the e-commerce sales data used in that tutorial.

## Author

**Mehul Jain**, B.Tech, Maulana Azad National Institute of Technology (MANIT), Bhopal
