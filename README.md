# SAMAKA7
# Analizador de regresión lineal

> Aplicativo web para explorar datos tabulares, construir modelos de regresión lineal simple o múltiple y generar predicciones de apoyo a la evaluación de emprendimientos y proyectos.

## Estado

Este documento define el alcance y el plan del producto. El aplicativo todavía debe implementarse; por tanto, las funciones descritas aquí son requisitos propuestos y no capacidades disponibles en el prototipo actual de SAMKA. https://valeriarevilla175-crypto.github.io/SAMAKA7/

## Objetivo

Permitir que una persona cargue un archivo CSV o Excel, seleccione una variable resultado y una o más variables explicativas, ajuste un modelo lineal, revise su desempeño y pruebe escenarios de predicción. En el contexto de SAMKA, el análisis puede aportar evidencia para detectar brechas y orientar una mentoría. El resultado estadístico no debe decidir por sí solo si un emprendimiento es viable ni reemplazar el criterio de una persona evaluadora.

## Funciones previstas

1. **Carga de datos:** importar CSV y Excel (`.xlsx`/`.xls`), seleccionar hoja de cálculo y mostrar una vista previa.
2. **Reconocimiento de columnas:** inferir cuáles son numéricas, categóricas, fechas o texto; mostrar valores faltantes, valores distintos y posibles problemas de formato.
3. **Preparación transparente:** permitir elegir cómo tratar filas incompletas, categorías y valores atípicos. Mostrar cuántas observaciones se conservaron y qué transformaciones se aplicaron.
4. **Selección del modelo:** escoger una variable objetivo (Y) y una o más variables explicativas (X). Una X corresponde a regresión simple; dos o más X, a regresión múltiple.
5. **Evaluación:** separar entrenamiento y prueba, o utilizar validación cruzada cuando el tamaño de la muestra lo permita. Evitar evaluar el modelo con los mismos datos usados para ajustarlo.
6. **Visualización:** presentar valores observados frente a predichos, residuos y, para modelos simples, la línea de regresión. Para modelos con varias X, usar gráficos de predicción y residuos; no representar una superficie 3D como si resumiera todas las variables.
7. **Predicciones:** introducir valores para las variables seleccionadas y obtener una predicción. Mostrar el rango de entrada permitido y, cuando esté implementado, un intervalo de predicción.
8. **Resultados exportables:** descargar un resumen del modelo y los resultados en CSV o JSON, junto con las transformaciones y métricas utilizadas.

## Métricas y lectura

- **R²:** proporción de variación de Y explicada por el modelo en los datos evaluados. No prueba causalidad ni garantiza predicciones futuras.
- **R² ajustado:** ajusta R² considerando el número de variables explicativas; sirve para comparar modelos sobre los mismos datos.
- **MAE:** error absoluto medio, expresado en las unidades de Y.
- **RMSE:** penaliza más los errores grandes y se expresa en las unidades de Y.
- **MAPE:** error porcentual medio. Debe omitirse o marcarse como no aplicable si Y contiene ceros o valores cercanos a cero.

Las métricas deben presentarse junto con el tamaño de muestra, el método de validación, las unidades de Y y una explicación breve. No se deben fijar umbrales universales de “modelo bueno”: la interpretación depende del contexto, la calidad de los datos y el costo de equivocarse.

## Enfoque metodológico

- Aplicar mínimos cuadrados ordinarios (OLS) para estimar los coeficientes.
- Usar una solución numéricamente estable (QR o SVD) en lugar de invertir directamente la matriz de diseño.
- Incluir intercepto por defecto y permitir desactivarlo solo como opción avanzada con explicación.
- Codificar variables categóricas de forma explícita (por ejemplo, variables indicadoras), definiendo una categoría de referencia.
- Revisar residuos, linealidad, colinealidad, observaciones influyentes y heterocedasticidad. Mostrar alertas como indicios para revisión, no como certificación automática.
- Para datos temporales o agrupados, no mezclar aleatoriamente observaciones relacionadas: la estrategia de validación debe respetar tiempo o grupos.
- Las predicciones fuera del rango observado deben marcarse como extrapolación y tratarse con cautela.

## Tecnologías sugeridas

Para un MVP estático en navegador:

- **HTML, CSS y JavaScript** para la interfaz.
- **Papa Parse** para CSV.
- **SheetJS (`xlsx`)** para leer archivos Excel en el navegador.
- **ml-matrix** u otra biblioteca numérica revisada para resolver mínimos cuadrados con QR/SVD.
- **Plotly.js** para gráficos interactivos.

Antes de elegir y publicar versiones concretas, comprobar compatibilidad, mantenimiento, licencias y vulnerabilidades de cada dependencia. No cargar datos del usuario en servicios externos para realizar los cálculos del MVP.

