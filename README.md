# Loading PLP — Prototipo Repsol

Prototipo interactivo de Product Listing Page (PLP) para la tienda online de Repsol que demuestra las recomendaciones del benchmark sobre carga y paginación de productos.

## Qué se demuestra

Las seis recomendaciones aplicadas en un solo flujo navegable:

1. **URL como fuente de verdad.** Filtros, orden y lote actual se reflejan en la URL en tiempo real (`?page=2&filter=movil&sort=price_desc`). Hay un panel inferior que muestra siempre la URL activa.
2. **Botón clicable "Mostrar más" + contador.** Al final de cada lote, botón explícito con "Has visto X de Y productos" y barra de progreso. Sin auto-load ni spinners automáticos.
3. **`history.pushState()` real.** Cada acción genera una entrada en el historial del navegador. El back-button funciona de forma nativa.
4. **Carga directa de URL profunda.** Abrir `?page=3` muestra solo ese lote, con un botón "Mostrar lote anterior" arriba. El receptor del enlace aterriza donde el emisor estaba, no en el principio.
5. **Lazy-loading de imágenes.** Atributo `loading="lazy"` en los elementos de imagen.
6. **Tamaño de lote responsive.** 12 productos en desktop / 8 en mobile (en producción serían 36/24).

## Cómo probarlo

Abre `index.html` en cualquier navegador o accede a la URL desplegada.

Cosas que merece la pena probar en directo:

- Filtra por "Tier 2-3-4" + ordena por precio descendente. Copia la URL y pégala en otra pestaña: deberías ver lo mismo.
- Carga 3 lotes, abre un producto y cierra. Vuelves al producto exacto con micro-highlight visual.
- Cambia manualmente la URL a `?page=2&filter=movil` y refresca. Aterriza en ese lote concreto con botón "Mostrar anterior" disponible.
- Pulsa el back-button del navegador repetidamente: deshace cada acción de forma coherente.

## Stack

HTML + CSS + JavaScript vanilla. Sin dependencias salvo Google Fonts (Poppins + Open Sans) cargadas vía CDN. Un único archivo `index.html` autocontenido.

## Contexto

Este prototipo nace de un benchmark sobre cómo Amazon, ASOS, Skechers, Zara, IKEA, El Corte Inglés y Muji resuelven la carga y paginación de productos en PLPs. Las conclusiones llevaron a recomendar el patrón de El Corte Inglés con dos correcciones: botón clicable en lugar de spinner automático, y URLs paginadas tipo `?page=N` en lugar de offsets de productos.
