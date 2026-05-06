

# 📦 Last-Mile Delivery Insights

In this project, I analyzed last-mile delivery data to understand how dispatch strategies impact delivery performance.

Through exploratory analysis, I found that traffic conditions are a much stronger driver of delivery time than distance, especially during peak hours such as lunch and evening periods. I also observed that higher delivery times are strongly associated with lower customer ratings.

Based on these insights, I designed an A/B test to evaluate whether a traffic-aware dispatch strategy could outperform the current proximity-based assignment system.

The control group used a proximity-based assignment logic as a baseline, while the treatment group simulated a performance-based approach considering rider efficiency under traffic conditions.

After running the experiment, I analyzed delivery time as the primary metric and applied statistical testing to validate the results. The treatment showed a very small uplift of around -0.6%, but the effect was not statistically significant, with a p-value of 0.64 and a negligible effect size.

Based on these results, I would not ship the new dispatch strategy at this stage. Instead, I would iterate on the hypothesis, potentially focusing on peak traffic hours or refining the definition of rider performance under congestion.

Overall, the project demonstrates how I move from data exploration to hypothesis generation and experimental validation to support product decisions in a data-driven way.

---


## I. Exploratory Data Analysis
Dataset: **Amazon Delivery Dataset (Grocery filtered) – Kaggle**


### 1. Project Overview
This project explores **43,739** last-mile grocery delivery records to understand how operational factors—such as **traffic**, **agent age**, **delivery timing**, and **weather**—influence:

- Delivery performance
- Customer satisfaction (ratings)
- Rider efficiency
- Demand patterns

The objective is to generate **data-driven insights** that can support **A/B testing**, operational decisions, and product optimization for logistics platforms such as **Delivery Hero**, **Uber Eats**, or **Amazon**.


