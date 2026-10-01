# professional-unit-converter

Sistema integral de conversión de medidas desarrollado como una Single Page Application (SPA). Construido utilizando HTML5, Tailwind CSS y JavaScript orientado a objetos (ES6+).

Este proyecto proporciona una herramienta de alta precisión para la conversión matemática entre múltiples sistemas métricos e imperiales, procesando los cálculos del lado del cliente en tiempo real mediante una arquitectura de componentes escalable y basada en datos.

## Tabla de Contenidos

- [Demostración](#demostración)
- [Capturas de Pantalla](#capturas-de-pantalla)
- [Características Principales](#características-principales)
- [Arquitectura y Estructura de Datos](#arquitectura-y-estructura-de-datos)
- [Tecnologías Utilizadas](#tecnologías-utilizadas)
- [Instalación y Ejecución](#instalación-y-ejecución)
- [Extensibilidad](#extensibilidad)
- [Licencia](#licencia)

## Demostración

El aplicativo se encuentra disponible y desplegado para su uso en producción a través de GitHub Pages:

[Enlace al Conversor en vivo] (Reemplaza este texto con tu enlace de GitHub Pages)

## Capturas de Pantalla

[Instrucción: Agrega capturas de pantalla de la interfaz en dispositivos de escritorio y móviles dentro de un directorio /assets y actualiza las rutas]

**Interfaz de Conversor (Escritorio):**
![Vista de Escritorio][(https://i.ibb.co/Gvvdy5F8/image.png)

## Características Principales

*   **Conversión en Tiempo Real:** Los cálculos se ejecutan instantáneamente a través de "Event Listeners" atados a los inputs y selects, eliminando la necesidad de botones de envío.
*   **Múltiples Magnitudes:** Soporte nativo para Longitud, Peso/Masa, Área, Volumen y Temperatura.
*   **Intercambio Rápido:** Función de inversión de unidades (swap) que invierte el origen y destino con un solo clic.
*   **Mitigación de Errores de Punto Flotante:** Implementación de formateo de salida (máximo 6 decimales) para corregir las imprecisiones aritméticas estándar del motor V8 de JavaScript.
*   **Diseño Adaptable (Responsive Design):** Interfaz fluida basada en CSS Grid y Flexbox que asegura usabilidad tanto en pantallas panorámicas como en dispositivos móviles.

## Arquitectura y Estructura de Datos

El diseño del software se fundamenta en separar estrictamente la configuración (datos) de la lógica de negocio (clase JS):

1.  **Patrón "Base Unit" (Unidad Base):** 
    En lugar de crear una matriz NxN de conversiones (lo que requeriría cientos de condicionales), el sistema emplea una estructura de complejidad O(N). Para cada categoría (ej. Longitud), se define una "Unidad Base" (ej. el metro con un factor de 1). Cualquier conversión se realiza primero transformando el valor de origen a la unidad base, y luego dividiendo por el factor de la unidad de destino.

2.  **Evaluación Condicional de Fórmulas:**
    Para magnitudes no lineales como la Temperatura, la clase `UnitConverter` detecta la propiedad `isFormulaBased` dentro del objeto de datos. Esto interrumpe el flujo algorítmico estándar y delega el cálculo a un método especializado (`convertTemperature`).

3.  **Encapsulamiento:**
    Toda la interacción con el Modelo de Objetos del Documento (DOM) se maneja a través de la instanciación de la clase `UnitConverter`, asegurando que no existan variables contaminando el ámbito global (Global Scope).

## Tecnologías Utilizadas

*   **HTML5:** Marcado semántico y validación de tipos de entrada numéricos.
*   **Tailwind CSS (V3 - vía CDN):** Utilitarios para el diseño de la interfaz de usuario, control de estados (hover, focus) y manejo responsivo.
*   **JavaScript (Vanilla ES6):** Lógica funcional de la aplicación.

## Instalación y Ejecución

El proyecto es estático y no requiere dependencias de servidor.

1. Clonar el repositorio en el entorno local:
   ```bash
   git clone [https://github.com/TU_USUARIO/professional-unit-converter.git](https://github.com/TU_USUARIO/professional-unit-converter.git)
