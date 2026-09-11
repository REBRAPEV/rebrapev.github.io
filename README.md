# REBRAPEV website

Source for the REBRAPEV organization website at https://rebrapev.github.io.

## Structure

- `_config.yml`: site-wide Jekyll configuration
- `_data/navigation.yml`: main navigation
- `_layouts/` and `_includes/`: shared page structure
- `assets/css/main.css`: visual design
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

## Design provenance

The first version was developed with the existing `hbrmn/hbrmn.github.io` site as a visual and structural reference and after reviewing the current Academic Pages template. The REBRAPEV layout and CSS were deliberately simplified rather than copying the full legacy theme stack.
