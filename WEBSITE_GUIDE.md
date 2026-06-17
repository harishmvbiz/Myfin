# Myfin Group — Website Guide & Context

This document is your complete reference for the new Myfin Group website: what's in it, the few things only you can fill in, how to put it live for free, and how to look after it afterwards. Keep it somewhere safe — you can hand it to anyone who helps you in future and they'll understand the whole project in ten minutes.

---

## 1. What this is

A brand-new, hand-built website for **Myfin Group Pty Ltd** — a static site (plain HTML + one CSS file + your logo images). There is no WordPress, no database, no monthly platform fee. That makes it fast, secure, cheap to host, and easy to move anywhere.

**Design direction:** corporate and structured — sharp, confident and business-like, in charcoal and near-white, with your green logo dot used only as a small accent. Your real **myfin wordmark logo** is used throughout (header, footer, social preview). There is no invented "box" mark anywhere.

**Fonts:** Spectral (headlines), IBM Plex Sans (body) and IBM Plex Mono (labels and figures), all loaded free from Google Fonts.

### Pages (18 total)

| Page | File |
|---|---|
| Home | `index.html` |
| Services hub | `services.html` |
| Accounting | `accounting.html` |
| Taxation | `tax.html` |
| Book-keeping | `bookkeeping.html` |
| Finance & Mortgage | `finance.html` |
| Specialisations | `specialisations.html` |
| About / Who We Are | `about.html` |
| Why Myfin | `why-choose-us.html` |
| Our Team | `team.html` |
| Testimonials | `testimonials.html` |
| FAQs | `faq.html` |
| Resources | `resources.html` |
| Contact | `contact.html` |
| Privacy | `privacy.html` |
| Disclaimer | `disclaimer.html` |
| Terms | `terms.html` |
| Not-found page | `404.html` |

### Supporting files

- `theme.css` — the single stylesheet that controls the whole look.
- `logo-myfin.png` — your wordmark in charcoal (used on light backgrounds).
- `logo-myfin-light.png` — your wordmark in white (used on the dark footer and social image).
- `og-default.png` — the preview image shown when the site is shared on social media / messaging.
- `sitemap.xml`, `robots.txt` — help Google find and index every page.
- `_headers`, `netlify.toml` — security and caching settings (used automatically by the host).
- `CNAME` — tells the host your domain is `www.myfin.net.au`.

### Built-in features

- Mobile-friendly, with a slide-in menu on phones.
- **Dark mode** toggle (moon icon) and an **accessibility panel** (person icon: larger text, grayscale, underline links, reduce motion). Choices are remembered on the visitor's device.
- **Three floating buttons** on every page — **WhatsApp**, **Email**, and the **Fino** assistant. WhatsApp and Email each open a short guided flow (service → topic → type → your details) that drafts a clear message and opens WhatsApp or your email app. **Fino** is a conversational assistant that collects your enquiry and emails it to you via Web3Forms. The Contact page repeats these as three tappable cards.
- A **contact form** that emails enquiries to you (needs a free key — see §3).
- SEO essentials on every page: unique titles and descriptions, social-share tags, and structured data (so Google can show your business, services, FAQs and reviews richly).

---

## 2. The short list of things only YOU can confirm

Everything below is wired and working; these are the human details to verify before go-live. None require coding — most are a quick find-and-replace.

1. **WhatsApp number** — currently a placeholder (`61732777700`, your Salisbury landline). A landline **cannot** run WhatsApp. Give a mobile number that has WhatsApp installed and I (or you) swap one line. See §3.
2. **Contact-form key** — add a free Web3Forms key so enquiries reach your inbox. See §3.
3. **Office details** — confirm the three addresses and phone numbers are current:
   - Salisbury — 5/668 Toohey Rd, QLD 4107 — (07) 3277 7700
   - Lutwyche — 623B Lutwyche Rd, QLD 4030 — (07) 3357 7777
   - Heathwood — 29 Gardenia Cct, QLD 4110 — (07) 3372 4903
