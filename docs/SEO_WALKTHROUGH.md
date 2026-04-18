# SEO Walkthrough — ddats.nl

Status per commit `719a5d6` (18 april 2026): `<title>`, meta description, canonical, Open Graph, Twitter Card, JSON-LD structured data, `robots.txt`, and `sitemap.xml` are in place. Google does not automatically discover these changes — you have to tell Search Console the site exists and that the sitemap should be crawled.

Estimated time for steps 1–5: ~20 minutes. Indexing by Google takes days to weeks.

## 1. Google Search Console — verify property

1. Go to **https://search.google.com/search-console** and sign in with the Google account you want to own the SEO reporting.
2. Click **Add property** (top-left dropdown → "+ Add property").
3. Choose **URL prefix** (not Domain). Enter `https://ddats.nl/`.
   - *Why URL prefix, not Domain?* Domain verification requires DNS (TXT record at registrar). URL prefix allows the easier HTML-file or meta-tag methods. Trade-off: URL prefix only covers the exact protocol+host, so `http://` and `https://www.` would each need separate verification. For a single-page GitHub Pages site on one canonical domain, URL prefix is sufficient.
4. Google shows verification methods. Pick **HTML file upload**:
   - Download the file (looks like `google1234abcd.html`).
   - Add it to the repo root next to `index.html`:
     ```
     cd /path/to/ddats-calculator
     cp ~/Downloads/google1234abcd.html ./
     git add google1234abcd.html
     git commit -m "Add Google Search Console verification file"
     git push
     ```
   - Wait ~1 minute for GitHub Pages to redeploy.
   - Click **Verify** in Search Console.

## 2. Submit sitemap

1. In Search Console, left sidebar → **Sitemaps**.
2. Enter `sitemap.xml` in the field (just the filename, Google appends it to the verified URL).
3. Click **Submit**. Status should become "Success" within minutes.

## 3. Request indexing for the homepage

1. Top bar search field in Search Console → paste `https://ddats.nl/` → Enter.
2. Page shows "URL is on Google" or "URL is not on Google". Either way, click **Request indexing**.
3. Google queues a crawl. Takes hours to days.

## 4. Check it worked (within 1–2 weeks)

- **Coverage report** (left sidebar → *Indexing* → *Pages*): homepage should appear under "Indexed".
- **Performance report** (left sidebar → *Performance*): after ~3 days, impressions for queries like "D-DATS", "Parkinson screening tool", "device-aided therapy screening" should appear.
- Sanity check: search `site:ddats.nl` in Google. Should list the homepage.

## 5. Validate structured data (immediate)

1. https://search.google.com/test/rich-results → paste `https://ddats.nl/` → **Test URL**.
2. Should detect `MedicalWebPage` and `SoftwareApplication`. No errors expected; warnings about optional fields are fine.
3. https://developers.facebook.com/tools/debug/ → paste URL → see how the Open Graph tags render on LinkedIn/WhatsApp/Facebook shares.

## 6. Optional — Bing Webmaster Tools

Smaller share but worth the 5 minutes (covers Bing, DuckDuckGo, ChatGPT browsing, some enterprise intranets):

1. https://www.bing.com/webmasters
2. **Import from Google Search Console** (one-click). Re-uses the verification.
3. Sitemap is copied automatically.

## 7. Optional — Google Analytics

Not recommended: you already run Umami (privacy-first, cookie-free, GDPR-compliant). Adding GA4 would:
- Require a cookie consent banner (GDPR)
- Introduce a tracking script from Google
- Conflict with the "independent academic tool" positioning

Stick with Umami.

## What Google will key on (why the metadata changes matter)

| Element | Effect |
|---|---|
| `<title>` "D-DATS \| Validated Parkinson Screening Tool for Device-Aided Therapy" | Keyword density for "Parkinson" + "screening" + "device-aided therapy" + "D-DATS". Appears as the blue link in SERPs. |
| `<meta description>` | Appears as the snippet under the link in SERPs. Short, specific, with the metrics that matter to clinicians. |
| `<link rel="canonical">` | Prevents duplicate-content penalties if `ddats.nl`, `d-dats.com`, and other redirecting domains get indexed separately. |
| Open Graph / Twitter | Rich link previews when the URL is shared in WhatsApp, LinkedIn, Teams, Slack, X. Doctors share tools this way — a plain-text link vs. a preview card is a huge click-through difference. |
| JSON-LD `MedicalWebPage` + `SoftwareApplication` | Tells Google *what kind* of page this is. Can trigger rich results (sidebar info, medical audience tagging). Also interpretable by AI search (Perplexity, ChatGPT browse). |

## What this setup does NOT fix

- **No inbound links.** SEO for a single-page site depends heavily on other pages linking to you. Ways to build backlinks:
  - Link to `ddats.nl` from the Parkinsonism & Related Disorders publication (if journal permits).
  - Link from UMCG department page, RUG promotietraject page.
  - Add URL to conference abstracts, talk slides.
  - List the tool in Parkinson's disease clinical resource registries (MDS website, Parkinson Vereniging).
- **Competing search intent.** Doctors searching "Parkinson screening" may find general symptom screeners (for diagnosis, not DAT referral). Your differentiator is "device-aided therapy" — make sure that phrase is in the `<title>` (it now is).
- **Country targeting.** Google Search Console → Settings → International Targeting → set to Netherlands if you want NL-biased ranking. Skip if you want broader EU/global reach (the tool is validated in NL but usable elsewhere).

## Re-run after content changes

Every time `index.html` changes substantively (new features, new metrics, banner added/removed):
1. Update `sitemap.xml` `<lastmod>` date.
2. In Search Console → Sitemaps → click the sitemap → **Re-submit** (forces a re-crawl queue).
3. No need to re-verify the property; that stays valid.