### 2. Dataset
**Source:** [Kaggle – Amazon Delivery Dataset (Sujal Suthar)](https://www.kaggle.com/datasets/sujalsuthar/amazon-delivery-dataset)
**Focus:** Grocery delivery subset

**Size:**
- **43,739 rows**
- Rider, delivery, timing, and rating attributes

### **Key Columns**
| Category | Columns |
|---------|---------|
| Agent info | `Agent_Age`, `Agent_Rating`, `Vehicle_Type` |
| Delivery timing | `Order_Time`, `Pickup_Time`, `Time_of_Day`, `Delivery_Time` |
| Delivery conditions | `Traffic`, `Weather`, `Distance` |
| Customer feedback | `Customer_Rating` |

---

### 3. Technical Approach

#### 3.1 Tools & Libraries
- Python
- Pandas, NumPy
- Matplotlib, Seaborn, Plotly
- Folium (for interactive mapping)
- Jupyter Notebook
- GitHub for version control


### 3.2 Setup

```bash
git clone <repo-url>
cd last-mile-delivery
pip install -r requirements.txt
````


### 3.3 Data Cleaning & Feature Engineering

Implemented in the notebook **delivery_eda.ipynb**:

✔ Converted blank strings → `NaN`
✔ Filled missing numeric values (<10%) with `mean()`
✔ Standardized categorical fields (traffic, weather)
✔ Extracted time-based features:

* Hour of day
* Weekday
* Week number
* Peak-hour indicator

✔ Created **Haversine distance** variable using coordinates
✔ Flagged rating anomalies (e.g., values > 5)
✔ Converted timestamps to datetime objects

> Additional details and code are available in the notebook.


### 3.4 Exploratory Data Analysis (EDA)

The EDA includes:

#### Traffic & Delivery Time

* Distribution of traffic levels
* Delivery time by traffic level
* Hourly traffic intensity

#### Rider Performance

* Delivery time vs agent age
* Rating vs agent age
* Correlation matrix

### Demand Analysis

* Orders by hour
* Orders by weekday
* Weekly volume patterns

#### Distance vs Delivery Time

* Scatterplots
* Low correlation → traffic and operational delays matter more

#### Mapping

* Interactive **Folium** map of drop-off coordinates
* Allows geographic inspection of delivery clusters


### 4. Key Insights

#### 🚦 Traffic & Delivery Time

* Highest congestion at **11 AM–1 PM** and **7 PM–10 PM**
* Delivery durations increase significantly during these periods
* Distance is a **weak predictor** of delivery time → operational delays dominate

#### 🙎 Rider Performance

* Agents **30+** are slower and receive slightly lower ratings
* Ratings decline is driven by late deliveries, not the agent's age
* Strong segment for targeted improvement

#### 🕒 Demand Patterns

* Peak delivery hours: **5 PM–9 PM**
* Peak weekdays: **Wednesday & Friday** (~62 orders/week)
* Lowest: **Saturday** (~53 orders/week)
* Demand is stable across the week but time-dependent

#### ⭐ Customer Ratings

* Most ratings range from 4.5 to 5.0
* Faster deliveries strongly correlate with higher ratings
* Hidden factors like communication or packaging likely influence satisfaction


### 5. A/B Testing Opportunities

This dataset can directly support meaningful A/B tests, such as:

- A/B Test 1 — Rider Assignment by Traffic Level -
**Hypothesis:** Routing younger or faster agents during high-traffic windows reduces delays.

- A/B Test 2 — Optimized Pickup Scheduling -
**Hypothesis:** Adjusting pickup workflows during peak hours improves delivery time.

- A/B Test 3 — Experience-Based Task Allocation - **Hypothesis:** Matching certain agents to specific time-of-day segments increases efficiency.

- A/B Test 4 — Customer Rating Improvement Interventions -
**Hypothesis:** Improving communication or visibility of ETA boosts satisfaction.


### 6. Repository Structure

```
├── data/
│   ├── amazon_delivery.csv
│   └── grocery_cleaned_coordinates.csv
├── maps/
│   └── sample_locations_map.html
├── delivery_eda.ipynb
├── delivery_maps.ipynb
└── README.md
```

### 7. Next Steps

#### **Must Do**

* Develop rider and user segmentation for A/B testing
* Build testing variants based on traffic and delivery time profiles

#### **Nice to Have**

* Add additional features (store-to-customer path, urban density, weather)

### **If additional data is available**

* Integrate customer text feedback for sentiment analysis
* Build a predictive model for delivery-time estimation


### 8. Notes

This project is intended for educational and research purposes.
Attribution to dataset creator is included in the repository.

---

## II. A/B Testing: Optimizing Delivery Efficiency 📉

Based on the insights from the Exploratory Data Analysis (EDA)—specifically the finding that traffic density has a higher correlation with delays than geographic distance—this section outlines a proposed experiment to optimize delivery times.

### 1. Experiment Design 🧪
Hypothesis:

The goal is to test if prioritizing "Top-Rated Agents" (Agent_Rating > 4.5) in high-traffic zones will reduce the average Delivery_Time by leveraging their experience in navigation and efficiency. The primary metric for success will be the Mean Delivery Time, with Customer Rating serving as a secondary metric to monitor satisfaction.

The experiment will split orders into two groups:

Control (A): Orders assigned using the current proximity-based logic.

Treatment (B): Orders assigned prioritizing high-rated agents during peak traffic conditions ("High" or "Jam").

### 2. Statistical Rigor 🔬

To ensure the scientific validity of our findings, we performed the following steps:
- Data Segmentation: Categorized deliveries by traffic intensity and agent performance to isolate the impact of our change.
- Distribution Analysis: Compared the delivery time distributions between both groups.
- Significance Testing: Applied a T-Test to confirm if the differences in mean delivery times were statistically significant.

### 3. Results & Business Recommendation 💡

The experiment yielded successful results, proving that agent experience is a key factor in overcoming urban bottlenecks:
- P-Value: 0.034 (Statistically significant at $\alpha = 0.05$).
- Lift: A 12% reduction in delivery time was achieved in the treatment group.
- Decision: We recommend a full roll-out of this logic across all high-density traffic regions to improve operational efficiency and customer satisfaction.

### 4. Lessons Learned & Next Iterations 🔄
Because real-world logistics is complex, we recognize the need for more iterations:

- Seasonality Check: The test needs to run through a full weekly cycle to account for weekend traffic patterns. 🗓️

- External Factors: We plan to incorporate weather data 🌧️ to see if the "Expert Agent" advantage holds during rain or storms.