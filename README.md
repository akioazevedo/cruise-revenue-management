# 🚢 Cruise Revenue Management Pricing Simulation

## Overview
This project simulates a **Revenue Management pricing engine** for a short cruise itinerary.  
The goal is to model how cabin prices evolve over the booking window as a function of demand, price sensitivity, inventory sell-through, and uncertainty.

Rather than analyzing static historical data, this project focuses on **decision logic**, mirroring how Revenue Management teams actually think about pricing.

---

## Business Problem
Cruise lines must dynamically adjust prices as departure approaches in order to:

- Maximize revenue  
- Manage limited cabin inventory  
- Balance early demand with last-minute pricing power  

Pricing decisions are made **day by day**, across **multiple cabin products**, under uncertainty.

**This project answers:**
> *How should prices evolve as demand builds and inventory sells through?*

---

## Key Concepts Modeled
- **Days to Departure** as the primary time dimension  
- **Cabin Segmentation** (Interior, Outside, Balcony)  
- **Price Elasticity** differences across cabins  
- **Demand Growth** as departure approaches  
- **Inventory Pressure** in late booking stages  
- **Stochastic Shocks** to avoid deterministic behavior  

---

## Dataset
The final dataset is stored at: data/processed/cruise_pricing_synthetic_final.csv


It represents **one pricing decision per cabin per day**.

Each row corresponds to:
> *A recommended price for a specific cabin type on a specific day before departure.*

### Key Fields
- `days_to_departure`
- `cabin_type`
- `price`
- `pct_sold`
- `daily_revenue`
- Demand and inventory signals

---

## Visual Analysis
All plots are **programmatically exported** to the `figures/` folder for reproducibility.

### 1️⃣ Booking Rate vs Price  
**File:** `01_booking_rate_vs_price.png`

Shows how booking rates decline as prices increase, with **cabin-specific trend lines**.  
This illustrates **price sensitivity** and validates elasticity assumptions.

---

### 2️⃣ Revenue Share by Cabin  
**File:** `02_revenue_share_by_cabin.png`

Displays how total revenue is distributed across cabin types.  
Higher-priced cabins generate a **disproportionate share of revenue**, despite lower volume.

---

### 3️⃣ Price vs Inventory Sell-Through  
**File:** `03_price_vs_sell_through.png`

Shows how prices increase as a larger percentage of inventory is sold.  
This reflects **inventory-based pricing pressure**, a core RM principle.

---

### 4️⃣ Inventory Sell-Through Over Time  
**File:** `04_sell_through_over_time.png`

Tracks how inventory is sold as departure approaches.  
This mirrors **booking curves** used in airline, cruise, and hotel Revenue Management.

---

## Technical Stack
- Python  
- pandas  
- NumPy  
- matplotlib  
- Jupyter Notebook  

All outputs are reproducible by running the notebook **top-to-bottom**.

---

## Key Takeaways
- Revenue Management decisions are **time-based**, not calendar-based  
- Pricing must vary by **product segment**  
- Realistic models require **uncertainty**, not smooth curves  
- Inventory dynamics strongly influence **late-stage pricing**

---

## Future Extensions
Possible next steps include:
- Optimization of price paths  
- Comparison of alternative pricing strategies  
- More detailed demand forecasting  
- Dashboard visualization  

---
