# Quarterly E-commerce Shop Performance Diagnosis

Read in: **English** | [Tiếng Việt](README_VI.MD)

---

## Project Overview

**Revenue growth alone is not enough to judge whether a shop is performing well.** A shop can grow sales while still leaking ad efficiency, over-relying on a few products or channels, and failing to convert new buyers into repeat customers.

This project builds a **quarterly business performance dashboard** for e-commerce shop review, designed to diagnose performance across **revenue, advertising, campaigns, products, channels, and customer behavior**.

Using **Power BI**, **Power Query**, and **SQL**, I built a reusable workflow that consolidates fragmented monthly files, prepares cohort logic, and allows the same dashboard structure to refresh across **multiple shops within one reporting structure** through a **shop-code parameter**. The goal is not just to visualize performance, but to make recurring business review faster, more consistent, and more actionable.

---

## Dataset

The dashboard consolidates monthly Excel files across a **quarterly reporting window (Jul–Sep 2025)** into one reusable reporting model.

Main source groups include:

- **Daily operational data**
- **Paid Ads data**
- **Product-level data**
- **Customer-level data**

Key analytical grains include:

- **daily performance level**
- **product level**
- **customer level**
- **campaign-day level**

The reporting model is designed for **multi-shop reuse** through a **shop-code parameter**, so the same dashboard structure can be refreshed across different shops without rebuilding separate reports.

---

## What I Built

- Built a **Power BI dashboard** covering business health, ads, campaigns, products, and buyers
- Built a **reusable shop-code parameter** so the same dashboard structure can refresh across different shops without rebuilding separate reports
- Used **Power Query** to merge monthly files with matching schemas into one reporting model
- Used **SQL** to prepare **first-purchase cohort tables** for retention-style visualization
- Designed a lightweight **insight summary** for business review and action planning

---

## Analytical Logic

The dashboard is structured around five analytical lenses:

### 1. Business Health
Used **orders, revenue, ad spend, AOV, and conversion rate** to assess whether topline growth came with stronger efficiency.

![Overview](image/dashboard_Overview.png)

### 2. Advertising Efficiency
Used **ROAS, cost per order, conversion funnel drop-off, and product-level ad contribution** to identify where ad spend was converting well and where it was leaking.

![Paid Ads](image/dashboard_PaidAds.png)

### 3. Campaign Effectiveness
Compared **Mini Spike vs Spike Day** using **orders, revenue, ad spend, AOV, and ROAS** to evaluate which campaign window produced better return.

![Campaign Day](image/dashboard_Campaign.png)

### 4. Product and Channel Contribution
Measured **revenue concentration, ROAS by product, and channel mix** to identify the **highest-return product-channel combinations**.

![Product](image/dashboard_Product.png)

### 5. Customer Retention Pattern
Used **buyer growth, order frequency, and cohort retention** to evaluate whether growth was driven mainly by **new-buyer acquisition** or supported by **repeat purchase behavior**.

![Buyer](image/dashboard_Buyer.png)
---

## Data Preparation Logic

A key challenge in this project was turning fragmented monthly files into a model that could support recurring business review.

### Power Query
I used **Power Query (M)** to:

- merge files across months
- align datasets with the same structure
- standardize column formats
- remove invalid rows
- create one reusable reporting layer across functions

This made it possible to combine scattered monthly files into one dashboard model instead of maintaining separate files for each month or business function.

### Dynamic Parameter Design
I built a **shop-code parameter** so the same dashboard could be reused across multiple shops.

Instead of rebuilding separate reports or manually replacing source files, users can change the shop code once and refresh the full dataset under the same analytical structure. This turns the dashboard from a one-off report into a **scalable reporting template**.

![Demo parameter](image/Gif_DB.gif)

### SQL for Cohort Analysis
I used **SQL** to prepare **first-purchase cohort tables** for retention-style visualization, making it easier to track repeat purchase behavior over time instead of relying only on aggregate buyer counts. [SQL_Cohort](sql/cohort_analysis)

---

## Key Findings

- The shop recorded **10.32K orders**, **$60.33K revenue**, and **7.15% conversion rate** in the quarter, while **AOV reached $5.84**. Revenue grew **+3.65% QoQ** while ad spend stayed nearly flat at **$5.59K (-0.18%)**, suggesting topline growth improved without a matching increase in paid spend.

- Advertising efficiency was uneven. Although **ROAS reached 9.01**, the biggest funnel drop happened at **Click → Add to Cart (-77.70%)**, showing that the main priority should be improving deeper-funnel conversion rather than just driving more traffic.

- **Livestream** was the strongest-performing paid channel, with ROAS rising from **7.84** in July to **8.79** in September. At product level, **Sunshade Cover** delivered the highest **ROAS at 13.32**, making this the clearest channel-product combination to scale.

- **Spike Day** outperformed **Mini Spike** with **ROAS 9.43 vs 8.69**, despite lower ad spend share (**39.07% vs 60.93%**), suggesting budget should be concentrated more heavily on Spike Day.

- Growth remained acquisition-led. Out of **9.54K buyers**, **8.59K were new buyers**, while average order frequency was only **1.08** and median cohort retention fell from **5.49% (week 2)** to **4.09% (week 6)**, indicating the need for stronger post-purchase retention efforts.


---

## Scope & Limitation

This project is designed for **business diagnosis and recurring performance review**, not forecasting or causal experimentation.

Its strength lies in identifying **patterns, bottlenecks, concentration risk, and action priorities** from quarterly shop, ads, product, and customer data. Cohort analysis is included to support repeat-purchase reading, but long-term retention conclusions remain limited by the available historical window.

---

## Deliverables

- **Power BI dashboard** with 5 analytical pages
- **Dynamic parameter setup** for multi-shop refresh
- **SQL cohort logic** for repeat purchase visualization
- **Insight summary report** for business review

---

## Results

- Reduced manual reporting time from **4 hours to under 5 minutes** through the dynamic parameter setup
- Built a reusable reporting structure that can refresh across **multiple shops** without rebuilding separate dashboards
- Identified a product group contributing around **60% of total profit**, supporting more focused marketing investment
