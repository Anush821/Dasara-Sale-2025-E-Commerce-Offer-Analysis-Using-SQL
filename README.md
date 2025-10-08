
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

**Insight:**

-🥇 Myntra led with an average 57% discount, followed by Meesho (49%) and Flipkart (43.4%).

-IndiaMART offered minimal discounts (~16%), consistent with its B2B focus.

2️⃣ Top 5 Brands with Highest Discounts
SELECT Brand, ROUND(AVG(Discount_Percentage),2) AS Avg_Discount
FROM dasara_sales
WHERE Sale_Period = 'During Dasara Sale'
GROUP BY Brand
ORDER BY Avg_Discount DESC
LIMIT 5;


**Insight:**

Fashion Brands like Lakme offered the deepest discounts 46% ,while electronic brands manintained moderate ones (40–45%)

3️⃣ Category-Wise Discount Analysis
SELECT Category, ROUND(AVG(Discount_Percentage),2) AS Avg_Discount
FROM dasara_sales
GROUP BY Category
ORDER BY Avg_Discount DESC;

** Insight:**

- Fashion and Beauty had the highest discount intensity (50–60%).

- Industrial/Wholesale categories had limited offers (~15%).

4️⃣ Rating vs Discount Correlation check
SELECT Platform, ROUND(AVG(Rating),2) AS Avg_Rating,
ROUND(AVG(Discount_Percentage),2) AS Avg_Discount
FROM dasara_sales
WHERE Sale_Period = 'During Dasara Sale'
GROUP BY Platform
ORDER BY AVG_discount DESC;


**Insight:**

- Platforms with moderate discounts (40–60%) such as Flipkart and Myntra recorded higher ratings (~4).
- Extremely high discounts correlated with slightly lower ratings (~3.6).

5️⃣ Before vs During Sale Comparison
SELECT Platform,
ROUND(AVG(CASE WHEN Sale_Period='Before Sale' THEN Discount_Percentage END),2) AS Avg_Before_Sale,
ROUND(AVG(CASE WHEN Sale_Period='During Dasara Sale' THEN Discount_Percentage END),2) AS Avg_During_Sale
FROM dasara_sales
GROUP BY Platform;


**Insight:**
Discounts jumped from an average of 55% before sale to 57% during Dasara — with Myntra showing the sharpest increase .

6️⃣ Delivery & Availability Analysis
SELECT Platform, ROUND(AVG(Delivery_Time_Days),2) AS Avg_Delivery,
SUM(CASE WHEN Stock_Status='Available' THEN 1 ELSE 0 END)*100.0/COUNT(*) AS Availability_Rate
FROM dasara_sales
GROUP BY Platform;


**Insight:**

- Amazon had the fastest delivery (3.1 days) and highest stock availability (50%).

- IndiaMART and Myntra had slower delivery times (5–6 days).

7️⃣ Top Cities by Discount Level
SELECT City, ROUND(AVG(Discount_Percentage),2) AS Avg_Discount
FROM dasara_sales
WHERE Sale_Period='During Dasara Sale'
GROUP BY City
ORDER BY Avg_Discount DESC
LIMIT 10;


**Insight:**

Tier-2 cities like Ahmedabad, Pune, and Kolkata received higher discounts (40%+) than metro cities.
```

## 📈 Business Summary

|Area |	Key Insight|
|-----|------------|
|Top Platform	| Myntra (highest discount, fashion-led strategy)|
|Top Category	|Fashion & Beauty (deepest discounts)|
|Customer Behavior|	Moderate discounts yield higher satisfaction|
|Operational Strength	|Amazon dominates logistics & availability|
|Regional Strategy	|Tier-2 cities targeted with aggressive pricing|

## 🧠 Recommendations

  1. **Balance discount depth** to maintain value perception.

  2. **Improve delivery speed** for fashion marketplaces.

  3. **Capitalize on Tier-2 growth** with regional marketing.

  4. **Combine discounts with loyalty rewards** for long-term retention.

 5. **Use post-sale analytics** for demand forecasting and inventory control.

## 🛠️ Tools & Skills

**SQL**: Aggregations, subqueries, conditional logic

**Data Cleaning**: Handling sale periods and discount calculations

**Business Intelligence**: Translating raw data into insights

**Visualization (optional)**: Power BI / Excel Dashboard

## 🏁 Conclusion

This SQL-based case study demonstrates how data analytics can reveal key performance insights from festive sale events.
By analyzing discount strategies, ratings, and logistics, we can better understand how different e-commerce platforms drive customer engagement and revenue during the festive season.

## 📂 Dataset

You can download the dataset used here:

👉 [Dasara_Sale_Offers_2025.csv](https://drive.google.com/file/d/1mTfKZsgOI5Gf9GOqGcqvxb8FiDkpH4zA/view?usp=sharing)

**Created by: Anusha**

**Role Targeted: Data Analyst / Business Analyst**

**Tools: SQL, Power BI, Excel**

**Focus Area: E-Commerce, Retail Analytics, Pricing Insights**
