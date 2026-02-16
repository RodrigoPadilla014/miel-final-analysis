# Análisis de Mieles Finales - Ingenios Guatemaltecos

## Objetivo
Analizar la composición de mieles finales de 8 ingenios guatemaltecos para responder preguntas clave sobre pureza, pérdidas y optimización del proceso de cristalización.

## Dataset
- **Período**: 5 zafras (2020-2021 a 2024-2025)
- **Muestras**: 264 registros mensuales
- **Variables**: 34 parámetros fisicoquímicos
- **Ingenios**: Trinidad, Santa Ana, Magdalena, Palo Gordo, Madre Tierra, Pantaleón, La Unión, Tulula

## Preguntas de Investigación

### Diagnóstico Multi-Zafra
1. **Estabilidad AR/C**: ¿Qué ingenios mantienen AR/C >1.0 consistentemente?
2. **Diferencia de Pureza Objetivo (DPO)**: ¿Se ha reducido o empeorado por ingenio?
3. **Patrones estacionales**: ¿Pureza y AR/cenizas cambian entre inicio, medio y fin de zafra?

### Análisis de Pérdidas
4. **Error sistemático**: Cuantificar diferencia entre Pol y Sacarosa HPLC
5. **Viscosidad**: ¿Umbral crítico que dificulta agotamiento?
6. **Destrucción de glucosa**: Ingenios con F/G >1.3 (reacción de Maillard)
7. **Correlación AR/C vs Pureza Real**: Validar teoría

## Estructura del Proyecto
```
miel-final-analysis/
├── README.md
├── requirements.txt
├── .gitignore
├── data/
│   ├── raw/              # Datos originales
│   └── cleaned/          # Datos limpios
├── notebooks/
│   ├── 01_null_analysis.ipynb
│   ├── 02_cleaning_strategy.ipynb
│   └── 03_data_validation.ipynb
└── reports/
    └── cleaning_report.md
```

## Tecnologías
- Python 3.9+
- pandas, numpy, openpyxl
- matplotlib, seaborn (visualización)
- jupyter notebook

## Contexto Teórico

### Pureza Objetivo (Smith, 1995)
```
Pureza_obj = 43.1 - 7.5 * (1 - exp(-1 * AR/C))
```

### Variables Clave
- **AR/C**: Relación azúcares reductores/cenizas (óptimo >1.0)
- **DPO**: Diferencia entre pureza real y objetivo
- **F/G**: Relación fructosa/glucosa (F/G >1.3 indica destrucción de glucosa)
- **Viscosidad**: Límite operativo ~150 Pa*s a 40°C

## Próximos Pasos
1. Análisis de valores nulos
2. Estrategia de limpieza
3. Dataset final limpio
4. Análisis estadístico (posterior)

## Autor
Rodrigo Padilla
Raisa Vega

## Data Access
   Data crudo: `2025_Base_Miel_Final-_calculos.xlsx` (no en repositorio)
   Contacto: rodrigopadilla267@gmail.com u observar DATA_DICTIONARY.md para estructura

## Referencias
- Vega, R. (2020). Caracterización de mieles finales de ingenios guatemaltecos. CENGICAÑA.
- Rein, P. (2012). Ingeniería de la caña de azúcar.
- Smith (1995). Target purity formula.
