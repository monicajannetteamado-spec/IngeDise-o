# IngeDise-o — Contratación Pública Interactiva (SECOP II)

Aplicación web interactiva para mostrar el **comportamiento de la contratación pública** teniendo en cuenta:

- **Adjudicatario** (`Proveedor Adjudicado`)
- **Objeto de la contratación** (`Objeto del Contrato`)
- **Valor** (`Valor del Contrato`)
- **Link de consulta al SECOP** (`URLProceso` → SECOP II)

Además, la aplicación **permite cambiar el conjunto de datos**: puedes subir otro CSV de SECOP II y todos los gráficos, indicadores y la tabla se recalculan automáticamente.

## Cómo usarla

1. Abre `index.html` en el navegador (o sirve la carpeta con un servidor local, por ejemplo: `python3 -m http.server 8000` y entra a `http://localhost:8000`).
2. Explora los indicadores, gráficos y la tabla de contratos.
3. Filtra por adjudicatario, entidad, tipo de contrato, modalidad, estado, departamento, año, rango de valor o texto libre (objeto/entidad/adjudicatario/ID).
4. Haz clic en una fila para ver el detalle completo y el botón **“Consultar en SECOP II”**, que abre la consulta oficial del proceso.
5. Exporta el conjunto filtrado a CSV con el botón superior.

## Cambiar el conjunto de datos

- Arrastra un archivo **CSV** sobre la zona “Cambiar conjunto de datos” (o haz clic para seleccionarlo).
- La app detecta automáticamente las columnas equivalentes (Proveedor Adjudicado, Objeto del Contrato, Valor del Contrato, URLProceso, Nombre Entidad, Tipo de Contrato, Modalidad de Contratación, Estado Contrato, Fecha de Firma, etc.).
- Para volver a los datos de ejemplo, usa el botón **“↺ Volver a datos SECOP”**.

## Estructura

```
index.html                                      # Aplicación (HTML + CSS + JS, Chart.js + PapaParse por CDN)
datos/
  SECOP_II_-_Contratos_Electrónicos_20261118.csv  # CSV original subido (270 contratos)
  data.json                                       # Versión compacta que carga la app al inicio
```

## Datos de ejemplo

- **270 contratos** electrónicos de SECOP II.
- Adjudicatario único en la muestra: **POWERSUN S.A.S.** (sector UPS / energía ininterrumpida).
- Valor total: **$27.161 millones COP** aprox. (suma de `Valor del Contrato`).
- Todos los registros incluyen `URLProceso` para consulta en SECOP II.
- Periodo de firma: 2016–2026.

## Notas técnicas

- Sin build ni dependencias locales: solo abre el archivo o sírvelo estáticamente.
- Los gráficos usan Chart.js y la lectura de CSV usa PapaParse (CDN).
- El mapeo de columnas es tolerante a acentos, mayúsculas y nombres ligeramente distintos.