## Estructura propuesta

```text
analizador-regresion/
├── index.html
├── css/
│   └── styles.css
├── js/
│   ├── app.js            # flujo de interfaz
│   ├── import-data.js    # lectura CSV/Excel y vista previa
│   ├── prepare-data.js   # tipos, faltantes y codificación
│   ├── regression.js     # ajuste, métricas y predicción
│   └── charts.js         # gráficos y diagnóstico
├── samples/
│   └── ejemplo.csv       # datos sintéticos, sin información real
└── README.md
```

La estructura puede simplificarse durante la primera prueba, pero conviene separar la interfaz, la importación, el cálculo y los gráficos para que cada parte pueda revisarse y probarse por separado.

## Flujo de uso

1. Abrir el aplicativo y cargar un CSV o Excel.
2. Elegir la hoja, revisar la vista previa y confirmar los tipos de columnas detectados.
3. Seleccionar Y y una o más X.
4. Definir las opciones de preparación y validación; revisar cuántas filas se usarán.
5. Ajustar el modelo y consultar métricas, coeficientes, gráficos y alertas.
6. Probar una predicción con valores ingresados y revisar si constituye extrapolación.
7. Exportar el resumen para documentar el análisis.

## Plan de desarrollo

### Fase 1 — MVP analítico

- Importar CSV y Excel, seleccionar hoja y previsualizar datos.
- Reconocer columnas numéricas y permitir elegir Y y X numéricas.
- Ajustar regresión simple y múltiple con intercepto.
- Separar datos de entrenamiento y prueba con semilla reproducible.
- Calcular R², R² ajustado, MAE y RMSE.
- Mostrar coeficientes, gráfico observado/predicho, línea para el caso simple y gráfico de residuos.
- Habilitar predicciones manuales y exportación de resumen.

### Fase 2 — Datos mixtos y diagnóstico

- Incorporar variables categóricas con codificación documentada.
- Añadir validación cruzada, intervalos y alertas de supuestos.
- Mejorar tratamiento explícito de faltantes y observaciones influyentes.
- Añadir pruebas con datasets sintéticos y casos de referencia.

### Fase 3 — Uso en SAMKA

- Diseñar una plantilla para indicadores de emprendimientos y proyectos.
- Separar claramente diagnóstico descriptivo, predicción y recomendación de mentoría.
- Validar variables y resultados con mentores y casos piloto locales.
- Integrar con el sistema SAMKA solo después de definir permisos, consentimiento, seguridad y almacenamiento.

## Privacidad y límites

- Procesar los archivos localmente en el navegador en la primera versión y no guardarlos de forma persistente por defecto.
- Mostrar una advertencia antes de cargar datos personales o información comercial confidencial.
- No presentar correlaciones o coeficientes como relaciones causales.
- No interpretar una predicción como garantía de ventas, supervivencia, crédito o éxito empresarial.
- Para evaluar emprendimientos, el modelo necesita datos relevantes, suficientes y representativos; las estadísticas agregadas de empresas no sustituyen registros comparables a nivel de proyecto.
- En futuras versiones con cuentas o backend, implementar consentimiento, minimización de datos, control de acceso, cifrado, retención limitada y eliminación segura.

## Criterios de aceptación del MVP

- Lee correctamente un CSV y un Excel de ejemplo con encabezados y varias hojas.
- Informa al usuario cuando no hay suficientes filas, faltan valores o una columna no puede interpretarse.
- Los coeficientes y métricas coinciden, dentro de tolerancias definidas, con casos de prueba calculados con una herramienta estadística de referencia.
- La evaluación se hace sobre observaciones no utilizadas para ajustar el modelo.
- Los gráficos identifican ejes, unidades y conjunto de datos usado.
- Una predicción rechaza entradas incompletas o inválidas y avisa sobre extrapolación.
- El usuario puede descargar los resultados sin que el archivo original se envíe a un servidor.

## Referencias metodológicas

- [NIST/SEMATECH e-Handbook of Statistical Methods — Linear Regression](https://www.itl.nist.gov/div898/handbook/pmd/section1/pmd141.htm): fundamentos y evaluación de modelos de regresión.
- [NIST/SEMATECH — Residual Plots](https://www.itl.nist.gov/div898/handbook/pri/section2/pri245.htm): uso de gráficos de residuos para revisar el ajuste.
- [Documentación de Papa Parse](https://www.papaparse.com/): lectura de archivos CSV en JavaScript.
- [Documentación de SheetJS](https://docs.sheetjs.com/): lectura de hojas de cálculo.
- [Documentación de Plotly.js](https://plotly.com/javascript/): visualización interactiva.

## Licencia

Definir una licencia antes de publicar el código o permitir su reutilización.

