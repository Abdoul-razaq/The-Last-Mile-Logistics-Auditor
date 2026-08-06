#  The Last Mile Logistics Auditor

## 🧠 Executive Summary

This project analyzes delivery performance and customer sentiment for Veridi Logistics using the Olist Brazilian E-Commerce dataset, spanning nearly 100,000 orders. The goal was to investigate whether negative customer reviews are driven primarily by delivery delays, or by something less obvious: unreliable delivery estimates. The analysis confirms that late deliveries do damage satisfaction — but the deeper issue is a mismatch between what customers are promised and what actually happens. Delays are also not evenly spread across the business: specific regions and product categories carry disproportionately higher failure rates, giving Veridi a clear starting point for operational fixes rather than a vague "improve logistics" mandate.

---

## 🔗 Project Links

| Deliverable | Link |
|---|---|
| 📓 Analysis Notebook (Google Colab / .ipynb) | [View Notebook](https://drive.google.com/file/d/1m7_BFeaHgN1dozPryo0K1nsFxqfq8qC0/view?usp=drive_link) |
| 📄 Notebook Export (PDF) | [View PDF](https://drive.google.com/file/d/10i4XMBFu7GohhA1z1jdKtQrRasG99WER/view?usp=drive_link) |
| 🎥 Presentation (Slides) | [View Presentation](https://docs.google.com/presentation/d/1ug_8JQ5pFgAFLhhHIjHDNSN-TCcu7G_x/edit?usp=sharing&ouid=116576799155137922183&rtpof=true&sd=true) |

---

##  Business Context

Veridi Logistics needed to answer a specific operational question: when customers leave negative reviews, is it *actually* because their delivery was late — or is something else at play? Treating every late order as an equivalent failure risks fixing the wrong problem. Before recommending any operational change, the data needed to show not just *that* satisfaction was suffering, but *where* the failures were concentrated and *why* they were translating into dissatisfaction at the rate they were.

---

##  Technical Explanation

### Data Integration (Schema Building)

The Olist dataset is split across multiple relational tables. To build a single analyzable view:

- Joined `orders`, `reviews`, and `customers` datasets
- Linked orders to reviews via `order_id`, and customers to orders via `customer_id`
- Audited the join for unintended row multiplication — an initial merge surfaced **551 duplicate order IDs**, which were identified and removed before any delivery metric was calculated, to avoid inflating counts or skewing the sentiment analysis

This produced a clean **master dataset of 99,441 orders**, combining delivery performance and customer sentiment in one table.

### Data Cleaning

- Removed the 551 duplicate order records found during the join
- Dropped orders with no recorded delivery date, since delivery-status classification depends on it
- Converted all date fields to proper datetime format for accurate day-difference calculations
- Verified consistency across the merged tables before proceeding to analysis

### Delivery Delay Calculation

A `Days_Difference` field (estimated delivery date minus actual delivery date) was calculated for every order and used to classify delivery performance into three tiers:

- **On Time** → delivered on or before the estimated date
- **Late** → delivered after the estimated date, by less than 5 days
- **Super Late** → delivered more than 5 days after the estimated date

This produced a clean, comparable performance label for every one of the 99,441 orders.

### Candidate's Choice (Added Value)

Beyond the core brief, an additional layer of analysis broke down delivery performance **by product category**.

**Why this matters:** logistical complexity isn't uniform across a product catalog. Bulky items like furniture carry different delivery risk than small electronics or everyday goods. Surfacing category-level failure rates lets Veridi prioritize operational fixes by product type, not just by region.

---

##  Key Insights

Across the cleaned dataset of 99,441 orders:

- **88,649 orders (89.2%)** were delivered On Time
- **3,162 orders (3.2%)** were Late
- **4,665 orders (4.7%)** were Super Late

**Delivery delays are not evenly distributed geographically.** The worst-performing states by late-delivery rate were:

| State | Late Delivery Rate |
|---|---|
| Alagoas (AL) | 23.9% |
| Maranhão (MA) | 19.7% |
| Piauí (PI) | 16.0% |
| Ceará (CE) | 15.3% |
| Sergipe (SE) | 15.2% |

This concentration in Brazil's North/Northeast states points to a regional logistics issue rather than a systemic, nationwide one.

**Delivery delays are not evenly distributed by product category either.** The highest late-delivery rates were found in:

| Category | Late Delivery Rate |
|---|---|
| Home Comfort (2) | 16.7% |
| Furniture, Mattress & Upholstery | 13.5% |
| Audio | 12.7% |
| Fashion Underwear & Beach | 12.6% |
| Christmas Supplies | 12.0% |

Bulkier, less time-sensitive categories cluster at the top — consistent with the hypothesis that logistical complexity, not just distance, drives delay risk.

---

##  Sentiment Correlation

The relationship between delivery performance and customer review score is direct and severe:

| Delivery Status | Average Review Score |
|---|---|
| On Time | **4.29 / 5** |
| Late | **3.59 / 5** |
| Super Late | **1.85 / 5** |

A Super Late delivery doesn't just lower satisfaction incrementally — it collapses it. The drop from Late (3.59) to Super Late (1.85) is far steeper than the drop from On Time to Late, indicating a tipping point where customer patience runs out and dissatisfaction becomes severe rather than mild.

---

##  Root Cause Insight

> The core issue is not simply that deliveries are late — it's that a meaningful share of orders fall into a "Super Late" tier where satisfaction doesn't just dip, it collapses.

This reframes the operational priority: rather than treating all lateness equally, Veridi should focus first on eliminating the conditions that produce Super Late outcomes specifically, since that tier is disproportionately responsible for the sentiment damage.

---

##  Final Recommendations

- Prioritize eliminating **Super Late** deliveries first — this tier does the most damage to customer sentiment per order, more than proportionally
- Focus regional operational review on **Alagoas, Maranhão, and Piauí**, where late-delivery rates are highest
- Audit fulfillment processes for **Home Comfort, Furniture, and Audio** categories, which show the highest delivery-risk profiles
- Use the On Time / Late / Super Late framework as a standing operational KPI, not a one-time analysis
- Investigate whether estimated delivery dates for high-risk regions and categories should be adjusted to better reflect real fulfillment timelines

---

##  Project Value

This project demonstrates the ability to:

- Catch and correct a data integrity issue (duplicate records) before it could distort business conclusions
- Convert a general sentiment problem into a specific, prioritized operational plan by segmenting across region and category
- Quantify exactly how much a service failure costs in customer sentiment, rather than stating that it "matters"
- Translate a large multi-table relational dataset into a single clean, decision-ready master table
