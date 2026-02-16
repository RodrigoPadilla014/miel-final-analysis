# Diccionario de Datos - Base Miel Final

## Información General
- **Archivo**: 2025_Base_Miel_Final-_calculos.xlsx
- **Registros originales**: 264 filas
- **Período**: Zafras 2020-2021 a 2024-2025
- **Ingenios**: 8 (Trinidad, Santa Ana, Magdalena, Palo Gordo, Madre Tierra, Pantaleón, La Unión, Tulula)

## Variables Identificadoras (6 columnas)

| Variable | Tipo | Descripción |
|----------|------|-------------|
| Zafra | Texto | Temporada de cosecha (YYYY-YYYY) |
| NoM | Entero | Número de mes (1-7) |
| Mes | Texto | Nombre del mes |
| Muestra | Texto | Tipo de muestra ("Miel final") |
| Código_ING | Entero | Código numérico del ingenio |
| Ingenio | Texto | Nombre del ingenio |

## Variables Fisicoquímicas (28 columnas)

### Mediciones Básicas
| Variable | Unidad | Descripción | Método |
|----------|--------|-------------|--------|
| Brix | % | Sólidos solubles totales (refractométrico) | ICUMSA GS 4/3/8-13 |
| Pol | % | Sacarosa aparente (polarimétrico) | ICUMSA GS 4/7-1 |
| Pureza_Pol | % | Pol/Brix × 100 | Calculado |
| Bx_MateriaSeca | % | Sólidos totales reales | Correlación Hoekstra |

### Análisis Cromatográfico (HPLC)
| Variable | Unidad | Descripción |
|----------|--------|-------------|
| Sacarosa | % | Sacarosa real (HPLC) |
| Glucosa | % | Glucosa |
| Fructosa | % | Fructosa |
| AzucaresTot | % | Suma de sacarosa + glucosa + fructosa |
| AR_HPLC | % | Glucosa + Fructosa |
| Pureza_Real | % | Sacarosa/MateriaSeca × 100 |

### Análisis Químico
| Variable | Unidad | Descripción |
|----------|--------|-------------|
| AR_Fehling | % | Azúcares reductores (método Lane & Eynon) |
| %Ceniza_Cond | % | Cenizas conductimétricas |
| pH | - | pH de la miel |
| Color | IU | Color (unidades ICUMSA) |

### Propiedades Físicas
| Variable | Unidad | Descripción |
|----------|--------|-------------|
| Viscosidad_25C | Pa*s | Viscosidad a 25°C |
| Viscosidad_40C | Pa*s | Viscosidad a 40°C |

### Indicadores Calculados
| Variable | Unidad | Descripción | Fórmula/Criterio |
|----------|--------|-------------|------------------|
| No_Pol | % | No-sacarosas basado en Pol | Brix - Pol |
| No_Sac | % | No-sacarosas basado en HPLC | MateriaSeca - Sacarosa |
| Pol_Clerget | % | Sacarosa por doble polarización | ICUMSA GS 4/7-1 |
| Pureza_Clerget | % | Pureza calculada con Pol Clerget | - |
| Fructosa/Glucosa | - | Relación F/G (indicador Maillard) | >1.3 indica degradación |
| AR_Cenizas | - | Relación AR/C | Óptimo >1.0 |

### Pérdidas y Pureza Objetivo
| Variable | Unidad | Descripción |
|----------|--------|-------------|
| kg/t_MF | kg/t | Kilogramos de miel final por tonelada |
| PerdPol_MF | kg/t | Pérdida basada en Pol |
| PerdSac_MF | kg/t | Pérdida basada en Sacarosa HPLC |
| Perd_Indet | kg/t | Pérdida indeterminada (PerdSac - PerdPol) |
| Pureza_Obj | % | Pureza objetivo (Smith 1995) |
| Mej_alcanzable_PUR | % | DPO = Pureza_Real - Pureza_Obj |

## Notas Importantes
1. **Viscosidad**: Datos 2020-2021 pueden tener problemas de equipo
2. **Tulula**: Algunas muestras pueden ser de períodos sin producción azucarera (producción de ron)
3. **Mayo**: Muestras de fin de zafra pueden tener menor completitud
