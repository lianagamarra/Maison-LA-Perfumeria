# Maison La Perfumería — catálogo

Sitio estático sin dependencias ni backend. Incluye catálogo responsive, búsqueda, filtros, ordenamiento, detalles, carrito con `localStorage` y preparación de pedido por WhatsApp. Los nombres, precios e imágenes proporcionados por el negocio se incluyen en el catálogo. Yara, Asad y Asad Bourbon aparecen con precio por confirmar y no se pueden agregar al carrito hasta configurarlo. La disponibilidad se debe confirmar y las presentaciones no indicadas quedan por confirmar.

## Ejecutar localmente

Abre `index.html` en un navegador moderno. Para simular un alojamiento web local, desde esta carpeta ejecuta `python -m http.server 8000` y visita `http://localhost:8000`.

## Personalizar

- **Nombre e identidad:** el encabezado y el pie usan temporalmente el rótulo tipográfico “Maison La”. Para usar el logo oficial, añade el archivo original a `assets/` y reemplaza el bloque `.brand` en `index.html`. El nombre del negocio aparece en `index.html` y en `BUSINESS_NAME` dentro de `app.js`.
- **WhatsApp:** en la primera línea de configuración de `app.js`, cambia `BUSINESS_WHATSAPP` por el número real en formato internacional, solo dígitos; por ejemplo, Colombia empieza por `57`. Está vacío a propósito. Mientras no se configure, el sitio no abre un enlace de pedido y muestra un aviso.
- **Productos, precios, inventario e imágenes:** edita `products.js`. Cada objeto contiene `id`, `name`, `brand`, `category`, `tags`, `description`, `notes`, `ml` (usa `null` si falta confirmar), `price` (usa `null` para mostrar “Precio por confirmar” y bloquear agregar al carrito), `oldPrice` (opcional), `image`, `available`, `featured` y `newest` (un orden numérico para novedades). Los precios se guardan como pesos colombianos completos; por ejemplo, 180 se convierte en 180000. Las imágenes de producto están en `assets/productos/`.
- **Filtros:** cambia `CATEGORIES` en `app.js` para que correspondan a las categorías usadas en `products.js`.

No existe un panel administrativo: los cambios de productos se realizan en `products.js`. El carrito queda guardado en el navegador del cliente. Los pedidos se terminan de enviar manualmente desde WhatsApp; la web no confirma un envío ni cobra en línea. El domicilio aparece como “por confirmar” y no se suma al total porque no hay una tarifa configurada.

## Publicar

Al ser archivos estáticos, puedes desplegar la carpeta en cualquier hosting de sitios estáticos. Antes de publicar, confirma existencias y presentaciones, configura el WhatsApp del negocio y prueba el enlace desde un teléfono.
