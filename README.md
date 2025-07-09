# Capstone-Submission
# 🅿️ Dynamic Pricing for Urban Parking Lots

A capstone project submitted for **Summer Analytics 2025**, organized by **Consulting & Analytics Club × Pathway**.  
This project aims to build a real-time, intelligent, and adaptive dynamic pricing system for urban parking lots to optimize utilization and enhance user experience.

---

## 🚀 Overview

Urban parking spaces often suffer from inefficiencies due to static pricing, resulting in overuse or underuse of spaces depending on the time and demand. This project addresses that issue by designing:

- A **real-time dynamic pricing engine** that adjusts based on demand.
- A **pricing logic** that incorporates factors such as occupancy, queue length, traffic congestion, special days, vehicle types, and competitor pricing.
- **Real-time visualization** of parking prices and competitor comparisons.

---

## 🛠️ Tech Stack

| Tool        | Purpose                                      |
|-------------|----------------------------------------------|
| Python      | Core implementation language                 |
| Pandas      | Data processing and manipulation             |
| Numpy       | Numerical operations                         |
| Pathway     | Real-time data stream processing             |
| Bokeh       | Real-time interactive visualizations         |
| Google Colab| Development and execution environment        |
| Mermaid     | Architecture diagram rendering (for README) |

---

## 📐 Architecture Diagram

```mermaid
graph TD
  A[Simulated Real-Time Data Stream] --> B[Pathway Stream Ingestion]
  B --> C[Feature Extraction]
  C --> D1[Model 1: Baseline Linear]
  C --> D2[Model 2: Demand-Based Pricing]
  C --> D3[Model 3: Competitive Pricing]
  D1 --> E[Price Decision Engine]
  D2 --> E
  D3 --> E
  E --> F[Price Emission (Live Updates)]
  F --> G[Real-Time Visualization with Bokeh]

 Model Architecture and Workflow
🔹 Input Data
14 Parking Lots

73 Days × 18 Time Points (8 AM to 4:30 PM at 30-min intervals)

Features include:

Location: Latitude, Longitude

Occupancy, Capacity, Queue Length

Traffic Level, Special Day Indicator

Vehicle Type

🔹 Real-Time Workflow
Streaming with Pathway

Simulates incoming data with timestamp delays.

Preserves chronological integrity for real-time decision making.

Feature Engineering

Calculate occupancy rate

Normalize queue length, traffic, etc.

Convert categorical variables (e.g., vehicle type)

Pricing Models

Model 1: Linear function based on occupancy

python
Copy
Edit
price_t+1 = price_t + α × (occupancy / capacity)
Model 2: Demand-based function using weighted feature sum

python
Copy
Edit
demand = α*(occupancy/capacity) + β*queue - γ*traffic + δ*isSpecialDay + ε*vehicleType
price = base_price × (1 + λ × normalized_demand)
Model 3: (Optional) Competitive pricing using:

Distance-based proximity

Competitor price logic

Smart rerouting if full

Pricing Engine

Ensures smoothness (no erratic jumps)

Caps prices between 0.5x and 2x base price

Visualization

Real-time plotting using Bokeh

Pricing trends per lot and comparison with nearby competitors
