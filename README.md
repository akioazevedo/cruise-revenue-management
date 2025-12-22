# 🚢 Cruise Revenue Management Pricing Simulation

## Overview

This project simulates a Revenue Management pricing engine for a short cruise itinerary.
The goal is to model how cabin prices evolve over the booking window as a function of demand,
price sensitivity, inventory sell-through, and uncertainty.

---

## Business Problem

Cruise lines must dynamically adjust prices as departure approaches in order to:

- Maximize revenue  
- Manage limited cabin inventory  
- Balance early demand with last-minute pricing power  

Pricing decisions are made **day by day**, across multiple cabin products, under uncertainty.

This project answers:

> **How should prices evolve as demand builds and inventory sells through?**

---

## Key Concepts Modeled

- Days to Departure as the primary time dimension  
- Cabin Segmentation (Interior, Outside, Balcony)  
- Price Elasticity differences across cabins  
- Demand Growth as departure approaches  
- Inventory Pressure in late booking stages  
- Stochastic shocks to avoid deterministic behavior  

---

## Project Structure

```text
cruise-revenue-management/
│
├── notebooks/
│   ├── 02_synthetic_data_generation.ipynb
│   ├── 03_demand_forecasting.ipynb
│   └── 04_price_optimization.ipynb
│
├── data/
│   └── processed/
│       ├── cruise_pricing_with_forecast_clean.csv
│       └── cruise_pricing_with_optimization_full.csv
│
├── figures/
│   └── (all exported plots)
│
├── requirements.txt
└── README.md

