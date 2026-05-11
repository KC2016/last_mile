## 🚚 Last-Mile Delivery A/B Test Simulation (Main A/B test using a simulated dataset)
### 📌 Project Overview

This project simulates an A/B test in a last-mile delivery system to evaluate whether an optimized dispatch strategy improves delivery performance compared to a baseline proximity-based assignment.

The goal is to assess the impact of a treatment algorithm that incorporates traffic conditions and rider efficiency versus a simple control strategy.

### 🧪 Experiment Design
- Control group: baseline dispatch based on proximity (simplified logic)
- Treatment group: optimized dispatch considering:
    - traffic conditions 🚦
    - rider speed 🏃
    - rider rating ⭐

Each order is randomly assigned to either group to simulate a controlled experiment.

### 📊 Key Metric
Primary KPI: delivery_time (minutes)
Objective: minimize delivery time

### 📈 Results
Group	Average Delivery Time
Control	20.25 min
Treatment	15.37 min

### 📉 Effect Size
Reduction of ~4.87 minutes (~24% improvement)

### 🧪 Statistical Test
t-test showed a statistically significant difference between groups (p-value ≪ 0.001)

### 🚀 Conclusion

The treatment group significantly outperformed the control group, reducing delivery time in a statistically significant way.

👉 This suggests that incorporating traffic conditions and rider efficiency into dispatch logic can meaningfully improve operational performance.

### 🛠️ Tools & Techniques
- Python (Pandas, NumPy, SciPy)
- A/B Testing Simulation
- Hypothesis Testing (t-test)
- Data Wrangling
- Synthetic Data Generation
- Exploratory Data Analysis (EDA)

### 🧠 Key Learnings
- How to design and simulate an A/B test
- Difference between statistical significance and business impact
- Importance of experiment design in causal inference
- Translating data results into product decisions (ship / no ship)

### 📌 Next Steps (Future Improvements)
- Add time-based seasonality (rush hours)
- Include weather effects 🌧️
- Simulate rider assignment constraints
- Extend to multi-metric evaluation (cost, customer rating)

