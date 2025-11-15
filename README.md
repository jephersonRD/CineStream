# CineStream

<p align="center">
  <img src="./public/logo512.png" alt="CineStream Logo" width="120" />
</p>

<p align="center">
  <strong>Tu plataforma para descubrir y disfrutar Películas, Series y Anime</strong><br/>
  Interfaz moderna tipo Cuevana, datos en tiempo real desde TMDB/Jikan, reproductor preparado para múltiples fuentes y progreso de visionado.
</p>

<p align="center">
  <a href="#caracteristicas">Características</a> •
  <a href="#demo">Demo</a> •
  <a href="#instalacion">Instalación</a> •
  <a href="#configuracion">Configuración</a> •
  <a href="#scripts">Scripts</a> •
  <a href="#arquitectura">Arquitectura</a> •
  <a href="#capturas">Capturas</a> •
  <a href="#roadmap">Roadmap</a>
</p>

---

## Características

- UI moderna inspirada en plataformas de streaming
- Enrutamiento con `HashRouter` para funcionar en subdirectorios o archivos locales
- Integración con APIs públicas:
  - TheMovieDB (TMDB) para películas y series (metadatos, tendencias, populares, etc.)
  - Jikan (MyAnimeList) para anime
- Páginas principales: Inicio, Películas, Series, Anime, Búsqueda, Detalles, Reproductor
- Reproductor preparado para múltiples fuentes (trailers/embeds ahora; listo para HLS/MP4 legales)
- Selector de Temporada/Episodio con indicador de visto y barra de progreso (Series)
- Truncado de descripciones con "Ver más / Ver menos"
- Landing fallback en `public/index.html` (se oculta automáticamente al montar React)

> Nota legal: TMDB y Jikan proveen metadatos. Para reproducir contenido completo debes usar fuentes/streams legales (p. ej. Mux, Cloudflare Stream, AWS CloudFront + HLS). Este proyecto no integra sitios de terceros no autorizados.

---

## Demo

- Desarrollo (dev server): `http://localhost:3002/#/` (puerto configurable)
- Estático (producción): `http://localhost:5000/#/`

> Si prefieres la versión de build estático, usa el script `serve_build.bat` (ver Scripts).

---

## Requisitos

- Node.js 18+ (recomendado) / 20+
- npm 8+

---

## Instalación

```bash
# Clona el repo
# git clone https://github.com/tu-usuario/CineStream.git
# cd CineStream/cinestream

# Instala dependencias
npm install
```

---

## Configuración

Crea un archivo `.env` en la carpeta `cinestream` con tu clave de TMDB:

```
# Puerto del dev-server
PORT=3002

# API Key de TMDB (solo metadatos)
REACT_APP_TMDB_API_KEY=TU_API_KEY_TMDB
```

- TMDB (gratuita): https://www.themoviedb.org
- Jikan (anime, no requiere clave): https://api.jikan.moe

> Importante: `.env` se lee al iniciar el dev server. Si cambias valores, reinicia `npm start`.

---

## Scripts

```bash
# Desarrollo
npm start

# Build de producción
npm run build

# Test (si aplica)
npm test

# Lint (si aplica)
npm run lint
```

Scripts Windows útiles incluidos:

- `start_dev_5000.bat`: inicia el dev server en el puerto 5000.
- `serve_build.bat`: construye y sirve el build estático en el puerto 5000.

```bat
# Uso típico
start_dev_5000.bat
# o
serve_build.bat
```

---

## Estructura principal

```
cinestream/
├─ public/
│  ├─ index.html        # landing fallback + root para React
│  └─ manifest.json
├─ src/
│  ├─ components/
│  │  ├─ Navbar/
│  │  ├─ Hero/
│  │  ├─ MovieGrid/
│  │  ├─ MovieSlider/
│  │  └─ Footer/
│  ├─ pages/
│  │  ├─ Home/
│  │  ├─ Movies/
│  │  ├─ Series/           # SeriesDetail incluye selector temporada/episodio
│  │  ├─ Anime/
│  │  ├─ MovieDetail/
│  │  ├─ SeriesDetail/
│  │  ├─ AnimeDetail/
│  │  └─ Player/
│  ├─ services/
│  │  └─ api.js            # TMDB + Jikan + helpers
│  ├─ utils/
│  │  └─ watchProgress.js  # progreso localStorage (visto/porcentaje)
│  ├─ App.js
│  ├─ index.js
│  └─ index.css
└─ README.md
```

---

## Arquitectura

- React + styled-components
- React Router con HashRouter
- Servicios HTTP:
  - TMDB para películas/series (metadatos) usando `REACT_APP_TMDB_API_KEY`
  - Jikan para anime (sin clave)
- Player preparado para:
  - `iframe` (trailers/embeds)
  - `<video>` (MP4)
  - Integración futura con HLS (m3u8) vía `hls.js`
- Persistencia local de progreso por contenido (localStorage)

---

## Capturas

> Reemplaza estas rutas con tus imágenes reales si lo deseas (colócalas en `docs/` o usa las que hay en `public/`).

<p align="center">
  <img src="./public/logo192.png" alt="Logo pequeño" width="80" />
</p>

- Home (tendencias, sliders)
- Detalle de Película/Serie/Anime (ficha, sinopsis con truncado)
- Series: selector de temporada/episodio con indicador de visto y progreso
- Player con reproducción y guardado de progreso

---

## Troubleshooting

- ENOENT package.json
  - Asegúrate de ejecutar los comandos dentro de `cinestream/`:
  ```bash
  cd C:\Users\Usuario\Documents\code\cinestream
  npm start
  ```
- "Upgrade Required" en desarrollo
  - Usa el build estático: `serve_build.bat` y abre `http://localhost:5000/#/`.
- Rutas rompen al abrir por archivo
  - Se usa `HashRouter`, siempre navega con `#/` (ej: `http://localhost:5000/#/peliculas`).
- No se ven datos de películas/series
  - Revisa tu `REACT_APP_TMDB_API_KEY` y reinicia `npm start`.

---

## Roadmap

- [ ] Estilos avanzados tipo Cuevana (tarjetas, badges HD/4K, sliders custom)
- [ ] Selector de episodios con progreso para Anime
- [ ] Player con HLS (`hls.js`) y múltiples fuentes
- [ ] Paginación e Infinite Scroll
- [ ] Modo oscuro/tema personalizable

---

## Contribuir

1. Fork ✨
2. Crea una rama: `git checkout -b feature/mi-feature`
3. Commit: `git commit -m "feat: mi feature"`
4. Push: `git push origin feature/mi-feature`
5. Pull Request

---

## Licencia

Este proyecto es solo con fines educativos y demostrativos. Verifica los términos de uso de TMDB y Jikan.

---

## Agradecimientos

- [TMDB](https://www.themoviedb.org/) por su API de metadatos de cine/series.
- [Jikan](https://jikan.moe/) por exponer datos de MyAnimeList.
- Comunidad React por las librerías utilizadas.
