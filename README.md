# 📍 Catálogo Dinámico de Sucursales Celucenter

## ✅ Objetivo

Crear una página web dinámica y visual donde se muestren las sucursales de Celucenter con:

- 📷 Foto representativa  
- 🏢 Dirección completa  
- ☎️ Teléfono de contacto  
- 📍 Link directo a Google Maps  

---

## 🗂️ Fuente de Datos

**Google Sheet publicado (pestaña `Lista CC`):**  
[Ver hoja pública](https://docs.google.com/spreadsheets/d/e/2PACX-1vQfbWoU8K3d4aAPvn6tBUvdFcdms6zjSa7_8E9bfMBShsdDdZf117-X2lVpH8LABasKzCIFzPFyremr/pubhtml?gid=1856771547&single=true)

**API JSON a través de OpenSheet:**  
`https://opensheet.elk.sh/1La-5XY4i9Ng3zpiXrre5tyAqANxpb9yuZeS8muFiZXA/Lista%20CC`

Documento para Editar:
https://docs.google.com/spreadsheets/d/1La-5XY4i9Ng3zpiXrre5tyAqANxpb9yuZeS8muFiZXA/edit?gid=1856771547#gid=1856771547 
---

## 📸 Repositorio de Imágenes

Las imágenes se alojan en GitHub y se consumen desde:  
📁 [`/fotos`](https://github.com/piztian/SucursalesCelucenter/tree/main/fotos)

**Ejemplo de ruta de imagen:**  
`https://raw.githubusercontent.com/piztian/SucursalesCelucenter/main/fotos/Atequiza.jpg`

---

## 🧠 Estructura esperada por el HTML

Cada objeto JSON debe contener:

- `Nombre de Sucursal`  
- `Dirección`  
- `Teléfono de Tienda`  
- `Link de Ubicación en Maps`  
- `URL` (link directo a la imagen)  
- `Archivo` (nombre del archivo de imagen)  

---

## 💻 HTML generado dinámicamente

- Cada sucursal se muestra como una **card** visual  
- Imagen con enlace directo al mapa (nueva ventana)  
- Diseño responsivo con CSS Grid  
- Compatible con pantallas móviles  

---

## 💡 Personalización

Puedes editar directamente el Google Sheet para:

- Agregar nuevas sucursales  
- Cambiar imágenes desde el GitHub  
- Corregir direcciones o teléfonos  

🔁 **Los cambios se reflejan automáticamente en la web sin tocar el código HTML**
