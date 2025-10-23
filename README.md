# Green AI Energy Forecasting Project

**HACK4EARTH Green AI 2025 Submission**  
**Name:** Mohammed Mehedi Masum  
**Track:** Build Green AI  

## Problem Statement

While studying grid efficiency, I noticed that power grids often waste 20–30% of energy because demand forecasts are inaccurate. This forces fossil fuel plants to overproduce energy "just in case," wasting both fuel and money.

I wanted to solve this problem by building lightweight ML models that can run directly on smart meters and make real-time forecasts with minimal carbon impact.

## My Solution

I built and compared two models:

- **Baseline:** RandomForest (accurate but computationally heavy)
- **Optimized:** Ridge Regression (lightweight and efficient for edge devices)

My main goal wasn't just accuracy — it was to minimize the **inference** carbon footprint. Each smart meter makes about 8,760 predictions per year, so even a small efficiency gain scales up to massive global impact.

## Quick Start

### Requirements
```bash
pip install -r requirements.txt
```

### Run the Notebook

1. Open `GREEN_AI_SOLUTION.ipynb` in Jupyter or VS Code
2. Run all cells sequentially
3. Check `submission.csv` for Kaggle submission results
4. Review `evidence.csv` and `FOOTPRINT.md` for carbon measurement details

### Dataset

- **Source:** PJM Hourly Energy Consumption (2002–2018)
- **Size:** 145,366 hourly samples
- **File:** `pjm_energy.csv` (included in project)
- **License:** Public domain

## Results

### Model Performance

| Model | MAE (MW) | R² Score | Inference Time | Annual Carbon |
|-------|----------|----------|----------------|---------------|
| RandomForest | 1,621.03 | 0.9076 | 100 ms | 7,300 kg CO₂ |
| Ridge | 1,629.02 | 0.9106 | 5 ms | 36.5 kg CO₂ |
| **Savings** | –8 MW | –0.30 % | **20× faster** | **99.5 % reduction** |

### Carbon Impact (Annual)

- **Inference Savings:** 7.3 tonnes CO₂ / year
- **Grid Optimization Potential:** 295,650 tonnes CO₂ / year (estimated)
- **Total Reduction:** 295,657 tonnes CO₂ / year
- **Equivalent to:** Taking 64,273 cars off the road

## Project Structure
```
├── GREEN_AI_SOLUTION.ipynb    # Main analysis notebook
├── pjm_energy.csv              # Dataset
├── submission.csv              # Kaggle submission
├── evidence.csv                # Carbon measurements
├── FOOTPRINT.md                # Measurement methodology
├── data_card.md                # Dataset documentation
├── impact_math.csv             # Impact scenarios
├── requirements.txt            # Python dependencies
└── README.md                   # This file
```

## How It Works

1. **Feature Engineering:** Created 15 time-series features (hour, day, month, cyclical encoding, lag features, rolling statistics).
2. **Model Training:** Trained RandomForest (baseline) and Ridge (optimized) on 80 % of data.
3. **Carbon Measurement:** Estimated energy use during inference using realistic hardware assumptions.
4. **Deployment Scenario:** 5 million smart meters × 8,760 predictions/year = 43.8 billion predictions.
5. **Impact Calculation:** Quantified carbon savings if all devices used the lightweight model.

## Reproducibility

All steps are clearly documented in the notebook.  
Just run the cells in order — the results are fully reproducible (I fixed `random_state = 42` for consistency).

**Hardware Used:** CPU-only (no GPU required for Ridge)  
**Measurement Method:** Manual energy estimation using TDP × runtime  
**Grid Carbon Intensity:** 0.4 kg CO₂ / kWh (U.S. average)

## Limitations & Next Steps

- Used conservative hardware assumptions; real power draw may vary
- Grid impact calculations are projected, not empirically verified
- **Next step:** test deployment on a Raspberry Pi to measure real power consumption
- Plan to explore TinyML and on-device training in the next phase

## License

MIT License – see LICENSE file

## Contact

**GitHub:** Mohammed-Mehedi-Masum  
**Repository:** Customer-Churn-Prediction-With-Deployment (branch: my-new-branch)

---

### ✳️ Personal Note

I built this project out of curiosity about how tiny, efficient models can create huge real-world impact. If every smart meter ran on a greener model, the collective savings could reshape how we think about sustainable AI.

