
# 💼 Dasara Sale 2025 — E-Commerce Offer Analysis Using SQL

## 🧭 Objective
This case study analyzes **Dasara Sale 2025** across India’s top e-commerce platforms — **Flipkart, Amazon, Meesho, Myntra, and IndiaMART** — to uncover patterns in **discounts, pricing, customer ratings, and delivery performance**.

The goal is to answer:
- Which platform offered the **highest discounts** during the sale?  
- How did **brands and categories** differ in their pricing strategies?  
- What **customer behavior trends** can be inferred from ratings and reviews?  
- How did **delivery time and availability** affect platform performance?

---

## 🧩 Dataset Overview
A **synthetic dataset of 1,000 records** was created to simulate real Dasara sale data.

| Column | Description |
|--------|--------------|
| Platform | E-commerce platform (Flipkart, Amazon, Meesho, Myntra, IndiaMART) |
| Category | Product category (Electronics, Fashion, Beauty, etc.) |
| Brand | Product brand (Samsung, H&M, Lakme, etc.) |
| Original_Price | Price before discount |
| Sale_Price | Price during sale |
| Discount_Percentage | % discount offered |
| Rating | Average customer rating (1–5) |
| No_of_Reviews | Number of customer reviews |
| Stock_Status | Available / Out of Stock |
| Delivery_Time(Days) | Estimated delivery time |
| Sale_Period | Before Sale / During Dasara Sale |
| City | City where sale occurred |

---

## 🧮 SQL Analysis & Key Insights

### 1️⃣ Average Discount by Platform
```sql
SELECT Platform, ROUND(AVG(Discount_Percentage),2) AS Avg_Discount
FROM dasara_sales
WHERE Sale_Period = 'During Dasara Sale'
GROUP BY Platform
ORDER BY Avg_Discount DESC;
Insight:

## 🥇 Myntra led with an average 66% discount, followed by Meesho (59%) and Flipkart (55%).

IndiaMART offered minimal discounts (~18%), consistent with its B2B focus.
