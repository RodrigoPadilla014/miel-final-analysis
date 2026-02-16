# Production Analysis - Monthly Consolidation

Extraction and consolidation of monthly production metrics from biweekly (catorcena) records.

## Overview

This analysis transforms raw catorcena-level production data into standardized monthly summaries for each mill across 5 harvest seasons (2020-2025).

## Data Processing

**Source**: Biweekly records with fecha de cierre (close dates) and catorcena numbers
**Method**:
1. Map catorcena periods to calendar months using median date
2. Extract one representative value per mill/month/zafra (closest to 15th)
3. Apply column fallbacks for missing values
4. Filter to valid mill-month-zafra combinations

**Coverage**:
- Pol en caña: 97% filled
- Pureza jugo: 95% filled
- Recuperación Total: 92% filled

**Note**: Magdalena reprocessed from separate accumulated file due to higher data availability in source.

## Output

`Consolidado_Productividad_Filtrado.xlsx` - 280 rows
- Columns: INGENIO, MES_NOMBRE, ZAFRA, Pol en caña, Pureza jugo, Recuperación Total

## Mills

Trinidad, Santa Ana, Magdalena, Palo Gordo, Madre Tierra, Pantaleón, La Unión, Tulula

## Use Cases

- Link production metrics (Pol, Purity, Recovery) to final honey composition
- Track mill efficiency evolution across harvest seasons
- Identify seasonal patterns and month-to-month changes
- Validate relationship between production and chemistry data
