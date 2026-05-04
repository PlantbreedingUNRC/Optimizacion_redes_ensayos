# Optimizacion_redes_ensayos

# Optimización del número de repeticiones, años y sitios para la evaluación en un megaambiente 

Este repositorio contiene el **Protocolo I**, un flujo de trabajo integral desarrollado en SAS para determinar la estructura óptima de la red de ensayos de trigo pan. El objetivo es maximizar la eficiencia en la captura de la varianza genotípica mediante la optimización secuencial de tres parámetros clave: $N_r$, $N_a$ y $N_s$.

## 📂 Estructura del Protocolo I

El análisis se divide en tres protocolos técnicos donde cada resultado alimenta el cálculo de la fase siguiente:

### Protocolo A: Optimización de Repeticiones ($N_r$)
Determina el número de repeticiones necesarias por ensayo para minimizar el error experimental.
* **Estimación de Varianza**: Uso de `PROC MIXED` (REML) para aislar componentes de varianza por cada ensayo individual.
* **Validación de Supuestos**: Evaluación de Normalidad (Shapiro-Wilk) y detección de Heterocedasticidad mediante análisis de residuos.
* **Cálculo de Heredabilidad Anual ($H_a$)**: Identificación del tercer cuartil ($Q_3$) de heredabilidad por sistema de manejo para establecer umbrales de precisión agronómica.

### Protocolo B: Optimización de Años ($N_a$)
Calcula la cantidad de campañas necesarias para capturar la interacción Genotipo x Año ($V_{gy}$).
* **Modelización Multi-anual**: Estimación de componentes de varianza incluyendo el efecto año como variable aleatoria.
* **Integración de $N_r$**: Se utiliza el valor de repeticiones optimizado en la Fase A para ajustar la precisión de la heredabilidad en el tiempo.
* **Ajuste de Tesis**: Aplicación de filtros de exclusión para descartar ensayos con error extremo y asegurar recomendaciones con sentido biológico.

### Protocolo C: Optimización de Localidades ($N_s$)
Define el número de sitios de evaluación requeridos dentro de cada subregión.
* **Interacción Genotipo x Localidad ($V_{gl}$)**: Estimación de la varianza ligada a la ubicación geográfica específica.
* **Parámetros Optimizados**: Unión de los valores de $r$ (repeticiones) y $a$ (años) calculados previamente para el cálculo de la estabilidad regional.
* **Resultado Final**: Generación de la tabla de sitios recomendados por subregión, manejo y época de siembra.

---

## 🛠️ Requisitos del Script
* **Software**: SAS (v9.4 o SAS OnDemand for Academics).
* **Entrada de Datos**: El script espera una tabla `WORK.IMPORT` con columnas estandarizadas: `Subregion`, `Loc`, `Manejo`, `Epoca`, `Anio`, `Cultivar` y `Rto`.
* **Salida Principal**: Tabla `TABLA_NS_FINAL_TESIS` con los valores de optimización final para la red de ensayos.

## 📝 Referencia de la Tesis
* **Autor:** Mójica, Claudia Julieta.
* **Título:** Desarrollo e implementación de protocolos para el análisis del rendimiento y calidad en redes de evaluación de cultivares de trigo.
* **Capítulo Relacionado:** Capítulo 4: Optimización del número de repeticiones, años y sitios para la evaluación en un megaambiente.
* **Grado:** Tesis para optar al título de Doctora en Ciencias Agropecuarias.
* **Estado:** En preparación / Finalización de manuscrito (2026).
