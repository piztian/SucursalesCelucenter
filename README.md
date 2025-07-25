# 🏪 Catálogo Dinámico de Sucursales - Celucenter

Este repositorio contiene las imágenes de las **sucursales de Celucenter** y sirve como fuente visual para una página HTML dinámica conectada a Google Sheets.

---

## 🧩 ¿Cómo funciona?

1. Las imágenes de las sucursales están alojadas en este repositorio (carpeta `/pics`).
2. Un archivo HTML consulta automáticamente una hoja de cálculo de Google Sheets para obtener:
   - Nombre de la sucursal
   - Dirección
   - Teléfono
   - Enlace de Google Maps
   - Nombre del archivo de imagen
3. El HTML genera un catálogo visual donde cada tarjeta muestra una sucursal, y al dar clic en la imagen se abre su ubicación en Google Maps.

---

## 📋 Estructura esperada de la hoja de cálculo (Google Sheets)

El HTML se conecta vía `opensheet.elk.sh` y espera una hoja llamada `Lista CC` con las siguientes columnas:

| archivo (imagen) | url_imagen | Nombre | Dirección | Teléfono | Mapa |
|------------------|------------|--------|-----------|----------|------|
| ATEQUIZA.jpg     | https://raw.githubusercontent.com/piztian/sucursales/main/pics/ATEQUIZA.jpg | Atequiza | Calle X #123 | 341 123 4567 | https://maps.google.com/?q=... |

> 📝 Asegúrate de que los nombres de archivo coincidan exactamente con los que están subidos al repositorio.

---

## 🔗 Recursos usados

- 📷 Imágenes en GitHub (ruta pública)
- 📊 Datos desde Google Sheets (via [opensheet.elk.sh](https://opensheet.elk.sh))
- 🌐 HTML dinámico que consume el JSON del Sheet y lo transforma en tarjetas visuales

---

## 🚀 Próximos pasos

- [ ] Subir imágenes de sucursales a la carpeta `/pics`
- [ ] Copiar rutas directas de las imágenes
- [ ] Insertar nombres de archivo y URLs en la hoja “Lista CC”
- [ ] Activar el catálogo HTML

---

## 🌍 Créditos

Proyecto desarrollado por el equipo de Celucenter para automatizar la presentación de sucursales con acceso rápido a contacto y ubicación.
