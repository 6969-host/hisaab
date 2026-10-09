# Hisaab: deployment guide

A static website. No server, database or build step is needed. Upload the folder as it is.

## What's inside

| URL | File |
|---|---|
| `/` | `index.html` (home page with all calculators) |
| `/in-hand-salary-calculator/` | CTC to in-hand salary |
| `/income-tax-calculator/` | Income tax, new vs old regime |
| `/sip-calculator/` | SIP with step-up |
| `/lumpsum-calculator/` | Lumpsum |
| `/swp-calculator/` | SWP |
| `/goal-sip-calculator/` | Goal planner |
| `/emi-calculator/` | Loan EMI |
| `/fd-calculator/` | Fixed deposit |
| `/ppf-calculator/` | PPF |
| `/about/`, `/privacy-policy/`, `/contact/`, `/disclaimer/` | Pages AdSense requires |
| `assets/style.css`, `assets/app.js` | Shared design and calculator logic |
| `sitemap.xml`, `robots.txt`, `ads.txt`, `404.html` | SEO and AdSense files |

## Step 1: Replace the placeholders

Use your editor's "Find and replace in files" (VS Code: Ctrl+Shift+H) across the whole folder.

1. `https://www.yourdomain.in` → your real domain, for example `https://www.hisaab.in`
2. `hello@yourdomain.in` → your real email
3. `G-XXXXXXXXXX` → your Google Analytics 4 Measurement ID. Then remove the `<!--` and `-->` lines around the Analytics block in every HTML file.
4. After AdSense approval, do the same for the AdSense block (`ca-pub-...`) and replace the contents of `ads.txt` with the line AdSense gives you.

## Step 2: Deploy (pick one, all free)

### Option A: Cloudflare Pages (recommended)
Fast in India and includes free analytics.
1. Sign up at dash.cloudflare.com and go to Workers & Pages, then Create, then Pages, then Upload assets.
2. Name the project and drag in the `hisaab-site` folder (or the zip).
3. You get a `*.pages.dev` link right away.
4. To use your own domain, open the project, go to Custom domains, and follow the DNS steps.

### Option B: Netlify Drop
1. Go to app.netlify.com/drop.
2. Drag the `hisaab-site` folder onto the page. It goes live in seconds.
3. Sign in to keep it, then add your domain under Domain management.

### Option C: GitHub Pages
1. Create a public repository and upload the contents of this folder to the root.
2. Go to Settings, then Pages, then deploy from the `main` branch, `/ (root)`.

## Step 3: After going live

1. **Google Search Console**: add your domain, then submit `https://your-domain/sitemap.xml` under Sitemaps.
2. **Google Analytics**: open your site and check Reports, then Realtime, to confirm tracking works.
3. **AdSense**: apply once you have more content and some traffic. Ad spaces are marked with dashed boxes ("Ad space"). Replace those boxes with AdSense ad units, or switch on Auto ads.

## Updating content

- Explainer text for each calculator is plain HTML inside that calculator's `index.html`, in the `<div class="explain">` section. Edit it directly.
- Calculator logic and the tax rules are in `assets/app.js`. Tax slabs are near the top (`NEW_SLABS`, `oldSlabs`).
- When you add a page, also add its URL to `sitemap.xml`.
