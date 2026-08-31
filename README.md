# Old West El Paso Construction — spec demo

Concept one-page lead-gen site to pitch **Old West El Paso Construction** (El Paso, TX).
Prospect #1 (Priority A, score 9) on `El-Paso-Website-Prospects.xlsx`. Adapted from the
`jada-landscaping-demo` template.

```
old-west-construction/
├── index.html    markup + inline SVG icons + keyless Google Maps embed
├── styles.css    Old West rust palette, before/after slider, gallery, service-area layout
├── script.js     EN/ES toggle, before/after slider, financing calc, form validation, carousel
└── assets/       web-optimized photos + the real logo + originals/
```

**Preview:** `cd old-west-construction && python3 -m http.server 8908` then open
<http://localhost:8908>.

---

## Why the page is built this way

Old West already has a website (`oldwestepconstruction.com`), but it is a dated IONOS
drag-and-drop template: one stock hero photo of two models in hard hats reused site-wide,
a dead "Google+" link in the footer, a personal Gmail as the only contact, and no real
lead form. Meanwhile they run Meta ads for outdoor kitchens, turf and roofing (jobs in the
$5k to $30k range) and every ad click dead-ends in Facebook Messenger.

They are clearly successful: **4.9 stars across 110 Google reviews**, **BBB Accredited A+**,
**12 years in business**. The web presence just does not match the reputation, and the paid
traffic has nowhere structured to land.

So this build leans on:

- **A quote form as the hero**, tailored to a general contractor: what to build, where on
  the property, rough budget. Javier walks into every call already knowing the job.
- **Before/after slider** of a real West Side backyard (dirt to turf + stamped concrete).
- **Photo carousel** of 7 real jobs: pergola, rock wall, turf, base prep, metal privacy
  screen, stucco, turf install.
- **Financing estimator** — outdoor kitchens and roofs get financed.
- **Service Area section rebuilt** around persuasion, not a bare city list: a real embedded
  Google map of the Remcon Circle shop, three reasons to book (free on-site estimate, one
  crew start to finish, 12 years and 4.9 stars locally), then a compact "areas we cover"
  checklist and a CTA.
- **EN/ES toggle** — standard for an El Paso trade.
- **The real logo** from their current site, used in the header and footer.

---

## Verified vs. placeholder

**Real — safe to keep:**

| Fact | Source |
|---|---|
| Old West El Paso Construction, 7362 Remcon Cir, El Paso, TX 79912 | BBB, their site |
| Owner: **Javier Calzada** (kept off the page; use for outreach) | BBB |
| Business started **2/19/2014** → 12 years | BBB |
| **BBB Accredited since 9/10/2021**, A+ rating | BBB |
| **4.9 stars, 110 Google reviews** | Google (also Angi 4.8, TrustAnalytica 4.9/58) |
| (915) 217-8471 — call or text | their site, BBB |
| jcalz337@gmail.com | their site (not shown on the demo; use a real business address before launch) |
| Facebook `/OldWestEPConstruction` | verified live |
| Services in the photos: outdoor kitchens, stamped concrete, artificial turf, pergolas, stone & retaining walls, roofing, stucco, metal privacy screens, kitchen & bath remodels | the 9 client photos + their gallery |

**Placeholder — fix before this goes live:**

- **Financing APR/terms.** `script.js` `APR = 0.0999`, terms 3/5/7 yr. Invented. The page
  carries a "not an offer of credit" disclaimer. Get the real finance-partner numbers, or
  drop the section if they do not offer financing.
- **Hours.** Footer says "Mon to Sat" with a visible `(confirm hours)` flag, and the
  Service Area panel says "Mon to Sat, free estimates." Their current site contradicts
  itself (Mon–Fri 9–5 in one place, "available seven days a week" in another). Confirm,
  then delete the `.demo-inline` span.
- **"One crew, no subs to chase"** in the Service Area panel — reasonable for an owner-run
  GC but not verified. Confirm with Javier before it goes live.
- **Contact email.** The demo deliberately does not show `jcalz337@gmail.com`. Set up a
  business address (or a form backend) before launch.
- **Form has no backend.** Submitting shows a success state and says "demo only" on screen.
  Wire to Formspree / email before launch.
- **Before/after photos** are the same backyard but shot from slightly different angles and
  cropped to 4:3 from a square/4:3 pair, so the stone wall does not line up perfectly across
  the wipe. Re-shoot a matched pair for a clean match.
