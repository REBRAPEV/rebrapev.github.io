# REBRAPEV website

Source for the REBRAPEV organization website at https://rebrapev.github.io.

## Structure

- `_config.yml`: site-wide Jekyll configuration
- `_data/navigation.yml`: main navigation
- `_layouts/` and `_includes/`: shared page structure
- `assets/css/main.css`: visual design
- `assets/images/`: logo, icons and photographs
- `assets/js/theme.js`: light/dark theme toggle
- root Markdown files: public site sections

## Editing content

Most routine updates only require editing a Markdown file. Navigation labels and destinations are centralized in `_data/navigation.yml`.

## Local preview

With Ruby and Bundler installed:

```bash
bundle install
bundle exec jekyll serve
```

Then open http://localhost:4000.

## Logo

The mark is an **amorphous atomic network**: nodes joined by bonds of near-constant
length but irregular angles, closing into rings of different sizes (4, 6 and 6). That
lack of long-range order is what distinguishes a glass from a crystal, so the mark
depicts the object of the network's research rather than merely decorating it. The
single warm node stands for a network modifier — the doping ion sitting in the
silicate network — and doubles as the focal point of the brand. Read as a graph
instead of as a structure, the same drawing is a *rede*: people and institutions
connected without a fixed hierarchy.

| File | Use |
| --- | --- |
| `assets/images/rebrapev-logo.svg` | Horizontal lockup (mark + wordmark) for slides, posters and documents |
| `assets/images/rebrapev-mark.svg` | Mark on its own |
| `assets/images/favicon.svg` | Browser tab icon; heavier strokes so it survives 16 px |
| `assets/images/favicon-32.png` | PNG fallback for browsers without SVG favicon support |
| `assets/images/apple-touch-icon.png` | 180x180 home-screen icon, brand tile |

The header draws the mark as inline SVG in `_includes/header.html` rather than
loading a file, so it picks up `--brand` and `--accent` and follows the light/dark
theme toggle. The standalone files carry those colours themselves and switch on
`prefers-color-scheme`. Both are generated from the same coordinates: if the geometry
is ever changed, update every copy together.

The lockup sets the wordmark in the same system font stack the site uses for its own
header, so it renders consistently with the live site; it is not converted to
outlines, which means it needs those fonts to be available.

## Design provenance

The first version was developed with the existing `hbrmn/hbrmn.github.io` site as a visual and structural reference and after reviewing the current Academic Pages template. The REBRAPEV layout and CSS were deliberately simplified rather than copying the full legacy theme stack.
