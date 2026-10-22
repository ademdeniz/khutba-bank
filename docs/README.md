# Khutba Bank

Bilingual (Bosnian / English) khutbas for the Bošnjačka Islamska Zajednica Erie.

Live site: https://ademdeniz.github.io/khutba-bank/

A static site: plain HTML, CSS and JavaScript with no build step. GitHub Pages serves it from the `/docs` folder on `main`.

## Files

| File | Purpose |
| --- | --- |
| `index.html` | Page layout, tabs (All Khutbas, Style Guide, Sources) and the app script |
| `style.css` | Styling: deep green `#1a472a`, gold `#d4af37`, dark mode, single column below 768px |
| `khutbas.js` | All khutba content, as the global array `window.KHUTBAS` |

## Adding a khutba

Append an object to `window.KHUTBAS` in `khutbas.js`:

```js
{
  id: "blagoslov-u-nevolji",          // unique, URL-safe; also the anchor (#blagoslov-u-nevolji)
  title_bs: "Blagoslov u Nevolji",
  title_en: "Blessing in Hardship",
  date: "2026-10-16",                 // YYYY-MM-DD; upcoming dates show first in delivery order, then past ones newest first
  source: "Original",                 // "Original" or "Adapted"
  source_url: "",                     // direct link to the khutbahbank.org.uk page when adapted
  tags: ["sabr", "tawakkul"],
  series: {                           // optional: groups khutbas into a numbered series
    name_bs: "Zajednica i odgovornost", name_en: "Community and Responsibility", part: 1, total: 6
  },
  references: [                       // optional: hadith and other sources, shown at the bottom
    { label: "Sahih Muslim 2999", url: "https://sunnah.com/muslim:2999" }
  ],
  rows: [
    {
      bs: "Bosnian paragraph",
      en: "English paragraph",
      arabic: "",                     // Qur'anic Arabic, copied from quran.com or tanzil.net
      arabic_ref: "",                 // e.g. "Al-Mulk 67:2"
      arabic_url: ""                  // e.g. "https://quran.com/67/2"
    }
  ]
}
```

A row with `arabic` renders a full-width, right-aligned Arabic row above its Bosnian and English cells. Every `arabic_url` and `references` entry, plus `source_url`, is listed automatically under "Izvori / Sources" at the bottom of the khutba.

## House style

- Bilingual only: every row has a Bosnian cell and an English cell.
- No fabricated hadith or Qur'anic verses. If a citation cannot be verified, omit it.
- Arabic for every cited verse comes from quran.com or tanzil.net, and links to quran.com.
- Every hadith names its collection (Bukhari, Muslim, Tirmidhi, ...).
- Keep it short: reading both languages aloud takes 10 to 15 minutes at most (about 1,300 to 1,800 words total). Each card shows its estimated reading time.
- Emotionally grounded, spiritually reflective, warm flowing prose.
- No em dashes in khutba text.
- All sources cited at the bottom with working links.

## Local preview

Open `docs/index.html` directly in a browser, or run `python3 -m http.server -d docs` and visit http://localhost:8000.
