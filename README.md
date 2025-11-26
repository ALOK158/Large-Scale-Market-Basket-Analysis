# 🛒 Market Basket Analysis: Optimizing Retail Strategy
[![Kaggle](https://img.shields.io/badge/Kaggle-View_Notebook-blue?logo=kaggle&logoColor=white)](https://www.kaggle.com/code/alok158/large-scale-market-basket-analysis?scriptVersionId=281885544)
![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![Library](https://img.shields.io/badge/Library-Mlxtend-orange)
![Status](https://img.shields.io/badge/Status-Completed-green)

## 📌 Executive Summary
In the competitive retail landscape, increasing the **Average Order Value (AOV)** is cheaper than acquiring new customers. 

This project analyzes **500,000+ transactional records** from an online retailer to uncover hidden product relationships. By implementing the **Apriori Algorithm** and optimizing for memory efficiency, I identified high-confidence cross-selling opportunities to drive product bundling strategies.

## 🔍 The Business Problem
**The Goal:** Move beyond simple "Top Sellers" and understand *purchasing patterns*.
* Which products are frequently bought together?
* How can we optimize store layout or website recommendations to trigger impulse buys?
* **Technical Challenge:** The dataset contains sparse transactional data which causes memory errors with standard processing. I implemented boolean sparse matrix optimizations to handle the scale.

---

## 📊 Strategic Insights & Visuals

### 1. Global Best Sellers (Volume)
*Understanding the "Anchors" of our catalog.*

![Top Selling Products](https://github.com/user-attachments/assets/43d13a27-0113-4bcf-b6c4-02c0f2bbb46e)

**Insight:** The "Paper Craft, Little Birdie" and "Medium Ceramic Top Storage Jar" are the highest volume drivers. These serve as the entry point for many customers.

### 2. Association Rules Heatmap (Lift)
*The "Treasure Map" for cross-selling. Darker blue = Stronger relationship.*

![Heatmap](https://github.com/user-attachments/assets/fb87ce62-63cc-46d7-847f-70b1fa162449)

**Key Finding:** The heatmap reveals distinct "product clusters." Specifically, customers don't just buy "Cups"; they buy specific *patterns* of Cups, Plates, and Napkins.

---

## 🎯 Actionable Recommendations

Based on the Association Rules generated (Min Support: 0.07, Metric: Lift), here is the top strategic finding:

| Antecedent (If they buy...) | Consequent (They also buy...) | Confidence | Lift | Strategy |
| :--- | :--- | :---: | :---: | :--- |
| **Red Spotty Paper Cups** | **Red Spotty Paper Plates** | **97.5%** | **7.49** | **Bundle It.** Virtually no one buys the cups without the plates. Create a "Red Party Pack" to simplify the user journey. |
| **Alarm Clock (Green)** | **Alarm Clock (Red)** | **83.7%** | **8.46** | **Cross-Sell.** Users buying one color often want the variant. Add "Also available in Red" on the checkout page. |

## 🛠️ Technical Implementation
### The Optimization
Running Association Rule mining on 500k rows often crashes standard RAM.
* **Solution:** I implemented **One-Hot Encoding with Boolean mapping**.
* Instead of storing quantities (int64), I converted the basket to sparse boolean values (True/False).
* **Result:** Reduced memory usage significantly, allowing the Apriori algorithm to converge in seconds.

### Tech Stack
* **Python:** Core logic.
* **Pandas:** Data manipulation and boolean indexing.
* **Mlxtend:** Implementation of Apriori and Association Rules.
* **Seaborn/Matplotlib:** Heatmaps and distribution visualization.

## 🚀 How to Run
1. Clone the repository.
2. Install dependencies:
   ```bash
   pip install pandas matplotlib seaborn mlxtend openpyxl