4. **Testimonials** — the quotes use real client names from your old site. If you'd prefer initials or written permission, tell me and I'll adjust.
5. **Fees & figures** — book-keeping rates ($35–$49/hr), "15+ years", "free first consult", and ATO/finance claims all came from your existing material. Confirm they're still accurate.
6. **ABN / Credit licence** — ABN 91 164 033 247; Credit Rep 444393 under ACL 389328. Confirm these are correct.

---

## 3. Two quick connections (WhatsApp + contact form)

### A) WhatsApp button

Open `parts.py`-built pages aren't edited directly for this — the number lives in one place. If you're editing the final HTML files, search every file for `61732777700` and replace it with your mobile in international format (no `+`, no spaces). Example: mobile `0412 345 678` becomes `61412345678`. There are two spots per page (the floating button link and the script). Easiest path: tell me the number and I'll rebuild and re-zip.

### B) Contact form (Web3Forms — free)

The form is ready; it just needs a key so submissions email you.

1. Go to **web3forms.com**.
2. Enter your email (`info@myfin.net.au`) and they email you an **Access Key** (free, unlimited).
3. Search **all files** for `YOUR_WEB3FORMS_ACCESS_KEY` and replace each with your key. It appears in `contact.html` (the enquiry form) and in the shared script that powers **Fino** (the chat assistant), so both send to your inbox.
4. Submit a test enquiry; it should arrive in your inbox.

Until the key is added, the form shows a friendly message and doesn't error — so the site is safe to launch first and connect the form right after.

---

## 4. Putting it live for free (Cloudflare Pages + GitHub)

You said your domain is at **Namecheap** and email is on **Microsoft 365**. The plan below keeps your email working untouched and hosts the site free on Cloudflare.

### Step 1 — Put the files on GitHub
1. Create a free account at **github.com**.
2. Click **New repository** → name it `myfin-website` → **Create**.
3. On the repo page, **Add file → Upload files**, drag in **all** the files from this package (the HTML files, `theme.css`, the three PNGs, and the config files), then **Commit**.

### Step 2 — Connect Cloudflare Pages
1. Create a free account at **cloudflare.com** → **Workers & Pages** → **Create application → Pages → Connect to Git**.
2. Authorise GitHub and pick `myfin-website`.
3. Build settings: leave the **build command empty** and **output directory** as `/` (this is a plain static site). **Save and Deploy**.
4. In a minute you'll get a live preview URL like `myfin-website.pages.dev`. Check it works.

### Step 3 — Point your domain at Cloudflare (the careful part — email stays safe)
Because your email is on Microsoft 365, take care not to disturb the mail DNS records.

