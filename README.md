# devrocksapps.github.io

The DevRocks site: what the business is, what PartyBook is, and the policy
pages a payment gateway and the Play Store both require.

Plain HTML and one stylesheet. No build step, no dependencies, no framework —
so it cannot break between edits, and anybody can fix a typo.

## Why it exists

Three separate requirements, one site:

1. **Razorpay activation** asks for a business website showing what is sold,
   at what price, with contact details and a refund policy.
2. **The Play Store requires a publicly hosted privacy policy URL** for every
   app. `/partybook/privacy-policy/` is PartyBook's.
3. **A route into the business from inside the app.** PartyBook's request
   screens point at `partybook.support@gmail.com`; this site is where somebody
   who wants to read before writing ends up.

## Publishing

```bash
git init
git add -A
git commit -m "The DevRocks site"
git branch -M main
git remote add origin https://github.com/devrocksapps/devrocksapps.github.io.git
git push -u origin main
```

Then **Settings → Pages → Source: deploy from branch `main`, folder `/`**.
Live at `https://devrocksapps.github.io/` within a couple of minutes, with HTTPS.

The repository has to be **public** for GitHub Pages on the free plan. That is
fine for policy pages — but never put anything secret in here.

## Before publishing

Everything still to be filled in is marked in the pages themselves with a
yellow highlight. Search for `class="todo"`:

- **City and state**, on `/contact/` and in the governing-law clause of
  `/terms/`.
- **The prices** on `/partybook/pricing/`. They come from the plan, not from a
  live price list, and a customer will hold you to them.
- **The refund timings** on `/refund-policy/`. The 3-working-day figure is a
  promise.
- **Water Sort** on the home page needs a link, and its own privacy policy
  before it is published.

A full postal address is deliberately absent. Razorpay may ask for one during
review; add it to `/contact/` then rather than up front.

## Structure

```
/                                 DevRocks, the publisher
/contact/
/terms/
/refund-policy/
/partybook/                       the app
/partybook/pricing/
/partybook/privacy-policy/        <- the URL the Play Store listing needs
```

A folder per app, so the next one is `/watersort/privacy-policy/` and the
business pages above are not written out a second time.

## Editing

Every page is standalone: same header, same footer, `/style.css` for
everything visual. Change a colour in that one file and the whole site
follows. The palette matches `lib/theme/app_theme.dart` in the PartyBook
repository, so the site and the app look like the same product.
