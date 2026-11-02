# CHANGELOG

## [0.1.0] — 2026-11-02

### Añadido
- Webhook `POST /nutrition-check` como punto de entrada.
- Validación para detectar códigos de barras ausentes.
- Validación para comprobar que el código de barras sea numérico.
- Consulta de productos a través de la API de Open Food Facts.
- Comprobación de si el producto existe en la base de datos.
- Nodo Edit Fields para preparar los datos del producto.
- Nodo Code para clasificar los datos nutricionales.
- Integración de Groq mediante Basic LLM Chain para generar recomendaciones.
- Nodo de preparación de la recomendación.
- Respuesta final del webhook con la información del producto.

### Gestión de errores
- Respuesta para códigos de barras ausentes.
- Respuesta para códigos de barras no válidos.
- Respuesta cuando el producto no se encuentra en Open Food Facts.

### Pendiente
- Incorporar la rama independiente para obtener la lectura del Nutri-Score y combinarla mediante Merge Append.
- Ejecutar y registrar las pruebas funcionales reales.
