# barton-entertainment.github.io

The public website of Barton Entertainment, served by GitHub Pages (Jekyll) at
https://barton-entertainment.github.io.

| Path | What it is |
| --- | --- |
| `/` | Landing page (`index.html`) |
| `/snooze-tones/privacy/` | Snooze Tones privacy policy (`snooze-tones/privacy.md`). This is the URL the app's Settings and the Play listing link to |
| `/app-ads.txt` | AdMob's authorized-sellers file, added once the AdMob publisher ID exists. It must stay at the site root |

Each app gets its own folder, so a later app gets `/<app>/privacy/` without moving anything. Styles live
in `assets/site.css` and follow the Snooze Tones design system: Nunito (self-hosted, SIL Open Font
License), dark first, one warm lamp color.

## Snooze Tones privacy policy

The policy waits on the `privacy-policy` branch until the company details exist. Fill the
placeholders there, check them with the grep below, and merge it into `main` to publish.

```
Fill every [[PLACEHOLDER]] before publishing. They use double square brackets, not double braces,
because Jekyll would read {{...}} as Liquid and silently print nothing. Before merging, check that
`grep -n "\[\[" snooze-tones/privacy.md` finds nothing:
  [[COMPANY_NAME]]          legal name of the company that publishes the app
  [[CNPJ]]                  company CNPJ
  [[ADDRESS]]               company's registered address
  [[CONTACT_EMAIL]]         the privacy and support email (the same one on the Play listing)
  [[EFFECTIVE_DATE]]        the date this version takes effect
  [[ANALYTICS_RETENTION]]   the event data retention set in the Firebase/Google Analytics console (2 or 14 months)

Legal choices made in this text (checked 2026-11-24 against the LGPD and ANPD rules, not by a lawyer):
  - Encarregado (DPO): none named. A micro or small company (LC 123) is a small processing agent
    under Resolution CD/ANPD 2/2022, which by art. 11 doesn't have to name one but must offer a
    communication channel (the contact email). The exemption is lost only for "high-risk"
    processing, which art. 4 defines as at least one general criterion (large scale, or a
    significant effect on rights) plus one specific one. Revisit if the app reaches a very large
    user base.
  - Outside the EEA, UK and Switzerland, personalized ads, analytics and crash reports run on
    legitimate interest with an opt-out, matching the code (src/ports/adapters/umpConsent.ts in the app repo).
    Analytics and crash reports are a solid fit: few fields, no names, no cross-app tracking.
    Personalized ads are the weak spot: the ANPD's cookie guide (2022) treats consent as the more
    fitting basis for advertising profiling. The safer alternative is to ask Brazilian users for
    consent too, or serve them non-personalized ads only. That needs a code change, and Brazil is
    a low-CPM market outside the app's target list, so it costs little revenue.

Keep the policy in step with the app. If the app adds an SDK, a permission, an analytics event or
an account system, update this policy and the Play Data safety form together.
```
