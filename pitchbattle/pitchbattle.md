# ⚡ PITCH BATTLE - GUÍA COMPLETA

## 📋 Índice
1. [Introducción](#introducción)
2. [Componentes del Sistema](#componentes-del-sistema)
3. [Requisitos Previos](#requisitos-previos)
4. [Configuración Inicial](#configuración-inicial)
5. [Descripción de Páginas](#descripción-de-páginas)
6. [Flujo de Eventos](#flujo-de-eventos)
7. [Instrucciones para Equipos](#instrucciones-para-equipos)
8. [Manual de Uso](#manual-de-uso)
9. [Solución de Problemas](#solución-de-problemas)

---

## Introducción

**PITCH BATTLE** es un sistema interactivo de competencia de ventas basado en los principios de Grant Cardone. Permite que 5 equipos de 10 personas cada uno presenten un producto ficción en 5 minutos, siendo evaluados por 3 jurados simultáneamente.

**Objetivo:** Entrenar vendedores 10X con energía, dominio de producto y manejo de objeciones.

**Duración Total:** 40 minutos
- 📋 Preparación: 10 minutos
- 🎤 Presentaciones: 5 minutos × 5 equipos = 25 minutos
- 🏆 Ranking Final: 5 minutos

---

## Componentes del Sistema

El sistema consta de **5 páginas HTML independientes**:

### 1. **Página Principal - Pitch Battle**
- **Propósito:** Pantalla de proyección principal para toda la audiencia
- **Dispositivo:** Proyector/Pantalla grande
- **Contenido:**
  - Equipo actual presentando
  - Producto asignado con descripción completa
  - Timer de 5 minutos (cuenta regresiva)
  - Ranking en vivo (actualiza cada 2 segundos)
  - Productos disponibles

### 2. **Panel Jurado 1**
- **Propósito:** Calificación independiente del Jurado 1
- **Dispositivo:** Laptop, tablet o teléfono del Jurado 1
- **Función:** Seleccionar equipo y calificar 6 criterios (1-5 puntos)

### 3. **Panel Jurado 2**
- **Propósito:** Calificación independiente del Jurado 2
- **Dispositivo:** Laptop, tablet o teléfono del Jurado 2
- **Función:** Seleccionar equipo y calificar 6 criterios (1-5 puntos)

### 4. **Panel Jurado 3**
- **Propósito:** Calificación independiente del Jurado 3
- **Dispositivo:** Laptop, tablet o teléfono del Jurado 3
- **Función:** Seleccionar equipo y calificar 6 criterios (1-5 puntos)

### 5. **Guía de Instrucciones**
- **Propósito:** Orientación para los equipos antes de comenzar
- **Dispositivo:** Pantalla grande o impreso
- **Contenido:**
  - Qué es Pitch Battle
  - Instrucciones paso a paso
  - Criterios de puntuación
  - Recomendaciones por criterio
  - Estructura de 5 minutos
  - Tips para ganar

---

## Requisitos Previos

### Hardware
- ✅ 1 proyector o pantalla grande (para página principal)
- ✅ 3 dispositivos adicionales (laptops, tablets o smartphones para jurados)
- ✅ Conexión a internet en todos los dispositivos
- ✅ Micrófono (opcional, pero recomendado)

### Software
- ✅ Navegador web moderno (Chrome, Firefox, Safari, Edge)
- ✅ Google Sheet compartido públicamente
- ✅ Apps Script configurado en Google Sheets

### Acceso a Internet
- ✅ Conexión WiFi estable en toda la zona
- ✅ Ancho de banda suficiente para 4+ conexiones simultáneas

---

## Configuración Inicial

### Paso 1: Crear Google Sheet para Calificaciones

1. Entra a https://sheets.google.com
2. Crea un nuevo Sheet llamado **"PITCH BATTLE CALIFICACIONES"**
3. En la primera pestaña, estructura así:

```
Columna A: Equipo
Columna B: Jurado1_Total
Columna C: Jurado2_Total
Columna D: Jurado3_Total
Columna E: Promedio (opcional)
```

**Ejemplo de filas:**
```
Los Titanes          | 28 | 27 | 29
Vendedores Imparables | 25 | 26 | 24
Guerreros 10X        | 26 | 28 | 27
Dinastía de Ventas   | 24 | 25 | 26
El Equipo Dorado     | 29 | 28 | 30
```

### Paso 2: Compartir el Google Sheet

1. Click en **Compartir** (arriba a la derecha)
2. Cambiar a **"Cualquiera con el enlace puede editar"**
3. **COPIAR EL LINK** - Será: `https://docs.google.com/spreadsheets/d/[ID]/edit?usp=sharing`
4. **GUARDAR EL ID** (la parte entre `/d/` y `/edit`)

**Ejemplo de ID:**
```
1XbOAGQd8RLfR4EIWavqKDSV7G-Z6Zc1v4cuXmYnSmZM
```

### Paso 3: Configurar Apps Script

1. En tu Google Sheet, click en **Extensiones → Apps Script**
2. Reemplaza TODO el código con esto:

```javascript
function doPost(e) {
  const sheet = SpreadsheetApp.getActiveSheet();
  const datos = JSON.parse(e.postData.contents);
  
  // Buscar la fila del equipo
  const range = sheet.getRange('A:A');
  const values = range.getValues();
  let filaEquipo = -1;
  
  for (let i = 1; i < values.length; i++) {
    if (values[i][0] === datos.equipo) {
      filaEquipo = i + 1;
      break;
    }
  }
  
  if (filaEquipo === -1) {
    // Si no existe, crear nueva fila
    sheet.appendRow([datos.equipo, '', '', '']);
    filaEquipo = sheet.getLastRow();
  }
  
  // Guardar según el jurado
  if (datos.jurado === 'Jurado1') {
    sheet.getRange(filaEquipo, 2).setValue(datos.total);
  } else if (datos.jurado === 'Jurado2') {
    sheet.getRange(filaEquipo, 3).setValue(datos.total);
  } else if (datos.jurado === 'Jurado3') {
    sheet.getRange(filaEquipo, 4).setValue(datos.total);
  }
  
  return ContentService.createTextOutput('OK');
}
```

3. Click en **Deploy → New deployment**
4. Tipo: **Web app**
5. Execute as: **Tu cuenta**
6. Who has access: **Anyone**
7. Click **Deploy**
8. **COPIAR LA URL** que genera (ejemplo):
```
https://script.google.com/macros/s/AKfycbyoBFl05dnuIDu8CXRPk6MdVvl72fxOJm56i7V7TakjJePTHQT0tSYJb8JEgSvMLnWZug/exec
```

### Paso 4: Actualizar URLs en las Páginas

En cada página de Jurado (1, 2, 3), busca esta línea:

```javascript
const urlSheet = 'https://script.google.com/macros/s/AKfycbyoBFl05dnuIDu8CXRPk6MdVvl72fxOJm56i7V7TakjJePTHQT0tSYJb8JEgSvMLnWZug/exec';
```

Y reemplázala con TU URL de Apps Script.

En la página principal, busca:

```javascript
const sheetId = '1XbOAGQd8RLfR4EIWavqKDSV7G-Z6Zc1v4cuXmYnSmZM';
```

Y reemplázalo con TU ID de Sheet.

---

## Descripción de Páginas

### 📺 Página Principal - Pitch Battle

**URL:** Guárdala como `pitch-battle-principal.html`

**Pantalla:**
```
┌─────────────────────────────────────────────┐
│  ⚡ PITCH BATTLE                             │
├──────────────────┬──────────────────────────┤
│  EQUIPO ACTUAL   │  TIEMPO: 5:00            │
│  Los Titanes     │  [- 5s] [+ 5s]          │
│  SmartBand 10X   │  Máximo: 5 min          │
│  [Descripción]   │                         │
├──────────────────────────────────────────────┤
│  🏆 RANKING EN VIVO                          │
│  🥇 1. Los Titanes      J1:28 J2:27 J3:29   │
│  🥈 2. Guerreros 10X    J1:26 J2:28 J3:27   │
│  🥉 3. El Equipo Dorado J1:29 J2:28 J3:30   │
├──────────────────────────────────────────────┤
│  📦 PRODUCTOS DISPONIBLES                    │
│  [SmartBand] [CloudPhone] [Tablet] [...]    │
└──────────────────────────────────────────────┘
```

**Funcionalidades:**
- ✅ Seleccionar equipo actual
- ✅ Ver producto asignado con descripción completa
- ✅ Timer de 5 minutos con controles (-5s, +5s, Reset)
- ✅ Ranking en vivo (actualiza cada 2 segundos)
- ✅ Botón Random para mezclar productos
- ✅ Lee directamente de Google Sheets

**Controles:**
```
▶ INICIAR TIEMPO   - Comienza el contador
⏸ PAUSAR          - Pausa el tiempo
🔄 RESET          - Reinicia a 5:00
🔀 RANDOM         - Mezcla productos entre equipos
-- SELECCIONAR EQUIPO -- - Dropdown con 5 equipos
```

---

### 📱 Panel Jurado 1, 2, 3

**URLs:** 
- `pitch-battle-jurado1.html`
- `pitch-battle-jurado2.html`
- `pitch-battle-jurado3.html`

**Pantalla:**
```
┌────────────────────────────────┐
│  ⚡ PITCH BATTLE              │
│  👨‍⚖️ JURADO 1                 │
├────────────────────────────────┤
│  Selecciona Equipo:            │
│  [-- SELECCIONAR EQUIPO --]    │
├────────────────────────────────┤
│  LOS TITANES                   │
│  SmartBand 10X                 │
├────────────────────────────────┤
│  📊 CALIFICACIÓN DEL EQUIPO    │
│                                │
│  1️⃣ Gancho/Presentación        │
│  [1-Deficiente ▼]              │
│                                │
│  2️⃣ Descripción Producto       │
│  [2-Regular ▼]                 │
│                                │
│  3️⃣ Manejo de Objeciones       │
│  [3-Bueno ▼]                   │
│                                │
│  4️⃣ Energía/Convencimiento     │
│  [4-Muy Bueno ▼]               │
│                                │
│  5️⃣ Cierre Efectivo            │
│  [5-Excelente ▼]               │
│                                │
│  6️⃣ Participación del Equipo   │
│  [5-Todo el equipo participa ▼]│
│                                │
│  TOTAL: 24 / 30                │
│                                │
│  [✓ GUARDAR CALIFICACIÓN]      │
│  [🔄 LIMPIAR]                  │
└────────────────────────────────┘
```

**Funcionalidades:**
- ✅ Selector de equipo (dropdown)
- ✅ 6 criterios de puntuación (1-5 puntos)
- ✅ Cálculo automático de total
- ✅ Guardar en Google Sheets automáticamente
- ✅ Mostrar mensaje de confirmación
- ✅ Opción de limpiar/resetear

**Criterios:**
1. **Gancho/Presentación** (1-5): ¿Captan atención desde el inicio?
2. **Descripción Producto** (1-5): ¿Explican bien qué es?
3. **Manejo Objeciones** (1-5): ¿Responden rápido y bien?
4. **Energía/Convencimiento** (1-5): ¿Transmiten pasión?
5. **Cierre Efectivo** (1-5): ¿Piden la venta claramente?
6. **Participación Equipo** (1, 3, 5): ¿Todo el equipo participa?

---

### 📋 Guía de Instrucciones para Equipos

**URL:** `pitch-battle-instrucciones.html`

**Contenido:**
```
PITCH BATTLE - GUÍA COMPLETA

¿QUÉ ES PITCH BATTLE?
└─ Competencia de ventas en 40 minutos
└─ 5 equipos × 10 personas × 5 minutos de presentación
└─ 3 jurados califican simultáneamente
└─ Ganador: Equipo con mejor promedio de notas

CRONOGRAMA
├─ 📋 Preparación: 10 minutos
├─ 🎤 Presentaciones: 5 minutos (c/equipo)
└─ 🏆 Total: 40 minutos

INSTRUCCIONES
├─ Paso 1: RECIBE TU PRODUCTO
│  └─ Tendrás 10 minutos para prepararte
│
├─ Paso 2: PREPARA ESTRATEGIA
│  └─ Todos deben participar
│  └─ Distribuye roles por etapa
│
├─ Paso 3: PRESENTA EN 5 MINUTOS
│  └─ Máximo 5 minutos
│  └─ Energía, convencimiento y dominio
│
├─ Paso 4: RESPONDE OBJECIONES
│  └─ Los jurados harán 2-3 preguntas
│  └─ Responde con datos sólidos
│
└─ Paso 5: RECIBE CALIFICACIÓN
   └─ Puntos por cada criterio (1-5)
   └─ Máximo: 30 puntos

ESTRUCTURA RECOMENDADA (5 MINUTOS)
├─ 0-30s: GANCHO (Persona 1)
│  └─ Pregunta provocadora, energía al 100%
│
├─ 30s-2m: DESCRIPCIÓN (Personas 2-4)
│  └─ Qué es, para qué sirve, beneficios
│
├─ 2m-3:30m: OBJECIONES (Personas 5-7)
│  └─ Problemas + soluciones
│
├─ 3:30m-4:30m: CASO DE ÉXITO (Personas 8-9)
│  └─ Ejemplo real con números
│
└─ 4:30m-5:00m: CIERRE (Persona 10)
   └─ Llamada a acción fuerte

CRITERIOS DE PUNTUACIÓN (1-5 cada uno)

1️⃣ GANCHO/PRESENTACIÓN
   1 = Aburrido, sin energía
   3 = Captan atención, energía media
   5 = Impactante, energía al 100%
   
   💡 TIP: Abre con pregunta provocadora

2️⃣ DESCRIPCIÓN PRODUCTO
   1 = Confuso, no se entiende
   3 = Claro, explica lo básico
   5 = Muy claro, con ejemplos y beneficios
   
   💡 TIP: Conecta beneficios = dinero ahorrado

3️⃣ MANEJO OBJECIONES
   1 = No responden o responden mal
   3 = Responden, pero poco convencentes
   5 = Rápidos, con datos, convencen
   
   💡 TIP: No digas "tienes razón", di "buena pregunta"

4️⃣ ENERGÍA/CONVENCIMIENTO
   1 = Sin movimiento, voz baja
   3 = Movimiento moderado, voz clara
   5 = Mucho movimiento, voz fuerte, pasión
   
   💡 TIP: Contacto visual directo con jurados

5️⃣ CIERRE EFECTIVO
   1 = No piden la venta
   3 = Piden de forma débil
   5 = Piden con urgencia y claridad
   
   💡 TIP: "¿Dónde firmas?" o "¿Cuándo empezamos?"

6️⃣ PARTICIPACIÓN DEL EQUIPO
   1 = Solo 1-2 personas presentan
   3 = Participa la mayoría (6-8)
   5 = TODO EL EQUIPO PARTICIPA
   
   💡 TIP: ¡CRÍTICO! Sin participación, pierdes puntos

TIPS PARA GANAR
├─ 1. TODOS HABLEN - Cada persona una etapa
├─ 2. ENERGÍA AL MÁXIMO - No es aburrido, es un SHOW
├─ 3. DATA REAL - Números y casos reales
├─ 4. OBJECIONES PREPARADAS - Anticípate
├─ 5. CIERRE FUERTE - No termines con "gracias"
├─ 6. RESPONDE RÁPIDO - No desconcentres
└─ 7. UNIFORME/BRANDING - Mismo color/accesorios

PUNTUACIÓN MÁXIMA
└─ 30 PUNTOS TOTALES
   ├─ 5 puntos (Gancho)
   ├─ 5 puntos (Descripción)
   ├─ 5 puntos (Objeciones)
   ├─ 5 puntos (Energía)
   ├─ 5 puntos (Cierre)
   └─ 5 puntos (Participación)
```

---

## Flujo de Eventos

### Antes del Evento (1-2 días)

```
1. Crear Google Sheet con calificaciones
2. Configurar Apps Script
3. Actualizar URLs en todas las páginas
4. Probar conexión y funcionalidad
5. Imprimir guías para equipos
6. Preparar lista de 5 equipos × 10 personas
```

### Día del Evento (0-40 minutos)

```
MINUTO 0:
├─ Todos llegan, se forman 5 equipos
├─ Se proyecta la Guía de Instrucciones
└─ Se explica el sistema

MINUTO 5:
├─ Se proyecta la Página Principal
├─ Los 3 jurados abren sus panels
├─ Se anuncia inicio de preparación
└─ Empieza el timer de 10 minutos

MINUTO 15:
├─ Equipo 1 sube a presentar
├─ Se selecciona Equipo 1 en la página principal
├─ Se inicia el timer (5 minutos)
├─ Los jurados califican en sus dispositivos
└─ Ranking se actualiza en vivo

MINUTO 20:
├─ Equipo 1 baja
├─ Equipo 2 sube a presentar
├─ Proceso se repite...
└─ (Lo mismo para equipos 3, 4, 5)

MINUTO 40:
├─ Último equipo termina
├─ Se muestra ranking final
├─ Se anuncian ganadores
└─ ¡CELEBRACIÓN! 🎉
```

---

## Instrucciones para Equipos

### Antes de Comenzar (10 minutos de preparación)

**Lee la Guía de Instrucciones** - Entiende:
- Los 6 criterios de puntuación
- La estructura de 5 minutos
- Los tips para ganar

**Forma tu equipo (10 personas):**
1. Selecciona 1 persona para GANCHO (30s)
2. Selecciona 3 personas para DESCRIPCIÓN (1.5 min)
3. Selecciona 3 personas para OBJECIONES (1.5 min)
4. Selecciona 2 personas para CASO DE ÉXITO (1 min)
5. Selecciona 1 persona para CIERRE (30s)

**Prepara tu estrategia:**
- Memoriza el producto (descripción, precio, público)
- Escribe un gancho impactante
- Prepara puntos clave de venta
- Anticipa objeciones y respuestas
- Prepara un caso de éxito real

---

## Manual de Uso

### Para el Conductor (Persona con Página Principal)

**Antes de que presente Equipo 1:**
1. Click en el dropdown **"-- SELECCIONAR EQUIPO --"**
2. Selecciona **"Los Titanes"** (o el equipo que presenta)
3. Aparecerá automáticamente:
   - Nombre del equipo
   - Integrantes (10 personas)
   - Producto asignado
   - Descripción completa del producto

**Cuando comience la presentación:**
1. Click en **"▶ INICIAR TIEMPO"**
2. El timer comenzará a contar de 5:00 hacia abajo
3. Cuando quedan 30 segundos, el timer parpadea en naranja
4. Cuando llega a 0:00, suena una alerta

**Controles del timer:**
- **[-5s]** = Resta 5 segundos (si se pasaron)
- **[+5s]** = Suma 5 segundos (si necesitan más)
- **[🔄 RESET]** = Vuelve a 5:00

**Botón Random (opcional):**
- Click **"🔀 RANDOM EQUIPOS/PRODUCTOS"** antes de comenzar
- Mezcla aleatoriamente qué producto vende cada equipo

**Ranking en vivo:**
- Se actualiza **automáticamente cada 2 segundos**
- Muestra calificaciones de Jurado 1, 2, 3
- Calcula promedio automáticamente
- Ordena por mayor puntaje

---

### Para los Jurados (Personas con Panel)

**Cuando comience una presentación:**
1. Click en **"-- SELECCIONAR EQUIPO --"**
2. Selecciona el equipo que está presentando
3. Aparecerá el nombre del equipo y su producto

**Mientras ves la presentación:**
1. Selecciona una calificación (1-5) para cada criterio:
   - 1️⃣ Gancho/Presentación
   - 2️⃣ Descripción Producto
   - 3️⃣ Manejo Objeciones
   - 4️⃣ Energía/Convencimiento
   - 5️⃣ Cierre Efectivo
   - 6️⃣ Participación del Equipo

2. El total se calcula automáticamente

**Cuando termine la presentación:**
1. Click **"✓ GUARDAR CALIFICACIÓN"**
2. Aparecerá un mensaje: **"✓ Calificación guardada correctamente"**
3. Los datos se envían automáticamente a Google Sheets

**Para el siguiente equipo:**
1. Click **"🔄 LIMPIAR"** para limpiar los campos
2. Repite el proceso con el siguiente equipo

---

## Solución de Problemas

### "El ranking no se actualiza"

**Problema:** La página principal no muestra calificaciones
**Soluciones:**
1. Verifica que Google Sheet esté **compartido públicamente**
2. Verifica que el ID del Sheet sea correcto en la página
3. Recarga la página (Ctrl+F5)
4. Verifica que los jurados hayan hecho click en "GUARDAR"

---

### "No se guardan las calificaciones en Google Sheets"

**Problema:** Los jurados califican pero no aparece en Sheets
**Soluciones:**
1. Verifica que la URL del Apps Script sea correcta
2. Verifica que el nombre del equipo sea **exacto** (mayúsculas/minúsculas)
3. Verifica que tengas internet activo
4. Abre la consola (F12) y busca errores

---

### "El timer está muy rápido/lento"

**Problema:** El contador no marca exactamente 5 minutos
**Soluciones:**
1. Usa los botones **[-5s]** y **[+5s]** para ajustar
2. O haz click **"🔄 RESET"** para volver a 5:00

---

### "Los jurados no pueden acceder a sus páginas"

**Problema:** Las páginas de Jurado no cargan
**Soluciones:**
1. Verifica conexión a internet en todos los dispositivos
2. Prueba con un navegador diferente (Chrome, Firefox)
3. Borra caché (Ctrl+Shift+Del)
4. Usa un punto de acceso WiFi más cercano

---

### "El Google Sheet no carga en la página principal"

**Problema:** El ranking dice "Error al cargar ranking"
**Soluciones:**
1. Verifica que el Sheet esté **compartido públicamente**
2. Verifica que hayas reemplazado correctamente el ID del Sheet
3. Espera 2-3 segundos (actualiza cada 2 segundos)
4. Abre el link del Sheet en tu navegador para verificar que exista

---

### "Un jurado no ve el equipo en el dropdown"

**Problema:** Falta un equipo en el selector
**Soluciones:**
1. Los equipos deben ser exactamente estos:
   - Los Titanes
   - Vendedores Imparables
   - Guerreros 10X
   - Dinastía de Ventas
   - El Equipo Dorado

2. Si necesitas otros nombres, edita el código en la sección:
```javascript
let equipos = [
    { id: 1, nombre: "Los Titanes", productoId: 1, integrantes: 10 },
    // ... etc
];
```

---

## Resumen de Archivos Necesarios

```
├── pitch-battle-principal.html      (Pantalla principal)
├── pitch-battle-jurado1.html        (Panel Jurado 1)
├── pitch-battle-jurado2.html        (Panel Jurado 2)
├── pitch-battle-jurado3.html        (Panel Jurado 3)
├── pitch-battle-instrucciones.html  (Guía para equipos)
├── Google Sheet (compartido)        (Base de datos)
└── README.md                        (Este archivo)
```

---

## Checklist Antes del Evento

- [ ] Google Sheet creado y compartido públicamente
- [ ] Apps Script configurado y deployado
- [ ] URLs de Apps Script actualizadas en Jurados (1, 2, 3)
- [ ] ID de Sheet actualizado en página principal
- [ ] Todas las 5 páginas HTML descargadas/guardadas
- [ ] WiFi testado y funcionando en todos los dispositivos
- [ ] 3 dispositivos para jurados (cargados, WiFi conectado)
- [ ] 1 proyector/pantalla grande para página principal
- [ ] Guías impresas para los 5 equipos
- [ ] Lista de 50 personas (5 equipos × 10)
- [ ] Música/sonido para ambiente
- [ ] Micrófono (opcional)

---

## Contacto & Soporte

Para problemas técnicos o mejoras, verifica:
1. Google Sheet está compartido públicamente
2. Apps Script tiene permisos correctos
3. Conexión a internet es estable
4. Navegador es moderno (Chrome, Firefox, Edge)

---

**¡LISTO PARA PITCH BATTLE! 🚀**

Recuerda: El éxito depende de la ENERGÍA, el DOMINIO del producto y la PARTICIPACIÓN COMPLETA del equipo.

**"Vendes o te venden" - Grant Cardone**
