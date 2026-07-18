# Assured Law Website

Marketing website for Assured Law, a Nevada firm handling nuisance damage claims, premises liability litigation, Justice Court claims, personal injury, and construction defect.

Live domain: www.assuredlaw.com
Host: Render (static site, auto-deploys on push to `main`)

## Structure

The site is a single self-contained HTML file with client-side JavaScript routing. No build step, no framework, no server-side dependency.

```
index.html                    Entire site: all pages, styles, and scripts
assets/assured-law-logo.svg   Original logo asset (the logo is also embedded
                              inline in index.html; this file is kept as the
                              canonical source)
```

## Pages

Routing is handled in JavaScript by the `navigate()` function. Page IDs:

| Route      | Content                                                    |
|------------|------------------------------------------------------------|
| `home`     | Dictionary hero, stats, practice areas, CTA                |
| `nuisance` | Public vs. private nuisance, five elements, remedies       |
| `premises` | Duty of care tiers, incident types, five elements, damages |
| `justice`  | Small claims vs. Justice Court, advantages, four elements  |
| `injury`   | Negligence framework, claim types, damages                 |
| `defect`   | NRS Chapter 40 process, defect categories, HOA claims      |
| `review`   | Clio Grow scheduler, nuisance intake embed, on-page form   |

## Third-Party Integrations

1. **Google Fonts.** Cormorant Garamond and Inter, loaded from fonts.googleapis.com.
2. **Clio Grow scheduler.** Iframe on the Case Consultation page, pointing to `https://mygoodlawyers.cliogrow.com/book`.
3. **Clio Grow nuisance intake form.** Iframe shown when "Nuisance Claim" is selected, pointing to `https://mygoodlawyers.cliogrow.com/intake/551caf0df0fccdca5be4e8de62d7ac0d`.

Both iframes have a fallback direct link beneath them in case embedding is blocked by response headers.

## Known Issues (Pre-Launch Blockers)

1. **The on-page intake form does not transmit data.** `submitForm()` validates input and displays a success message, but nothing is sent anywhere. This affects four of the five case-type paths (premises, Justice Court, personal injury, construction defect). Only the nuisance path routes to a live Clio form. Resolve before directing any traffic to the site.
2. **Five placeholder links** (`href="#"`): Our Attorneys, Results, Privacy Policy, Terms of Use, Disclaimer. A privacy policy is needed given the third-party Clio embeds.
3. **Single-URL architecture.** All pages share one URL, so search engines index one page. Acceptable at launch; revisit before investing in search traffic.

## Deployment (Render)

Connected as a Render Static Site. Configuration:

- Branch: `main`
- Build Command: (blank)
- Publish Directory: `.`

Pushes to `main` trigger automatic redeploy. For the custom domain, add `www.assuredlaw.com` under Settings > Custom Domains and follow Render's DNS instructions. Render provisions HTTPS automatically.

## Compliance Notes

Content in this repository is attorney advertising. Before publishing changes, verify:

1. **Experience attribution.** All references to the founders' 25 years must be attributed to property management, regulatory compliance, and the construction industry, never to the practice of law. The firm's attorneys have practiced for approximately one year.
2. **Statutory figures.** The Justice Court civil jurisdictional limit is $15,000 (NRS 4.370); small claims is $10,000 (NRS 73.010). These were verified in July 2026 and are subject to legislative amendment. Chapter 40 (constructional defect) and NRS 11.190 (limitations) citations should also be reconfirmed periodically.
3. **No superlatives or results claims.** Avoid "premier," "best," "we deliver results," and similar language the firm cannot substantiate.
4. **No fabricated testimonials.** Client statements require real, consented sources.
5. **No privilege claims on web submissions.** Submitting a form does not create attorney-client privilege or an attorney-client relationship. Disclaimers must say so.
6. **Fee representations** must match the firm's actual fee agreements, including the allocation of case costs.
