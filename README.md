# Monitoreo Bioclimático — Cuenca del Lago de Atitlán

Dashboard de clima, aves y árboles para la red de 10 estaciones de monitoreo en la
Reserva de Uso Múltiple Cuenca del Lago de Atitlán (RUMCLA), Sololá, Guatemala.

Es una aplicación web de un solo archivo (`index.html`) — no necesita servidor,
base de datos ni instalación de nada para funcionar. Los datos de clima, aves y
árboles se sincronizan solos desde Google Sheets cada vez que se abre.

## 1. Subirlo a GitHub

1. Crea un repositorio nuevo en GitHub (puede ser público o privado — si es
   privado, GitHub Pages solo funciona en el plan Pro/Team/Enterprise).
2. Sube **todos** estos archivos a la raíz del repositorio (no en una subcarpeta):
   ```
   index.html
   manifest.json
   sw.js
   icons/icon-192.png
   icons/icon-512.png
   icons/icon-512-maskable.png
   icons/apple-touch-icon.png
   ```
   Los archivos `Code.gs`, `Code_Aves.gs` y `Code_DAP.gs` son los scripts de Google
   Apps Script que ya desplegaste — inclúyelos también, sirven como respaldo/documentación
   de cómo está configurada la sincronización en vivo, pero el sitio no los necesita
   para funcionar.

## 2. Activar GitHub Pages (para tener una URL pública)

1. En el repositorio: **Settings → Pages**.
2. En "Source" elige **Deploy from a branch**, rama `main`, carpeta `/ (root)`.
3. Guarda. Después de 1–2 minutos tu dashboard queda disponible en:
   ```
   https://<tu-usuario>.github.io/<nombre-del-repo>/
   ```

## 3. Instalarlo como app en el teléfono

**Android (Chrome):**
Abre la URL → menú (⋮) → **"Instalar app"** o **"Agregar a pantalla de inicio"**.
Queda con su propio ícono, abre sin barra de navegador, como cualquier app.

**iPhone/iPad (Safari):**
Abre la URL → botón de compartir (□↑) → **"Agregar a pantalla de inicio"**.
*(Tiene que ser desde Safari — Chrome en iOS no permite instalar apps.)*

## 4. Instalarlo en la computadora

**Chrome / Edge:** abre la URL → ícono de instalar (⊕ o pantalla con flecha) en la
barra de direcciones, a la derecha → **Instalar**. Queda como una ventana propia,
con ícono en el escritorio/menú de aplicaciones.

## Cómo funciona la actualización de datos

- Al abrir la app (o reabrirla), se sincroniza sola con las 3 hojas de Google Sheets
  (clima, aves, árboles) — revisa el indicador junto al título.
- Si subes datos nuevos a esas hojas, no hace falta tocar nada más: la próxima vez
  que se abra la app, los va a jalar automáticamente.
- Si necesitas una actualización inmediata sin cerrar la app, usa el botón
  **"🔄 Actualizar datos"** en el encabezado.
- La app funciona sin internet para navegar lo que ya cargó (gracias al ícono
  instalado), pero para traer datos *nuevos* siempre necesita conexión — no es
  un modo 100% offline, es "abre rápido y muestra lo último que logró sincronizar".

## Si algo dejó de sincronizar

Los tres scripts de Google Apps Script (`Code.gs` para clima, `Code_Aves.gs` y
`Code_DAP.gs` para biodiversidad) deben seguir desplegados con acceso "Cualquier
usuario". Si alguno se re-despliega o cambia de URL, hay que actualizar la URL
correspondiente dentro de `index.html` (búscala por `SHEET_CSV_URLS`,
`AVES_CSV_URLS` o `DAP_CSV_URLS`) y volver a subir el archivo a GitHub.
