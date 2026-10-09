# H-M-Customer-Products-Trend-Dashboard

A two-page Power BI dashboard built on H&M's public transaction data to answer three consumer-insight questions:

1. **What sells?** Top product categories, graphical styles and colours over the past year
2. **What's trending?** Which product types are gaining share of H&M's sales mix
3. **Who buys what?** How product preferences differ across age groups

📄 [Full dashboard (PDF)](HM_Project_Dashboards.pdf)

---

## Data

[H&M Personalized Fashion Recommendations](https://www.kaggle.com/competitions/h-and-m-personalized-fashion-recommendations) (Kaggle)

| Table | Rows | Used for |
|---|---|---|
| transactions | ~31.8M | Sales (Sep 2018 – Sep 2020) |
| customers | ~1.37M | Age groups |
| articles | ~105K | Product type, category, colour, graphical style |

Prices in the dataset are scaled, so revenue is shown as a **revenue index**, not in euros.

## Approach

- **Data model:** star schema with the transactions table as the fact table, customer and article tables as dimensions, plus a custom date table that defines the "past year" and "prior year" periods.
- **Metric toggle:** a field parameter lets the user switch every chart between units and revenue.
- **Trend metric:** instead of raw growth, each product type's *share of H&M's total sales* in Jun–Aug 2020 is compared with Jun–Aug 2019. This separates real winners from items that only fell less than the rest of the business.
- **Trend status:** each product type is classified (based on units sold):

| Status | Share of mix | Units sold |
|---|---|---|
| Genuine growth | ▲ | ▲ |
| Resilient (falling less than total) | ▲ | ▼ |
| Growing slower than total | ▼ | ▲ |
| Declining | ▼ | ▼ |

- **Age affinity index:** each age group's share of purchases in a product group, divided by the average customer's share (100 = average, above 100 = buys more than average).

## Key findings

**What's popular (Sep 2019 – Aug 2020)**
- Sales fell year on year: units −11.2%, revenue −8.8%.
- Ladieswear brings in about two-thirds of revenue.
- Customers mostly buy basics: solid patterns are ~58% of revenue and black alone ~35%.
- Age groups mostly buy the same things. Under-25s over-index on bags, swimwear and accessories (index ~120–140); 55+ lean toward full-body and upper-body garments.

**What's trending (Jun–Aug 2020 vs 2019)**
- Clear winners, gaining share and growing in units: blazers (+42% units), leggings/tights, socks, heeled sandals, cardigans, bodysuits.
- High-volume lines (dresses, trousers, tops) are resilient: falling, but less than H&M overall.
- Summer and holiday items fell hardest (shorts, swimwear, vest tops, sunglasses, sandals: about −25% to −50% units).

## Limitations

- Trend status is based on units sold, not revenue.
- Share growth is relative to H&M's own total, not the market. A product type can gain share simply because others fell faster.
- Factors not captured in the data (e.g. promotions, campaigns) can create short-term spikes that look like trends.
- The dashboard should be read alongside real company and market context.
