# 🚢 Cruise Revenue Management Pricing Simulation

---

## **Overview**

This project simulates a **Revenue Management (RM) pricing engine** for a short cruise itinerary. My goal is to model how cabin prices should evolve over the booking window based on **expected demand**, **price sensitivity (elasticity)**, and **remaining inventory**, in order to **maximize expected revenue**.

Pricing decisions are made **day by day**, **before demand is realized**, under uncertainty and capacity constraints — similar to how real RM teams operate in cruise, airline, and hospitality industries.

---

## **What This Project Answers**

**Main question:**

> **Given what I expect demand to look like today, what price should I set today?**

I break the project into three steps:

- **02 — Create a realistic synthetic dataset**
- **03 — Build the expected (forecast) demand profile**
- **04 — Optimize prices using elasticity and inventory constraints**

---

## **1) Synthetic Data Generation**  
📓 `notebooks/02_synthetic_data_generation.ipynb`

### **What I did**

Because real cruise pricing and booking data is not publicly available, I generated a **synthetic but realistic dataset** that mimics real cruise booking behavior.

I created:

- **Days to departure** as the main time axis (booking window)
- **Cabin types**: Interior, Outside, Balcony
- **Initial prices** and **total inventory** per cabin type
- A demand pattern where:
  - demand is low far from departure  
  - demand increases as departure approaches  
  - late-stage behavior reflects **inventory pressure**
- **Random demand shocks** to avoid deterministic patterns

### **Why it matters**

This provides a **controlled and explainable environment** where I can test RM logic end-to-end (**forecast → optimize**) without relying on proprietary data.

---

## **2) Demand Forecasting (Expected Demand)**  
📓 `notebooks/03_demand_forecasting.ipynb`

### **What I did**

Using the synthetic dataset, I constructed an **expected demand profile** over the booking window.

Specifically, I:

- modeled **expected cumulative sell-through** by **days to departure**
- converted cumulative sell-through into **expected daily bookings**
- built expected demand **by cabin type**
- treated demand as an **expected value**, not realized bookings

### **Key outputs**

- `expected_pct_sold`
- `forecast_cum_units`
- `expected_daily_bookings`
- `expected_daily_revenue`

### **Why it matters**

In real revenue management, pricing decisions rely on **forecasts**, because actual bookings are only observed **after** the price decision is made. This notebook produces the **decision-time inputs** a pricing engine requires.

---

## **3) Price Optimization**  
📓 `notebooks/04_Optimization.ipynb`

### **What I did**

For each **day** and **cabin type**, I selected the price that maximizes **expected feasible revenue**.

The optimization logic is:

- start with **expected daily demand** from the forecasting step
- apply **price elasticity** to estimate demand response at different prices
- test a discrete set of candidate prices (e.g., ±15%)
- enforce **remaining inventory as a hard constraint**
- choose the price that maximizes:
expected revenue = price × expected bookings (capped by inventory)
- 
### **Key outputs**

- `optimal_price`
- `expected_optimal_daily_bookings`
- `optimized_daily_revenue`
- `daily_revenue_uplift`
- cumulative expected vs optimized revenue

### **Important design choice**

I intentionally exclude **actual outcomes** from the pricing decision table to avoid **look-ahead bias**.  
This mirrors real RM systems:
forecast → decide → observe (later)

---

## **Key Outputs**

- **Pricing decision table (expected vs optimized)** showing:
  - expected demand
  - optimal prices
  - expected revenue impact
- **Visualization** comparing:
  - expected cumulative revenue
  - optimized cumulative revenue  
  by cabin type

## How to Run the Project

1. **Clone the repository**

   Clone the repository from GitHub and navigate into the project directory.

   git clone https://github.com/akioazevedo/cruise-revenue-management.git  
   cd cruise-revenue-management

2. **Install dependencies**

   Install the required Python libraries using the provided requirements file.

   pip install -r requirements.txt

3. **Run the notebooks in order**

   Run the following notebooks sequentially, since each step depends on the outputs of the previous one:

   - 02_synthetic_data_generation.ipynb  
     Generates the synthetic cruise pricing, demand, and inventory dataset.

   - 03_demand_forecasting.ipynb  
     Builds the expected (forecasted) demand profile by cabin type and days to departure.

   - 04_Optimization.ipynb  
     Runs the pricing optimization using elasticity and inventory constraints and produces the final pricing decision table and plots.

4. **Outputs**

   After running all notebooks, the following outputs will be available:

   - Pricing decision table:  
     data/processed/cruise_pricing_decision_table_expected_vs_optimized.csv

   - Visualizations:  
     figures/

   These outputs represent the decision-time pricing recommendations generated by the model.


---

## **Project Structure**

```text
cruise-revenue-management/
│
├── notebooks/
│   ├── 02_synthetic_data_generation.ipynb
│   ├── 03_demand_forecasting.ipynb
│   └── 04_Optimization.ipynb
│
├── data/
│   └── processed/
│       ├── cruise_pricing_with_forecast_clean.csv
│       └── cruise_pricing_decision_table_expected_vs_optimized.csv
│
├── figures/
│   └── (exported plots)
│
├── requirements.txt
└── README.md
