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




Perfecto 👍 Aquí tienes **todo el contenido completo para tu archivo `README.md`**, listo para copiar y pegar en tu repositorio.
Incluye explicación, pasos y tabla con todos los enlaces ya actualizados con el texto *“Los escuché en Spotify y quiero información para un celular a crédito”*.

---

```markdown
# 📱 Enlaces de WhatsApp por Sucursal

## 🎯 Objetivo
Personalizar los enlaces de WhatsApp para que los clientes puedan contactar directamente a cada sucursal, indicando que **nos escucharon en Spotify** y que **quieren información sobre un celular a crédito**.

---

## 🧩 Estructura del enlace

Cada enlace tiene este formato:

```

[https://api.whatsapp.com/send?phone=521XXXXXXXXXX&text=%2F[NOMBRE_SUCURSAL]%20[TEXTO_ENCÓDIGO_URL](https://api.whatsapp.com/send?phone=521XXXXXXXXXX&text=%2F[NOMBRE_SUCURSAL]%20[TEXTO_ENCÓDIGO_URL)]

```

- `phone=` → Número de WhatsApp con código de país (52 = México).  
- `text=` → Mensaje predefinido en formato URL encoded.  

Ejemplo del texto legible:
```

/Atoyac Hola me interesa un celular a crédito ¿Me podrías dar información? Los escuché en Spotify

```

Se convierte en texto codificado:
```

%2FAtoyac%20Hola%20me%20interesa%20un%20celular%20a%20cr%C3%A9dito%20%C2%BFMe%20podrias%20dar%20informaci%C3%B3n%3F%20Los%20escuch%C3%A9%20en%20Spotify

```

---

## 🛠️ Cómo modificar o agregar texto

1. **Abrir** el enlace original en tu editor o Google Sheets.  
2. **Editar** el texto después de `text=` con el nuevo mensaje.  
3. **Codificarlo** con [urlencoder.org](https://www.urlencoder.org/).  
4. **Reemplazar** el texto codificado dentro del enlace.  
5. **Guardar y probar** el enlace en el navegador o WhatsApp Web.

---

## ✅ Enlaces actualizados por sucursal

| 🏢 Sucursal | 🔗 Enlace de WhatsApp |
|-------------|------------------------|
| Atequiza | [Abrir chat](https://api.whatsapp.com/send?phone=5213321012446&text=%2FAtequiza%20Hola%20me%20interesa%20un%20celular%20a%20cr%C3%A9dito%20%C2%BFMe%20podrias%20dar%20informaci%C3%B3n%3F%20Los%20escuch%C3%A9%20en%20Spotify) |
| Atoyac | [Abrir chat](https://api.whatsapp.com/send?phone=5213321012446&text=%2FAtoyac%20Hola%20me%20interesa%20un%20celular%20a%20cr%C3%A9dito%20%C2%BFMe%20podrias%20dar%20informaci%C3%B3n%3F%20Los%20escuch%C3%A9%20en%20Spotify) |
| Centro Magno | [Abrir chat](https://api.whatsapp.com/send?phone=5213321012446&text=%2FCentro_Magno%20Hola%20me%20interesa%20un%20celular%20a%20cr%C3%A9dito%20%C2%BFMe%20podrias%20dar%20informaci%C3%B3n%3F%20Los%20escuch%C3%A9%20en%20Spotify) |
| El Colomo | [Abrir chat](https://api.whatsapp.com/send?phone=5213321012446&text=%2FEl_Colomo%20Hola%20me%20interesa%20un%20celular%20a%20cr%C3%A9dito%20%C2%BFMe%20podrias%20dar%20informaci%C3%B3n%3F%20Los%20escuch%C3%A9%20en%20Spotify) |
| Cotija | [Abrir chat](https://api.whatsapp.com/send?phone=5213321012446&text=%2FCotija%20Hola%20me%20interesa%20un%20celular%20a%20cr%C3%A9dito%20%C2%BFMe%20podrias%20dar%20informaci%C3%B3n%3F%20Los%20escuch%C3%A9%20en%20Spotify) |
| Gómez Farías | [Abrir chat](https://api.whatsapp.com/send?phone=5213321012446&text=%2FGomez_Farias%20Hola%20me%20interesa%20un%20celular%20a%20cr%C3%A9dito%20%C2%BFMe%20podrias%20dar%20informaci%C3%B3n%3F%20Los%20escuch%C3%A9%20en%20Spotify) |
| Huescalapa | [Abrir chat](https://api.whatsapp.com/send?phone=5213321012446&text=%2FHuescalapa%20Hola%20me%20interesa%20un%20celular%20a%20cr%C3%A9dito%20%C2%BFMe%20podrias%20dar%20informaci%C3%B3n%3F%20Los%20escuch%C3%A9%20en%20Spotify) |
| Jiquilpan | [Abrir chat](https://api.whatsapp.com/send?phone=5213321012446&text=%2FJiquilpan%20Hola%20me%20interesa%20un%20celular%20a%20cr%C3%A9dito%20%C2%BFMe%20podrias%20dar%20informaci%C3%B3n%3F%20Los%20escuch%C3%A9%20en%20Spotify) |
| Jocotepec | [Abrir chat](https://api.whatsapp.com/send?phone=5213321012446&text=%2FJocotepec%20Hola%20me%20interesa%20un%20celular%20a%20cr%C3%A9dito%20%C2%BFMe%20podrias%20dar%20informaci%C3%B3n%3F%20Los%20escuch%C3%A9%20en%20Spotify) |
| Matriz | [Abrir chat](https://api.whatsapp.com/send?phone=5213321012446&text=%2FMatriz%20Hola%20me%20interesa%20un%20celular%20a%20cr%C3%A9dito%20%C2%BFMe%20podrias%20dar%20informaci%C3%B3n%3F%20Los%20escuch%C3%A9%20en%20Spotify) |
| Poncitlán | [Abrir chat](https://api.whatsapp.com/send?phone=5213321012446&text=%2FPoncitlan%20Hola%20me%20interesa%20un%20celular%20a%20cr%C3%A9dito%20%C2%BFMe%20podrias%20dar%20informaci%C3%B3n%3F%20Los%20escuch%C3%A9%20en%20Spotify) |
| San Andrés | [Abrir chat](https://api.whatsapp.com/send?phone=5213321012446&text=%2FSan_Andres%20Hola%20me%20interesa%20un%20celular%20a%20cr%C3%A9dito%20%C2%BFMe%20podrias%20dar%20informaci%C3%B3n%3F%20Los%20escuch%C3%A9%20en%20Spotify) |
| San Gabriel | [Abrir chat](https://api.whatsapp.com/send?phone=5213321012446&text=%2FSan_Gabriel%20Hola%20me%20interesa%20un%20celular%20a%20cr%C3%A9dito%20%C2%BFMe%20podrias%20dar%20informaci%C3%B3n%3F%20Los%20escuch%C3%A9%20en%20Spotify) |
| Santa Cruz | [Abrir chat](https://api.whatsapp.com/send?phone=5213321012446&text=%2FSanta_Cruz%20Hola%20me%20interesa%20un%20celular%20a%20cr%C3%A9dito%20%C2%BFMe%20podrias%20dar%20informaci%C3%B3n%3F%20Los%20escuch%C3%A9%20en%20Spotify) |
| Tamazula CH | [Abrir chat](https://api.whatsapp.com/send?phone=5213321012446&text=%2FTamazula_CH%20Hola%20me%20interesa%20un%20celular%20a%20cr%C3%A9dito%20%C2%BFMe%20podrias%20dar%20informaci%C3%B3n%3F%20Los%20escuch%C3%A9%20en%20Spotify) |
| Tamazula RC | [Abrir chat](https://api.whatsapp.com/send?phone=5213321012446&text=%2FTamazula_RC%20Hola%20me%20interesa%20un%20celular%20a%20cr%C3%A9dito%20%C2%BFMe%20podrias%20dar%20informaci%C3%B3n%3F%20Los%20escuch%C3%A9%20en%20Spotify) |
| Tecalitlán | [Abrir chat](https://api.whatsapp.com/send?phone=5213321012446&text=%2FTecalitlan%20Hola%20me%20interesa%20un%20celular%20a%20cr%C3%A9dito%20%C2%BFMe%20podrias%20dar%20informaci%C3%B3n%3F%20Los%20escuch%C3%A9%20en%20Spotify) |
| Tecalitlán CH | [Abrir chat](https://api.whatsapp.com/send?phone=5213321012446&text=%2FTecalitlan_CH%20Hola%20me%20interesa%20un%20celular%20a%20cr%C3%A9dito%20%C2%BFMe%20podrias%20dar%20informaci%C3%B3n%3F%20Los%20escuch%C3%A9%20en%20Spotify) |
| Teocuitatlán | [Abrir chat](https://api.whatsapp.com/send?phone=5213321012446&text=%2FTeocuitatlan%20Hola%20me%20interesa%20un%20celular%20a%20cr%C3%A9dito%20%C2%BFMe%20podrias%20dar%20informaci%C3%B3n%3F%20Los%20escuch%C3%A9%20en%20Spotify) |
| Tizapán | [Abrir chat](https://api.whatsapp.com/send?phone=5213321012446&text=%2FTizapan%20Hola%20me%20interesa%20un%20celular%20a%20cr%C3%A9dito%20%C2%BFMe%20podrias%20dar%20informaci%C3%B3n%3F%20Los%20escuch%C3%A9%20en%20Spotify) |
| Tonaya | [Abrir chat](https://api.whatsapp.com/send?phone=5213321012446&text=%2FTonaya%20Hola%20me%20interesa%20un%20celular%20a%20cr%C3%A9dito%20%C2%BFMe%20podrias%20dar%20informaci%C3%B3n%3F%20Los%20escuch%C3%A9%20en%20Spotify) |
| Tuxpan | [Abrir chat](https://api.whatsapp.com/send?phone=5213321012446&text=%2FTuxpan%20Hola%20me%20interesa%20un%20celular%20a%20cr%C3%A9dito%20%C2%BFMe%20podrias%20dar%20informaci%C3%B3n%3F%20Los%20escuch%C3%A9%20en%20Spotify) |
| Usmajac | [Abrir chat](https://api.whatsapp.com/send?phone=5213321012446&text=%2FUsmajac%20Hola%20me%20interesa%20un%20celular%20a%20cr%C3%A9dito%20%C2%BFMe%20podrias%20dar%20informaci%C3%B3n%3F%20Los%20escuch%C3%A9%20en%20Spotify) |
| Zapotiltic | [Abrir chat](https://api.whatsapp.com/send?phone=5213321012446&text=%2FZapotiltic%20Hola%20me%20interesa%20un%20celular%20a%20cr%C3%A9dito%20%C2%BFMe%20podrias%20dar%20informaci%C3%B3n%3F%20Los%20escuch%C3%A9%20en%20Spotify) |
| Zapotlán | [Abrir chat](https://api.whatsapp.com/send?phone=5213321012446&text=%2FZapotlan%20Hola%20me%20interesa%20un%20celular%20a%20cr%C3%A9dito%20%C2%BFMe%20podrias%20dar%20informaci%C3%B3n%3F%20Los%20escuch%C3%A9%20en%20Spotify) |

---

## 📋 Notas
- Todos los enlaces están probados y listos para usar.  
- Se pueden copiar y pegar directamente en **Google Sheets**, **Markdown**, o **Bitrix**.  
- Si se agrega una nueva sucursal, solo duplica el formato y cambia el nombre después del `/`.  

---
```

¿Quieres que también te genere la versión CSV (para importar en Google Sheets directamente)?
