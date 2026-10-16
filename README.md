# SAMKA | Tablero de acompañamiento a emprendimientos

[![Abrir tablero](https://img.shields.io/badge/Abrir-tablero-176B5B)](https://valeriarevilla175-crypto.github.io/SAMAKA7/)

## Resumen ejecutivo

SAMKA es un prototipo de tablero para apoyar la coordinación del acompañamiento a emprendimientos. Reúne información demostrativa sobre casos, etapas, sectores, asignación de mentores y necesidades de seguimiento en una sola vista. Su propósito es facilitar la exploración de los registros y ayudar a priorizar conversaciones de mentoría y próximos pasos.

El tablero presenta indicadores de emprendimientos activos, casos en etapa de idea, asignación de mentor y acciones atrasadas. También muestra brechas prioritarias, la distribución de casos por etapa y una tabla para explorar los emprendimientos. La vista de seguimiento permite buscar casos y filtrar por etapa y estado.

> **Importante:** los registros y valores visibles actualmente son ficticios y se usan únicamente para demostrar el funcionamiento del prototipo. No representan resultados reales de SAMKA y no deben usarse para tomar decisiones sobre emprendimientos.

## Acceso al tablero

**[Abrir SAMKA | Incubadora](https://valeriarevilla175-crypto.github.io/SAMAKA7/)**

La página está publicada como sitio estático en GitHub Pages y es accesible mediante el enlace público.

## Contenido del tablero

- **KPIs:** emprendimientos activos, casos en etapa de idea, casos con mentor asignado y acciones atrasadas.
- **Visualizaciones:** brechas prioritarias y casos por etapa.
- **Exploración:** tabla con proyecto, etapa, sector, factibilidad preliminar, mentor y estado.
- **Búsqueda y filtros disponibles:** búsqueda de casos y filtros por etapa y estado.

El prototipo todavía no ofrece un filtro específico por departamento o segmento. Si ese filtro es requerido para la entrega, debe incorporarse en la aplicación antes de presentar el requisito como cumplido.

## Problema que aborda

En un proceso de incubación, la coordinación debe revisar en qué etapa se encuentra cada emprendimiento, qué necesidades de acompañamiento aparecen y qué casos requieren seguimiento. Cuando esa información se consulta de forma dispersa, puede resultar más difícil priorizar la atención y dar continuidad a las mentorías. SAMKA explora una vista consolidada para apoyar esa revisión; el tablero no sustituye el criterio de mentores ni demuestra por sí solo el impacto de una intervención.

## Estructura del repositorio

```text
SAMAKA7/
├── index.html   # Interfaz y funcionamiento del tablero
└── README.md    # Descripción, alcance e instrucciones
```

## Cómo ejecutar y reproducir

### Abrir localmente

1. Descarga o clona este repositorio.
2. Abre `index.html` en un navegador actualizado.

El prototipo es una página estática y no requiere instalar Python, Streamlit ni ejecutar un servidor para la vista local básica. No hay un archivo `requirements.txt` porque el repositorio no es una aplicación Python.

### Publicar o actualizar en GitHub Pages

1. Sube `index.html` y `README.md` a la rama `main` del repositorio.
2. En GitHub, abre **Settings → Pages**.
3. En la configuración de publicación, selecciona la rama `main` y la carpeta raíz (`/root`), y guarda los cambios.
4. Espera a que termine la publicación y comprueba el enlace público: https://valeriarevilla175-crypto.github.io/SAMAKA7/

## Privacidad y uso responsable

- Usa datos ficticios o debidamente anonimizados para demostraciones públicas.
- No publiques nombres, contactos, información financiera ni datos comerciales confidenciales de emprendimientos sin autorización.
- Interpreta los indicadores como descripciones de los registros cargados, no como prueba de causalidad o garantía de éxito.
- Revisa los datos y el contexto con las personas responsables antes de decidir acciones de mentoría.

## Tecnologías y dependencias

La aplicación se distribuye como una página web estática (`index.html`) y se publica con GitHub Pages. No necesita dependencias de Python ni un paso de compilación para abrirse. Si se agregan bibliotecas externas o herramientas de construcción, deberán documentarse aquí junto con sus versiones y pasos de instalación.

## Estado del proyecto

Prototipo demostrativo en evolución. Las cifras son de ejemplo. La incorporación de datos reales, el filtro por departamento/segmento y cualquier recomendación gerencial basada en evidencia requieren validación con los datos autorizados del proyecto.