1. In Cloudflare, **Add a site** → enter `myfin.net.au` → choose the **Free** plan.
2. Cloudflare scans your current DNS. **Before continuing, confirm these Microsoft 365 records were imported** (they're what keep email working):
   - An **MX** record pointing to `myfin-net-au.mail.protection.outlook.com` (or similar).
   - A **TXT (SPF)** record containing `include:spf.protection.outlook.com`.
   - **CNAME** records for `autodiscover` and the two `selector1`/`selector2` DKIM records.
   - Any **TXT** record for DMARC if you have one.
   If anything is missing, add it exactly as it appears in your Microsoft 365 admin centre (Microsoft 365 admin → Settings → Domains → myfin.net.au → DNS records).
   **Set every one of these mail records to "DNS only" (grey cloud), not proxied.**
3. Cloudflare gives you **two nameservers** (like `xxx.ns.cloudflare.com`). In **Namecheap → Domain List → Manage → Nameservers**, choose **Custom DNS** and paste both. Save.
4. Nameserver changes take anywhere from a few minutes to 24 hours.

> ⚠️ **Do not enable Cloudflare "Email Routing"** on this domain — it can override the Microsoft 365 MX record and break your email. Leave email entirely to Microsoft 365.

### Step 4 — Attach the domain to the site
1. Back in **Workers & Pages → your project → Custom domains → Set up a custom domain**.
2. Add `www.myfin.net.au` (Cloudflare creates the record automatically).
3. Add `myfin.net.au` and set up a redirect so the bare domain forwards to `www` (Cloudflare offers this, or use a Redirect Rule).
4. HTTPS (the padlock) is automatic and free.

Done — the site is live at `https://www.myfin.net.au`. From now on, any change you push to GitHub redeploys automatically in under a minute.

### Alternative: Netlify
If you'd rather use Netlify, drag the same folder onto **app.netlify.com** (Sites → Add new → Deploy manually), then **Domain settings → Add custom domain**. The included `netlify.toml` and `_headers` are picked up automatically. You'd still manage DNS/email as above.

---

## 5. After launch — tell Google you exist

1. **Google Search Console** (search.google.com/search-console) — add `https://www.myfin.net.au`, verify (easiest via a DNS TXT record in Cloudflare), then **Sitemaps → submit** `sitemap.xml`. This gets your pages indexed and shows search performance.
2. **Google Business Profile** (business.google.com) — claim/verify each office location. This is the single biggest driver of local "accountant near me" visibility, with your hours, phone, reviews and map pin.
3. **Bing Webmaster Tools** — optional, quick, and you can import directly from Search Console.

---

## 6. Go-live checklist

- [ ] Confirm the three offices, phones, ABN and credit licence numbers.
- [ ] Provide a **mobile** WhatsApp number (replace the landline placeholder).
- [ ] Add the **Web3Forms** key and send a test enquiry.
- [ ] Upload all files to GitHub.
- [ ] Deploy on Cloudflare Pages; check the `.pages.dev` preview.
- [ ] Move nameservers to Cloudflare **after** confirming Microsoft 365 mail records are present and "DNS only".
- [ ] Send yourself a test email to prove email still works.
- [ ] Attach `www.myfin.net.au`; confirm the padlock (HTTPS) shows.
- [ ] Submit the sitemap in Search Console; set up Google Business Profile.
- [ ] Click through every page on a phone and a laptop, test dark mode, the menu, both popups and the form.

---

## 7. Editing the site later

- **Text/wording:** open the relevant `.html` file in any plain-text editor (even Notepad), change the words between the tags, save, and re-upload to GitHub. Avoid touching anything inside `< >`.
- **Colours/fonts:** all live at the top of `theme.css` under `:root` (the `--ink`, `--paper`, `--green` values, etc.). Change once, applies everywhere.
- **Re-using the build scripts:** the Python files (`parts.py`, `helpers.py`, `build_*.py`) are how the HTML was generated. They aren't needed for hosting (don't upload them), but keep them — they make bulk changes (like a new phone number across every page) a one-line edit and rebuild. Ask me and I can regenerate the whole site in seconds.

---

## 8. Security & good habits

- Turn on **two-factor authentication** for GitHub, Cloudflare and Namecheap.
- Keep your Web3Forms key and logins out of public places.
- The site already sends sensible security headers (`_headers`) and forces HTTPS.
- Nothing on the site stores visitor data on a server — the form posts straight to Web3Forms, which emails you.

---

## 9. Reference — business facts baked into the site

- **Myfin Group Pty Ltd**, ABN 91 164 033 247.
- Credit Representative 444393 under Australian Credit Licence 389328.
- Director: **Suresh Swarna** — CPA, FIPA, Chartered Accountant, Registered Tax Agent, MFAA Credit Advisor.
- Email: info@myfin.net.au · Facebook: facebook.com/pages/Myfin-Group/436011683159539
- Tagline: *Trust · Value · Growth*.
- Offices: Salisbury · Lutwyche · Heathwood (all Brisbane, QLD).

---

*Built as a clean, dependency-free static site so you stay in control: cheap to host, easy to move, and simple to edit. If you'd like any wording, colours, or the WhatsApp number changed, just say the word and I'll regenerate and repackage.*
