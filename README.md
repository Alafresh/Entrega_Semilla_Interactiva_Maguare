# Entregables Semilla Interactiva - Repositorio Oficial

En este repositorio se encuentran los tres archivos comprimidos (`.zip`) correspondientes a las plataformas de distribución del proyecto:

- `Entregable_ANDROID_Semilla_Interactiva_Maguare.zip`
- `Entregable_WINDOWS_Semilla_Interactiva_Maguare.zip`
- `Entregable_WEB_Semilla_Interactiva_Maguare.zip`

Cada una de estas versiones ha sido desarrollada, adaptada y "brandeada" respetando rigurosamente los lineamientos de marca y la línea visual exigida por la convocatoria Arte, Juego, Territorios y Vida.

El desarrollo completo fue construido de forma nativa utilizando el motor gráfico **Unity**, garantizando que el aplicativo sea autónomo y no posea dependencias de ningún otro framework web externo para su ejecución.

## Auditoría y Despliegue del Entregable Web

Para la compilación de la versión web, se dio cumplimiento estricto al instructivo [Documentación Técnica Interactivos - aplicativos maguare.gov.co](./Requerimientos/Documentación%20Técnica%20Interactivos%20-%20aplicativos%20maguare.gov.co.pdf)

### Entorno de Pruebas (Staging)

