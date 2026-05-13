# ma-site — AZ Consultoría

Landing page for Mario Azeta / AZ Consultoría.

- **Live:** https://popex404.github.io/ma-site/ (GitHub Pages)
- **Target domain:** azetas365.com (TBD)
- **Stack:** vanilla HTML/CSS/JS, single file, no build step.

## Origin

Base page imported from a Claude artifact built with Mario:
https://claude.ai/public/artifacts/c715cf85-332a-4c9a-94d9-8fff24ed8b58

## Development

No build step. Open `index.html` directly in a browser, or serve locally:

```
python -m http.server 8080
```

## Brand tokens

Defined in `:root` CSS variables at the top of `index.html`:

| Token | Hex | Role |
|---|---|---|
| `--azul` | `#0B2B5C` | Azul oscuro principal |
| `--azul-mid` | `#1A4A8A` | Azul medio |
| `--cyan` | `#2EB5E8` | Cyan logo |
| `--naranja` | `#F5831F` | CTA / acento |

Fonts: Syne (headings) + DM Sans (body), Font Awesome icons — all from CDN.
