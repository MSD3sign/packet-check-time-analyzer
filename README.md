The app is live here:

https://msd3sign.github.io/packet-check-time-analyzer/

# Packet Check Time Analyzer (v2.8.5)

Herramienta de una sola página (HTML/CSS/JS, sin dependencias externas) para analizar el
Area Walk Report y calcular, por bloques de 30 minutos, cuántos "package checks" se
necesitan y cuántos de esos asociados son Seasonals.

## Uso local
Abre `index.html` en cualquier navegador — no requiere servidor ni build.

## Uso en línea (GitHub Pages)
Una vez subido este repo a GitHub:

1. Ve a **Settings → Pages**.
2. En "Build and deployment" → Source, elige **Deploy from a branch**.
3. Branch: `main`, carpeta `/ (root)` → **Save**.
4. En un par de minutos la app quedará disponible en:
   `https://TU_USUARIO.github.io/NOMBRE_DEL_REPO/`

## Qué hace
- Pega el contenido completo del Area Walk Report.
- Genera la tabla "Walk Report by 30 min" (Schedule Out / Meal Out / Total), marcando
  entre paréntesis cuántos de cada conteo son Seasonals.
- Checkbox "Show only seasonals" junto al filtro, para mostrar en la tabla solo las
  horas donde hay al menos un Seasonal.
- Módulo "Seasonal Associates": lista con nombre y apellido, número de asociado y
  schedule de cada Seasonal encontrado en el reporte.
- Dashboard con una gráfica de asociados por hora (con su propio checkbox para
  sincronizarse o no con el filtro de la tabla).
- Filtro por cantidad de package checks del día.
- Impresión lista para llenar en piso.

## Versiones
- **v2.8.5** (10/01/2026): el campo "Date:" de la hoja impresa ahora usa la fecha del encabezado del reporte pegado ("Area Walk Report for: ...") en vez de la fecha de hoy, para poder analizar datos de otros días. El campo "Day:" se calcula desde esa misma fecha, así Day y Date siempre corresponden.
- **v2.8.4** (09/29/2026): al filtrar el gráfico "Associates by Hour" mantiene altura, grosor de barras y escala vertical (calculados con los datos completos).
- **v2.8.3** (09/29/2026): módulos Import Walk Report, Walk Report by 30 min, Associates by Hour, Seasonal Schedule List; botón print condicional; filtros y lista reorganizados.
