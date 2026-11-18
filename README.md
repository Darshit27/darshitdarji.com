# darshitdarji.com

Personal website of Darshit Darji, hosted on **GitHub Pages** with a custom domain bought from **Hostinger**.

> **For an AI assistant (Claude or any other) editing this repo:** read this whole file first.
> The rules under **"Never break these"** protect the domain, HTTPS and Google search visibility.
> Every new version of the site must keep them. When you hand back a new version, give the
> **complete site** (all files below), not only the changed file.

---

## Folder structure

```
/                                   ← repo root = website root
├── index.html                      ← portfolio / profile page  (https://darshitdarji.com/)
├── 404.html                        ← "page not found" page
├── favicon.ico                     ← site icon, 16/32/48 px (Google looks for it at the root)
├── robots.txt                      ← tells search engines they may crawl; points to the sitemap
├── sitemap.xml                     ← list of public pages for Google
├── CNAME                           ← contains exactly: darshitdarji.com
├── .nojekyll                       ← empty file; stops GitHub from processing the site with Jekyll
├── README.md                       ← this file
├── assets/
│   ├── darshit.jpg                 ← profile photo, 900 × 900 (also the image shown in Google / link previews)
│   ├── favicon-48.png              ← round face crop of darshit.jpg
│   ├── favicon-96.png
│   ├── favicon-192.png
│   ├── favicon.png                 ← 256 px copy (spare)
│   └── apple-touch-icon.png        ← 180 px, square (iPhone home screen)
└── guides/
    ├── index.html                  ← "Lab guides" list page        (https://darshitdarji.com/guides/)
    └── ac-current-source-v1/
        └── index.html              ← AC Current Source V1 operating guide
                                      (https://darshitdarji.com/guides/ac-current-source-v1/)
```

Every page is a single self-contained HTML file (CSS and JavaScript inside the file). There is no
build step, no framework and no package manager. Fonts come from Google Fonts.

---

## Never break these

1. **Keep the `CNAME` file**, unchanged, containing only `darshitdarji.com`.
   If it is missing, GitHub detaches the custom domain and the site goes offline at darshitdarji.com.
2. **Keep the `.nojekyll` file** (empty).
3. **Keep the page addresses (URLs) the same:**
   `/`, `/guides/`, `/guides/ac-current-source-v1/`.
   - Do not rename folders or move pages. Google and the QR sticker on the instrument point to these.
   - The QR sticker on the AC Current Source V1 hardware links to `https://darshitdarji.com/guides/ac-current-source-v1/`
     and **cannot be changed after printing**. This URL must always work.
   - A page that must move needs a page at the old address that redirects to the new one.
4. **Keep `robots.txt`** allowing everything and pointing to the sitemap:
   ```
   User-agent: *
   Allow: /

   Sitemap: https://darshitdarji.com/sitemap.xml
   ```
5. **Keep `sitemap.xml`** listing every public page with full `https://` addresses.
   When a page changes, update its `<lastmod>` date (YYYY-MM-DD). When a page is added, add it here.
6. **Never add `noindex`** (in a `<meta name="robots">` tag or anywhere else). The home page uses
   `<meta name="robots" content="index, follow, max-image-preview:large">`; keep it.
7. **All links and SEO tags use `https://darshitdarji.com/...`**, never `http://` and never `www.`.
   This includes `<link rel="canonical">`, `og:url`, `og:image` and the JSON-LD blocks.
8. **Keep the `<head>` SEO block of `index.html`** (edit the text if needed, but keep the tags):
   - `<title>`, `<meta name="description">`
   - `<link rel="canonical" href="https://darshitdarji.com/">`
   - Open Graph and Twitter tags (`og:title`, `og:description`, `og:image` + width/height, `og:url`, `twitter:*`)
   - Three JSON-LD scripts: `Person`, `WebSite` (site name) and `ProfilePage` (`primaryImageOfPage` = darshit.jpg)
9. **Keep the icons on every page** (index, 404, guides, guide):
   ```html
   <link rel="icon" href="/favicon.ico" sizes="48x48">
   <link rel="icon" type="image/png" sizes="192x192" href="/assets/favicon-192.png">
   <link rel="icon" type="image/png" sizes="96x96" href="/assets/favicon-96.png">
   <link rel="apple-touch-icon" href="/assets/apple-touch-icon.png">
   ```
   Google only shows square icons whose size is a **multiple of 48 px**. Keep `assets/darshit.jpg`
   at 900 × 900 or larger, and keep the profile `<img>` on the page pointing to it.
10. **Do not commit private files** (DNS screenshots, passwords, verification files you were not asked to add).

---

## How to update the site

1. Unzip the new site on your computer.
2. In the GitHub repo (`Darshit27/<repo>`, branch `main`, folder `/ (root)`), replace all files with the
   new ones. **Keep the hidden `.git` folder** if you work with a local clone.
   On github.com: *Add file → Upload files*, drag in everything, commit.
3. Wait 1–2 minutes, then open https://darshitdarji.com and hard-refresh (Ctrl/Cmd + Shift + R).
4. After a big change: Google Search Console → **URL inspection** → `https://darshitdarji.com/` → **Request indexing**.

Check before uploading: `CNAME`, `.nojekyll`, `robots.txt`, `sitemap.xml`, `favicon.ico` and `assets/` are present.

---

## Hosting setup (already done; do not change unless moving host)

**GitHub → repo → Settings → Pages**
- Source: *Deploy from a branch* → `main` → `/ (root)`
- Custom domain: `darshitdarji.com`
- **Enforce HTTPS: ticked**

**Hostinger DNS (domain darshitdarji.com)**

