# TERMA

Landing corporativa construida con Astro + Tailwind CSS y preparada para deploy estático en Cloudflare Pages.

## Stack

- Astro
- Tailwind CSS v4 mediante `@tailwindcss/vite`
- Salida estática (`output: 'static'`)

## Requisitos

- Node.js 20 o superior
- npm 10 o superior

## Desarrollo local

```bash
npm install
npm run dev
```

## Scripts

```bash
npm run dev
npm run build
npm run preview
```

## Estructura principal

- `src/pages/index.astro` — landing principal
- `src/layouts/BaseLayout.astro` — layout base, fuentes y metadatos
- `src/styles/global.css` — Tailwind y estilos utilitarios compartidos
- `astro.config.mjs` — configuración Astro + plugin de Tailwind

## Deploy en Cloudflare Pages

Este proyecto queda intencionalmente como **sitio estático** porque la landing no necesita SSR ni edge logic para renderizar.

### Opción 1 — Dashboard de Cloudflare Pages

1. Creá un proyecto en Cloudflare Pages y conectá tu repositorio.
2. Configurá:
   - **Framework preset**: `Astro`
   - **Build command**: `npm run build`
   - **Build output directory**: `dist`
3. Variables opcionales:
   - `NODE_VERSION=20`
4. Hacé deploy.

### Opción 2 — CI/CD desde Git

También podés dejar que Cloudflare haga deploy automático con cada push a la rama principal manteniendo la misma configuración:

- Build command: `npm run build`
- Output directory: `dist`

## Nota sobre Cloudflare Workers

Cloudflare hoy empuja **Workers** como recomendación general para proyectos nuevos. Aun así, en este caso **Pages es la opción más simple y correcta** porque estamos desplegando una landing estática sin SSR.

Si más adelante necesitás:

- render dinámico,
- personalización por request,
- API en el edge,
- o integración SSR,

recién ahí conviene migrar a Astro con adapter de Cloudflare para Workers.

## Próximos pasos recomendados

- Reemplazar placeholders de logos de clientes por assets reales.
- Conectar el formulario a Forms, email API o backend.
- Definir dominio final y metadatos SEO definitivos.
