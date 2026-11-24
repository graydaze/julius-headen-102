# AGENTS.md — Repository Guardrails for Julius A. Headen Lodge No. 102 (`jah102.com`)

These rules are permanent for this repository. Every automated agent and human contributor must preserve them across all edits.

## 1. Zero Icon Dependencies
- **NEVER** install `astro-icon` or any `@iconify-json/*` packages. They conflict with modern Astro / Rolldown bundling and bloat builds.
- Use strictly raw, inline `<svg>` elements for all icons and emblems.

## 2. Explicit Dimensions on Every Inline SVG
- **ALWAYS** hardcode explicit HTML `width` and `height` attributes on every `<svg>` tag (for example: `width="24" height="24"` or `width="36" height="36"`), in addition to `viewBox`, so icons can never scale unconstrained if CSS loads late or utility classes change.

## 3. Tailwind CSS v4 & Design System Conventions
- Tailwind CSS v4 is loaded via `@tailwindcss/vite` in `astro.config.mjs` and configured via `@import "tailwindcss";` and `@theme` in `src/styles/global.css`.
- Keep global element selectors (`html`, `h1`, `h2`, `h3`) wrapped inside `@layer base` so Tailwind utility classes can override them cleanly.
- Preserve the Lodge visual tokens (`--color-navy-deep`, `--color-navy-lodge`, `--color-gold-metallic`, `--color-gold-bright`, `--color-gold-antique`, `--font-display`, `--font-sans`) and reduced-motion accessibility overrides.

## 4. GitHub Pages & CI/CD Requirements
- Keep `site: 'https://jah102.com'` in `astro.config.mjs`.
- Keep `public/.nojekyll` (empty file) and `public/CNAME` (`jah102.com`) so GitHub Pages serves the custom domain without Jekyll interference.
- In `.github/workflows/deploy.yml`:
  - **ALWAYS** keep `node-version: "24"` as a quoted string (never an unquoted number).
  - Use strictly standard ASCII spaces (`0x20`) — never non-breaking spaces (`U+00A0`) or tabs.

## 5. Mandatory Build Verification
- **ALWAYS** run `npm run build` and verify zero compiler, TypeScript, or bundler errors before concluding any edit.
