 Nuestro Plan

Web app móvil para planear y vivir un fin de semana en pareja: itinerario paso a paso, ruta del día, misiones con foto, control de gastos, puntos, ruleta de colores y álbum de recuerdos. Es un **único archivo HTML**, sin servidor, sin dependencias y sin cuentas: todo se guarda en el propio celular.

Funcionalidades

- **Itinerario guiado:** avanzas paso a paso; los pasos futuros quedan bloqueados hasta resolver el actual.
- **Ruta del día:** mapa esquemático (SVG) con pines numerados y botón para abrir el recorrido completo en Google Maps.
- **Vista detallada de cada lugar:** foto, horario, dirección, misión, presupuesto y botón "Cómo llegar".
- **Puntualidad:** registra la hora de llegada y suma puntos si llegan a tiempo (tolerancia de 5 min).
- **Misiones con foto:** las fotos se guardan en el dispositivo (IndexedDB) y alimentan el álbum.
- **Gastos:** presupuesto vs. gasto real, quién pagó y cómo, con factura y sobrante por día.
- **Resumen del día:** marcador de puntos, línea del día con puntualidad y factura.
- **Extras y ruleta de colores:** retos opcionales y una ruleta que asigna un color a cada persona.
- **Diseño tipo app:** tema oscuro violeta/rosa, íconos de línea, responsive (máx. 480 px centrado en pantallas grandes).

Uso

1. Descarga o clona el repositorio.
2. Abre `index.html` en el navegador del celular (o en el computador).

Para publicarlo en línea: **Settings → Pages → Deploy from a branch → `main` / root** en GitHub.

> Fuentes (Google Fonts) y fotos de lugares (Wikipedia/Wikimedia) requieren internet. Sin conexión la app funciona con la tipografía del sistema y sin fotos.

 Personalizar tu plan

Edita la constante `DAYS` al inicio del `<script>` principal de `index.html`. Cada día tiene `id`, `n` (nombre), `date` (`AAAA-MM-DD`), `t` (título), `sub` (subtítulo) e `items`.

| Campo | Descripción |
|---|---|
| `s`, `e` | Hora de inicio y fin (`"HH:MM"`) |
| `k` | `"stop"` (parada) o `"move"` (trayecto) |
| `id` | Identificador único de la parada |
| `n`, `d` | Nombre y descripción |
| `r` | Misión con foto (opcional) |
| `map` | Lugar para Google Maps y para la ruta del día |
| `q` | Búsqueda para la foto del lugar en Wikipedia |
| `cost:1`, `pay`, `est`, `en` | Pide gasto real. `pay`: `"b"` presupuesto o `"e"` lo pone Persona A. `est`: valor estimado, `en`: nota |
| `opt:1` | Parada opcional (no suma puntos) |
| `mode`, `from`, `to` | En trayectos: `"transit"` para bus; origen y destino |
| `url`, `ut` | Enlace y texto del botón (opcional) |

Otros ajustes:

- **Nombres:** busca y reemplaza `Persona A` / `Persona B` por los nombres reales.
- **Íconos:** asocia cada `id` de parada a un ícono en `M` (emoji, color) y en `IC` (nombre del ícono del sprite SVG).
- **Ids especiales:** `ruleta` (misión con la ruleta de colores) y `regalo` (tarjeta con mensaje) tienen comportamiento propio.
- **Puntos:** 10 por llegar puntual, 20 por misión cumplida y 5 por anotar el gasto real.
- **Extras:** lista `EX`.

Datos y privacidad

Todo se almacena localmente con `localStorage` e `IndexedDB`. No se envía nada a ningún servidor. Cada dispositivo tiene sus propios datos; el botón ⚙️ permite borrarlos.

 Estructura

```
├── index.html   # toda la app (HTML + CSS + JS)
├── README.md
└── LICENSE
```

 Licencia

MIT — ver `LICENSE`.
