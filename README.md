# Chic Beyond 40 — Website

A complete static website (pure HTML/CSS, **no build step**) for the Chic Beyond 40
Pinterest-driven fashion blog: tummy-friendly, anti-frumpy outfit ideas for women
over 40 / 50 / 60, targeting the US first and the UK second.

All internal links are **relative**, so the site works unchanged on the free
GitHub Pages address first and on `chicbeyond40.com` later.

## Site structure

```
index.html                                  Homepage (hero, categories, post grid, email signup)
about.html                                  About page
privacy-policy.html                         Privacy policy (AdSense-ready, covers cookies + Google ads)
contact.html                                Contact page (email + form placeholder)
affiliate-disclosure.html                   FTC/ASA affiliate disclosure
post-template.html                          COPY THIS to write a new post (do not publish as-is)
category-template.html                      COPY THIS to make a new category page
categories/fall-outfits.html                Example finished category page
posts/tummy-friendly-fall-outfits-over-40.html
posts/winter-capsule-wardrobe-over-50.html
posts/how-to-wear-cardigans-without-looking-frumpy.html
assets/style.css                            All styling (mobile-first, beige/white/black)
sitemap.xml                                 Update when you add a page
robots.txt
```

Images are CSS placeholder blocks labelled with the photo that belongs there.
Replace a block with a real image like:
`<img src="../assets/images/my-photo.jpg" alt="Woman over 40 in a rust wrap top and straight-leg jeans">`
and keep the `📌 PIN IMAGE` blocks at 1000 × 1500 px (2:3) — that is the size
Pinterest rewards.

---

## 1. Deploy to GitHub Pages (free)

1. Create a GitHub account if you don't have one (github.com → Sign up).
2. Create a **new public repository** named exactly: `YOUR-USERNAME.github.io`
   (replace YOUR-USERNAME with your GitHub username). This makes the site's
   free address `https://YOUR-USERNAME.github.io/`.
   - Alternative: name the repo anything (e.g. `chicbeyond40`) — the free
     address then becomes `https://YOUR-USERNAME.github.io/chicbeyond40/`.
     The username-site option above is cleaner, so prefer it.
3. Upload all files/folders from this project into the repository, keeping the
   folder structure exactly as-is (`assets/`, `posts/`, `categories/`).
   Easiest: on the repo page choose **Add file → Upload files**, drag everything in, Commit.
   Or with git:
   ```
   git init && git add . && git commit -m "Chic Beyond 40 launch"
   git branch -M main
   git remote add origin https://github.com/YOUR-USERNAME/YOUR-USERNAME.github.io.git
   git push -u origin main
   ```
4. In the repo: **Settings → Pages** → Build and deployment → Source:
   **Deploy from a branch**, Branch: `main`, Folder: `/ (root)` → Save.
5. Wait 1–5 minutes, then open `https://YOUR-USERNAME.github.io/` — the site is live.
6. Every future push/upload to `main` updates the live site automatically within a minute or two.

## 2. Add a new post

1. Copy `post-template.html` into the `posts/` folder.
2. Rename it with a keyword-rich slug, all lowercase with hyphens, e.g.
   `posts/winter-outfits-over-50-hide-tummy.html`.
3. Open it and replace every `[BRACKETED]` placeholder: title, meta description,
   H1, intro, the outfit sections (repeat the outfit block until you reach the
   number in your title), Shop-the-Look links, and the pin-image description.
   - In the copied file the stylesheet link already says `assets/style.css` with a
     note: change it to `../assets/style.css`, and make sure root links
     (`index.html`, `about.html`…) also start with `../`. The 3 starter posts in
     `posts/` are finished examples — compare yours against them.
   - Aim for **800+ words**, numbered outfits, one Shop-the-Look block per outfit.
4. Add a card for the post to `index.html` (copy an existing card in the
   "Latest Outfit Ideas" grid and change its text/link).
5. Add the same card to its category page in `categories/` (copy
   `categories/fall-outfits.html` if you need a new category — see
   `category-template.html`).
