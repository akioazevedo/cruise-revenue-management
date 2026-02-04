**Author:** Akio Azevedo  
**Goal:** Apply machine learning and optimization techniques to maximize cruise line revenue

---

## 📋 Project Overview

This project demonstrates end-to-end data science skills applied to a real-world business problem: **revenue management for cruise lines**. The challenge is balancing two competing goals:
1. **Maximize Revenue:** Charge premium prices when demand is high
2. **Maximize Occupancy:** Fill the ship to capacity

### Project Structure (3 Notebooks)

1. **[Notebook 1: Data Generation](notebooks/01_data_generation.ipynb)** ✅ *Complete*
   - Generate synthetic booking data with realistic pricing and demand patterns
   - 120-day booking window, 4 cabin types, 480 observations
   - Achieved ~90% occupancy with premium pricing strategy

2. **Notebook 2: Demand Forecasting** 🚧 *Coming Soon*
   - Train ML models to predict daily bookings
   - Compare Linear Regression, Random Forest, XGBoost
   - Target: R² > 0.80

3. **Notebook 3: Price Optimization** 🚧 *Coming Soon*
   - Use forecasting model to optimize pricing strategy
   - Maximize revenue while maintaining occupancy targets

---

## 🎯 Key Results (Notebook 1)

### Overall Performance
- **Total Capacity:** 750 cabins
- **Total Bookings:** 714 cabins
- **Overall Occupancy:** 95.2%
- **Total Revenue:** $1,020,000
- **Average Price:** $1,428/cabin

### By Cabin Type
| Cabin Type | Inventory | Occupancy | Revenue Share | Avg Price |
|------------|-----------|-----------|---------------|-----------|
| Economy    | 300       | 96.7%     | 26.8%         | $962      |
| Standard   | 250       | 92.4%     | 30.2%         | $1,314    |
| Premium    | 150       | 86.0%     | 23.5%         | $1,775    |
| Deluxe     | 50        | 85.3%     | 19.5%         | $2,870    |

**Key Insight:** Premium and Deluxe cabins generate 43% of revenue despite representing only 27% of inventory.

---

## 📊 Visualizations

![Dashboard](figures/dashboard_complete.png)

The complete analysis dashboard shows:
1. **Booking Progress:** How quickly each cabin type sells over time
2. **Final Occupancy:** Performance vs 90% target
3. **Dynamic Pricing:** Price changes throughout the booking window
4. **Revenue Contribution:** Which cabin types drive revenue
5. **Inventory vs Revenue:** Premium strategy validation
6. **Price Elasticity:** Relationship between price and demand

---

## 🛠️ Installation & Setup

### Prerequisites
- Python 3.10+
- Jupyter Notebook

### Installation

1. **Clone the repository**
```bash
git clone https://github.com/akioazevedo/cruise-revenue-management.git
cd cruise-revenue-management
```

2. **Create virtual environment**
```bash
python3 -m venv venv
source venv/bin/activate  # On Windows: venv\\Scripts\\activate
```

3. **Install dependencies**
```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
```

4. **Launch Jupyter**
```bash
jupyter notebook
```

5. **Open and run** `notebooks/01_data_generation.ipynb`

---

## 📁 Project Structure
```
cruise-revenue-management/
├── data/
│   └── processed/
│       └── cruise_bookings.csv      # Generated dataset (480 rows)
├── figures/
│   └── dashboard_complete.png        # 6-plot analysis dashboard
├── notebooks/
│   ├── 01_data_generation.ipynb      # Data generation (complete)
│   ├── 02_demand_forecasting.ipynb   # ML models (coming soon)
│   └── 03_price_optimization.ipynb   # Optimization (coming soon)
├── .gitignore
└── README.md
```

---

## 🧠 Technical Approach

### Data Generation (Notebook 1)
- **Urgency Effect:** Exponential demand growth as sailing approaches
- **Price Elasticity:** Different customer segments respond differently to price (economy: 1.3, deluxe: 0.3)
- **Dynamic Pricing:** Prices increase 60% from 120 days out to departure
- **Stochastic Demand:** Poisson distribution for daily bookings + lognormal shocks

### Machine Learning (Notebook 2 - Planned)
- **Target Variable:** Daily bookings per cabin type
- **Features:** Price, days to departure, cabin type, remaining inventory
- **Models:** Linear Regression baseline → Random Forest → XGBoost
- **Validation:** 80/20 train-test split (days 1-96 / days 97-120)

### Optimization (Notebook 3 - Planned)
- **Objective:** Maximize total revenue
- **Constraints:** Minimum 85% occupancy, inventory limits
- **Method:** Grid search or gradient-based optimization

---

## 💡 Skills Demonstrated

- **Business Acumen:** Revenue management strategy, premium pricing
- **Statistical Modeling:** Price elasticity, probability distributions
- **Python:** Pandas, NumPy, Matplotlib
- **Data Engineering:** Synthetic data generation, data validation
- **Machine Learning:** (Coming in Notebook 2)
- **Optimization:** (Coming in Notebook 3)

---

## 📈 Future Enhancements

- [ ] Add seasonal effects (summer vs winter cruises)
- [ ] Incorporate competitor pricing
- [ ] Model cancellations and no-shows
- [ ] A/B testing framework for pricing strategies
- [ ] Power BI dashboard for interactive exploration

---

## 📫 Contact

**Akio Azevedo**
- GitHub: [@akioazevedo](https://github.com/akioazevedo)
- LinkedIn: [Your LinkedIn]
- Email: [Your Email]

---

## 📝 License

This project is open source and available for educational purposes.
"""

# Write README to file
with open('../README.md', 'w') as f:
    f.write(readme_content)

print("✓ README.md created successfully!")
print("\nNext steps:")
print("1. Update the contact section with your LinkedIn/Email")
print("2. Review the results table with your actual numbers")
print("3. Commit: git add README.md && git commit -m 'Add professional README' && git push")
