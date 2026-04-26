# The-Last-Mile-Logistics-Auditor
The Last Mile Logistics Auditor
# 🚚 The Last Mile Logistics Auditor

## 🧠 Executive Summary

This project analyzes delivery performance and customer sentiment for Veridi Logistics using the Olist E-Commerce dataset. The goal was to investigate whether negative customer reviews are driven by delivery delays or inaccurate delivery estimates. The analysis reveals that while late deliveries do impact satisfaction, the core issue lies in unreliable delivery promises, leading to a mismatch between customer expectations and actual performance. Additionally, delays are not uniformly distributed, with certain regions and product categories experiencing higher failure rates.

---

## 🔗 Project Links

- 📊 **Dashboard (Power BI):**  
  [View Dashboard](https://drive.google.com/file/d/1aUU3FM7V16dv3THmVqBJEYeBATCXSYHH/view?usp=drive_link)

- 📓 **Notebook (Google Colab / .ipynb):**  
  [View Notebook](https://drive.google.com/file/d/1m7_BFeaHgN1dozPryo0K1nsFxqfq8qC0/view?usp=drive_link)

- 📄 **Notebook Export (PDF):**  
  [View PDF](https://drive.google.com/file/d/10i4XMBFu7GohhA1z1jdKtQrRasG99WER/view?usp=drive_link)

- 🎥 **Presentation (Slides):**  
  [View Presentation](https://docs.google.com/presentation/d/1ug_8JQ5pFgAFLhhHIjHDNSN-TCcu7G_x/edit?usp=sharing&ouid=116576799155137922183&rtpof=true&sd=true)

---

## 🧹 Technical Explanation

### Data Integration (Schema Building)

The Olist dataset consists of multiple relational tables. To enable analysis:

- Joined `orders`, `reviews`, and `customers` datasets
- Used:
  - `order_id` → link orders and reviews  
  - `customer_id` → link customers and orders  
- Ensured no duplication during joins (avoiding 1-to-many errors)

This resulted in a **master dataset** combining delivery performance and customer sentiment.

---

### Data Cleaning

- Removed canceled and unavailable orders
- Handled missing delivery dates
- Converted date columns to proper datetime format
- Ensured consistency across merged tables

---

### Delivery Delay Calculation

Orders were classified into:

- **On Time** → Delivered on or before estimated date  
- **Late** → Delivered after estimated date  
- **Super Late** → More than 5 days late  

This allowed clear segmentation of delivery performance.

---

### Candidate’s Choice (Added Value)

An additional analysis was introduced to evaluate **delivery performance by product category**.

#### Why this matters:
Different products have different logistical complexity. For example:
- Large items (e.g., furniture) may experience more delays  
- Smaller items (e.g., electronics) may be delivered faster  

This insight helps prioritize operational improvements by product type.

---

## 📊 Key Insights

- Average customer review score: **~4.08**
- Late and super-late deliveries significantly reduce customer satisfaction
- Delivery delays are **not evenly distributed geographically**
- Certain regions experience higher rates of late deliveries
- Some product categories show higher delivery risk than others

---

## 🌍 Geographic Insight

The analysis shows that delivery performance varies by region:

- Some states have a higher concentration of late deliveries  
- This suggests logistical inefficiencies are **region-specific, not nationwide**

---

## 💬 Sentiment Correlation

There is a clear relationship between delivery performance and customer reviews:

- **On-time deliveries → Higher ratings**
- **Late deliveries → Lower ratings**
- **Super-late deliveries → Significant drop in satisfaction**

This confirms that logistics performance directly impacts customer experience.

---

## 💡 Root Cause Insight

> The primary issue is not just delivery delays, but inaccurate delivery estimates.

Customers are often given unrealistic expectations, leading to dissatisfaction even when delays are small.

---

## 🚀 Final Recommendations

- Improve delivery time prediction models  
- Set more realistic estimated delivery dates  
- Focus operational improvements on worst-performing regions  
- Monitor high-risk product categories  
- Align logistics performance with customer expectations  

---

## 📈 Project Value

This project demonstrates how data analytics can:

- Identify operational inefficiencies  
- Link logistics performance to customer sentiment  
- Provide actionable insights for business improvement  
- Support data-driven decision-making in supply chain management  

A key metric was created:
