# Assured Law Website

Marketing website for Assured Law, a Nevada firm handling nuisance damage claims, premises liability litigation, Justice Court claims, personal injury, and construction defect.

Host: Render (static site, auto-deploys on push to `main`)
Status: **not yet connected to a custom domain.** This site is served only at its
Render-assigned URL. `www.assuredlaw.com` currently serves a separate, unrelated
Wix site; this repository is its intended replacement. Pushing to `main` therefore
does not change anything at www.assuredlaw.com. See Deployment below for the
cutover steps.

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

| Route        | Content                                                    |
|--------------|------------------------------------------------------------|
| `home`       | Dictionary hero, stats, practice areas, CTA                |
| `nuisance`   | Public vs. private nuisance, five elements, remedies       |
| `premises`   | Duty of care tiers, incident types, five elements, damages |
| `justice`    | Small claims vs. Justice Court, advantages, four elements  |
| `injury`     | Negligence framework, claim types, damages                 |
| `defect`     | NRS Chapter 40 process, defect categories, HOA claims      |
| `review`     | On-page case review form (per-case-type dynamic fields)    |
| `privacy`    | Privacy Policy                                             |
| `terms`      | Terms of Use                                               |
| `disclaimer` | Disclaimer                                                 |
| `about`      | Firm story, values                                         |

Our Attorneys and Results pages existed briefly but were removed in July 2026:
Results pending real, substantiated representative matters, and Our Attorneys
because the firm currently has a single attorney. Recover either from git
history if needed.

## Third-Party Integrations

1. **Google Fonts.** Cormorant Garamond and Inter, loaded from fonts.googleapis.com.
2. **Web3Forms.** The on-page case review form POSTs to `https://api.web3forms.com/submit`. On failure it surfaces an error and directs the visitor to call the firm instead.

The Clio Grow scheduler and intake embeds were removed in July 2026: the firm
schedules consultations only after reviewing a submitted intake, so the on-page
form is the single intake path. Recover the embeds from git history if needed.

## Open Items

1. **Single-URL architecture.** All pages share one URL, so search engines index one page. Acceptable at launch; revisit before investing in search traffic.
2. **Web3Forms access key is public.** This is inherent to a client-side form — the key is visible to any browser, so it is not a leak. It does mean anyone can POST to the endpoint. Enable domain restriction and spam filtering in the Web3Forms dashboard to limit abuse.

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
