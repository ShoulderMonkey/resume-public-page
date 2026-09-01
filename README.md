# resume-public-page

This repository's only purpose is to host my resume as a web page.

Having spent way too much time using different resume builder apps, I decided it would be
faster and easier to just build a webpage.

## Where

https://shouldermonkey.github.io/resume-public-page/

## What it does

- **Bilingual** — Italian and English, switched with a button. No page reload, no second
  file. The language you pick is remembered in `localStorage`, and the first visit
  defaults to your browser language.
- **Print to PDF** — the download button opens the browser's native print dialog. The
  toolbar is hidden in `@media print`, so it never shows up in the exported file. Enable
  *Background graphics* in the print options or the sidebar comes out white.
- **Two A4 pages in print** — page 1 holds profile and experience, page 2 education,
  with the sidebar band repeated on every page. On screen the layout collapses to a
  single column on narrow screens.
- **Certificates** — the AI training certificates are linked from the education section
  and served from `certificates/`.

## Stack

None. One HTML file, inline CSS, ~20 lines of vanilla JS. No build step, no framework, no
CDN, no dependencies. Open `index.html` in a browser and that's it.

## Structure

```
index.html                                  the whole resume
certificates/attestato-ai-base-2026.pdf     GOL AI Foundations, Apr 2026
certificates/attestato-ai-avanzato-2026.pdf GOL AI Advanced, May–Jun 2026
```

## Editing

Text that changes with the language carries a `data-l="it"` or `data-l="en"` attribute.
CSS hides whichever doesn't match the current language:

```css
html[data-lang="it"] [data-l="en"] { display: none !important; }
html[data-lang="en"] [data-l="it"] { display: none !important; }
```

So when adding content, always add both variants. Missing one means that block silently
disappears in the other language.

Sections marked `TODO [agent]` in the source are the ones still to be filled in.

## Notes

The certificate PDFs are redacted: fiscal code, date and place of birth were removed from
the file content, not covered with a box — the text is genuinely gone and can't be
recovered by copy-paste or `pdftotext`. Don't replace them with the originals: this page is
public and indexable. Phone number is left out of the page for the same reason.
