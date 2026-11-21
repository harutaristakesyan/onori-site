# onori.money

The website of Onori, a paycheck budget for iPhone and Mac. Jekyll on GitHub Pages.

## What is here

- `index.html`: the homepage. It carries its own inline CSS (`_includes/index-css.scss`), the two
  films and the live demo card.
- The content pages (`family`, `receipts`, `multi-currency`, `pricing`, `privacy-first`, `privacy`,
  `faq`, `demo`, `press`, `whats-new`, the blog) use `_layouts/page.html` and `assets/site.scss`.
- `_sass/`: the shared design tokens and partials. The site follows the system light and dark
  setting, like the app, and its only colours are the app's own category colours.
- `rates/latest.json`: the exchange-rate snapshot the app downloads once a day.
  `scripts/build_rates.py` builds it; `.github/workflows/rates.yml` runs that every day.
- `.github/workflows/deploy.yml`: builds with the Jekyll pinned in `Gemfile.lock` and publishes
  on every push to `main`.

## Rules

- A claim on a page has to be true of the app as it ships. Check the app's code before writing one.
- The pages ask no other company for anything: fonts, films and images are served from this site.
  The homepage counts its own third-party requests, and the count has to stay 0.
- `rates/latest.json` keeps its path and shape. The app decodes it as
  `{"base": "EUR", "asOf": "yyyy-MM-dd", "rates": {"USD": 1.0842}}`.
- Screenshots are real captures of the app with the demo ledger, never drawn.

## The App Store button

`_config.yml` holds `app_store_url` and `app_store_id`. While they are empty, every button that
would lead to the store reads "Coming soon" (`_includes/cta.html`). Set both on launch day.

## Preview

    bundle install
    bundle exec jekyll serve      # http://127.0.0.1:4000

## Domain

`onori.money` points at GitHub Pages: four `A` records on the apex
(`185.199.108.153` to `185.199.111.153`) and a `CNAME` for `www` to `harutaristakesyan.github.io`.
