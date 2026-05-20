# PDFReady — Deployment & Revenue Checklist

A single-file HTML site for a PDF accessibility remediation service.  
No build step. No dependencies. One file, live in minutes.

---

## 🚀 3 Steps to Your First $100

### Step 1 — Add Stripe Payment Links (15 minutes)

The site has three preset packages: **$40**, **$100**, and **$80**. Add card payment to each:

1. Create a free account at [stripe.com](https://stripe.com)
2. Go to **Payment Links** → **Create a payment link**
3. Add a one-time product for each package:
   - **Starter** — $40 (label: "10 Standard pages")
   - **Compliance Pack** — $100 (label: "25 Standard pages") ← this is your $100 order
   - **Complex Pack** — $80 (label: "10 Complex pages")
4. Copy each payment link URL
5. In `index.html`, replace these three placeholders:
   - `STRIPE_LINK_STARTER` → your $40 payment link
   - `STRIPE_LINK_COMPLIANCE` → your $100 payment link
   - `STRIPE_LINK_COMPLEX` → your $80 payment link

Stripe deposits funds to your bank account automatically (2-day rolling payout by default).

---

### Step 2 — Add Formspree for Form Submissions (5 minutes)

The contact form currently falls back to `mailto:` if Formspree isn't set up. To capture all leads reliably:

1. Sign up free at [formspree.io](https://formspree.io) (free tier: 50 submissions/month)
2. Create a new form — Formspree will give you a form ID like `xabc1234`
3. In `index.html`, find the `<form>` action and replace `YOUR_FORMSPREE_ID` with your form ID:
   ```
   action="https://formspree.io/f/xabc1234"
   ```
4. Formspree will email all submissions to the address you registered with

---

### Step 3 — Deploy (5 minutes)

**Netlify (recommended — free):**
1. Go to [netlify.com](https://netlify.com) → Add new site → Deploy manually
2. Drag the `pdfready-site/` folder onto the dropzone
3. Done — you get a URL like `https://random-name.netlify.app`
4. Add a custom domain in Site Settings → Domain

**GitHub Pages (already set up):**
The repo is already at `dansvillewilliamston/pdfready-site`. Enable GitHub Pages:
→ Repo Settings → Pages → Source: main branch / root  
→ Live at: `https://dansvillewilliamston.github.io/pdfready-site`

---

## What's Already Wired Up

| Item | Status |
|---|---|
| Contact email | ✅ `dmw342@gmail.com` throughout |
| Live days-past-deadline counter | ✅ Calculates from April 24, 2026 |
| Post-deadline urgency messaging | ✅ "You're in violation" positioning |
| Red violation banner (top of page) | ✅ Drives traffic to quick-order section |
| Self-service payment packages | ✅ $40 / $100 / $80 (needs Stripe links) |
| Formspree form (with mailto fallback) | ✅ (needs your Formspree form ID) |
| Form success state (no page reload) | ✅ |
| Free sample CTA | ✅ |
| Per-page pricing reference | ✅ |
| Mobile responsive | ✅ |

---

## Sections

| Section | Anchor |
|---|---|
| Violation banner (sticky top) | — |
| Navigation | — |
| Hero (post-deadline urgency) | — |
| The Problem | `#problem` |
| What We Fix (8 cards) | `#what-we-fix` |
| Quick Order / Pay Now (3 packages) | `#quick-order` |
| Per-Page Pricing reference | `#pricing` |
| How It Works (4 steps) | `#how-it-works` |
| File Intake | `#file-intake` |
| Free Sample CTA | `#free-sample` |
| Contact Form | `#contact` |
| Footer | — |

---

## Optional Enhancements

### Google Analytics
Paste your GA4 snippet just before `</head>`.

### Chat widget
Add Crisp, Tawk.to (free), or Intercom before `</body>` for live chat — high-value for closing hesitant buyers.

### Netlify Forms
If you deploy to Netlify, you can use their built-in form handling instead of Formspree:
1. Add `netlify` attribute to the `<form>` tag
2. Change `action` to `action="/success"`
3. Netlify captures all submissions and emails them to you

---

*Built for deployment. Add Stripe links, add Formspree ID, push the file, drive traffic.*
