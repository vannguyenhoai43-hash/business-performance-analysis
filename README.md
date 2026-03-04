# Quarterly Shop Business Performance Analysis

Read in: **English** | [Tiếng Việt](README_VI.MD)

---

## 1. Project Overview

This project focuses on analyzing a shop’s quarterly business performance on an e-commerce platform,  
aiming to support shop owners in optimizing revenue and marketing costs.

The dashboard is built using **dynamic Parameters** in Power BI, allowing users to switch shop codes and automatically refresh the entire dataset with a single action. This enables efficient management of multiple shops within the same report.

- **Target users:** Shop owners  
- **Industry:** Automotive Accessories  
- **Analysis objectives:**  
  - Evaluate overall business performance  
  - Optimize costs and assess advertising risks  
  - Analyze operational performance on campaign days: Spike & Mini Spike  
  - Evaluate performance by sales channel and product  
  - Understand customer purchasing behavior  

---

## 2. Tools & Techniques

- **Power BI:** Data modeling, DAX measures, interactive dashboards  
- **SQL:** Query processing and calculations for Cohort analysis visualization [View here](sql/cohort_analysis)  
- **Power Query (M):** ETL processing, data transformation & dynamic Parameter setup  
- **Canva:** Insight report design in A4 format  

---

## 3. Data Processing & ETL

Input data is organized by business function and separated by month.  
Each data group consists of multiple Excel files, which are automatically consolidated in Power BI  
to enable quarterly and yearly analysis.

Main data groups include:

- Daily operational performance  
- Paid Ads  
- Product data  
- Customer data  

Power Query is used for:

- Merging multi-month datasets  
- Standardizing formats  
- Removing invalid rows  

A dynamic Parameter system is designed to allow switching shop codes with a single action.  
When selecting a different shop, the entire dataset and dashboard update automatically,  
enabling performance management and comparison across multiple shops within one unified report.

![Input Data](image/project_flow.png)

---

## 4. Analytical Dashboard

![Dashboard](image/Gif_DB.gif)

### Main dashboard pages:

1. **Overview:** Overall business health metrics of the shop  
2. **Paid Ads:** Conversion funnel, ROAS by channel, and advertising cost by product  
3. **Campaign Day:** Sales performance during Spike and Mini Spike events  
4. **Product:** Sales performance of each product across channels  
5. **Buyer:** Purchase frequency, key customer segments, and retention rate  

<details>
  <summary> View detailed dashboard screenshots</summary>

  ![Overview](image/dashboard_Overview.png)  
  ![Paid Ads](image/dashboard_PaidAds.png)  
  ![Campaign Day](image/dashboard_Campaign.png)  
  ![Product](image/dashboard_Product.png)  
  ![Buyer](image/dashboard_Buyer.png)

</details>

---

## 5. Insights & Action Plan

In addition to the interactive dashboard, the project provides an A4-formatted insight report  
to support strategic meetings and decision-making.

**Key insights:**  

- **Growth:** Revenue and average order value increased steadily, with strong conversion rates.  
- **Advertising:** Performance declined before and after campaign days; bottleneck identified at the “Add to Cart” stage.  
- **Channels & Products:** Livestream is the most effective channel; the “Sunshade Cover” product delivers the highest ROAS.  
- **Campaigns:** Spike Day outperformed Mini Spike.  
- **Customers:** Mostly new customers, with a low repeat rate; males aged 25–54 represent the key customer segment.  

**Action plan:**  

- Increase advertising budget on Spike Day and Livestream sessions.  
- Prioritize core products in three high-potential provinces: Da Nang, Hai Phong, and Dong Nai.  
- Increase Livestream frequency and optimize video content.  
- Stimulate demand with vouchers and promotional messages before/after campaign days.  
- Focus on male customers aged 25–54 and strengthen post-purchase engagement strategies.  

👉 [View full insight report](https://www.canva.com/design/DAG9s3TrI1E/cRN25avmiY0nkDxe0fObDw/view?utm_content=DAG9s3TrI1E&utm_campaign=designshare&utm_medium=link2&utm_source=uniquelinks&utlId=h3d8a1d75ec#1)

<details>
  <summary>📊 Insight report preview</summary>

<!-- COVER PAGE -->
<p align="center">
  <img src="image/pagebia.png" width="70%">
</p>

<!-- ROW 1 -->
<p align="center">
  <img src="image/page1.png" width="23%">
  <img src="image/page2.png" width="23%">
  <img src="image/page3.png" width="23%">
  <img src="image/page4.png" width="23%">
</p>

<!-- ROW 2 -->
<p align="center">
  <img src="image/page5.png" width="23%">
  <img src="image/page6.png" width="23%">
  <img src="image/page7.png" width="23%">
  <img src="image/page8.png" width="23%">
</p>

<!-- ROW 3 -->
<p align="center">
  <img src="image/page9.png" width="23%">
  <img src="image/page10.png" width="23%">
</p>

</details>

---

## 6. Results Achieved

- Reduced manual reporting time from 4 hours to under 5 minutes using the dynamic Parameter mechanism  
- Identified the product group contributing ~60% of total profit to prioritize marketing investment  
