# Netlify Drag-and-Drop Deploy

This repository ships as a no-build static owner portal. The home page is both a business case for the Ancestral Healing workspace and a searchable, browser-based source explorer.

## Deploy

1. Use the generated `ancestral-healing-netlify-drop.zip` file in this repository.
2. In Netlify, choose **Add new site → Deploy manually**.
3. Drag the zip into Netlify’s upload area.
4. Open the generated URL. Netlify serves root-level `index.html` automatically; no build command or environment variables are required.

> Do not upload the project folder and the zip together. Upload the generated zip by itself.

## What the owner portal includes

- **Business case:** executive summary, owner Q&A, evidence, cost scenarios, and the six-week rollout.
- **Pilot offer:** a low-risk, two-week Automation Pilot, a Phase 2 expansion offer, optional optimization support, explicit scope boundaries, and owner-approval safeguards.
- **Four workspace layers:** AH Brain knowledge base, channel intelligence, autopilot workflow plan, and owner portal.
- **Source proof:** shortcut cards plus a searchable and filterable file explorer powered by `site-manifest.json`.
- **Browser review:** markdown renders in the built-in reader (with a raw mode); HTML and PDFs can be previewed, opened, or downloaded.

The pilot CTA is intentionally a recipient-free `mailto:` inquiry placeholder because this repository does not contain a project contact email. Add the intended recipient to that link in `index.html` before sharing the public portal if a direct email destination is available.

## Deployment contents

The zip contains all non-Git project files except the final zip itself, including:

- `index.html` — owner pitch and source portal
- `site-manifest.json` — generated file index used by the explorer
- `NETLIFY-DEPLOY.md` — these instructions
- Markdown documentation, dashboards, PDFs, JSON data, and existing project archives

## Updating the deploy package

When project files change:

1. Regenerate `site-manifest.json` from all deploy files, excluding `.git` and `ancestral-healing-netlify-drop.zip`.
2. Rebuild `ancestral-healing-netlify-drop.zip` with those same files, keeping `index.html` at the archive root.
3. Validate that the manifest file list/count matches the deploy files, JavaScript in `index.html` parses, and the archive includes `index.html`, `site-manifest.json`, and this file with no `.git` paths.
4. Deploy the newly generated zip.

The explorer relies on browser `fetch`, so it should be viewed through Netlify (or another static HTTP server), rather than opening `index.html` directly from a local file path.
