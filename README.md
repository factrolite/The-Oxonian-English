# The Oxonian English

A small static site served with GitHub Pages. No build step, no installs, no framework — every page is a self-contained HTML file that keeps working offline.

**Live site:** https://factrolite.github.io/The-Oxonian-English/

## Pages

| File | What it is |
| --- | --- |
| `index.html` | MCQ practice library for Class 12 chemistry, Hindi medium — ठोस अवस्था, विलयन, रासायनिक बलगतिकी, वैद्युतरसायन, पृष्ठ रसायन. Ships an offline KaTeX build so formulas render without a network connection. |
| `ph.html` | The Oxonian English landing page. |
| `reading-page.html` | Demo reading page laid out like an open book — two-page spread, running heads, drop cap, and paper / sepia / night themes. |
| `upnote-ui.html` | UpNote interface demo. |
| `mcq_library_v7-1.html` | Old URL for the MCQ library. Now a redirect stub that forwards to `index.html`, so existing bookmarks keep working. |
| `404.html` | Custom not-found page used by GitHub Pages. |
| `favicon.svg` | Site icon. |

## Adding questions to the MCQ library

`index.html` is roughly 700 KB, but almost all of that is the offline math engine bundled at the very bottom of the file (below the `KATEX PAYLOAD` marker). That block is never edited.

To add a chapter, insert a new block immediately **before** the end-of-chapters marker comment:

```html
<script type="text/plain" class="chapter-src" data-id="unique-ascii-slug" data-title="अध्याय का नाम">
  ...questions...
</script>
```

Then make one precise string replacement rather than rewriting the file — the page is too large to regenerate safely by hand, and a full rewrite risks losing the bundled engine.

## Local preview

```bash
python3 -m http.server 8000
# then open http://localhost:8000
```

## Deploying

Push to `main`. GitHub Pages (legacy build, source: `main` branch, `/` root) republishes automatically within about a minute.

## Notes

- The site is dark-first and written for Hindi-medium readers; the reading page is the one English-language demo.
- No licence file is included. That is a deliberate choice by the owner — add one only if you want to grant explicit reuse rights.
