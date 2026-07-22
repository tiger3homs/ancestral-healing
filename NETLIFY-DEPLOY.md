# Netlify Drag-and-Drop Deploy

This repository now includes a static owner portal at `index.html`.

## Deploy

1. Use the generated zip: `ancestral-healing-netlify-drop.zip`.
2. In Netlify, go to **Add new site → Deploy manually**.
3. Drag and drop the zip file into Netlify.
4. Netlify will serve `index.html` as the home page.

No build command is required.

## What is inside

- The owner portal: `index.html`
- The generated file index: `site-manifest.json`
- All markdown documents, dashboards, PDFs, JSON data, and repo support files
- Existing pages such as:
  - `ancestral-healing-kb.html`
  - `ah-brain/reference/knowledge-base.html`
  - `ah-analytics/index.html`
  - `ah-autopilot/index.html`

## Updating the deploy zip later

If files are added, removed, or renamed, regenerate `site-manifest.json` and rebuild the zip so the portal file browser stays accurate.
