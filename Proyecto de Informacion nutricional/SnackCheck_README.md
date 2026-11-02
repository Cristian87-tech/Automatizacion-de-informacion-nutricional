# SnackCheck — Revisión de alimentos

## ¿Para qué sirve?
SnackCheck permite consultar un alimento usando su código de barras y conocer, de forma sencilla, si es una buena opción para el día a día o si conviene consumirlo solo de vez en cuando.

La información nutricional se obtiene de Open Food Facts, una base de datos pública de alimentos.

## ¿Cómo funciona?
1. La persona envía el código de barras del producto.
2. SnackCheck comprueba que el código esté presente y que solo contenga números.
3. Busca el producto en Open Food Facts.
4. Lee su nombre, marca, Nutri-Score y los datos de azúcar, sal y grasa por cada 100 gramos.
5. Compara esos datos con las reglas de evaluación.
6. La inteligencia artificial redacta una explicación breve y fácil de entender.
7. SnackCheck devuelve el resultado con un titular, los datos principales y una recomendación.

## ¿Cómo se usa?
Envía una solicitud con el código de barras del producto.

Ejemplo de información enviada:

```json
{
  "barcode": "3017620422003"
}
```

Si no se envía un código de barras, SnackCheck explica qué información necesita y muestra un ejemplo.

## ¿Cómo se decide el resultado?
SnackCheck revisa tres datos por cada 100 gramos:

- **Azúcar:** se considera alto si supera los 22,5 gramos.
- **Sal:** se considera alta si supera los 1,5 gramos.
- **Grasa:** se considera alta si supera los 17,5 gramos.

Después, cuenta cuántos de estos datos son altos:

- Ninguno: saludable.
- Uno: moderado.
- Dos o tres: no saludable.

También tiene en cuenta la letra del Nutri-Score:
- A o B: saludable.
- C: moderado.
- D o E: no saludable.

Si las dos evaluaciones dan resultados diferentes, SnackCheck muestra el resultado menos favorable. Si no hay Nutri-Score, utiliza la evaluación de los nutrientes.

La puntuación de preocupación indica cuántos de los tres nutrientes están altos, de 0 a 3. No determina por sí sola el resultado final.

## ¿Qué pasa si hay un problema?
- **Falta el código de barras:** muestra instrucciones y un ejemplo.
- **El código contiene letras u otros caracteres:** explica que debe contener solo números.
- **El producto no aparece en la base de datos:** informa que no se encontró y ofrece un ejemplo de código válido.
- **Faltan datos nutricionales:** indica que no hay información suficiente para evaluar el producto.

## ¿Qué se necesita para configurarlo?
- Una cuenta de n8n.
- Una clave de Groq para generar la explicación.
- Open Food Facts, que se puede consultar gratuitamente y sin crear una cuenta.

## Limitaciones
La información depende de los datos disponibles en Open Food Facts, que pueden estar incompletos o desactualizados. La evaluación es orientativa y no sustituye el consejo de un profesional de la salud.