6. Add one `<url>` block for the new page to `sitemap.xml`.
7. Upload/commit the changed files. Create the Pinterest pin (1000 × 1500)
   linking to the new post's URL.

## 3. Attach chicbeyond40.com later

Do this once traffic is coming and you have bought the domain (check
`chicbeyond40.com` availability again on the day you buy — e.g. at Cloudflare
Registrar or Namecheap; buy the `.com` only, no extras needed).

1. In your GitHub repo: **Settings → Pages → Custom domain** → type
   `chicbeyond40.com` → Save. GitHub creates a `CNAME` file in the repo — leave it there.
2. At your domain registrar, add these DNS records:
   - Four **A records** for the root domain (`@`) pointing to GitHub Pages:
     `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - One **CNAME record**: name `www`, value `YOUR-USERNAME.github.io`
3. Wait for DNS (usually 15 minutes – a few hours). Back in **Settings → Pages**,
   tick **Enforce HTTPS** once it becomes available (free SSL from GitHub).
4. **Redirects:** GitHub Pages automatically redirects the old
   `YOUR-USERNAME.github.io` address to `chicbeyond40.com`, and `www` to the root
   domain — so pins and links you shared on the free address keep working.
   No redirect code is needed. (All internal links on this site are relative,
   so nothing inside the site breaks.)
5. After the switch: update the `Sitemap:` line in `robots.txt` if you changed it,
   submit `https://chicbeyond40.com/sitemap.xml` in Google Search Console,
   and update the website URL in your Pinterest profile.
6. Note the date: Journey by Mediavine's domain-age requirement counts from the
   domain's registration date, so keep the purchase receipt/date for later.

## 4. Where to paste the Pinterest claim tag

Every HTML page on this site has a clearly marked comment in its `<head>`:

```
<!-- PINTEREST DOMAIN CLAIM: paste <meta name="p:domain_verify" content="..."/> here -->
```

Steps:
1. In Pinterest: profile → **Settings → Claim** → enter your website
   (you can claim the free `github.io` address first, then claim
   `chicbeyond40.com` again after the domain switch — repeat these steps then).
2. Choose **"Add HTML tag"**. Pinterest shows you a tag like
   `<meta name="p:domain_verify" content="abc123..."/>`.
3. Paste that exact tag where the comment sits — do it in `index.html` at minimum
   (Pinterest only checks the homepage), but the placeholder exists on every page.
4. Upload/commit, wait a minute for GitHub Pages to update, then click
   **Verify** in Pinterest. Rich Pins: the Open Graph tags are already in every
   page's head; after claiming, validate any post URL at Pinterest's Rich Pins
   validator once and Rich Pins apply account-wide.

## 5. Where to paste the AdSense code later

Apply for AdSense **only after** `chicbeyond40.com` is attached (AdSense does not
approve free subdomains like `github.io`) and you have ~15–20 real posts plus the
About / Privacy Policy / Contact / Affiliate Disclosure pages (already included).

1. **Verification / ads.txt code:** Google gives you a `<script>` tag — paste it
   just before `</head>` in `index.html` (and ideally every page). Add a comment
   `<!-- AdSense -->` above it so it is easy to find.
2. **ads.txt:** create a plain file named `ads.txt` in the repo root containing
   the single line Google provides (it looks like
   `google.com, pub-XXXXXXXXXXXXXXXX, DIRECT, f08c47fec0942fa0`).
3. **Ad units:** after approval, paste each ad unit's code where you want the ad
   to appear — good spots on this layout: after the intro paragraph in posts,
   between outfit sections, and in the homepage below the post grid. Keep ads out
   of the hero so the page stays fast.
4. The Privacy Policy page already contains the required Google advertising /
   cookie disclosures — keep it linked in the footer (it is).

## Notes

- No JavaScript frameworks and no build step — edit the HTML, upload, done.
- Keep page weight low: compress photos before uploading (aim < 300 KB each,
  pin images < 500 KB). Fast pages = more Pinterest outbound clicks.
- Back up this folder somewhere besides GitHub (the repo itself is already a backup).
