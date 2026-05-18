# Modelo de Clasificación Automática de Inventario SAP para Carga en Odoo

# Clasificación y Carga de Artículos SAP hacia Odoo CRM

## Descripción del Proyecto

Este proyecto tiene como objetivo desarrollar una herramienta para preparar, clasificar y cargar artículos provenientes de SAP Business One hacia Odoo, asegurando que cada producto sea identificado correctamente por el API de Odoo dentro del CRM.

La correcta clasificación de los artículos es un punto crítico del proyecto, ya que dependiendo de la categoría asignada, Odoo podrá aplicar distintas reglas de cálculo de inventario, disponibilidad, comportamiento comercial o lógica de integración.

El proyecto busca automatizar este proceso para reducir errores manuales, mejorar la calidad de los datos maestros y facilitar una integración más confiable entre SAP y Odoo.

---

## Contexto del Problema

Actualmente, los artículos del inventario se encuentran registrados en SAP con diferentes descripciones, fabricantes, unidades de medida y estructuras de codificación. Para que estos artículos puedan ser utilizados correctamente dentro de Odoo CRM, es necesario clasificarlos de forma estandarizada.

El problema principal es que no todos los artículos pueden tratarse de la misma manera. Dependiendo de su tipo o categoría, el cálculo de inventario puede variar. Por ejemplo, algunos productos pueden manejarse por unidad, otros por longitud, área, metros, cantidad de costillas o otras unidades comerciales.

Por esta razón, antes de cargar los artículos a Odoo, se requiere una etapa de análisis, limpieza y clasificación automática o semiautomática.

---

## Objetivo General

Desarrollar un proceso automatizado para clasificar artículos provenientes de SAP Business One y prepararlos para su carga correcta hacia Odoo CRM mediante API, considerando reglas de negocio, unidades de medida, fabricantes y análisis de texto sobre las descripciones de producto.

---

## Objetivos Específicos

- Extraer información relevante de los artículos desde SAP Business One.
- Limpiar y normalizar las descripciones de productos.
- Identificar patrones en nombres, códigos, unidades de medida y fabricantes.
- Clasificar los artículos en categorías funcionales para Odoo.
- Definir reglas de clasificación basadas en unidades, fabricantes y palabras clave.
- Evaluar el uso de algoritmos de NLP para clasificación automática.
- Preparar la estructura de datos requerida por el API de Odoo.
- Reducir errores manuales en la carga y categorización de artículos.
- Facilitar el cálculo correcto del inventario según la categoría del producto.

---

## Alcance del Proyecto

El proyecto contempla el procesamiento de artículos provenientes de SAP para su posterior carga a Odoo. La herramienta debe permitir clasificar los artículos según criterios comerciales, técnicos y operativos.

Entre los criterios considerados se incluyen:

- Código del artículo.
- Descripción del artículo.
- Fabricante.
- Unidad de medida.
- Categoría o familia del producto.
- Tipo de producto.
- Reglas específicas de cálculo de inventario.
- Palabras clave dentro de la descripción.
- Patrones técnicos en el nombre del producto.

---

## Enfoque de Clasificación

La clasificación podrá realizarse mediante una combinación de reglas de negocio y modelos de procesamiento de lenguaje natural.

### Clasificación basada en reglas

Se podrán definir reglas en función de criterios como:

- Unidad de medida del artículo.
- Nombre del fabricante.
- Palabras clave en la descripción.
- Estructura del código del producto.
- Familias conocidas de productos.
- Patrones técnicos específicos.

Ejemplos de reglas:

- Si la unidad de medida es `MT`, el artículo puede clasificarse como producto vendido por longitud.
- Si el fabricante pertenece a una familia específica, se puede asignar una categoría técnica determinada.
- Si la descripción contiene palabras como `banda`, `correa`, `rodamiento`, `sensor`, `variador`, `motor`, etc., se puede inferir una categoría inicial.
- Si el producto pertenece a ciertos fabricantes industriales, se pueden aplicar reglas especiales de inventario.

### Clasificación mediante NLP

También se contempla la aplicación de técnicas de NLP para analizar las descripciones de los artículos y clasificarlos automáticamente.

Algunas técnicas posibles incluyen:

- Limpieza y normalización de texto.
- Tokenización de descripciones.
- Extracción de palabras clave.
- Vectorización con `CountVectorizer` o `TF-IDF`.
- Modelos supervisados de clasificación.
- Agrupamiento de productos similares mediante clustering.
- Clasificación semiautomática con revisión manual.

El objetivo del uso de NLP es aprender patrones en las descripciones de productos para mejorar la asignación automática de categorías.

---

## Flujo General del Proyecto

```text
SAP Business One
      ↓
Extracción de artículos
      ↓
Limpieza y normalización de datos
      ↓
Análisis de descripción, unidad y fabricante
      ↓
Clasificación por reglas o modelo NLP
      ↓
Validación de categoría asignada
      ↓
Preparación de estructura para Odoo
      ↓
Carga mediante API de Odoo
      ↓
Uso correcto del artículo dentro del CRM
