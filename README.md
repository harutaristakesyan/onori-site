# onori.money

The website of Onori, a paycheck budget for iPhone and Mac. Plain static files in `site/`, no build
step.

## What is here

- `site/index.html`, `site/privacy.html`, `site/404.html`: the pages. One stylesheet, `site/assets/site.css`.
- `site/rates/latest.json`: the exchange-rate snapshot the app downloads once a day.
- `scripts/build_rates.py`: builds that snapshot from the provider.
- `.github/workflows/deploy.yml`: publishes `site/` to GitHub Pages on every push to `main`.
- `.github/workflows/rates.yml`: runs the script every day, commits a changed snapshot and asks for a deploy.

## Rules

- A claim on a page has to be true of the app as it ships. Check the app's code before writing one.
- The pages ask no other company for anything: fonts and images are served from this site.
- `site/rates/latest.json` keeps its path and shape. The app decodes it as
  `{"base": "EUR", "asOf": "yyyy-MM-dd", "rates": {"USD": 1.0842}}`.

## Preview

    python3 -m http.server 8765 --directory site

Then open `http://localhost:8765/`.

## Domain

`onori.money` points at GitHub Pages: four `A` records on the apex
(`185.199.108.153` to `185.199.111.153`) and a `CNAME` for `www` to `harutaristakesyan.github.io`.
