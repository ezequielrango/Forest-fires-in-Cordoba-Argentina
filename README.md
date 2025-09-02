# Forest fires in Córdoba, Argentina
**Riesgo de incendios forestales en la provincia de Córdoba (AR)**  
Proyecto de análisis y modelado predictivo con ciencia de datos y SIG para apoyar la prevención y la toma de decisiones.

---

## Resumen
Este trabajo integra variables **meteorológicas** (temperatura, humedad relativa, viento, precipitación), **ambientales** (NDVI) y el **Fire Weather Index (FWI)** para modelar la ocurrencia de incendios en Córdoba. Se entrenan modelos de **Regresión Logística**, **Random Forest** y **SVM**, evaluados con **accuracy**, **F1-score**, **recall**, **matriz de confusión** y **validación cruzada (K=5)**. El objetivo es aportar una herramienta reproducible de **alerta temprana** y **gestión del riesgo**.

**Palabras clave:** incendios forestales, FWI, meteorología, NDVI, aprendizaje automático, SIG.

---

## 👀 Vista rápida (galería)

<!-- CRISP-DM -->
<p align="center">
  <img alt="CRISP-DM 1" src="https://github.com/user-attachments/assets/0f467ed3-7124-473b-8c98-dc454154ea9c" width="420">
  <img alt="CRISP-DM 2" src="https://github.com/user-attachments/assets/8363c171-4974-4a60-8bc8-44e033117c6e" width="420">
</p>

<!-- Series y gráficos de superficie afectada -->
<p align="center">
  <img alt="Series de superficie afectada (últimos 5 años)" src="https://github.com/user-attachments/assets/91e33278-da16-4075-aa00-4907b4017c88" width="520">
</p>

<p align="center">
  <img alt="Superficie afectada - Gráfico 1" src="https://github.com/user-attachments/assets/b9870562-a61c-4b49-8dbd-2e9cb0e7999e" width="880">
</p>

<p align="center">
  <img alt="Superficie afectada - Gráfico 2" src="https://github.com/user-attachments/assets/58f1990a-c8b6-4ec0-9d26-40f0b4d2244e" width="560">
</p>

<!-- Mapas y otras vistas -->
<p align="center">
  <img alt="Mapa 1" src="https://github.com/user-attachments/assets/3a9087cc-6c83-4c3f-a4b0-bc63c3ea58fc" width="880"><br/>
  <img alt="Mapa 2" src="https://github.com/user-attachments/assets/9bce91ff-5797-4ce8-9bf2-f70f2a9d28a6" width="360">
  <img alt="Mapa 3" src="https://github.com/user-attachments/assets/96b29c60-a9c6-4dae-b1cc-97377346648c" width="420">
</p>

> **Tip:** si querés, puedo reemplazar esta galería por un carrusel o un mosaico con captions.

---

## Índice
- [Objetivos e hipótesis](#objetivos-e-hipótesis)
- [Marco conceptual](#marco-conceptual)
- [Datos y fuentes](#datos-y-fuentes)
- [Variables](#variables)
- [Metodología](#metodología)
- [Modelado y evaluación](#modelado-y-evaluación)
- [Resultados y visualizaciones](#resultados-y-visualizaciones)
- [Reproducibilidad](#reproducibilidad)
- [Estructura del repositorio](#estructura-del-repositorio)
- [Roadmap](#roadmap)
- [Autores y contacto](#autores-y-contacto)
- [Licencia](#licencia)
- [Cómo citar](#cómo-citar)

---

## Objetivos e hipótesis
**Objetivo general:** analizar factores climáticos, geográficos y antrópicos que inciden en la ocurrencia de incendios en Córdoba y desarrollar modelos predictivos para **segmentar zonas críticas** y **priorizar prevención**.

**Hipótesis específicas (ejemplos):**
- ↑ **Temperatura** + ↓ **Humedad relativa** ⇒ ↑ probabilidad de incendio.  
- **FWI** predice con alta precisión el riesgo por región.  
- ↓ **Lluvia acumulada** + ↑ **Velocidad del viento** ⇒ ↑ riesgo.

---

## Marco conceptual
- **Teoría del Riesgo Ambiental**: riesgo = f(amenaza, exposición, vulnerabilidad).  
- **Sistemas complejos**: dinámica no lineal entre clima, combustible y factores humanos.  
- **FWI**: índice compuesto (FFMC, DMC, DC, ISI, BUI, FWI) calibrado por zonas; útil para anticipar condiciones propicias y planificar medidas.

---

## Datos y fuentes
- **Meteorológicos**: SMN, INTA (temp., HR, viento, precipitación, FWI).  
- **Satelitales**: NASA MODIS/VIIRS (NDVI, focos FIRMS).  
- **Geográficos**: IGN, capas SIG (pendiente, altitud, cercanía a rutas/urbano).  
- **Histórico de incendios**: Ministerio de Ambiente y reportes provinciales.  
Formatos: `.csv`, `.shp`, integrados con **Python (pandas, geopandas)** y **QGIS**.

---

## Variables
- **Climáticas:** Temp (°C), RH (%), Wspd (km/h), Rn24 (mm), **FWI** y subcomponentes (FFMC, DMC, DC, ISI, BUI).  
- **Geográficas:** cobertura/uso del suelo, topografía (pendiente/altitud), proximidad a agua/rutas/urbano.  
- **Objetivo:** clase de **riesgo** (bajo vs. moderado/alto).

---

## Metodología
Enfoque **cuantitativo, explicativo**, no experimental, longitudinal y correlacional.  
**Pipeline**:
1. Adquisición y unificación (SMN/INTA, FIRMS/MODIS, IGN).  
2. Limpieza (nulos/duplicados), parseo de fechas, estandarización de unidades.  
3. Integración geoespacial (buffers y join por coordenadas).  
4. **Partición** 80/20 (estratificada).  
5. **Balanceo** de clases con **SMOTE**.  
6. **GridSearchCV (cv=5)** para RF; métricas: Accuracy, F1, Recall; matriz de confusión.  

---

## Modelado y evaluación
**Modelos:**  
- **Regresión Logística** (interpretable).  
- **Random Forest** (no lineal, robusto).  
- **SVM** (exploratorio).

**Validación:** **K-fold (K=5)** y **prueba externa 2023**.

---

## Resultados y visualizaciones
> Las principales figuras ya están en la **[Vista rápida](#-vista-rápida-galería)** de arriba.  

