# Cruise Revenue Management & Pricing Simulation

## Overview

This project simulates a **Revenue Management (RM) pricing system** for a short cruise itinerary.
The goal is to model how cruise cabin prices should evolve over time as departure approaches, accounting for demand growth, price sensitivity, seasonality, and operational constraints.

The project is inspired by pricing and revenue optimization practices used by cruise lines such as Royal Caribbean and Carnival.

---

## Business Problem

Cruise lines sell a **fixed inventory** of cabins over a limited booking window.
Pricing decisions must balance:

* Maximizing total revenue
* Managing price-sensitive vs premium demand
* Responding to increasing demand closer to departure
* Avoiding unrealistic price volatility

This project answers the question:

> *How should cruise cabin prices dynamically change as days-to-departure decrease in order to reflect realistic revenue management behavior?*

---

## Dataset Description

The final dataset is a **synthetic revenue management pricing table**, where each row represents:

> One cabin type, on one day before departure, with a recommended price.

### Key dimensions

* **Time:** Days to departure (90 → 1)
* **Product:** Cabin category (Interior, Outside, Balcony)

### Key variables

* `days_to_departure`: Time remaining until sailing
* `cabin_type`: Cabin category
* `base_price`: Anchor price for each cabin
* `demand_index`: Simulated booking pressure
* `elasticity`: Price sensitivity by cabin type
* `seasonality`: Peak vs normal demand adjustment
* `daily_shock`: Random demand noise
* `inventory_pressure`: Late-stage pricing push
* `price`: Final recommended price

---

## Pricing Logic

Prices are generated using a **dynamic pricing model** that incorporates:

1. Demand growth as departure approaches
2. Cabin-level price elasticity
3. Seasonality effects
4. Inventory pressure near sailing
5. Stochastic daily shocks to avoid deterministic behavior
6. Price floors and caps to ensure realistic bounds
7. Smoothing to prevent unrealistic day-to-day jumps

This mirrors how real RM teams simulate and evaluate pricing strategies internally.

---

## Key Insights

* Prices generally **increase as departure approaches**
* Premium cabins (Balcony) show **lower price sensitivity**
* Interior cabins show **steeper price acceleration**
* Late-stage pricing exhibits **controlled volatility**, reflecting tactical RM decisions

---

## Tools & Technologies

* Python (Pandas, NumPy)
* Jupyter Notebook
* Git & GitHub

---

## Project Structure

```
cruise-revenue-management/
├── data/
│   └── processed/
│       └── cruise_pricing_synthetic_final.csv
├── notebooks/
│   └── 02_synthetic_data_generation.ipynb
├── README.md
└── requirements.txt
```

---

## Next Steps

Potential extensions of this project include:

* Simulating cabin bookings and inventory depletion
* Calculating daily and cumulative revenue
* Comparing alternative pricing strategies
* Building a revenue management dashboard
