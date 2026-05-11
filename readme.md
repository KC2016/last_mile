
# 📦 Last-Mile Delivery Insights & A/B Testing
## 🟡 1. Exploratory Data Analysis (Real Dataset)
🧭 Objective

Analyze real last-mile delivery data to understand operational drivers of delivery performance.

### 📊 Key Insights
🚦 Traffic is the strongest driver of delays
- Traffic impacts delivery time more than distance
- Peak congestion: 11–13h and 19–22h

### 🕒 Demand Patterns
- Peak demand: 17h–21h
- Highest activity: Wednesday & Friday
- Lowest activity: Saturday

- Slight increase in delivery time for older agents
- Strong correlation between delivery time and customer rating

### ⭐ Customer Satisfaction
- Ratings concentrated between 4.5–5.0
- Faster deliveries → higher satisfaction

## 🟢 2. Experiment 1 (Exploratory Hypothesis Test)
### 🧪 Objective

Test whether prioritizing high-rated agents improves delivery performance under high traffic conditions.

### 🧪 Design
Control: proximity-based assignment
Treatment: prioritize high-rated agents in high traffic

### 📊 Result
- 📉 12% reduction in delivery time
- 🧪 statistically significant (p = 0.034)

### 💡 Insight
- Agent experience plays an important - role in mitigating traffic impact.

### ⚠️ Limitation
- Not fully controlled simulation
- Limited feature scope (no full dispatch logic)
- No real-world data


## 🔵 3. Experiment 2 (A/B Test Simulation – Core Project)
### 🧪 Objective

Evaluate whether a traffic-aware dispatch system improves delivery efficiency compared to a baseline proximity-based system.

### 🧪 Experiment Design
- Control: proximity-based assignment
- Treatment: traffic + rider efficiency-based dispatch
### 📊 Metric
Primary: Delivery Time (minutes)
### 📈 Results
- 🚀 Treatment reduced delivery time by ~12%
- 🧪 Statistically significant (p < 0.05)
- 📉 Strong improvement in operational efficiency

### 💡 Business Recommendation

👉 Deploy traffic-aware dispatch in high-density regions with phased rollout.

### 🔄 Next Steps
- Add weather impact 🌧️
- Include weekly seasonality 🗓️
- Extend to customer satisfaction optimization ⭐

### 🧠 Key Learnings
- Traffic is more important than distance in last-mile delivery
- Experimental design is critical for valid product decisions
- A/B testing bridges analytics and product strategy
- Statistical significance ≠ business impact alone

### 🛠️ Tools
- Python (Pandas, NumPy, SciPy)
- Data Visualization (Matplotlib, Seaborn, Plotly)
- Geospatial Analysis (Haversine, Folium)
- A/B Testing (t-test, effect size, hypothesis testing)