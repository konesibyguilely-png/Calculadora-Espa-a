# Calculadoras España

Plataforma de calculadoras gratuitas en español, optimizada para SEO en Google y monetización con Google AdSense.

🔗 **Demo:** _(añadir URL tras el despliegue en Vercel)_

## ✨ Características

- **8 calculadoras interactivas** con resultados en tiempo real:
  - 💶 IVA (general, reducido, superreducido)
  - 🏠 Hipoteca (sistema francés de amortización)
  - 📈 Interés Compuesto
  - 🎓 EVAU / Selectividad (nota de acceso y admisión)
  - 📖 Nota media de Bachillerato (ponderada por créditos)
  - ⚖️ IMC (Índice de Masa Corporal, criterios OMS)
  - 🎂 Edad exacta (años, meses, días, signo zodiacal)
  - 📅 Diferencia entre fechas (días, semanas, laborables)
- Cada calculadora incluye: explicación de la fórmula, ejemplos resueltos, tabla comparativa y FAQ con schema `FAQPage`.
- SEO técnico: `sitemap.xml`, `robots.txt`, URLs canónicas, breadcrumbs con schema `BreadcrumbList`, JSON-LD `SoftwareApplication`/`WebSite`/`ItemList`.
- Páginas legales completas (RGPD): Política de Privacidad, Cookies, Términos y Condiciones, Contacto.
- Espacios publicitarios para Google AdSense + bloques de afiliados.
- Diseño responsive, accesible y con tipografía autoalojada (`next/font`).

## 🛠 Stack técnico

| | |
|---|---|
| Framework | Next.js 15 (App Router) |
| Lenguaje | TypeScript (`strict`) |
| Estilos | Tailwind CSS 3 |
| Fuente | Inter (`next/font/google`) |
| Despliegue | Vercel |

## 🚀 Empezar

```bash
npm install
npm run dev
```

Abre [http://localhost:3000](http://localhost:3000).

### Scripts disponibles

```bash
npm run dev     # servidor de desarrollo
npm run build   # build de producción
npm run start   # servidor de producción (tras build)
npm run lint    # ESLint
```

## 📁 Estructura del proyecto

```
src/
├── app/
│   ├── page.tsx                  # Homepage
│   ├── layout.tsx                # Layout raíz (metadata, fuentes, AdSense script)
│   ├── globals.css               # Estilos globales + tokens de diseño
│   ├── sitemap.ts                # Generador de sitemap.xml
│   ├── robots.ts                 # Generador de robots.txt
│   ├── manifest.ts               # Web app manifest
│   ├── not-found.tsx             # Página 404
│   ├── calculadoras/
│   │   ├── page.tsx              # Índice de todas las calculadoras
│   │   ├── iva/
│   │   │   ├── page.tsx          # Página SEO (metadata, contenido, FAQ)
│   │   │   └── IVACalculator.tsx # Componente interactivo ("use client")
│   │   ├── hipoteca/...
│   │   ├── interes-compuesto/...
│   │   ├── evau/...
│   │   ├── bachillerato/...
│   │   ├── imc/...
│   │   ├── edad/...
│   │   └── diferencia-fechas/...
│   ├── contacto/
│   │   ├── page.tsx
│   │   └── ContactForm.tsx
│   └── legal/
│       ├── privacidad/page.tsx
│       ├── cookies/page.tsx
│       └── terminos/page.tsx
├── components/
│   ├── layout/
│   │   ├── Header.tsx            # Navegación + búsqueda
│   │   └── Footer.tsx
│   └── ui/
│       ├── Breadcrumb.tsx        # Con schema BreadcrumbList
│       ├── FAQ.tsx                # Acordeón con schema FAQPage
│       ├── CalculatorCard.tsx
│       └── AdSense.tsx           # Componentes de anuncios + afiliados
└── lib/
    ├── config.ts                  # SITE_CONFIG, CATEGORIES, CALCULATORS
    └── utils.ts                   # formatCurrency, formatNumber, cn, etc.
```

## ⚙️ Configuración pendiente antes de producción

Estos valores son placeholders y deben actualizarse:

1. **`src/lib/config.ts`**
   - `SITE_CONFIG.url` → dominio real
   - `SITE_CONFIG.adsenseId` → tu Publisher ID de AdSense (`ca-pub-...`)
   - `SITE_CONFIG.email` → email de contacto real

2. **`src/app/layout.tsx`**
   - `metadata.verification.google` → código de verificación de Google Search Console
   - El `<script>` de AdSense usa `SITE_CONFIG.adsenseId` automáticamente

3. **`src/components/ui/AdSense.tsx`**
   - Sustituir los `data-ad-slot` de ejemplo por los IDs reales de tus bloques de anuncios
   - `AdPlaceholder` se muestra como placeholder gris hasta que AdSense esté aprobado/activo

4. **`src/app/contacto/ContactForm.tsx`**
   - Actualmente simula el envío (`setTimeout`). Conectar a un backend real (Resend, Formspree, API Route propia, etc.)

5. **Imágenes/iconos referenciados pero no incluidos** (añadir a `/public`):
   - `og-image.png` (1200×630, Open Graph)
   - `favicon.ico`, `icon.svg`, `apple-touch-icon.png`
   - `icon-192.png`, `icon-512.png` (referenciados en `manifest.ts`)

6. Ver `.env.example` para variables de entorno opcionales.

## 📦 Despliegue en Vercel

1. Sube este repositorio a GitHub.
2. En [vercel.com](https://vercel.com), **New Project** → importa el repo.
3. Framework Preset: **Next.js** (autodetectado).
4. Deploy.

No se requieren variables de entorno para que el build funcione — la configuración vive en `src/lib/config.ts`. Las variables de `.env.example` son opcionales para integraciones futuras.

## 📄 Licencia

Todos los derechos reservados © Calculadoras España.
