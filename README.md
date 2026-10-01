# REBRAPEV website

Source for the REBRAPEV organization website at https://rebrapev.github.io.

## Structure

- `_config.yml`: site-wide Jekyll configuration
- `_data/navigation.yml`: main navigation
- `_layouts/` and `_includes/`: shared page structure
- `assets/css/main.css`: visual design
- `assets/images/`: logo, icons and photographs (event photos in `assets/images/eventos/<slug>/`)
- `_eventos/`: one Markdown file per event (Jekyll collection, see below)
- `assets/js/theme.js`: light/dark theme toggle
- root Markdown files: public site sections

## Editing content

Most routine updates only require editing a Markdown file. Navigation labels and destinations are centralized in `_data/navigation.yml`.

## Adding an event

Each event is one file in `_eventos/`, published at `/eventos/<file name>/`. The
index at `/eventos/` and the event block on the home page are generated from these
files, so nothing else needs editing.

1. Copy an existing file in `_eventos/` and name it `AAAA-MM-DD-short-name.md`
   (the name becomes the URL, e.g. `/eventos/2026-09-28-kickoff-curitiba/`).
2. Fill in the front matter:

   ```yaml
   title: "Event title"
   date: 2027-03-10          # start date: sorting and upcoming/past split
   end_date: 2027-03-12      # optional, multi-day events
   time: "09:00–18:00"       # optional
   location: "Venue, City, UF"
   format: presencial        # presencial | online | híbrido
   context: "Host event"     # optional
   participants: "..."       # optional
   type: rede                # rede (REBRAPEV event) | comunidade (event of interest)
   summary: "One sentence for the index card and the home page."
   cover: /assets/images/eventos/<slug>/photo.jpg      # optional
   cover_alt: "Description of the photo"
   cover_caption: "Caption on the home page"          # optional
   gallery:                  # optional
     - src: /assets/images/eventos/<slug>/photo.jpg
       alt: "Description of the photo"
       caption: "Caption. <span>City, date.</span>"
       width: 2000
       height: 1126
       wide: true            # full width; items without it go two per row
   ```

3. Write the description below the front matter. The gallery appears after the
   text, or where you put the line `<!-- galeria -->` (use it once). A single extra
   photo can be placed anywhere in the text with
   `{% include event-figure.html src="..." alt="..." caption="..." width="..." height="..." wide=true %}`.
4. Put the photos in `assets/images/eventos/<slug>/`, where `<slug>` is the file
   name without `.md`.

"Próximos eventos" versus "Eventos realizados" is decided when the site is built
(GitHub Pages is static): an event moves to the past list on the first build after
its last day. Pushing any change, or re-running the Pages build, refreshes it.

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
