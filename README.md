<div align="center">

# 📈 ShopEasy Marketing Analytics
### Power BI · SQL · Python · Sentiment Analysis

**Diagnosing declining engagement and conversion for an online retailer — from raw data to an executive-ready story.**

![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![SQL](https://img.shields.io/badge/SQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![DAX](https://img.shields.io/badge/DAX-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/mutyaba-sulah-525510203/)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/maka971)

</div>

---

## 📑 Table of Contents

- [📸 Dashboard Preview](#-dashboard-preview)
- [🧭 Overview](#-overview)
- [🧩 Business Case](#-business-case)
- [🎯 Business Objective](#-business-objective)
- [🛠️ Tools & Technologies](#️-tools--technologies)
- [🔁 Project Workflow](#-project-workflow)
- [🗺️ Data Model](#️-data-model)
- [📊 Dashboard Pages](#-dashboard-pages)
- [🔍 Key Findings](#-key-findings)
- [🎯 Goals & Recommended Actions](#-goals--recommended-actions)
- [📌 Business Impact](#-business-impact)
- [🔮 Future Improvements](#-future-improvements)
- [📁 Project Structure](#-project-structure)
- [🚀 Getting Started](#-getting-started)
- [👨‍💻 About the Author](#-about-the-author)

---

## 📸 Dashboard Preview

<div align="center">

| Overview | Conversion Details |
|:---:|:---:|
| ![Overview](marketing-images/overview-dashboard.png) | ![Conversion Details](marketing-images/conversion-details.png) |

| Social Media Details | Customer Review Details |
|:---:|:---:|
| ![Social Media Details](marketing-images/social-media-details.png) | ![Customer Review Details](marketing-images/customer-review-details.png) |

</div>

> A quick look at the four-page Power BI report before diving into the full write-up below. Page-by-page breakdowns are in the [Dashboard Pages](#-dashboard-pages) section.

---

## 🧭 Overview

This project is an end-to-end marketing analytics solution built for **ShopEasy**, a fictional online retail business, using **SQL**, **Python**, and **Power BI**. It walks through the full analytics lifecycle — from business case intake, through data modeling and sentiment enrichment, to an interactive dashboard and an executive presentation with recommended actions.

### ✨ Project Highlights

- 🧱 Modeled a **star schema** connecting customer journeys, engagement, reviews, products, customers, and a custom date table
- 🐍 Used **Python** to enrich raw customer reviews with **sentiment scores and categories** before loading them into the model
- 📐 Built a custom **Calendar DAX table** (2023–2025) to support time-intelligence across the whole report
- 🗺️ Delivered a **4-page Power BI report** — Overview, Conversion Details, Social Media Details, Customer Review Details
- 🖥️ Packaged the findings into a **stakeholder-ready PowerPoint** with goals, actions, and supporting visuals

### 🧠 Skills Demonstrated

`SQL (Data Extraction & Staging)` · `Python (Data Cleaning & Sentiment Analysis)` · `Power Query (ETL)` · `DAX` · `Star Schema Design` · `Data Storytelling` · `Executive Reporting` · `Stakeholder Communication`

---

## 🧩 Business Case

> The following business case initiated this project:

---

**Client:** ShopEasy (Online Retail Business)

ShopEasy is facing **reduced customer engagement** and **conversion rates** despite launching several new online marketing campaigns. They reached out to conduct a detailed analysis and identify areas for improvement in their marketing strategies.

### Key Points

- 📉 **Reduced Customer Engagement** — The number of customer interactions and engagement with the site and marketing content has declined.
- 📉 **Decreased Conversion Rates** — Fewer site visitors are converting into paying customers.
- 💸 **High Marketing Expenses** — Significant investments in marketing campaigns are not yielding expected returns.
- 💬 **Need for Customer Feedback Analysis** — Understanding customer opinions about products and services is crucial for improving engagement and conversions.

---

## 🎯 Business Objective

Give the marketing and leadership teams a single source of truth to answer:

- What does the customer journey look like — and where do people drop off before purchasing?
- How is social media / content engagement trending, and which content types perform best?
- What are customers saying in their reviews, and how does sentiment relate to ratings over time?
- Which products convert best, and which months need marketing attention?

---

## 🛠️ Tools & Technologies

![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![SQL](https://img.shields.io/badge/SQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![DAX](https://img.shields.io/badge/DAX-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![PowerPoint](https://img.shields.io/badge/PowerPoint-B7472A?style=for-the-badge&logo=microsoftpowerpoint&logoColor=white)

---

## 🔁 Project Workflow

The project was built in five stages, each documented in the repository:

| Stage | Deliverable | Description |
|-------|-------------|-------------|
| **1. Business Case** | `Stage 1-Marketing_Analytics_Business_Case.pdf` | Business problem, goals, and stakeholder requirements |
| **2. Data Staging (SQL)** | `dim_customers.sql`, `dim_products.sql`, `fact_customer_reviews.sql`, `fact_engagement_data.sql`, `fact_customer_journey.sql` | Extracted and structured raw data into dimension and fact tables |
| **3. Sentiment Enrichment (Python)** | `customer_reviews_enriched`, `fact_customer_reviews_with_sentiment.sql` | Cleaned review text and generated sentiment scores/categories in Python before reloading to SQL |
| **4. Modeling & Dashboard (Power BI)** | `Calendar DAX Script.txt`, `Dashboard powerbi.pbix` | Built the star-schema model, DAX calendar table, and the 4-page interactive report |
| **5. Executive Presentation** | `Presentation.pptx` | Summarized findings into goals, actions, and next steps for stakeholders |

<details>
<summary><strong>📅 Calendar DAX Script (click to expand)</strong></summary>

```dax
Calendar =
ADDCOLUMNS (
    CALENDAR ( DATE ( 2023, 1, 1 ), DATE ( 2025, 12, 31 ) ),
    "DateAsInteger", FORMAT ( [Date], "YYYYMMDD" ),
    "Year", YEAR ( [Date] ),
    "Monthnumber", FORMAT ( [Date], "MM" ),
    "YearMonthnumber", FORMAT ( [Date], "YYYY/MM" ),
    "YearMonthShort", FORMAT ( [Date], "YYYY/mmm" ),
    "MonthNameShort", FORMAT ( [Date], "mmm" ),
    "MonthNameLong", FORMAT ( [Date], "mmmm" ),
    "DayOfWeekNumber", WEEKDAY ( [Date] ),
    "DayOfWeek", FORMAT ( [Date], "dddd" ),
    "DayOfWeekShort", FORMAT ( [Date], "ddd" ),
    "Quarter", "Q" & FORMAT ( [Date], "Q" ),
    "YearQuarter",
        FORMAT ( [Date], "YYYY" ) & "/Q"
            & FORMAT ( [Date], "Q" )
)
```

</details>

---

## 🗺️ Data Model

The report is built on a **star schema** with three fact tables (`fact_customer_journey`, `fact_engagement`, `fact_customer_reviews_with_sentiment`) connected to shared dimensions (`dim_customers`, `dim_products`, `Calendar`), plus a `_Calculations` table for standalone DAX measures.

![Data Model](marketing-images/data-model.png)
*Star schema linking customer journey, engagement, and sentiment-enriched review data to customer, product, and calendar dimensions.*

---

## 📊 Dashboard Pages

### 🗂️ Overview

![Overview](marketing-images/overview-dashboard.png)
*High-level view of Conversion, Social Media, and Customer Review performance for the selected year — filterable by product.*

- Conversion Rate KPI + trend by month and by product
- Views, Clicks & Likes KPI cards + monthly trend
- Average Rating KPI + trend by month and by product

### 🔄 Conversion Details

![Conversion Details](marketing-images/conversion-details.png)
*Funnel view of the customer journey from View → Click → Drop-off → Purchase, with conversion rate broken down by month and product.*

- Customer Journeys by Action (funnel: View, Click, Drop-off, Purchase)
- Conversion Rate trend by month
- Conversion Rate by Product (ranked)
- Full product × month conversion rate matrix

### 📱 Social Media Details

![Social Media Details](marketing-images/social-media-details.png)
*Engagement view tracking Views, Clicks, and Likes across time and content type (Blog, Social Media, Video).*

- Views, Clicks & Likes KPI cards
- Views/Clicks/Likes trend by month
- Views by month and content type
- Full product × month views matrix

### 💬 Customer Review Details

![Customer Review Details](marketing-images/customer-review-details.png)
*Deep dive into customer sentiment — rating distribution, sentiment category breakdown, and a searchable review log.*

- Average Rating KPI
- Number of Reviews by Star Rating (1–5)
- Number of Reviews by Sentiment Category (Positive, Neutral, Mixed Positive/Negative, Negative)
- Rating trend by month, split by sentiment
- Rating vs. Review Volume scatter plot
- Full customer review log (date, customer, review text, sentiment, rating)

---

## 🔍 Key Findings

### 1. 📉 Decreased Conversion Rates
Conversion demonstrated a strong **rebound in December, reaching 10.2%**, despite a notable dip to **5.0% in October**. Across the year, **January recorded the highest overall conversion rate at 18.5%**, driven significantly by Ski Boots at a remarkable 150% conversion — likely fueled by seasonal demand. **May was the lowest month at 4.3%**, with no single product standing out, suggesting a need to revisit marketing or promotions during that period.

### 2. 👥 Reduced Customer Engagement
Views peaked in **February and July** but declined steadily from **August onward**, indicating reduced audience engagement in the second half of the year. Clicks and likes remained consistently low relative to views — although the click-through rate of **15.37%** shows that engaged users are still interacting effectively once reached. **Blog content drove the most views**, especially in April and July, while social media and video maintained steady but comparatively lower engagement.

### 3. 💬 Customer Feedback Analysis
Customer ratings remained fairly consistent, **averaging around 3.7** throughout the year — stable, but **below the 4.0 target**, pointing to a need for focused improvements in customer satisfaction, particularly for products rating below 3.5.

---

## 🎯 Goals & Recommended Actions

![Goals and Actions](marketing-images/goals-and-actions.png)
*Executive summary slide translating each finding into a concrete goal and action plan.*

| Goal | Action |
|------|--------|
| **Increase Conversion Rates** — identify factors impacting conversion and highlight where visitors drop off | Focus marketing on high-performing product categories (Kayaks, Ski Boots, Baseball Gloves); run seasonal or personalized campaigns during peak months (e.g., January, September) |
| **Enhance Customer Engagement** — determine which content types drive the highest engagement | Revitalize content strategy with more interactive formats (e.g., interactive videos, user-generated content); optimize call-to-action placement, especially in historically lower-engagement months (Sept–Dec) |
| **Improve Customer Feedback Scores** — understand recurring themes in reviews | Build a feedback loop to analyze mixed/negative reviews, develop improvement plans, follow up with dissatisfied customers, and encourage re-rating to move the average toward the 4.0 target |

<details>
<summary><strong>🖼️ Supporting presentation slides (click to expand)</strong></summary>

**Overview — Findings Summary**
![Overview Findings](marketing-images/overview-findings.png)

**Decreased Conversion Rates**
![Decreased Conversion Rates](marketing-images/decreased-conversion-rates.png)

**Reduced Customer Engagement**
![Reduced Customer Engagement](marketing-images/reduced-customer-engagement.png)

</details>

---

## 📌 Business Impact

| Before | After |
|--------|-------|
| No visibility into where the conversion funnel breaks down | Clear View → Click → Drop-off → Purchase funnel by product and month |
| Engagement tracked informally, campaign ROI unclear | Centralized dashboard tracking views, clicks, likes, and content-type performance |
| Customer reviews read manually, sentiment untracked | Reviews enriched with sentiment scores and monitored on a live dashboard |
| Findings shared ad hoc | Structured, stakeholder-ready presentation with clear goals and actions |

---

## 🔮 Future Improvements

- 🔔 Add automated alerts when conversion rate or average rating drops below a set threshold
- 🤖 Extend the Python sentiment pipeline with topic modeling to auto-surface recurring complaint themes
- ⏱️ Schedule automatic data refresh via Power BI Service / Gateway
- 📱 Optimize report layout for mobile viewing
- 🔁 Add campaign-level ROI tracking to directly tie engagement back to marketing spend

---

## 📁 Project Structure

```
DataAnalystPortfolioProject_PBI_SQL_Python_MarketingAnalytic/
│
├── Stage 1 - Marketing_Analytics_Business_Case.pdf     # Business problem & requirements
│
├── Stage 2 - dim_customers.sql                         # Customer dimension
├── Stage 2 - dim_products.sql                          # Product dimension
├── Stage 2 - fact_customer_reviews.sql                 # Raw customer reviews
├── Stage 2 - fact_engagement_data.sql                  # Engagement fact table
├── Stage 2 - fact_customer_journey.sql                 # Customer journey fact table
│
├── Stage 3 - customer_reviews_enriched                 # Python sentiment enrichment output
├── Stage 3 - fact_customer_reviews_with_sentiment.sql   # Sentiment-enriched reviews loaded back to SQL
│
├── Stage 4 - Calendar DAX Script.txt                   # Custom date table (DAX)
├── Stage 4 - Dashboard powerbi.pbix                    # Main Power BI report (4 pages)
│
├── Stage 5 - Presentation.pptx                         # Executive summary deck
│
├── marketing-images/
│   ├── overview-dashboard.png
│   ├── conversion-details.png
│   ├── social-media-details.png
│   ├── customer-review-details.png
│   ├── data-model.png
│   ├── overview-findings.png
│   ├── decreased-conversion-rates.png
│   ├── reduced-customer-engagement.png
│   └── goals-and-actions.png
│
└── README.md
```

---

## 🚀 Getting Started

1. **Clone the repository**
   ```bash
   git clone https://github.com/maka971/DataAnalystPortfolioProject_PBI_SQL_Python_MarketingAnalytic
   ```

2. **Review the business case** in `Stage 1-Marketing_Analytics_Business_Case.pdf`

3. **Inspect the SQL staging scripts** in the Stage 2 and Stage 3 files to see how the dimension/fact tables and sentiment-enriched reviews were built

4. **Open the report** in Power BI Desktop:
   `Stage 4 - Dashboard powerbi.pbix`

5. **Refresh the data connections** via Power Query (update connection strings as needed) and explore the four report pages

6. **Review the findings deck** in `Stage 5 - Presentation.pptx` for the executive summary

---

## 👨‍💻 About the Author

**Sulah Mutyaba**
Data Analyst | Power BI Developer | SQL | Python

- 💼 LinkedIn: [linkedin.com/in/mutyaba-sulah-525510203](https://www.linkedin.com/in/mutyaba-sulah-525510203/)
- 💻 GitHub: [github.com/maka971](https://github.com/maka971)

---

<div align="center">

*Built as part of a data analytics portfolio. Open to feedback and collaboration.*

</div>
