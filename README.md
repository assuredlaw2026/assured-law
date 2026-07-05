# Assured Law Website

Marketing website for Assured Law, a Nevada firm handling nuisance damage claims, premises liability litigation, and Justice Court claims.

Live domain: www.assuredlaw.com

## Structure

The site is a single self-contained HTML file with client-side JavaScript routing. There is no build step, no framework, and no server-side dependency.

```
index.html                    Entire site: all pages, styles, and scripts
assets/assured-law-logo.svg   Original logo asset (the logo is also embedded
                              inline in index.html; this file is kept as the
                              canonical source)
```

## Pages

Routing is handled in JavaScript by the `navigate()` function. Page IDs:

| Route      | Content                                              |
|------------|------------------------------------------------------|
| `home`     | Hero, stats, practice areas, testimonials, CTA       |
| `nuisance` | Public vs. private nuisance, elements, remedies      |
| `premises` | Duty of care tiers, incident types, damages          |
| `justice`  | Small claims vs. Justice Court, advantages, approach |
| `review`   | Embedded Clio Grow scheduler and intake form         |

## Third-Party Integrations

1. **Google Fonts.** Cormorant Garamond and Inter, loaded from fonts.googleapis.com.
2. **Clio Grow scheduler.** Embedded via iframe on the Case Consultation page, pointing to `https://mygoodlawyers.cliogrow.com/book`. A fallback link is provided beneath the frame in case embedding is blocked by response headers.

## Intake Form

The case review form is currently front-end only. The `submitForm()` function validates input and displays a success message but does not transmit data. Before production use, wire the submission to a backend endpoint or a form service, and confirm the handling of uploaded files complies with the firm's confidentiality obligations.

## Deployment

Any static host will work: GitHub Pages, Netlify, Vercel, or a standard web server. For GitHub Pages:

1. Push this repository to GitHub.
2. In repository Settings, enable Pages from the main branch, root directory.
3. Point the `assuredlaw.com` DNS at GitHub Pages per GitHub's custom domain documentation, and add a `CNAME` file containing `www.assuredlaw.com`.

## Compliance Notes

Content in this repository is attorney advertising. Before publishing changes, verify:

1. All references to the founders' 50+ years of experience are attributed to property management and regulatory compliance, not to the practice of law.
2. Statutory citations (NRS 4.370, NRS 73.010) remain current.
3. Fee representations match the firm's actual fee agreements.
