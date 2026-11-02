# Examples

Mocks built against this design system. Each one links `../../tokens/tokens.css` and
`../../components/fluent.css` and uses only `.f-*` classes and `var(--token)` values,
so all of them work in light and dark.

Serve the repository root and open them from there:

```bash
python3 -m http.server 4321
```

| Example | What it shows |
|---|---|
| [`sketchup-fluent/`](sketchup-fluent/) | The SketchUp 2027 desktop window rebuilt on Fluent: command bar with tool fly-outs, document tabs, viewport, the Default Tray panels, a panel icon rail and a status bar. Light and dark, with a theme toggle. |
| [`hatch-scale/`](hatch-scale/) | Six layouts for scaling a hatch pattern — X/Y sliders from fine to coarse, exact number fields, and a chain link or lock switch to keep the aspect ratio. All six are interactive. |
| [`plg-onboarding/`](plg-onboarding/) | A three-step feature walkthrough dialog, with step dots, Back/Next and a Help Center link card. Open `multiplayer-walkthrough.html?step=2` to start on a given step. |

## Icons

`sketchup-fluent/icons/` holds 144 SketchUp icons (light in `icons/`, dark in `icons/dark/`)
exported from Trimble's own SketchUp icon library. They are Trimble's artwork, included here
only so the example renders; they are not part of the design system and are not covered by
this repository's licence.

The other examples draw their icons inline in the Fluent style.
