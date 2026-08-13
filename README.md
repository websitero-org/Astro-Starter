# Astro Starter

Astro starter for agency and business sites — demo pages, a Decap CMS blog, SEO tooling, dark mode, and Netlify-ready deployment.

## Quick Start

```bash
git clone https://github.com/websitero-org/Astro-Starter
cd Astro-Starter
npm install
npm run dev
```

Open [http://localhost:4321](http://localhost:4321).

## What's Included

**Pages**

| Route | File |
| --- | --- |
| `/` | Landing page (Hero, Services, Gallery, FAQ, CTA, etc.) |
| `/about/` | About |
| `/contact/` | Contact |
| `/faq/` | FAQ |
| `/portfolio/` | Portfolio |
| `/reviews/` | Reviews |
| `/services/` | Services overview |
| `/services/service-1/`, `/services/service-2/` | Service detail pages |
| `/blog/` | Blog index |
| `/blog/[slug]/` | Blog post |
| `/admin` | Decap CMS dashboard |

**Stack**

- Astro 7 with View Transitions (`ClientRouter`)
- CSS stylesheets in `src/styles/` (design tokens in `root.css`, dark mode in `dark.css`)
- Decap CMS + [DecapBridge](https://decapbridge.com/) authentication
- Content Collections for blog posts (`src/content.config.ts`)
- `@astrojs/sitemap`, `astro-icon`, Autoprefixer
- Image optimization via `astro:assets` (`<Image />`, `<Picture />`, and `CSPicture`)

## Configure

| File | Purpose |
| --- | --- |
| `src/data/client.ts` | Site title, URL, business info, SEO/OG defaults |
| `src/components/Header/StaticHeader.astro` | Navigation links (hardcoded markup) |
| `src/styles/root.css` | CSS variables — colors, fonts, spacing |
| `astro.config.mjs` | Site URL, sitemap, icon integration |
| `public/admin/config.yml` | Decap CMS backend and blog fields |
| `public/robots.txt` | Crawler rules and sitemap URL |

Copy `src/pages/_template.astro` when scaffolding new pages.

## Project Structure

```
src/
├── assets/images/       # Optimized images (blog uploads go here via CMS)
├── components/        # UI sections (component-per-folder, each imports its CSS)
├── content/blog/        # Blog markdown
├── data/client.ts       # Site and business configuration
├── icons/               # SVGs for astro-icon <Icon />
├── js/                  # nav.js, JSON-LD schema helpers, utils
├── layouts/             # BaseLayout, blog layouts
├── pages/               # Routes
└── styles/              # Global and component stylesheets

public/
├── admin/               # Decap CMS config and preview styles
└── assets/favicons/     # Favicon set
```

**Path aliases** (see `tsconfig.json`): `@components`, `@layouts`, `@assets`, `@data`, `@styles`, `@js`.

## Navigation

Navigation lives in `StaticHeader.astro` — edit the markup directly to add, remove, or reorder links and dropdowns. `BaseLayout.astro` imports this header by default.

## Scripts

| Command | Description |
| --- | --- |
| `npm run dev` | Dev server on port 4321 |
| `npm run build` | Production build to `dist/` |
| `npm run preview` | Preview the production build |
| `npm run remove-demo` | Remove demo pages and components |
| `npm run remove-decap` | Remove Decap CMS (optionally keep blog files) |
| `npm run remove-dark-mode` | Remove dark mode styles and toggle |

Removed files are backed up under `scripts/deleted/`.

## Deployment

Target platform: **Netlify** (`netlify.toml` includes build cache via `netlify-plugin-cache`).

Before going live, update:

1. **`astro.config.mjs`** and **`src/data/client.ts`** — set your production URL
2. **`public/robots.txt`** — replace `<YOUR SITE>` with your domain
3. **`src/data/client.ts`** — business name, address, phone, email, social links
4. **`public/assets/favicons/`** — replace with your favicon set
5. **`public/assets/social.jpg`** — add a 1200×600 default OG image (referenced in `client.ts`)
6. **`public/admin/config.yml`** — set your GitHub repo and DecapBridge credentials

Set up authentication at [decapbridge.com](https://decapbridge.com/), then paste the backend snippet into `config.yml`. Access the CMS at `/admin` on your deployed site.

Verify locally:

```bash
npm run build && npm run preview
```

## Learn More

- [Astro documentation](https://docs.astro.build)
- [Decap CMS documentation](https://decapcms.org/docs/intro/)
- [Content Collections](https://docs.astro.build/en/guides/content-collections/)
