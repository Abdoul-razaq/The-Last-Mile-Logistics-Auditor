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

A key metric was created:
