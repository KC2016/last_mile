# 📦 Last-Mile Delivery Insights: A/B Testing with Amazon Dataset


## 📄 Project Description

This project explores a last-mile grocery delivery dataset to uncover patterns that affect customer ratings, rider performance and rider operational flow. The goal is to generate actionable insights that support A/B testing and product optimization for logistics platforms like Delivery Hero.

The dataset contains over 43,000 delivery records and includes information such as agent age, vehicle type, order/pickup/delivery time, traffic, weather, and customer rating.

## 🎯 Objectives

- Analyze the relationship between traffic and delivery time
- Understand if agent age influences ratings or performance
- Identify peak hours and days for grocery delivery
- Define user segments that could benefit from A/B testing

## 📊 Key Insights

### 🚦 Traffic & Delivery Time (rider performance)

- Traffic jams are most common between 7 PM and 10 PM.
- High traffic is also seen between 11 AM and 1 PM.
- Longer delivery times are observed in the afternoon and evening.
- Surprisingly, delivery time has weak correlation with distance, suggesting traffic, wait time, or agent behavior have greater impact.

### 🙎🏻‍♂️ Agent Performance

- Older agents (30+) receive slightly lower ratings and take longer to deliver.
- Lower ratings may be indirectly caused by longer delivery time, not age itself.

### 🕒 Time-of-Day & Demand

- Peak grocery delivery hours: 5 PM to 9 PM
- Highest order volumes on Wednesdays and Fridays (~62 orders/week)
- Saturday has the lowest average (~53 orders/week)
- Overall, delivery demand is balanced across weekdays.

### ⭐ Customer Ratings

- Most ratings are between 4.5 and 5.0.
- Faster deliveries tend to result in higher ratings.
- Ratings are also likely influenced by unobserved factors such as communication, packaging, and professionalism.

### 🗺️ Interactive Map
View the delivery drop-off locations in this [interactive map (HTML)](http://localhost:8889/files/repositories/my_projects/last_mile/maps/sample_locations_map.html).

## 📂 Dataset

Name: Amazon Delivery Dataset

Source: [Kaggle - Sujal Suthar](https://www.kaggle.com/datasets/sujalsuthar/amazon-delivery-dataset)

Focus: Filtered for grocery deliveries


## 📁 Structure
```
├── data/
│   ├── ammazoon_delivery.csv
│   └── grocery_cleaned_coordinates.csv
├── maps/
│   └── sample_locations_map.html
├── delivery_eda.ipynb
├── delivery_maps.ipynb
└── readme.md
```

## ⚙️ Tools Used

- Python (Pandas, Seaborn, Matplotlib, Plotly, Folium)
- Jupyter Notebook
- GitHub for version control

## ✨ Next Steps

- **Must do:** Segment users for A/B testing based on traffic or delivery time to impact rider satisfaction, efficiency, or retention.
- **Maybe do:** Build a distance variable from coordinates.
- **It would be great to do if I had another dataset to join:** Consider integrating customer feedback text or sentiment data.

**NOTE:** This project is for learning/demo purposes. Attribution appreciated.