- **Logo** is their real logo lifted from `oldwestepconstruction.com` (`assets/logo.jpg`,
  re-cropped and compressed). If Javier has a clean PNG/SVG, swap it in — the JPEG has mild
  artifacts on the black outlines at small sizes.
- Footer keeps "Concept site prepared for Old West El Paso Construction. Not an official
  page." until he buys.
- `noindex` is set so this does not compete with their real domain.

---

## Photos

`assets/originals/` holds the 9 client originals plus `logo-full.jpg`. The page uses the
optimized copies:

| file | used as | from |
|---|---|---|
| `hero.jpg` | hero background | `after.jpg` (finished turf + stamped concrete backyard) |
| `before.jpg` / `after.jpg` | before/after slider | `before.jpg` (cropped to 4:3) / `after.jpg` |
| `g1-pergola.jpg` | carousel | `pergola.jpg` |
| `g2-wall.jpg` | carousel | `brick-wall.jpg` (El Paso rock wall + raised planter) |
| `g3-turf.jpg` | carousel | `turf.jpg` |
| `g4-base.jpg` | carousel | `landscaping2.jpg` (plate compactor / base prep) |
| `g5-screen.jpg` | carousel | `worker.jpg` (metal privacy screen) |
| `g6-stucco.jpg` | carousel | `workers.jpg` (stucco / parapet) |
| `g7-turf-install.jpg` | carousel | `landscaping.jpg` (turf underlayment) |
| `logo.jpg` | header + footer | their current site's header logo |

Re-optimize a swap with:
`sips -Z 1450 -s format jpeg -s formatOptions 45 new.jpg --out g5-screen.jpg`

---

## Palette (sampled from their site)

Their live site header is `#792007` (a dark rust). The logo lettering is an orange-to-gold
gradient. Set as CSS custom properties at the top of `styles.css`:

```css
--rust:#792007;      /* exact brand color — buttons, links, header text */
--rust-deep:#4E1604;  /* darkest — headings, dark sections, footer */
--ember:#C6551C;      /* logo orange — secondary accent */
--gold:#E4A32B;       /* logo gold — eyebrows / highlights on dark */
--sand:#F5EEE3;       /* warm cream — tinted section backgrounds */
--sage:#5F7355;       /* one desert green — checkmarks / success */
```

Headings are **Zilla Slab**; body is **Manrope**.

---

## Service Area map

The map is a keyless Google Maps embed:
`https://www.google.com/maps?q=7362+Remcon+Cir,+El+Paso,+TX+79912&z=11&output=embed`
No API key, no billing. It may not render inside some sandboxed preview tools but works on
GitHub Pages and any normal host.

---

## Repo & hosting

Same setup as the other demos: private repo, hosted free on GitHub Pages (needs the repo
public). To publish:

```
cd old-west-construction
printf '.DS_Store\n*.log\n' > .gitignore
git init -q && git add -A
git -c user.name="Kassandra-Rodriguez" -c user.email="kassandra.rodriguez2014@gmail.com" \
  commit -q -m "Old West El Paso Construction concept site"
git branch -M main
gh repo create old-west-construction-demo --private --source=. --remote=origin --push
```

Then Kassandra runs (the assistant is blocked from these):

```
gh repo edit Kassandra-Rodriguez/old-west-construction-demo --visibility public --accept-visibility-change-consequences
gh api --method POST /repos/Kassandra-Rodriguez/old-west-construction-demo/pages -f "source[branch]=main" -f "source[path]=/"
```

Live ~1 min later at `https://kassandra-rodriguez.github.io/old-west-construction-demo/`.

---

## Talk track

> "Hi Javier, I'm Kassandra, a web designer here in El Paso. Your reviews are excellent —
> 4.9 stars, 110 of them, A+ with the BBB, 12 years in. The thing is your ads for outdoor
> kitchens and roofing all send people into Facebook Messenger, and the website you have
> doesn't really show the quality of your work. I built you a sample: your real logo, a
> drag-to-compare before and after of one of your West Side backyards, a gallery of your
> jobs, a map of the shop, and a quote form that asks what they want built and their budget
> so you walk into every call already knowing the job. English and Spanish. Want the link?"

Lead with the compliment and the gap: "your work and your reviews are already there, the
ad clicks just have nowhere to land." Not a criticism of the current site.
