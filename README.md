# PDFReady — Deployment Instructions

## What's Here

A single-file HTML website (`index.html`) for a PDF accessibility remediation service.  
No build step. No dependencies. No CDN. Just one file.

---

## Before You Go Live — Checklist

1. **Replace email placeholder:**  
   Search for `dan@PLACEHOLDER.com` and replace with your real email address.  
   It appears in two places: the `<form>` action and the `handleFormSubmit()` function.

2. **Replace company name:**  
   Search for `PDFReady` / `[Company Name Placeholder]` and update to your actual business name.

3. **Update the countdown chip:**  
   The hero section says "22 Days Away" — update the number or switch to a dynamic countdown  
   (see "Optional Enhancements" below).

4. **Swap the form handler (optional):**  
   The form currently uses `mailto:` which opens the user's email client. To capture submissions  
   without requiring the user to have a mail app configured, replace with:
   - [Formspree](https://formspree.io) — free tier, just change the action URL
   - [Netlify Forms](https://docs.netlify.com/forms/setup/) — add `netlify` attribute if deploying to Netlify
   - [Typeform](https://www.typeform.com) — embed or link out

---

## Deploy to GitHub Pages (5 minutes)

```bash
# 1. Create a new repo on github.com (e.g., "pdfready-site")

# 2. Clone and add the file
git clone https://github.com/YOUR_USERNAME/pdfready-site
cd pdfready-site
cp /path/to/index.html .

# 3. Push
git add index.html
git commit -m "Initial site"
git push origin main

# 4. Enable GitHub Pages
# → Repo Settings → Pages → Source: main branch / root
# Your site will be live at: https://YOUR_USERNAME.github.io/pdfready-site
```

---

## Deploy to Netlify (2 minutes — recommended)

1. Go to [netlify.com](https://netlify.com) → "Add new site" → "Deploy manually"
2. Drag and drop the `pdf-biz-website/` folder onto the deploy dropzone
3. Done. Netlify gives you a URL like `https://random-name.netlify.app`
4. In Site Settings → Domain → add your custom domain

**Netlify Forms bonus:** Add `netlify` to the `<form>` tag and rename the action  
to `action="/success"` — Netlify will handle form capture automatically without  
any backend code.

---

## Custom Domain (optional)

- Buy a domain (Namecheap, Cloudflare Registrar, etc.)
- Point DNS to GitHub Pages / Netlify per their docs
- Both offer free HTTPS (Let's Encrypt) automatically

---

## Optional Enhancements

### Live countdown timer
Replace the static "22 Days Away" chip with a live countdown:

```javascript
function updateCountdown() {
  var deadline = new Date('2026-04-24T00:00:00-07:00');
  var now = new Date();
  var diff = deadline - now;
  var days = Math.ceil(diff / (1000 * 60 * 60 * 24));
  document.getElementById('countdown-days').textContent = days + ' Days Away';
}
updateCountdown();
// Update every hour
setInterval(updateCountdown, 3600000);
```

Then add `id="countdown-days"` to the span inside `.countdown-chip`.

### Google Analytics
Paste your GA4 snippet just before `</head>`.

### Chat widget
Add a Crisp, Tawk.to, or Intercom snippet before `</body>` for live chat.

---

## File Size

The `index.html` is approximately 36 KB — extremely lightweight. No images, no external fonts,  
no JavaScript frameworks. Loads in under 0.5 seconds on a 3G connection.

---

## Sections Included

| Section | ID |
|---|---|
| Navigation (sticky) | `nav` |
| Hero + veraPDF stamp | — |
| The Problem (stats + consequences) | `#problem` |
| What We Fix (8 cards) | `#what-we-fix` |
| Pricing (3 tiers) | `#pricing` |
| How It Works (4 steps) | `#how-it-works` |
| File Intake Instructions | `#file-intake` |
| Free Sample CTA | `#free-sample` |
| Contact Form | `#contact` |
| Footer | — |

---

*Built for deployment. Swap the email, push the file, done.*
