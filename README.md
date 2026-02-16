# Honey Exhaustion Analysis - Guatemalan Sugar Mills

Multi-harvest analysis of honey composition and production efficiency from 8 Guatemalan sugar mills (2020-2025).

## Overview

This project investigates sugar exhaustion patterns by analyzing the relationship between production metrics, honey composition, and mill efficiency across 5 harvest seasons. Focus areas include:

- **Temporal evolution** of key quality ratios (AR/C, Purity) per mill
- **Seasonal patterns** in composition throughout harvest
- **Loss accounting** (analytical methods vs. actual recovery)
- **Viscosity and carbohydrate destruction** as exhaustion predictors

## Project Structure

```
analysis/
├── chemical-analysis/       # Physicochemical analysis of final honey (248 samples)
│   ├── notebooks/
│   │   ├── 01_null_analysis.ipynb
│   │   └── 02_data_cleaning.ipynb
│   └── data/
│       ├── raw/
│       └── cleaned/
│
└── production-analysis/     # Monthly production consolidation (280 records)
    ├── notebooks/
    │   └── 01_data_consolidation.ipynb
    └── data/
        └── output/
```

## Datasets

### Chemical Analysis (Final Honey)
- **248 samples** across 8 mills, 5 harvest seasons (Nov-May)
- **Variables**: Brix, Pol%, Sacarosa HPLC, Glucosa, Fructosa, AR/C ratio, Pureza, Viscosity, Color
- **Quality**: 99.95% completeness after removing non-sugar production months and sampling failures
- See `FINDINGS.md` for cleaning details

### Production Analysis (Monthly Metrics)
- **280 records** per mill/month/zafra across 8 mills, 5 harvest seasons
- **Variables**: Pol en caña, Pureza jugo, Recuperación Total
- **Consolidation**: Biweekly (catorcena) records aggregated to monthly values
- See `FINDINGS.md` for processing details

## Analysis Framework

### 1. Temporal Evolution (Multi-Harvest)
- AR/C ratio consistency per mill (>1.0 target)
- Pureza Objetivo Difference (DPO) trends
- Year-over-year mill improvement or deterioration

### 2. Seasonal Patterns
- Purity and AR/ceniza changes across harvest phases (early, mid, late)
- Correlation with Pol%caña and final honey yield (kg/t)
- Systematic relationships within harvest vs. across mills

### 3. Loss Analysis
- Systematic error quantification: Pol vs. Sacarosa HPLC
- Indeterminate loss by analytical method
- Mill-to-mill loss profiles

### 4. Composition-Level Drivers
- **Viscosity (40°C)**: Predictive threshold for exhaustion difficulty
- **F/G ratio**: Glucose destruction indicator (Maillard correlation with Color)
- **AR/C validation**: Relationship to actual juice purity

## Authors

Rodrigo Padilla
Raisa Vega

## Contact

rodrigopadilla267@gmail.com
