# Fluent 2 Web design system

A code version of the **Microsoft Fluent 2 Web** community Figma file, for building HTML mocks.

Source: https://www.figma.com/design/X5qiNutiFaiAwk6CJ7aPA8/Microsoft-Fluent-2-Web--Community-
Extracted: 2026-10-28

## What's here

| Path | What it is |
|---|---|
| `tokens/tokens.css` | All design tokens as CSS custom properties: Light and Dark themes, spacing, radius, stroke, type, shadow, motion. Also includes the `.text-*` type ramp classes. |
| `tokens/tokens.json` | The same tokens as JSON, each color listing its original Figma variable path. |
| `tokens/tokens.js` | The same data as `window.FLUENT_TOKENS`, for pages opened from `file://`. |
| `tokens/figma-source.json` | Raw export from the Figma variables and styles, plus an inventory of the Figma component variants. |
| `tokens/build_tokens.py` | Rebuilds the three token files from `figma-source.json`. |
| `components/fluent.css` | Component styles (`.f-*` classes) built only from the tokens. |
| `index.html` | Live reference gallery for every token and component. |
| `templates/starter.html` | App-shell starting point for a new mock. |
| `examples/` | Mocks built on the system, with their own [README](examples/README.md). |

## Using it in a mock

```html
<link rel="stylesheet" href="fluent-2-web/tokens/tokens.css">
<link rel="stylesheet" href="fluent-2-web/components/fluent.css">
<body class="f-root"> … </body>
```

To start a new mock, copy `templates/starter.html` into a folder beside the others in `examples/`; its stylesheet paths already resolve from there. See [`examples/`](examples/README.md) for working mocks.

**Theme:** Light is the default. Without a `data-theme` attribute the page follows the OS. To force a theme, set `<html data-theme="dark">` or `data-theme="light"`.

## Token naming

Color tokens are the Figma **Mode** variable path in camelCase with `Rest` dropped:

| Figma variable | CSS token |
|---|---|
| `Neutral/Background/1/Rest` | `--colorNeutralBackground1` |
| `Neutral/Background/1/Hover` | `--colorNeutralBackground1Hover` |
| `Brand/Background/1/Rest` | `--colorBrandBackground1` |
| `Neutral/Foreground/On Brand/Rest` | `--colorNeutralForegroundOnBrand` |
| `Status/Danger/Foreground/1/Rest` | `--colorStatusDangerForeground1` |
| `Palette/Blue/Background/2/Rest` | `--colorPaletteBlueBackground2` |

Other tokens:
- **Spacing:** `--spacingHorizontal{None,XXS,XS,SNudge,S,MNudge,M,L,XL,XXL,XXXL}` and `--spacingVertical…` (0 2 4 6 8 10 12 16 20 24 32)
- **Radius:** `--borderRadius{None,Small,Medium,Large,XLarge,Circular}` (0 2 4 6 8 9999)
- **Stroke:** `--strokeWidth{Thin,Thick,Thicker,Thickest}` (1 2 3 4)
- **Type:** `--fontSizeBase100…600`, `--fontSizeHero700…1000`, the matching `--lineHeight…`, and `--fontWeight{Regular,Semibold,Bold}`
- **Type classes:** `.text-display`, `.text-large-title`, `.text-title-1…3`, `.text-subtitle-1/2`, `.text-body-1`, `.text-body-1-strong`, `.text-body-2`, `.text-caption-1`, `.text-caption-2`, and so on
- **Elevation:** `--shadow2 / 4 / 8 / 16 / 28 / 64`, plus `--shadow2Brand` and the other brand shadows
- **Brand ramp:** `--colorBrand10 … --colorBrand160`
- **Motion** (from the Fluent web defaults; the Figma file has none): `--duration*`, `--curve*`

## Components

Variants mirror the Figma component properties.

