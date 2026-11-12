# La Posta Bar — proyecto completo

Aplicación local para mesas, productos, medios de pago, ingresos, egresos y cierres de caja. Estética neón. Moneda: pesos argentinos.

## Ejecutar en Windows

1. Extraer todo el ZIP (clic derecho → Extraer todo).
2. Conservar la carpeta extraída en una ubicación fija.
3. Abrir `ABRIR LA POSTA.bat`; alternativamente, abrir `La Posta Bar.html` con Microsoft Edge o Google Chrome.
4. Revisar los productos y precios de ejemplo y abrir Caja antes de cargar consumos.

No necesita instalación, Internet, Node.js, Python ni servidor para el uso normal. No es un ejecutable nativo .exe. El lanzador .bat utiliza el navegador predeterminado. Si ese navegador no es compatible, elegir Abrir con → Edge o Chrome para el HTML.

## Archivos fuente y recursos

- `La Posta Bar.html`: código fuente completo, sin minificar, con HTML, CSS y JavaScript incorporados. Es también la aplicación ejecutable en navegador. No hay una compilación separada.
- `ABRIR LA POSTA.bat`: lanzador para Windows.
- `LEEME.txt`: uso diario, respaldos, alcance y mejoras sugeridas.
- `DEPENDENCIAS.json`: requisitos y dependencias declaradas.
- `package.json`: dependencia y comando para las pruebas opcionales.
- `tests/smoke.cjs`: prueba automatizada del circuito de caja.
- `MANIFEST.sha256`: comprobantes de integridad de los archivos anteriores.

Todos los recursos visuales son CSS, texto y caracteres Unicode; las fuentes son las del sistema. No hay imágenes, tipografías descargables, CDN, APIs ni recursos externos pendientes.

## Guardado y traslado de datos

Los datos se guardan en localStorage del navegador, no dentro del HTML ni del ZIP. Utilizar siempre el mismo navegador, perfil y ubicación del archivo. No usar modo incógnito. En Ajustes, descargar una copia JSON para conservar datos o migrar de PC; restaurarla en el destino. Borrar datos del navegador puede borrar el historial. Verificar que los respaldos de cada cierre estén efectivamente descargados y conservar otra copia en una unidad externa.

Esta exportación contiene código y datos de ejemplo, sin historial operativo ni datos guardados en navegadores. Usar en una sola ventana y PC. Los comprobantes impresos no son facturas fiscales. Los pagos se registran manualmente; no procesa tarjetas ni se integra con ARCA. El saldo de movimientos no es ganancia contable.

## Desarrollo

Editar directamente `La Posta Bar.html` con un editor de texto. Hacer una copia de los datos antes de modificarlo. No hay paso de compilación ni dependencias de ejecución JavaScript.

## Pruebas opcionales

Requieren Node.js 22 o superior y npm. Desde la carpeta extraída:

```powershell
npm install
npx playwright install chromium
npm test
```

La única dependencia npm es Playwright, utilizada exclusivamente en pruebas. Su navegador y node_modules no se incluyen. La prueba inicia un servidor temporal en 127.0.0.1 con un puerto disponible, usa un contexto de navegador nuevo y cierra ambos al terminar. No toca los datos de uso real. Puede usarse un Chromium existente mediante la variable `PLAYWRIGHT_CHROMIUM_EXECUTABLE_PATH`.

Verifica apertura de caja, consumos, cobro dividido, egresos, arqueo, descarga de respaldo, persistencia al recargar, validación de estructura y edición de productos. Se ejecutó en Chromium sobre Linux; no se ha probado Windows directamente ni la apertura file:// en el navegador administrado de este entorno (su política la bloquea).

## Contenido excluido

Sin contraseñas, tokens, archivos .env, datos personales, historial de navegador, respaldos operativos, node_modules, cachés, capturas de pruebas, archivos temporales ni ZIP anteriores. El generador intermedio usado durante la creación no se necesita: el código fuente definitivo está íntegro en el HTML.
