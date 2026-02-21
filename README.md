# 🌿 Daniela Montali — Sitio Web

Sitio web profesional para **Daniela Montali**, Psicóloga Clínica (CABA, Argentina). Construido con [Astro](https://astro.build/), Tailwind CSS y componentes estáticos optimizados para performance y accesibilidad.

---

## 📁 Estructura del Proyecto

```
/
├── public/
│   └── images/
│       ├── bg-hero.webp          # Imagen de fondo del hero
│       └── user-*.jpg            # Fotos de testimonios
│
├── src/
│   ├── layouts/
│   │   └── Layout.astro          # Layout base (head, nav, footer)
│   │
│   ├── components/
│   │   ├── Nav.astro             # Navegación fija con scroll y menú mobile
│   │   ├── Hero.astro            # Sección hero con animaciones
│   │   ├── Services.astro        # Cards de servicios con expand automático
│   │   ├── Workshops.astro       # Talleres con expand por click
│   │   ├── Testimonials.astro    # Grid de testimonios
│   │   ├── Contact.astro         # CTA de contacto
│   │   └── Footer.astro          # Footer con links y redes
│   │
│   └── pages/
│       ├── index.astro           # Página principal
│       ├── aviso-legal.astro     # Aviso legal (Ley 25.326, 24.240, 11.723)
│       └── politica-de-privacidad.astro  # Política de privacidad (Ley 25.326)
│
├── astro.config.mjs
├── tailwind.config.mjs
└── package.json
```

---

## 🧩 Componentes

### `Nav.astro`
Navegación fija con dos estados:
- **Top (hero):** transparente, textos en blanco con efecto glass.
- **Scrolled (>60px):** fondo dark glass (`rgba(10,18,18,0.88) + blur`), siempre visible sobre cualquier sección.
- **Mobile:** overlay fullscreen con animación de entrada escalonada. El botón hamburger muta a X y recupera colores oscuros sobre fondo blanco.
- Detecta sección activa mediante `IntersectionObserver`.

### `Hero.astro`
- Imagen de fondo con zoom suave (12s).
- Glows ambientales flotantes animados.
- Entrada en cascada de badge → título → descripción → CTAs → stats.
- Stats row responsivo (etiquetas adaptadas en mobile).
- Scroll indicator animado.

### `Services.astro`
Cards de servicios con **expansión automática rotatoria**:
- Se expande una card cada 4 segundos.
- Entrada con animación suave, salida instantánea (t=0).
- Progress bar por card.
- Pausa al hacer hover, reanuda al salir.
- Click manual salta a esa card y reinicia el ciclo.
- Dots indicadores interactivos.

### `Workshops.astro`
Cards de talleres con **expansión por click**:
- Click en header → expande con `opacity + translateY` suave.
- Click nuevamente → colapsa instantáneamente.
- Cada taller incluye: descripción completa, programa horario, qué incluye, info práctica y **referencias académicas** con links externos.
- Soporte para campo `url` + `urlLabel`: muestra un badge pill en el header con link directo (ej. "Taller para adolescentes").
- Incluye el taller **AUTOADOLE** — diseñado para adolescentes de 13 a 17 años.

### `Testimonials.astro`
Grid de 3 testimonios en dark mode:
- Glassmorphism con gradiente hover.
- Número decorativo, comilla tipográfica, keyword destacada.
- Ícono `verified` animado por hover.

### `Contact.astro`
Sección CTA con imagen lateral:
- En mobile: solo texto y CTAs (imagen oculta en `<sm`).
- Trust signals en columna en mobile, fila en tablet+.
- Botones full-width en mobile.
- Badge de social proof dentro del contenedor (sin overflow).

### `Footer.astro`
Grid de 3 columnas (marca / navegación / contacto):
- Dark mode consistente con hero y testimonios.
- Links con underline animado.
- Social icons circulares con hover `bg-primary`.
- Footer inferior con links legales.

---

## 📄 Páginas Legales

Ambas páginas comparten el mismo sistema de diseño que el resto del sitio (hero dark, índice navegable, secciones numeradas) y están adaptadas íntegramente al **marco legal argentino**.

### `aviso-legal.astro`
Marco normativo:
- **Ley N° 25.326** — Protección de los Datos Personales
- **Ley N° 24.240** — Defensa del Consumidor
- **Ley N° 11.723** — Propiedad Intelectual
- **Ley N° 23.277** — Ejercicio Profesional de la Psicología
- **Código Civil y Comercial de la Nación**

Secciones: Datos del titular · Objeto · Propiedad intelectual · Limitación de responsabilidad · Servicios profesionales · Defensa del consumidor · Datos personales · Cookies · Jurisdicción (CABA) · Actualización.

### `politica-de-privacidad.astro`
Marco normativo:
- **Ley N° 25.326** + **Decreto Reglamentario 1558/2001**
- Organismo de control: **AAIP** (Agencia de Acceso a la Información Pública)

Secciones: Responsable del tratamiento · Marco legal · Finalidades y bases de legitimación · Datos sensibles · Categorías de datos · Destinatarios (tabla) · Derechos del titular (7 derechos) · Seguridad · Menores · Cookies · Actualización.

> ⚠️ **Reemplazar antes de publicar:** CUIL/CUIT, matrícula, dirección, teléfono, condición ante AFIP.

---

## 🎨 Sistema de Diseño

### Colores (definidos en `tailwind.config.mjs`)

| Token | Uso |
|---|---|
| `primary` | Verde teal — acento principal, CTAs, íconos |
| `background-dark` | Fondo oscuro — hero, nav, testimonios, footer |
| `background-light` | Fondo claro — secciones intermedias |
| `text-main` | Texto principal |
| `text-muted` | Texto secundario |
| `accent-sage` | Acento suave para bloques de fecha en talleres |

### Tipografía
- **Display / Headings:** serif itálica para énfasis emocional (`font-serif italic`)
- **Body:** fuente ligera (`font-light`) para legibilidad y tono cálido
- **Labels / Tags:** uppercase + tracking amplio (`uppercase tracking-widest`)

### Iconografía
[Material Symbols Outlined](https://fonts.google.com/icons) — cargado desde Google Fonts CDN.

```html
<link href="https://fonts.googleapis.com/css2?family=Material+Symbols+Outlined" rel="stylesheet" />
```

---

## 🚀 Instalación y Desarrollo

```bash
# Instalar dependencias
npm install

# Servidor de desarrollo
npm run dev

# Build de producción
npm run build

# Preview del build
npm run preview
```

**Requisitos:** Node.js ≥ 18 · npm ≥ 9

---

## 📦 Dependencias Principales

| Paquete | Versión | Uso |
|---|---|---|
| `astro` | ^4.x | Framework principal |
| `@astrojs/tailwind` | ^5.x | Integración Tailwind |
| `tailwindcss` | ^3.x | Estilos utilitarios |

---

## 📱 Responsividad

Todos los componentes están diseñados mobile-first:

| Breakpoint | Prefijo | Ancho |
|---|---|---|
| Mobile | *(base)* | < 640px |
| Tablet | `sm:` | ≥ 640px |
| Desktop medio | `md:` | ≥ 768px |
| Desktop | `lg:` | ≥ 1024px |
| Desktop XL | `xl:` | ≥ 1280px |

---

## ✅ Checklist antes de publicar

- [ ] Reemplazar datos placeholder en `aviso-legal.astro` (CUIL, matrícula, dirección, teléfono, condición AFIP)
- [ ] Reemplazar datos placeholder en `politica-de-privacidad.astro`
- [ ] Registrar la base de datos ante la **AAIP** y actualizar el número de registro
- [ ] Agregar imagen real `/public/images/bg-hero.webp`
- [ ] Agregar fotos de testimonios `/public/images/user-0.jpg`, `user-1.jpg`, `user-2.jpg`
- [ ] Reemplazar URL de AUTOADOLE (`https://www.example.com/autoadole`) por la URL real
- [ ] Actualizar links de redes sociales (Instagram, WhatsApp, LinkedIn) en Nav y Footer
- [ ] Actualizar email y teléfono en Footer y páginas legales
- [ ] Configurar dominio y SSL
- [ ] Verificar `sitemap.xml` y `robots.txt`

---

## 📬 Contacto del Proyecto

**Daniela Montali García** · Psicóloga Clínica  
📧 hola@danielamontali.com  
📍 Ciudad Autónoma de Buenos Aires, Argentina  
🌐 www.danielamontali.com