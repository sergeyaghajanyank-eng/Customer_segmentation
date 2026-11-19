# Bank Customer Segmentation with K-Means

In this project, I grouped 1,000 bank customers into segments: 650 Retail customers and 350 Wholesale customers. I gave each group a short description and suggested a campaign idea and a way to measure its results.

**Business question:** How can a bank understand its different types of customers and make more relevant offers to them?

> **Note:** The dataset is synthetic, not real bank data. This project is a practice example, so the results should not be treated as findings about an actual bank.

## What I did

1. Explored the dataset and looked at Retail and Wholesale customers separately because their values and activity levels were quite different.
2. Chose 7 numeric features: income or revenue, account balance, number and value of transactions, outstanding loans, number of products, and the share of digital transactions.
3. Used `StandardScaler` to put these features on comparable scales, then applied K-Means separately to Retail and Wholesale customers.
4. Tested 2, 3, 4, and 5 groups and compared the Silhouette Scores. This score helps show how clearly the groups are separated.
5. Used 3 groups for each customer type and named them based on their main characteristics. I did not use `next_90d_revenue_amd` or `last_campaign_response` to create the groups; I checked these columns afterwards to help describe the groups.
6. Suggested one campaign idea and one KPI (a measure of success) for each group.

## Main findings

| Segment | Retail | Wholesale |
|---|---|---|
| Top group (Premium Active / Key Accounts) | 12% of customers, **50%** of 90-day revenue | 10% of customers, **58%** of 90-day revenue |
| Digital Core / Digital Mid-size | 49% of customers, **42%** of revenue, around 81% digital transactions | 48% of customers, **37%** of revenue, around 81% digital transactions |
| Passive / Low-Activity | 39% of customers, **8%** of revenue | 43% of customers, **5%** of revenue |

A few things stood out:

- The top group is relatively small but brings in about half of the revenue. Keeping these customers active is important.
- The digital group is another important source of revenue. Among Wholesale customers, this group had the highest response to previous campaigns (24.6%).
- The passive groups make up around 40% of customers but account for only 5–8% of revenue. Any campaign for these groups should be low-cost.

## Campaign ideas and KPIs

| Segment | Campaign idea | KPI (success measure) |
|---|---|---|
| Premium Active / Key Accounts | Personal contact and a service plan focused on keeping these customers | Customer retention rate; 90-day revenue per customer |
| Digital Core / Digital Mid-size | Offer related products through the banking app, with a simple sign-up process | Product activation rate; number of products per customer |
| Passive / Low-Activity | Encourage customers to make their first digital transaction, with a small incentive | Share of customers who make a digital transaction within 30 days |

These are ideas to test in a small pilot. The analysis does not prove that the campaigns will work.

## Limitations and choices

- **Why I used 3 groups:** The Silhouette Score was higher with 2 groups (Retail: 0.478; Wholesale: 0.563). With 3 groups, the score was around 0.33. I chose 3 groups on my mentor's advice because this split made it possible to identify a separate digital customer group and suggest a campaign for it.
- **The results are affected by customer size:** Some features are strongly skewed. A log transformation did not improve the Silhouette Score and changed the group assignments. This suggests that customer size still has an effect on the segments.
- **Past campaign response is only a description of previous results.** It does not guarantee that a new campaign will get the same response.
- The dataset contains 1,000 synthetic customers, so the results may differ from real bank data.

## Project files

- `customer_segmentation.ipynb` — the notebook with the analysis and saved outputs.
- `banking_customer_segmentation.csv` — the dataset used in the project.
- `requirements.txt` — the Python libraries needed to run the notebook.
- `customer_segmentation_presentation.pdf` — the presentation (in Armenian).

## How to run

```bash
pip install -r requirements.txt
jupyter notebook customer_segmentation.ipynb
```

Keep the CSV file in the same folder as the notebook.

## Tools used

Python, pandas, scikit-learn (`StandardScaler`, `K-Means`, and Silhouette Score), matplotlib, and seaborn.
