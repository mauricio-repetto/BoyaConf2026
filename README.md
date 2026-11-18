# El ML clásico no está muerto todavía — BoyaConf 2026

**"El ML clásico no está muerto todavía: un caso de estudio de un cliente en la industria de la preservación de flores"**, charla de Mauricio Repetto (ML/AI Engineer en Nortal) en BoyaConf 2026.

Es una charla de caso de estudio que cuenta cómo se construyó una solución de predicción de ventas con ML clásico (series temporales con Prophet) en lugar de LLMs o agentes, con un aditivo interesante que es que la empresa trabajaba con IA/ML por primera vez.

## Contenido de las slides

| Bloque | Temas |
|---|---|
| El cliente y los desafíos | Empresa de preservación de flores (fundada en 1988 en París; abastecimiento en España, Colombia y Japón); objetivo: predecir el volumen de ventas para planificar compras de insumos |
| ¿ML clásico? | AI / ML / DL / GenAI en una slide; ML clásico = ML sin redes neuronales (KNN, K-Means, PCA, árboles, random forest, SVM) |
| El problema | Predicción de series temporales; métricas MAE, RMSE, MAPE |
| Expectativa vs. realidad | +1.000 productos, +60 países, 8 tipos de cliente, +2.500 clientes, 5 unidades de medida; ~6M de registros pero solo 3 años de historia y ~10% de productos con datos suficientes (~200k registros útiles) |
| Educando al cliente | Considerar solo productos vendidos el año anterior (80%), modelos pre-entrenados para ellos, simplificar filtros (País → Tipo de cliente), entrenamiento al vuelo, mostrar métricas junto a las predicciones, "familias de productos" |
| La solución | Front end en Azure Static Web App; back end en Azure Functions (Python) con Durable Functions para el entrenamiento al vuelo y las operaciones bulk; modelos con Prophet (estacionalidad anual/semanal/diaria + feriados), un modelo por producto; demo |
| Resultados y próximos pasos | Feedback del cliente, automatizar el reentrenamiento, dockerizar, probar otros algoritmos |
| Conclusiones | No todo es LLMs/agentes; transparencia, saber decir que no y ofrecer alternativas; explicar simple; anotar mejoras para priorizar |

## Estructura del repo

```
BoyaConf2026/
├── README.md
├── drive_assets.json
├── slides/
│   └── el_ml_clasico_no_esta_muerto_todavia.pdf
└── scripts/
    └── fetch_assets.py          # Re-descarga las slides desde Drive
```

## Archivos en Google Drive

La carpeta de Drive solo contiene la presentación: no hay modelos, datos ni notebooks asociados. La versión original (66,9 MB en Drive) está en Google Slides.

**Carpeta raíz:** <https://drive.google.com/drive/folders/1HnOPlIBtMUTMz42iJiuaSFEBRI4fQKyl>

| Recurso | Link |
|---|---|
| Slides originales (Google Slides) | [presentación](https://docs.google.com/presentation/d/1k1JXYeW4cSiYYEXgT3ajzVxVKufFE5bKkEEaCun6tEQ/edit) |

## Actualizar las slides desde Drive

```bash
python scripts/fetch_assets.py          # baja lo que falte
python scripts/fetch_assets.py --force  # vuelve a bajar todo
```
