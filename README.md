# 5G-QoS-ML-Analysis
ML-based QoS and QoE analysis for 5G video conferencing traffic
# ML-Based 5G QoS and QoE Analysis for Video Conferencing Traffic

## Overview
This project presents a data-driven analysis of **5G network performance** using
**packet-level Zoom video conferencing traffic**. Machine learning models are used
to predict **throughput (QoS)**, analyze **traffic bursts**, and estimate **Quality of
Experience (QoE)**. The work focuses on **network analytics** rather than protocol
implementation, aligning with modern telecom and software monitoring systems.

---

## Problem Statement
Real-time applications such as video conferencing are highly sensitive to network
conditions. The objective of this project is to:
- Derive meaningful QoS metrics from raw packet data
- Predict network throughput using ML models
- Analyze traffic behavior and bursts
- Map QoS to user-centric QoE levels

---

## Dataset
- **Source:** Packet-level Zoom traffic (CSV) captured from real network traces  
- **Traffic Type:** UDP-based video conferencing packets  
- **Scope:** A representative subset (`Zoom_1.csv`) was selected to balance realism
  and computational efficiency.

---

## Feature Engineering
Raw packet data was aggregated into **1-second time windows** to extract QoS features:
- `packet_count` – number of packets per window
- `avg_packet_size` – mean packet size (bytes)
- `std_packet_size` – packet size variation
- `total_bytes` – total bytes per window
- `throughput_mbps` – computed throughput in Mbps

This packet → window → QoS transformation follows standard telecom analytics practice.

---

## Exploratory Data Analysis (EDA)
Key observations from EDA:
- Throughput exhibits a **right-skewed distribution**, typical of adaptive video traffic
- Strong correlation between packet statistics and throughput
- Temporal variation reflects dynamic bitrate adaptation
- Traffic bursts were identified using percentile-based thresholds

EDA guided feature selection and model choice.

---

## Machine Learning Models
The following regression models were implemented and compared:
- **Linear Regression** (baseline)
- **Random Forest Regressor**
- **Gradient Boosting Regressor**

### Model Comparison (RMSE)
| Model | RMSE (Mbps) |
|------|------------|
| Linear Regression | ~0.0308 |
| Random Forest | ~0.0050 |
| Gradient Boosting | ~0.0127 |

Random Forest achieved the best performance due to its ability to capture
non-linear traffic patterns.

---

## Evaluation Metrics
Regression metrics:
- **RMSE**
- **MAE**
- **R² Score**

Service-level evaluation:
- Throughput values were mapped to **QoS classes** (Poor / Medium / Good)
- Precision, Recall, and F1-score were computed for QoS classification

The low prediction error is expected, as throughput is derived from packet-level
statistics that are strongly correlated with the input features.

---

## QoE Estimation (Add-on Feature)
To enhance practical relevance, QoS predictions were mapped to **QoE scores**:
- Poor QoS → Bad experience
- Medium QoS → Average experience
- Good QoS → Excellent experience

This bridges the gap between network-level metrics and user experience.

---

## Burst Detection
Traffic bursts were detected using high-percentile packet rate thresholds.
This highlights periods of sudden traffic increase, which are critical for
network monitoring and congestion analysis.

---

## Tools & Technologies
- **Programming:** Python
- **Libraries:** Pandas, NumPy, Scikit-learn, Matplotlib, Seaborn
- **Environment:** Google Colab
- **Version Control:** GitHub

---

## Key Takeaways
- Demonstrates packet-level to QoS modeling used in real networks
- Combines **Core ECE concepts** (5G, QoS, traffic behavior) with
  **Software/Data Science practices** (ML, EDA, evaluation)
- Provides an industry-aligned approach to 5G network analytics

---

## Future Scope
- Extend to latency and jitter modeling
- Integrate real-time inference API for monitoring systems
- Apply the pipeline to additional 5G application categories

---

## Author
HP
cross-domain expertise in **5G networks, machine learning, and data science**.
