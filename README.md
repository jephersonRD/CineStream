# CineStream

<p align="center">
  <img src="./public/logo512.png" alt="CineStream Logo" width="120" />
</p>

<p align="center">
  <strong>CineStream</strong> es un proyecto personal creado por <a href="https://github.com/jephersonRD">@jephersonRD</a> que explora cómo construir una experiencia moderna de streaming para películas, series y anime, con una estética inspirada en plataformas populares como Cuevana.
</p>

---

## ¿De qué trata CineStream?

CineStream es una interfaz web enfocada en la experiencia del usuario para descubrir y disfrutar contenido audiovisual. Su objetivo es ofrecer:

- Descubrimiento ágil de contenido (tendencias, populares, novedades)
- Fichas visuales atractivas con sinopsis, géneros y calificaciones
- Navegación por secciones: Películas, Series y Anime
- Una experiencia cuidada para series: selector de temporada/episodio, indicador de visto y progreso
- Un reproductor preparado para múltiples fuentes legales (trailers/embeds por ahora), con la arquitectura lista para integrar HLS/MP4 propios en el futuro

El proyecto pone énfasis en el diseño, la navegación fluida y una base técnica sólida que permita crecer hacia integraciones de streaming legítimas.

---

## Visión y objetivos

- Crear una UI moderna, rápida y agradable para explorar cine, series y anime
- Mantener una arquitectura clara y extensible para integrar proveedores de video legales (HLS/MP4)
- Priorizar la experiencia de series con una gestión transparente de temporadas y episodios
- Respetar buenas prácticas de accesibilidad y desempeño

> Importante: CineStream usa APIs públicas de metadatos (TMDB y Jikan) para información, pósters y estructura de temporadas/episodios. No aloja ni distribuye contenido con derechos. La reproducción completa de títulos requiere integrar fuentes legales propias (no incluidas), como Mux, Cloudflare Stream o AWS.

---

## Público al que va dirigido

- Entusiastas del frontend interesados en UIs tipo streaming
- Desarrolladores que busquen referencias para construir catálogos audiovisuales
- Creadores que quieran una base para integrar sus propios streams legales

---

## Características clave

- Estética oscura tipo “cine”, con secciones y tarjetas pulidas
- Inicio con carruseles, grillas y bloques temáticos
- Páginas: Inicio, Películas, Series, Anime, Búsqueda, Detalle y Reproductor
- Series con selector de temporada y episodios, más:
  - Indicador de "visto" (👁️)
  - Barra de progreso por episodio (persistencia local)
- Descripciones largas con truncado elegante y botón "Ver más / Ver menos"
- Fallback estático en `public/index.html` para mejorar la percepción de carga

---

## Diseño y experiencia

- Paleta oscura con acentos en rojo para acciones clave
- Tarjetas con sombras suaves, efectos hover y cintillas (HD, 1080p, etc.)
- Secciones limpias con tipografía legible y jerarquía visual
- Navegación con HashRouter para funcionar también en subdirectorios

---

## Stack y fuentes de datos

- React + styled-components
- React Router (HashRouter)
- APIs de metadatos:
  - TMDB (películas y series)
  - Jikan (anime)
- Persistencia local para progreso y "visto" (localStorage)

> CineStream no integra ni promueve sitios de streaming no autorizados. La arquitectura del reproductor está preparada para integrar fuentes legales cuando el creador lo disponga.

---

## Capturas (vista previa)

<p align="center">
  <img src="./public/logo192.png" alt="Logo secundario" width="80" />
</p>

- Home: carruseles y grillas de contenido
- Detalle: ficha visual con sinopsis truncada
- Series: selector de temporada/episodios con progreso y "visto"
- Reproductor: preparado para múltiples fuentes (embeds ahora; HLS/MP4 en roadmap)

> Si clonas el proyecto, puedes añadir capturas reales en una carpeta `docs/` y referenciarlas aquí.

---

## Créditos y autor

Proyecto creado por:

- Creador: **@jephersonRD**
- GitHub: https://github.com/jephersonRD/CineStream
- YouTube: https://www.youtube.com/channel/UCm-l4Ek4AGfBEqVWXsb25PA?app=desktop
- TikTok: https://www.tiktok.com/@jepherson_rd

---

## Roadmap (alto nivel)

- Mejoras visuales en sliders y tarjetas (badges HD/4K, transiciones)
- Selector de episodios con progreso para Anime
- Reproductor con soporte HLS (`hls.js`) y selección de fuente/calidad
- Paginación / Infinite scroll
- Temas personalizables (modos de color)

---

## Nota legal

CineStream es un proyecto con fines educativos. TMDB y Jikan proveen metadatos; las imágenes y marcas pertenecen a sus respectivos dueños. La reproducción de contenido completo requiere fuentes legales bajo tus propios términos y licencias.