| Component | Classes |
|---|---|
| Button | `.f-button` + `--primary --outline --subtle --transparent`, `--small --large`, `--icon`, `--circular --square`, `--compound`, `.f-split-button` |
| Link | `.f-link` + `--subtle --inverted` |
| Field / Label | `.f-field` (+ `--error --warning --success --horizontal`), `.f-label`, `.f-field__hint`, `.f-field__message` |
| Input family | `.f-input .f-textarea .f-select .f-searchbox .f-spinbutton` + `--filled-darker --filled-lighter --underline`, `--small --large`, `.is-error .is-disabled .is-readonly` |
| Checkbox / Radio / Switch | `.f-checkbox` (`--circular`), `.f-radio`, `.f-radio-group`, `.f-switch` |
| Slider | `.f-slider` on `<input type=range>` (`--small`); set `--fill` from script to draw the filled rail |
| Badge | `.f-badge` + color `--brand --danger --success --warning --severe --important --informative --subtle-color`, appearance `--tint --outline --subtle`, size `--small --large --xlarge`, `--rounded` |
| Presence | `.f-presence--available/busy/away/oof/offline` |
| Avatar / Persona | `.f-avatar` (`--size`, palette colors, `--brand`, `--square`), `.f-avatar-group`, `.f-persona` |
| Card | `.f-card` + `--filled-alt --outline --subtle --interactive --small --large`, `__header __title __subtitle __preview __footer` |
| Divider | `.f-divider` + `--subtle --strong --brand --vertical` |
| Dialog / Drawer | `.f-overlay`, `.f-dialog` (`--small`), `.f-drawer` (`--inline`) |
| Popover / Tooltip | `.f-popover`, `.f-tooltip` + `--brand --inverted` |
| Menu | `.f-menu`, `.f-menu-item`, `.f-menu__section-header`, `.f-menu__divider` |
| Tabs | `.f-tablist` (`--vertical --small --circular`), `.f-tab[aria-selected]` |
| Nav | `.f-nav`, `.f-nav-item[aria-current=page]`, `--sub`, `.f-nav__section` |
| Breadcrumb | `.f-breadcrumb`, `__item`, `__divider` |
| Message bar | `.f-messagebar` + `--success --warning --error --multiline` |
| Toast | `.f-toast` |
| Progress / Spinner / Skeleton | `.f-progress` (`--value`, `--large`, status modifiers, `--indeterminate`), `.f-spinner`, `.f-skeleton` |
| Tag | `.f-tag` + `--outline --brand --small --xsmall --circular`, `.is-selected`, `__dismiss` |
| Toolbar | `.f-toolbar` (`--floating`), `__divider` |
| Accordion | `.f-accordion` on `<details>` |
| List / Tree / Table | `.f-list .f-list-item`, `.f-tree .f-tree-item` (`--level`), `.f-table` (`--small --smaller --large`) |
| Rating | `.f-rating` + `--marigold --brand` |
| Step dots | `.f-step-dots` > `.f-step-dot[aria-current=step]` (Carousel "Steps" nav) |
| Layout helpers | `.f-stack`, `.f-row` (`--gap`), `.f-spacer`, `.f-surface`, `.f-text-secondary/tertiary/brand` |

These Figma components have no CSS yet: Carousel, Swatch picker, Tag picker, Info label and Material acrylic. Their tokens exist, so they can be added when a mock needs them.

**Icons:** the gallery uses a few inline SVGs in the Fluent icon style. For more, use [Fluent UI System Icons](https://github.com/microsoft/fluentui-system-icons) at 16/20/24px with `class="f-icon"`.

## Viewing the gallery

`index.html` loads its CSS with relative paths, so serve the folder rather than opening the file directly:

```bash
python3 -m http.server 4321
```

Then open http://localhost:4321/

## Updating from Figma

Edit or re-export `tokens/figma-source.json`, then run:

```bash
python3 tokens/build_tokens.py
```

## Credits and licensing

The tokens and component specs come from the **Microsoft Fluent 2 Web (Community)** Figma file. Fluent, Fluent 2 and Segoe UI are Microsoft's; this repository only re-expresses the published design values as CSS so they can be used in code. It is not affiliated with or endorsed by Microsoft. Check Microsoft's own terms before shipping anything built on it, and note that Segoe UI itself is licensed by Microsoft and is not redistributed here — the font stack falls back to the system UI font where it is unavailable.

The CSS and build script in this repository are free to reuse.
