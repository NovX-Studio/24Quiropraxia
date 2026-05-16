# 24 Quiropraxia — sitio estático

Stack: Tailwind CDN, Google Fonts (Playfair Display + DM Sans), GSAP + ScrollTrigger CDN, SVG `<symbol>` sprite.

## Páginas

- `index.html` — landing principal (hero, stats, qué-es, beneficios CTA, vóley, testimonios, QS CTA, sucursales, FAQ, charlas, contacto)
- `beneficios.html` — 5 cards de beneficios en grilla 2-col
- `quienes-somos.html` — about + galería + misión/visión/valores + CTA

Todas se enlazan entre sí. Misma navbar y footer en todas.

## Comandos

No hay build step. Abrir archivos `.html` directamente en el navegador.

## Stack y tooling

- **Tailwind**: CDN vía `<script src="https://cdn.tailwindcss.com">`, config inline en `<script>` propio. Colores personalizados en OKLCH: `tierra`, `hueso`, `noche`, `verde`, `claro`, `cobre`.
- **GSAP**: `defer` desde CDN. Código dentro de `DOMContentLoaded` con guard `typeof gsap === 'undefined'`.
- **ScrollTrigger**: registrado via `gsap.registerPlugin(ScrollTrigger)`.
- **Iconos**: SVG `<symbol>` inline en `<head>`, usados con `<use href="#icon-*">`.
- **Fuentes**: Playfair Display (display) + DM Sans (body). Nunca Inter, Roboto, Arial.

## Reglas críticas de estilo

- **Contenido siempre visible**: NO usar CSS `opacity: 0` en elementos de contenido. GSAP solo anima posición (`y`, `x`) no opacidad para elementos que revelan contenido. La página debe ser legible aunque GSAP no cargue.
- **Navbar**: `bg-noche` (sólido oscuro) con texto blanco. Nunca transparente, blanco/95, ni con backdrop-blur.
- **Vertebra**: pueden animarse con opacidad (decorativo, aceptable).
- **Testimonios slider**: pixel-based `translateX` con `flex: 0 0 100%` en slides. Sin `onclick` inline — usar `data-slide` attributes + `addEventListener`.
- **Paleta** definida en OKLCH, no usar hex/rgb para colores de marca.
- **Favicon** desde `https://24quiropraxia.com.ar/wp-content/uploads/2019/04/logo-24.png`.

## Skills instaladas (`.agents/skills/`)

Se cargan automáticamente cuando la tarea coincide. No invocar manualmente.

- `frontend-design` — diseño distintivo, tipografías no genéricas, animaciones, composición espacial. Prohíbe Inter/Roboto/Arial, purple gradients, layouts genéricos.
- `impeccable` — reglas de calidad visual. (GitHub source, no local)
- `seo` — meta tags, canonical, JSON-LD structured data, robots.
- `accessibility` — WCAG 2.2, alt texts, labels, aria, focus-visible, skip links.

## Convenciones

- Secciones con `scroll-margin-top: 80px` para offset de navbar fija.
- `prefers-reduced-motion` desactiva animaciones.
- WhatsApp links con número exacto por sucursal.
- No incluir crédito "Diseñado por Nico Melian".
- No incluir badge "Avalado por la OMS" ni tagline "Confianza que crece".
