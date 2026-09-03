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

- **Water Sort** on the home page needs a link, and its own privacy policy
  before it is published.

**Settled, so nobody has to wonder again:**

- **The price** is Rs.999 per branch per year, described on the pricing page as
  introductory so raising it later is a plan that was announced rather than a
  surprise. There are no tiers and no order cap: BILLING_PLAN.md has the
  argument, but the short version is that a soft cap cannot be enforced on an
  annual cycle without a payment mandate, and the machinery would have been
  protecting about ninety rupees a year. A refund is started within 7 working
  days. All of these are published promises, so a change has to be made in the
  pages and not only in the plan.
- The **Grievance Officer** is Sarankumar R, named on `/contact/` and in
  section 10 of the privacy policy. India's SPDI Rules 2011 want a named
  person rather than a role, which is why it is a name and not "the
  proprietor".
- **No postal address and no phone number**, deliberately. The Consumer
  Protection (E-commerce) Rules 2020 are generally read as expecting both from
  an online seller, and a gateway may ask during review — add them to
  `/contact/` if asked, rather than up front. The governing-law clause says
  "the courts of India" for the same reason: naming one court needs an address
  to match it.

  **A note saying all of that used to appear on `/contact/` itself, and was
  removed on 3 September 2026 at the vendor's request.** It was written as a
  reminder to the vendor and it was on the wrong side of the screen: a
  customer reading it learns only that the seller is unsure whether their own
  page is compliant, which reads worse than the omission it was explaining.
  Razorpay's KYC review then passed with the address absent and never asked.
  The open question is unchanged and is recorded here and in
  `SaiBrindhavanApp/PLAY_LISTING.md` — where the vendor will see it and a
  customer will not.

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
