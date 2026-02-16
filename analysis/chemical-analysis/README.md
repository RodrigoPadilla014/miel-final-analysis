# Chemical Analysis - Final Honey Composition

Physicochemical analysis of final honey samples from 8 Guatemalan sugar mills across 5 harvest seasons.

## Overview

**Final Dataset**: 248 samples with 99.95% completeness
- **Removed**: 16 rows (Tulula non-sugar production months) + sampling failures
- **Retained**: High-quality honey composition data

## Quality Parameters

- **AR/C Ratio**: Ash/Reducing sugars (mill efficiency metric)
- **Pureza (Purity)**: Sucrose percentage in juice
- **Pol%**: Apparent sucrose content
- **Sacarosa HPLC**: Direct sucrose measurement (reference)
- **Glucosa HPLC**: Glucose content (decomposition indicator)
- **Fructosa HPLC**: Fructose content

## Physical Properties

- **Brix**: Refractive index (dissolved solids)
- **Viscosity (25°C & 40°C)**: Pa·s (flagged for 2020-21 equipment issues)
- **Color**: Absorbance units (Maillard reaction indicator)

## Data Processing Steps

1. **Step 1**: Remove Tulula non-sugar months (16 rows with all-null data)
2. **Step 2**: Remove May end-of-harvest sampling failures
3. **Step 3**: Flag unreliable viscosity readings (2020-21 equipment malfunction)
4. **Output**: Cleaned dataset with zero information loss on usable data

## Notebooks

- `01_null_analysis.ipynb` - Missing data patterns and characteristics
- `02_data_cleaning.ipynb` - Cleaning decisions and final dataset generation

## Files

- `data/raw/` - Original 2025_Base_Miel_Final_calculos.xlsx
- `data/cleaned/` - 2025_Base_Miel_Final_CLEANED.xlsx (248 rows)
- `reports/` - cleaning_report.md

## Period

5 harvest seasons: November 2020 through May 2025

## Mills

Trinidad, Santa Ana, Magdalena, Palo Gordo, Madre Tierra, Pantaleón, La Unión, Tulula

## Analysis Applications

- AR/C evolution and stability per mill
- Pureza evolution (DPO - Diferencia de Pureza Objetivo)
- Viscosity as exhaustion predictor
- F/G ratio for glucose destruction detection
- Seasonal composition patterns
