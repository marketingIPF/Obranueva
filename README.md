# RK Obra Nueva — Dashboard de Promociones

Dashboard PWA para mostrar en oficina las promociones de obra nueva de RK Palanca Fontestad. Los clientes pueden seleccionar viviendas favoritas y se les envía un correo con toda la información.

## ¿Qué es esto?

Una app web (instalable como PWA, igual que Drape) que vive en el navegador. Los datos se cargan desde un Excel y se guardan localmente en el dispositivo (IndexedDB). No necesita servidor.

## Archivos incluidos

- `index.html` — Dashboard completo
- `manifest.json` — Configuración PWA
- `sw.js` — Service Worker (offline básico)
- `icon-192.png` y `icon-512.png` — Iconos de la app
- `plantilla_dashboard_obra_nueva.xlsx` — Excel con datos de ejemplo

## Cómo desplegarlo (recomendado: GitHub Pages)

Igual que Drape:

1. Crea un repo nuevo en GitHub, p. ej. `rkObraNueva`.
2. Sube los archivos `index.html`, `manifest.json`, `sw.js`, `icon-192.png`, `icon-512.png`.
3. En Settings → Pages, activa GitHub Pages desde la rama `main`.
4. Tu dashboard estará en `https://robertoarroyo89.github.io/rkObraNueva/`.

Para usarlo en la oficina, abre esa URL en la tablet, dale a "Añadir a pantalla de inicio" y se instalará como app.

## Cómo cargar las viviendas

1. Abre el dashboard.
2. Haz clic en el icono ⚙ (arriba derecha).
3. Carga el Excel con las dos hojas (`Promociones` y `Viviendas`).
4. Listo. Los datos se guardan y siguen ahí cuando vuelvas a abrir.

Para actualizar precios o añadir viviendas, edita el Excel y vuelve a cargarlo (sobrescribe los datos anteriores).

## Estructura del Excel

**Hoja "Promociones"** — Una fila por promoción:
`id_promocion`, `nombre`, `ubicacion`, `municipio`, `estado`, `descripcion`, `fecha_entrega_prevista`, `imagen_principal_url`

Estados válidos: `precomercializacion`, `con_licencia`, `en_obras`, `terminada`.

**Hoja "Viviendas"** — Una fila por vivienda:
`id_vivienda`, `id_promocion`, `numero`, `estado`, `habitaciones`, `banos`, `m2_construidos`, `m2_utiles`, `terraza_m2`, `balcon`, `planta`, `orientacion`, `garaje`, `trastero`, `precio`, `plano_2d_url`, `plano_3d_url`, `fotos_urls`, `certificacion_energetica`

Estados válidos: `disponible`, `reservada`, `vendida`, `precomercializacion`.

`id_promocion` debe coincidir con uno existente en la hoja Promociones.

`fotos_urls` admite varias URLs separadas por comas.

## Uso en oficina

1. El cliente llega y abre el dashboard en la tablet.
2. Filtra por promoción, habitaciones o precio.
3. Toca el corazón en las viviendas que le gustan.
4. Pulsa "Favoritas" arriba a la derecha.
5. Introduce su email y se abre el cliente de correo con todo formateado, listo para enviar.

En administración puedes configurar un email interno para recibir copia (CC) de cada envío.

## Atajos

- `ESC` cierra modales y paneles.
- Las imágenes pueden ser URLs externas (Unsplash, tu hosting, Imgur…).
- Las viviendas vendidas/reservadas se ocultan por defecto. Activa el toggle si quieres mostrarlas en gris.
