# CÀNONE Template Community

Ready-to-use templates for [CÀNONE Studio](https://github.com/marcozeus/canone) — the desktop visual builder for professional static websites.

Every template is a `.canone` file that opens directly in the app: zero setup, zero dependencies, zero subscriptions.

---

## Available templates

| Template | Category | Pages |
|----------|----------|-------|
| **Business Starter** | business | Home, Contacts |
| **Portfolio Creativo** | portfolio | Home, Works, Contacts |
| **Landing Conversion** | landing | Single page |
| **Ristorante & Locale** | business | Home (menu, reservations, story) |
| **Blog Minimal** | blog | Home, About |

Downloadable directly from the CÀNONE HomeScreen → **TEMPLATE COMMUNITY** button.

---

## Repository structure

```
index.json                          ← index read by the app every 24h (localStorage cache)
templates/
  <template-slug>/
    progetto.canone                 ← project file (JSON)
    preview.jpg                     ← preview image 1200×800px (required for external PRs)
```

---

## Contributing a template

Built something great in CÀNONE Studio and want to share it? Welcome.

### 1. Build your template in CÀNONE Studio

Design your site as usual in the editor. Use library blocks, Unsplash images or SVG placeholders, and credible placeholder text (not just "Lorem ipsum everywhere"). When you're happy with it, save the `.canone` file.

### 2. Prepare the files

```
templates/
  your-template-name/
    progetto.canone     ← the file saved from CÀNONE Studio
    preview.jpg         ← screenshot 1200×800px
```

### 3. Update index.json

Add your entry to the `templates` array:

```json
{
  "id": "your-template-slug",
  "nome": "Your Template Name",
  "descrizione": "One sentence describing the template (max 120 characters).",
  "categoria": "business",
  "autore": "Your Name",
  "badge": null,
  "preview": "https://raw.githubusercontent.com/marcozeus/canone-templates/main/templates/your-template-slug/preview.jpg",
  "rawUrl": "https://raw.githubusercontent.com/marcozeus/canone-templates/main/templates/your-template-slug/progetto.canone"
}
```

### 4. Open a Pull Request

Title: `Template: Your Template Name [category]`

Description: brief explanation of the template, who it's for, what it contains.

---

## `.canone` file schema

The `.canone` file is JSON. CÀNONE Studio accepts both **English keys** (recommended for community templates) and Italian keys. Use English — it's the official schema for this repo.

### Root object

```json
{
  "version": "3.0.0",
  "name": "Your Site Name",
  "created": "2026-01-01T00:00:00.000Z",
  "updated": "2026-01-01T00:00:00.000Z",
  "globalSettings": { ... },
  "layouts": [ ... ],
  "folders": [],
  "assets": [],
  "pages": [ ... ]
}
```

| Field | Type | Description |
|-------|------|-------------|
| `version` | string | Always `"3.0.0"` |
| `name` | string | Project name shown in the app |
| `globalSettings` | object | Colors, typography, tokens — see below |
| `layouts` | array | Layout templates (header/footer zones) |
| `folders` | array | Page folders — leave `[]` for flat structure |
| `assets` | array | Downloadable files (PDF, ZIP…) — usually `[]` |
| `pages` | array | Pages — see below |

### `globalSettings`

```json
{
  "primaryColor": "#C9A84C",
  "secondaryColor": "#1a1a2e",
  "fontHeading": "'Montserrat', sans-serif",
  "fontBody": "'Inter', sans-serif",
  "favicon": "",
  "tokenPrimary": "#C9A84C",
  "typographyBase": 16,
  "typographyRatio": 1.333,
  "fontPairId": null,
  "temiSalvati": []
}
```

### `layouts`

Always include at least the Standard layout (id `"layout-standard"`):

```json
[
  {
    "id": "layout-standard",
    "nome": "Standard",
    "zone": {
      "header": { "components": [], "styles": {} },
      "footer": { "components": [], "styles": {} }
    },
    "menu": []
  }
]
```

### `pages` — each page

```json
{
  "id": "page-home",
  "name": "Home",
  "slug": "index",
  "order": 0,
  "folderId": null,
  "layoutId": null,
  "seo": {
    "title": "Page Title",
    "description": "Meta description.",
    "ogTitle": "OG Title",
    "ogDescription": "OG Description.",
    "ogImage": "",
    "canonical": "",
    "robots": "index"
  },
  "customCode": { "head": "", "bodyEnd": "", "css": "" },
  "gsapTimeline": [],
  "variantiAB": [],
  "variantiLingua": {
    "it": {
      "gjsData": {
        "components": [ ... ],
        "styles": [],
        "assets": []
      },
      "seo": { ... },
      "customCode": { "head": "", "bodyEnd": "", "css": "" }
    }
  }
}
```

| Field | Type | Notes |
|-------|------|-------|
| `slug` | string | `"index"` for the homepage, kebab-case for others |
| `order` | number | Determines page order in the sidebar (0-based) |
| `folderId` | string\|null | `null` = root level |
| `layoutId` | string\|null | `null` = inherits from folder or Standard layout |
| `variantiLingua` | object | Keys are language codes (`"it"`, `"en"`, …). At least `"it"` required. |
| `gjsData.components` | array | GrapesJS component tree |

### Language support

If your template supports multiple languages, add them to `variantiLingua`:

```json
"variantiLingua": {
  "it": { "gjsData": { ... }, "seo": { ... }, "customCode": { ... } },
  "en": { "gjsData": { ... }, "seo": { ... }, "customCode": { ... } }
}
```

---

## Acceptance rules

**Content**
- Template must open correctly in CÀNONE Studio 3.0+
- Credible placeholder text (not just "Lorem ipsum everywhere")
- Images only from approved CDNs: Unsplash (`images.unsplash.com`), inline SVG placeholders
- Category must be one of: `business` `portfolio` `landing` `blog` `ecommerce` `evento`

**Code and dependencies**
- External CDNs only from the CÀNONE whitelist: GSAP, Google Fonts, Tailwind CDN
- Forms only via: Web3Forms, Mailchimp, Brevo — no proprietary backends
- No calls to external APIs that require authentication
- `.canone` file < 5MB, base64 images < 2MB total

**Preview**
- JPG or PNG, minimum 1200×800px
- Must show the Home page (not an internal page)
- No watermarks, no personal logo prominently visible in the image

**License**
- By contributing you agree your template is distributed under the MIT license
- Your name stays in the `autore` field permanently

---

## FAQ

**Can I use real client images?**
No. Use Unsplash images (free license) or graphic placeholders. Client images must not end up in a public repo.

**Can the template have multiple languages?**
Yes, CÀNONE supports multi-language. Include as many language variants as you want in `variantiLingua`.

**Can I make a "premium" template I sell elsewhere?**
Templates in this repo are free for everyone. If you want to sell premium templates, wait for the CÀNONE Pro release (coming soon) where there will be a dedicated channel.

**Can I set the "premium" or "popular" badge myself?**
No, badges are assigned by the maintainer based on downloads and quality.

---

*Created and maintained by the CÀNONE Team. Issues and suggestions welcome.*