El código fuente del aplicativo web sin comprimir se encuentra alojado en la rama `deploy-web`. Para facilitar el proceso de revisión por parte del equipo técnico, se ha desplegado una versión en vivo mediante GitHub Pages, disponible en el siguiente enlace:
👉 [https://alafresh.github.io/Entrega_Semilla_Interactiva_Maguare/](https://alafresh.github.io/Entrega_Semilla_Interactiva_Maguare/)

### Herramientas de Validación (QA)

Durante la fase de optimización, se utilizaron los siguientes enlaces oficiales compartidos en la documentación técnica para garantizar los mejores resultados posibles en rendimiento, estructuración de datos y visualización en redes sociales:

- **Rendimiento y Core Web Vitals:** [PageSpeed Insights](https://pagespeed.web.dev/?hl=es-419)
- **Validación de Schema.org:** [Google Rich Results Test](https://search.google.com/test/rich-results)
- **Verificación de Metadatos:** [OpenGraph.xyz](https://www.opengraph.xyz/)

Se escogieron los mejores resultados de la aproximación

[Page-Speed-insights-Desktop](./imagenes/page-speed-insights.png)
[Page-Speed-insights-Mobile](./imagenes/page-speed-insights-mobile.png)
[Page-Speed-insights-Desktop](./imagenes/google-test-rich-results.png)
[Page-Speed-insights-Desktop](./imagenes/OpenGraph.png)

---

_Quedo a su disposición para aplicar de cualquier corrección necesaria sobre los entregables y muy agradecido de recibir su guía técnica ante cualquier implementación adicional que requieran para el ecosistema Maguaré._

## 1. Información General y Límite de Peso

- **Formato:** Aplicativo interactivo (Videojuego WebGL).
- **Peso total:** El aplicativo tiene un peso de 41 MB sin comprimir, cumpliendo con el límite objetivo recomendado (≤ 75 MB y no superior a 100 MB).

## 2. Web Performance Optimization (WPO)

- **Peticiones HTTP:** El videojuego opera 100% offline en sus versiones (PC y Android) y en su versión web no realiza llamadas HTTP externas. Solo carga archivos internos locales. Al interactuar con el botón "Salir", el aplicativo redirige a la página principal de Maguaré.

- **Lazy Loading:** Las imágenes correspondientes a la plantilla de carga (logo, barra de progreso y botón de pantalla completa) se ejecutan como fondos mediante CSS (`style.css`), por lo que no es aplicable el atributo `loading="lazy"`. El documento `index.html` no contiene etiquetas `<img>`, `<iframe>` ni `<video>` directas.

- **Carga de Fuentes:** Las tipografías utilizadas son fuentes instaladas nativamente en el dispositivo (`Arial`), evitando descargas adicionales. Las tipografías internas del juego se encuentran empaquetadas en el archivo `.data` y se renderizan dentro del canvas.

- **Minificación:** El motor gráfico Unity procesa automáticamente la minificación de los recursos ejecutables en el empaquetado final.

## 3. Seguridad y Privacidad

- **HTTPS y CORS:** El proyecto no consume APIs externas ni recursos de terceros, eliminando cualquier riesgo asociado a políticas de dominio.

- **Sanitización y Privacidad:** La aplicación no incluye formularios, no solicita datos al usuario ni almacena información de Identificación Personal (PII) mediante Cookies.

## 4. Tracking y Analítica

- **Google Tag Manager (GTM):** Se han reservado e identificado mediante comentarios los bloques exactos en el `<head>` y el `<body>` del archivo `index.html` para la inyección del script contenedor oficial `<!--! GTM: espacio para el script del contenedor oficial de Maguaré -->`

- **Scripts:** No se incluyen eventos personalizados de seguimiento ni se utilizan paquetes de analítica de terceros.

## 5. SEO, Metadatos y Estructura

- **Metadatos Básicos:**
- Se configuró el título como `<title>Semilla - Maguaré - Ministerio de las Culturas de Colombia</title>`.

- Se redactó una meta descripción optimizada detallando la naturaleza del videojuego `<meta
    name="description"
    content="Semilla Interactiva es un videojuego de juego libre para la primera infancia colombiana. Explora cinco mundos llenos de naturaleza y creatividad."
  />`.

- Se incluyó la etiqueta de `viewport` (`width=device-width, initial-scale=1.0`) para diseño responsivo.

- Se generaron 5 resoluciones de iconos (Favicon y App Icons), ubicados en el directorio `TemplateData`.

- **URL Canonical:** La etiqueta `<link rel="canonical" href="...">` se encuentra presente y comentada, a la espera de que el administrador de servidor asigne la ruta absoluta final.

- **Redes Sociales (Open Graph y Twitter Cards):** Se implementaron los metadatos de Open Graph (`og:type`, `og:url`, `og:title`, `og:description`, `og:image`) y Twitter Cards utilizando las dimensiones y el peso reglamentarios (1200x630 píxeles, < 500 KB).

- **HTML Semántico:**
- El documento declara el idioma regional `<html lang="es-CO">`.

- Se incluyó un único `<H1>` con el título del videojuego para mantener la jerarquía semántica.

- Se evitaron los divs genéricos en favor de etiquetas estructurales (`<main>`, `<footer>`, `button`).

- Al ser una Single Page Application (SPA), no cuenta con subpáginas internas HTML.

- **Indexación y Rastreo (Entorno de Pruebas):** Para la actual fase de validación técnica, se configuró la etiqueta obligatoria `<meta name="robots" content="noindex, nofollow" />`, actualmente esta comentada para las pruebas en - **Rendimiento y Core Web Vitals:** [PageSpeed Insights](https://pagespeed.web.dev/?hl=es-419).

- _Nota de QA: Modificar el atributo a `index, follow, max-image-preview:large` previo al paso a producción._

## 6. Accesibilidad, UI y Marca

- **Responsividad (Mobile First):** El código fuente incluye un validador condicional que detecta agentes de usuario móviles y les asigna la clase `unity-mobile` para adaptar el formato a tablets y celulares de forma automática.

- **Identidad de Marca:** Los distintivos institucionales correspondientes al Ministerio y a la convocatoria han sido integrados nativamente dentro de la interfaz del videojuego, acorde a lo establecido en los acuerdos de diseño.

- **Accesibilidad (WCAG 2.1 AA):**
- El diseño cromático del videojuego dispone de un alto contraste visual y soporte audioguiado.

- El control de interacción externa emplea el botón semántico `<button id="unity-fullscreen-button" aria-label="Activar pantalla completa" tabindex="0"></button>`, posibilitando la navegación completa del reproductor web mediante teclado.

## 7. Especificaciones Servidor VPS y Despliegue

- **Entorno de Ejecución:** El aplicativo es estático y agnóstico al backend. Únicamente requiere un servidor web estándar capaz de suministrar archivos estáticos (`.html`, `.wasm`, `.data`). No precisa entornos de ejecución del lado del servidor como Node.js, PHP o Python.

- **Carga Operativa:** El procesamiento gráfico y lógico del aplicativo recae exclusivamente en la memoria RAM del dispositivo cliente (Mobile/Desktop), sin consumo intensivo en el servidor.

- **Base de Datos:** Al no disponer de sistemas de registro de usuarios, no requiere asignación de privilegios para bases de datos.

- **Rutas Relativas y Subdirectorios:** El proyecto está estructurado para operar fluidamente desde cualquier subdirectorio asignado. La variable nativa `var buildUrl = 'Build'` garantiza que el motor WebGL busque y cargue los dependientes binarios de forma paralela al directorio base, anulando llamadas de ruta absoluta.
