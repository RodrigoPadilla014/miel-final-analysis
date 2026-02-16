# Findings and Data Processing Documentation

## Project Overview

Analysis of honey and sugar production metrics from 8 Guatemalan sugar mills across 5 harvest seasons (2020-2025). This document summarizes the data processing steps, cleaning decisions, and dataset characteristics.

---

## Chemical Analysis - Final Honey

### Data Processing Steps

#### 1. Raw Dataset
- **Source**: `2025_Base_Miel_Final_calculos.xlsx`
- **Original size**: 264 rows
- **Columns**: 50+ physicochemical variables

#### 2. Data Cleaning Strategy

**Step 1: Remove Tulula - Non-Sugar Production Months (16 rows)**
- Tulula operated in rum-only production months with zero sugar output
- All data columns were completely null for these rows
- Decision: Remove entirely as data is not relevant to sugar production analysis

**Step 2: Remove May - Sampling Failures (0 rows retained)**
- End-of-harvest samples were not received/analyzed
- Decision: Exclude months with missing core analyses

**Step 3: Flag Unreliable Viscosity (flag applied, not deleted)**
- Equipment malfunction in 2020-2021 caused null viscosity readings
- Applied 'X' marker instead of deletion to preserve other variables
- Affected rows can be excluded in analysis as needed

### Final Cleaned Dataset

- **Final rows**: 248 rows
- **Rows eliminated**: 16 (6% of original)
- **Data completeness**: 99.95%
- **Null values remaining**: <0.05% (mostly in secondary/derived columns)

### Variables Available

#### Key Quality Parameters
- **AR/C Ratio**: Ash/Reducing sugars relationship (key efficiency metric)
- **Pureza (Purity)**: Percentage of sucrose in juice
- **Brix**: Refractive index (dissolved solids)
- **Pol%**: Apparent sucrose content
- **Sacarosa HPLC**: Direct sucrose measurement (reference standard)
- **Glucosa HPLC**: Glucose content (decomposition indicator)
- **Fructosa HPLC**: Fructose content

#### Physical Properties
- **Viscosity (25°C & 40°C)**: Pa·s (flagged where unreliable)
- **Color**: Absorbance units (Maillard reaction indicator)

#### Source Data
- **Zafra (Harvest)**: 2020-21 through 2024-25
- **Month**: November through May (harvest season)
- **Mills**: 8 Guatemalan sugar mills
- **Muestra (Sample)**: Unique sample identifiers

---

## Production Analysis - Monthly Consolidation

### Data Processing Steps

#### 1. Source Data
- **Files**:
  - `Consolidado_de_Productividad_filtrado.xlsx` (7 mills)
  - `Magdalena_acumulado.xlsx` (Magdalena-specific data, higher coverage)
- **Format**: Biweekly (catorcena-level) records with date and month-specific metrics

#### 2. Catorcena-to-Month Mapping
- Each biweekly period (catorcena 1-26) mapped to calendar months
- Multiple records per catorcena → median date used for month assignment
- Example: Catorcena 1-2 → November, Catorcena 3-4 → December

#### 3. Monthly Extraction Logic

**For each Mill/Zafra/Month combination:**

1. **Primary data** (fecha de cierre - close date):
   - Filter records matching calendar month
   - Select value closest to 15th of month

2. **Fallback data** (if no fecha de cierre):
   - Use catorcena mapping to locate month
   - Apply same closest-to-15th rule

3. **Column substitution** (if primary metric null):
   - Pol en caña: `Pol bascula` → `Pol industrial`
   - Pureza jugo: `Pureza core sampler` → `Pureza primario`
   - Recuperación: No substitute available

#### 4. Validation Against Reference Table
- Filtered by mill-month-zafra combinations known to be valid
- Removes months where mills were not operating

#### 5. Magdalena Special Handling
- Magdalena had higher data coverage in separate accumulated file
- Reprocessed with same logic, then merged into main dataset
- Replaced initial Magdalena records with higher-quality version

### Final Consolidated Dataset

- **Output**: `Consolidado_Productividad_Filtrado.xlsx`
- **Total rows**: ~280 rows (8 mills × 5 zafras × ~7 months)
- **Coverage**:
  - Pol en caña: ~97% filled
  - Pureza jugo: ~95% filled
  - Recuperación Total: ~92% filled
- **Format**: One row per mill per month per zafra

### Variables Available

- **Pol en caña**: Apparent sucrose in cane at harvest (Brix units)
- **Pureza jugo**: Purity of extracted juice (percentage sucrose)
- **Recuperación Total**: Overall recovery efficiency (%)

---

## Data Linking & Analysis Potential

The two datasets can be linked through:
- **Zafra** (harvest season)
- **Mill** (ingenio)
- **Month** (mes)

This enables analysis of:
- Production metrics (Pol, Purity, Recovery) → Final honey composition
- Temporal evolution within and across harvests
- Mill-specific efficiency patterns
- Seasonal influences on final product

---

## Planned Analysis Frameworks

### 1. Multi-Harvest Temporal Evolution
- AR/C ratio stability per mill across 5 years
- Pureza Objetivo Difference (DPO) trends
- Mill improvement/deterioration patterns

### 2. Seasonal Patterns
- Harvest phase analysis (early, mid, late season)
- Purity and ash/reducing sugar changes through season
- Correlation with Pol%caña and honey yield (kg/t final)

### 3. Loss Analysis & Accounting
- Systematic error quantification (Pol vs. HPLC Sacarosa)
- Indeterminate loss estimation by analytical method
- Mill-to-mill comparisons

### 4. Component-Level Analysis
- Glucose destruction correlation (F/G ratio vs. Color)
- Viscosity as exhaustion predictor (40°C threshold analysis)
- AR/C relationship validation against actual purity

---

## Data Quality Notes

- **Completeness**: Both datasets >95% complete for core variables
- **Measurement standards**: HPLC for chemical composition, gravimetric/optical for production metrics
- **Sampling period**: Consistent methodology across mills and years
- **Flag considerations**: Viscosity (2020-21) and May samples should be handled appropriately in downstream analysis

---

## Next Steps for Analysis

1. Temporal coherence check: Link production → final composition by zafra/mill/month
2. Establish AR/C reference ranges by mill and month
3. Calculate DPO (Diferencia de Pureza Objetivo) trends
4. Correlate production variables with honey composition
5. Identify thresholds (e.g., viscosity at 40°C, F/G ratio) predictive of processing difficulty
