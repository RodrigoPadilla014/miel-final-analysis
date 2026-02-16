# Data Dictionary - Final Honey Database

## General Information

- **File**: 2025_Base_Miel_Final-_calculos.xlsx
- **Original records**: 264 rows
- **Period**: Harvest seasons 2020-2021 to 2024-2025
- **Mills**: 8 (Trinidad, Santa Ana, Magdalena, Palo Gordo, Madre Tierra, Pantaleón, La Unión, Tulula)

## Identifier Variables (6 columns)

| Variable | Type | Description |
|----------|------|-------------|
| Zafra | Text | Harvest season (YYYY-YYYY) |
| NoM | Integer | Month number (1-7) |
| Mes | Text | Month name |
| Muestra | Text | Sample type ("Final honey") |
| Código_ING | Integer | Mill numerical code |
| Ingenio | Text | Mill name |

## Physicochemical Variables (28 columns)

### Basic Measurements

| Variable | Unit | Description | Method |
|----------|------|-------------|--------|
| Brix | % | Total soluble solids (refractometric) | ICUMSA GS 4/3/8-13 |
| Pol | % | Apparent sucrose (polarimetric) | ICUMSA GS 4/7-1 |
| Pureza_Pol | % | Pol/Brix × 100 | Calculated |
| Bx_MateriaSeca | % | Real total solids | Hoekstra correlation |

### Chromatographic Analysis (HPLC)

| Variable | Unit | Description |
|----------|------|-------------|
| Sacarosa | % | Real sucrose (HPLC) |
| Glucosa | % | Glucose |
| Fructosa | % | Fructose |
| AzucaresTot | % | Sum of sucrose + glucose + fructose |
| AR_HPLC | % | Glucose + Fructose |
| Pureza_Real | % | Sucrose/MateriaSeca × 100 |

### Chemical Analysis

| Variable | Unit | Description |
|----------|------|-------------|
| AR_Fehling | % | Reducing sugars (Lane & Eynon method) |
| %Ceniza_Cond | % | Conductimetric ash |
| pH | - | Honey pH |
| Color | IU | Color (ICUMSA units) |

### Physical Properties

| Variable | Unit | Description |
|----------|------|-------------|
| Viscosidad_25C | Pa*s | Viscosity at 25°C |
| Viscosidad_40C | Pa*s | Viscosity at 40°C |

### Calculated Indicators

| Variable | Unit | Description | Formula/Criterion |
|----------|------|-------------|------------------|
| No_Pol | % | Non-sugars based on Pol | Brix - Pol |
| No_Sac | % | Non-sugars based on HPLC | MateriaSeca - Sacarosa |
| Pol_Clerget | % | Sucrose by double polarization | ICUMSA GS 4/7-1 |
| Pureza_Clerget | % | Purity calculated with Pol Clerget | - |
| Fructosa/Glucosa | - | F/G ratio (Maillard indicator) | > 1.3 indicates degradation |
| AR_Cenizas | - | AR/C ratio | Optimal > 1.0 |

### Losses and Target Purity

| Variable | Unit | Description |
|----------|------|-------------|
| kg/t_MF | kg/t | Kilograms of final honey per ton |
| PerdPol_MF | kg/t | Loss based on Pol |
| PerdSac_MF | kg/t | Loss based on HPLC Sucrose |
| Perd_Indet | kg/t | Indeterminate loss (PerdSac - PerdPol) |
| Pureza_Obj | % | Target purity (Smith 1995) |
| Mej_alcanzable_PUR | % | TPD = Real_Purity - Target_Purity |

## Important Notes

1. **Viscosity**: Data from 2020-2021 may have equipment issues
2. **Tulula**: Some samples may be from periods without sugar production (rum production)
3. **May**: End-of-harvest samples may have lower data completeness
