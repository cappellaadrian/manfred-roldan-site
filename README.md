# Manfred Roldán — Servicios

Personal-practice marketing page for **Manfred Roldán**, asesor patrimonial in San José, Costa Rica. Vanilla HTML/CSS/JS — no build step, no framework. Spanish (CR), *usted*.

## Run it locally

Any static server will do. From this folder:

```bash
python -m http.server 8080
# then open http://localhost:8080
```

Or open `index.html` directly in a browser (file:// works because there are no module imports or fetches).

## File map

| File | Purpose |
|---|---|
| `index.html` | The Servicios page — 13+ sections (nav · hero · aphorism · enfoque · servicios · type-wall · cifras · testimonios · sobre · notas · animated CTA · FAQ · contacto · footer) |
| `colors_and_type.css` | Brand design tokens — colors, type scale, spacing, motion. The source of truth. |
| `image-slot.js` | Web component used for the Sobre portrait placeholder |
| `assets/logo-monogram.png` | MR monogram (placeholder reconstruction) |
| `assets/logo-monogram-inverse.png` | MR monogram, light variant |

## Brand

- Surface: navy `#0E0D2C`
- Text: white `#FFFFFF`
- Accent: electric cobalt `#495CFF` — operative-words-only (the contrastive emphasis pattern). Never as a large fill except inside the animated CTA card gradient.
- Type: **Montserrat** ALL-CAPS for headlines, sentence-case for body. **Bodoni Moda** for the MR monogram only. **JetBrains Mono** for numerals.
- Voice: confident-not-boastful, plainspoken. No emoji. No exclamation marks. *Usted* by default.

Full brand documentation lives in the upstream design system bundle (out of repo).

## What's different from the source `Servicios.html`

The page was ported from the design bundle's `manfred-rold-n-design-system/project/Servicios.html`. Three changes from the source:

1. **Stripped the Tweaks panel.** The bundle ships a React/Babel-driven design-mode `<TweaksPanel>` that lets a designer mutate brand tokens at runtime. Removed in this production port — three unpkg `<script>` CDN tags and two inline script blocks.
2. **Newsletter form moved from Notas into the Footer.** Now sits as the footer's 5th column (`Marca · Servicios · Práctica · Contacto · Boletín`). Existing `#newsletter-form` JS validation handler still binds.
3. **New animated CTA card** inserted between Notas and FAQ. Lifted from the bundle's `ui_kits/website/cta-faq.html` — five radial-gradient blobs in cobalt/cream that drift across the card and pulse in radius, using CSS `@property` for GPU-friendly custom-property interpolation. Respects `prefers-reduced-motion`.

## Caveats

- **Portrait placeholder** in the Sobre section. The `image-slot` web component renders a labeled placeholder until a real portrait is dropped in. Replace by giving the slot a real `src`.
- **Logo is the bundle's placeholder reconstruction.** Swap `assets/logo-monogram.png` when Manfred provides the real wordmark.
- **Form submissions are client-side only.** Contact form and newsletter both `preventDefault` and show a success message — no backend wired.
- **Copy/numbers are from the design system's draft content.** AUM, retention %, rendimiento — these are illustrative until Manfred confirms real numbers.