| Type  | Name                               | Value                         |
|-------|------------------------------------|-------------------------------|
| A     | @                                  | 185.199.108.153               |
| A     | @                                  | 185.199.109.153               |
| A     | @                                  | 185.199.110.153               |
| A     | @                                  | 185.199.111.153               |
| CNAME | www                                | darshit27.github.io           |
| TXT   | _github-pages-challenge-darshit27  | (GitHub domain verification)  |
| TXT   | @                                  | google-site-verification=…    |

Do not delete the verification TXT records. The other records in Hostinger (mail: SPF, DKIM, DMARC)
are for email and unrelated to the website.

If HTTPS ever breaks (certificate stuck): in Pages settings click **Remove** on the custom domain,
wait a minute, enter `darshitdarji.com` again, **Save**, wait up to 24 h, then tick **Enforce HTTPS** again.

**Google Search Console** (property `https://darshitdarji.com` or domain property `darshitdarji.com`)
- Sitemap submitted: `https://darshitdarji.com/sitemap.xml` (or just `sitemap.xml` if the prefix is shown).
- After major updates: URL inspection → Request indexing.

---

## Design conventions

Keep these so new pages match the existing ones.

**General**
- Clean, light UI. No heavy borders, no "show-off" tone. Text is factual and short.
- Mobile first: most visitors, and every guide user, are on a phone. No sideways scrolling at 375 px width.
- Fonts: Inter-style sans for text, a monospace for labels, **Georgia** (serif) only for greetings and
  large headings where already used. Do not add more serif text.
- Light mode is the default on the portfolio and the Lab guides page; a moon button switches to dark
  (saved in `localStorage` key `dd-theme`).
- Footer of the portfolio: `© <year> Darshit Darji. All rights reserved.`
- One heading per section (no small label repeating the large heading).
- Do not add content about the owner that is not already on the site or provided by him directly.

**Portfolio (`index.html`)**
- Sections: About, Experience, Projects (with filters), Patents, Awards, Skills (Hardware, Software),
  Education, Contact. No GitHub link in Contact.
- Project cards can have a "Watch video" button (YouTube) — currently iDropX21, OxidaneX21, Quadcopter.

**Lab guides page (`guides/index.html`)**
- One card per guide with a small icon on the left (AC Current Source V1 = sine wave).
- Subtle `darshitdarji.com` link at the very bottom of the page, linking to `/`.

**AC Current Source V1 guide (`guides/ac-current-source-v1/index.html`)**
- **Dark mode is the default** inside the guide; the toggle switches to light.
- Greeting page: random greeting (Georgia). Options: Beginner / Experienced, then Shutdown guide and
  Calculator side by side. Top-left button: back arrow to `/guides/` on the greeting page, home icon
  (back to the greeting page) inside a session.
- Session end shows a random closing line in the same Georgia style as the greeting. No other fun
  lines inside steps.
- Most frequent choice = solid orange button; less common choice = outline button.
- Running page has a **Shutdown guide** button in the bottom bar (centred; moves above Back/Home on phones).
- The guide is also published as a Claude artifact. The site file is that artifact's HTML wrapped
  in a normal `<!doctype html><html><head>…</head><body>…</body></html>` page, with the SEO and icon tags
  added at the top of `<head>`.

---

## AC Current Source V1: facts the guide depends on

Change these only if the hardware changes, and then update every place they appear (steps, Help,
calculator, Experienced "Operating limits" table).

| Item | Value |
|---|---|
| DC supply | ITECH IT-M3904C-80-80, **40 V**, current limit **3.5 A** (OVP/OCP already set; users don't change them) |
| Signal generator | Tektronix AFG1062, **Setup 0** = sine, 10 kHz, **700 mVpp**, 20 mV offset, High Z |
| Oscilloscope | Keysight DSOX3054T, CH1, 10:1 probe |
| Probe position | hook tip on the test pin (male header) beside the OUT XT90; ground clip on the OUT XT90 black wire |
| Signal input | twisted red/black pair from SIG IN (JST), bare ends clipped to generator Out1 with alligator clips |
| DC input | XT90 (keyed, polarity cannot be reversed) |
| Load | 4 × 0.2 Ω 200 W resistors, series-parallel → 0.2 Ω, 800 W, fan-cooled |
| Loop inductance | 0.55 µH default (measured 0.488–0.528 µH) |
| Current formula | I pk = (ΔY ÷ 2) ÷ \|Z\|, \|Z\| = √(0.2² + (2π·f·L)²); ΔY read with scope cursors on a frozen trace |
| Limits | **15 A peak**, **6.6 Vpp** generator, 10–50 kHz (tested at 10 kHz only), hotspot **85 °C** |
| Idle / at 700 mVpp | ≈ 0.26 A, 0.010 kW / ≈ 0.52 A, 0.021 kW |
| Offset check | at 10 kHz, 700 mVpp only: (Y1 + Y2) ÷ 2 within ±5 mV, using cursors (not auto Pk-Pk/Max/Min) |
| Amplitude steps | 0.1 Vpp: cursor on the "7" of 700 mVpp, turn knob clockwise |
| Start-up order | wiring inspection (all off) → supply on → generator on → scope on → supply output on → confirm 10 kHz / 700 mVpp → generator output on → Auto Scale → horizontal scale → Run/Stop → offset check |
| Shutdown order | supply output off → generator output off → generator back to 700 mVpp → power everything off; don't touch PCBs/load for 5 min (hot) |
| Safety | Smoke, burning smell, spark or unusual sound → press E-STOP. Never touch any PCB during operation. ESD strap at all times. E-STOP: press = OFF, release (rotate clockwise) = ON |

The calculator strikes through any value that is not usable (above 15 A peak or above 6.6 Vpp).
