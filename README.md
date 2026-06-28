# KinoRecord

Web personal para explorar tu universo musical: historial de escucha (Last.fm) y colección física (Discogs), en un mismo lugar.

## Dos mundos

### 🔴 ESCUCHA — Last.fm
| Módulo | Qué hace |
|---|---|
| **Dashboard** | Estadísticas, scrobbles recientes, últimos en colección |
| **KinoPlayer** | Top tracks / loved tracks reproducibles via YouTube |
| **Máquina del Tiempo** | Qué escuchabas en cualquier fecha desde sep 2008 |
| **Playlist IA** | Claude genera playlists narrativas de 12 tracks desde tu historial |
| **Isla Desierta** | Núcleo duro: tracks más reproducidos × loved, con constelación visual |
| **Retrovisor** | Hoy, pero hace N años — qué sonaba ese mismo día |

### 🟣 COLECCIÓN — Discogs
| Módulo | Qué hace |
|---|---|
| **Vinilos** | Grid de portadas con búsqueda, filtros de formato/género, modal con tracklist |
| **Wantlist** | Grid de lo que quieres conseguir |

---

## Instalación en GitHub Pages

```bash
# 1. Crea el repo "kinorecord" en github.com/kinoluiggi
git clone https://github.com/kinoluiggi/kinorecord.git
cd kinorecord

# 2. Copia el index.html
cp /ruta/al/index.html .

# 3. Sube
git add .
git commit -m "init: KinoRecord v1.0"
git push
```

Luego: **Settings → Pages → Branch: main → /root → Save**

URL: `https://kinoluiggi.github.io/kinorecord/`

---

## Conectar Discogs

1. Ve a [discogs.com/settings/developers](https://www.discogs.com/settings/developers)
2. Clic en **Generate new token**
3. En KinoRecord → sección **Colección** → pega el token → Conectar
4. El token se guarda en `localStorage` de tu navegador (nunca sale de tu máquina)

Sin token funciona la parte de Last.fm; Discogs solo muestra datos públicos básicos.

---

## Configuración en el código

```javascript
const LFM_KEY  = '6b8d7a206bd7449cedb73dc6182d028e';  // Last.fm API key
const LFM_USER = 'kinoluiggi';
const DG_USER  = 'kinoluiggi';                          // Discogs username
```

El token de Anthropic (módulo IA) se ingresa en la interfaz y no se persiste.

---

## Stack

- Vanilla JS (sin frameworks, sin build step)
- Last.fm API v2 (pública con key)
- Discogs API v2 (token personal)
- YouTube embed iframe
- Anthropic API (claude-sonnet-4-6)
- GitHub Pages (hosting gratuito, un solo HTML)

## Estructura

```
kinorecord/
└── index.html    ← todo en un archivo
```

## Roadmap posible

- [ ] Estadísticas de colección: géneros en pie chart, años en histograma
- [ ] Cruzar colección Discogs con historial Last.fm (¿cuántas veces has escuchado cada LP que tienes?)
- [ ] Modo "sesión de vinilo": selecciona un disco de tu colección, reproduce sus tracks en secuencia
- [ ] Exportar wantlist como lista de texto/CSV
- [ ] Vista de colección por formato (LP / 7" / 12" / Cassette)
- [ ] Integración con Bandcamp wishlist
