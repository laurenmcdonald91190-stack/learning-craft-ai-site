# Learning Craft AI — Claude Project Context

This document gives Claude everything it needs to continue working on the Learning Craft AI project without needing to re-explain the business, tech stack, or decisions made so far.

---

## What This Business Is

**Learning Craft AI** is a two-sided business:

1. **B2B Consulting** — auditing and improving the contributor training infrastructure of AI data companies (evaluation frameworks, onboarding programs, QA systems, rubric design)
2. **Individual Courses** — teaching people the practical skills needed for AI training roles (RLHF, prompt evaluation, rubric writing, data quality, red teaming)

**Core positioning:** The specialist partner for companies and individuals who need to get AI training *right* — not just understand it in the abstract. The gap in the market is that platforms like Scale AI/Outlier and Appen have broken, unpaid onboarding with no investment in contributor quality. Learning Craft AI solves this.

**Founded by:** Lauren McDonald (she/her)

**Website:** learningcraftai.com

---

## Tech Stack

Everything is built as single-file HTML — no frameworks, no backend, no Python. Just HTML + CSS + JavaScript.

- **Main marketing site:** `index.html`
- **Course platform:** `courses.html` (deployed as `index.html` in a separate repo)
- **Fonts:** DM Sans (all weights including 700, 800) + DM Mono — loaded from Google Fonts
- **Color palette:**
  - Background: `#080b10`
  - Secondary bg: `#0d1117`, `#111820`, `#151e28`
  - Cyan accent: `#00e5c8`
  - Violet accent: `#9b5de5`
  - Text: `#e8edf2`
  - Muted text: `#7a8a9a`
  - Gold: `#f5c842`

---

## Infrastructure

| Asset | Repo | Live URL |
|---|---|---|
| Marketing site | `learning-craft-ai-site` | `learning-craft-ai-site.vercel.app` |
| Course platform | `courses-learning-craft-ai` | `courses.learningcraftai.com` (subdomain) |

- Both repos on GitHub under `laurenmcdonald91190-stack`
- Both connected to Vercel — auto-deploys on every push
- Edit files directly in GitHub browser → Vercel deploys in ~30 seconds
- Domain managed separately; `courses` subdomain pointed at Vercel via DNS
- No extra domain purchase needed for subdomain

---

## Course Platform — Key Details

### Login Credentials

| Role | Email | Password |
|---|---|---|
| Admin | `admin@learningcraftai.com` | `lcai2025admin` |
| Demo (B2B prospects) | `demo@learningcraftai.com` | `lcaidemo2026` |
| Student | any email | any password |

### Demo Mode
- Accessed via `demo@learningcraftai.com` / `lcaidemo2026` OR clicking "View demo" on login screen
- Shows ONLY the demo course — real courses are hidden
- Purple "Business Demo Mode" banner appears at top
- "View Course Builder →" button lets prospects see the admin builder
- "← Back to Student View" button returns them to student experience
- Demo course: "AI Contributor Training — Sample Module" (id: `course-demo`, marked `isDemo: true`)

### Courses (Pre-loaded)
1. **Intro to AI Model Training Platforms** — Introductory, 5 lessons, 3 quiz questions
2. **Prompt Evaluation Fundamentals** — Intermediate, 4 lessons, 2 quiz questions
3. **AI Training Reviewer Fundamentals** — Advanced, 5 lessons, 2 quiz questions
4. **AI Contributor Training — Sample Module** — Demo only, 3 lessons, 2 quiz questions (RLHF + writing eval + rubric design)

### Platform Features
- XP system (+50 per lesson, +25 per correct quiz answer)
- Level progression (500 XP per level)
- 8 badges with unlock conditions
- Streak tracking
- Floating XP pop animations
- Level-up modal
- Leaderboard
- Admin course builder (create/edit courses, lessons, quiz questions)
- Video support: YouTube, Vimeo, Google Drive, generic iframe (HeyGen/Synthesia)

### Gamification
- XP per lesson: 50
- XP per correct answer: 25
- XP per level: 500
- Badges: First Lesson, Quiz Ace, On Fire (3-day streak), Century (100 XP), Halfway (300 XP), Scholar (500 XP), Graduate (course complete), Week Warrior (7-day streak)

---

## Marketing Site — Key Details

### Pages
- Home
- About
- Business Services
- Individual Courses
- Contact

### Contact Form
- Wired to Formspree: `https://formspree.io/f/xojkegkk`
- Uses fetch/JSON with loading state, error handling, success message
- Dropdown options: B2B Consulting (4 types), Individual Course Waitlist, Corporate Training License, Something else

### B2B Consulting Services (4 offerings)
1. Training Infrastructure Audit
2. Evaluation Framework Audit
3. Onboarding Program Design
4. QA Framework Design

### Individual Courses on Site
1. Intro to AI Model Training Platforms — Introductory
2. Prompt Evaluation Fundamentals — Intermediate
3. AI Training Reviewer Fundamentals — Advanced (no certification/credential language)

---

## Design Decisions (Don't Revert These)

- **No Syne font** — was causing stretched/squished text; replaced with DM Sans bold everywhere
- **No DM Mono** — replaced with DM Sans throughout for cleaner professional look
- **No grid lines on favicon/LinkedIn assets** — removed per Lauren's preference
- **No credential/certification language** on Course 3 — removed deliberately
- **No "Each course earns you a credential" line** — removed from courses intro
- **Favicon** — inline SVG data URI, dark bg, gradient LC lettermark (cyan→violet), glowing cyan dot top-right. Same favicon used on both marketing site and course platform.

---

## Favicon (Inline SVG — use this everywhere)

```html
<link rel="icon" type="image/svg+xml" href="data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 32 32'%3E%3Cdefs%3E%3ClinearGradient id='g' x1='0%25' y1='0%25' x2='100%25' y2='100%25'%3E%3Cstop offset='0%25' stop-color='%2300e5c8'/%3E%3Cstop offset='100%25' stop-color='%239b5de5'/%3E%3C/linearGradient%3E%3C/defs%3E%3Crect width='32' height='32' rx='7' fill='%23080b10'/%3E%3Cline x1='10.5' y1='4' x2='10.5' y2='28' stroke='%2300e5c8' stroke-width='0.4' stroke-opacity='0.2'/%3E%3Cline x1='21.5' y1='4' x2='21.5' y2='28' stroke='%2300e5c8' stroke-width='0.4' stroke-opacity='0.2'/%3E%3Cline x1='4' y1='10.5' x2='28' y2='10.5' stroke='%2300e5c8' stroke-width='0.4' stroke-opacity='0.2'/%3E%3Cline x1='4' y1='21.5' x2='28' y2='21.5' stroke='%2300e5c8' stroke-width='0.4' stroke-opacity='0.2'/%3E%3Ctext x='5' y='23' font-family='sans-serif' font-weight='900' font-size='18' fill='url(%23g)' letter-spacing='-1'%3ELC%3C/text%3E%3Ccircle cx='26' cy='7' r='3' fill='%2300e5c8' opacity='0.9'/%3E%3Ccircle cx='26' cy='7' r='5' fill='%2300e5c8' opacity='0.15'/%3E%3C/svg%3E">
```

---

## LinkedIn Assets (Already Created)

- **Profile picture / logo:** `learningcraftai-favicon.png` — 400×400px, dark bg, gradient LC lettermark, glowing cyan dot, no grid lines
- **Banner:** `learningcraftai-linkedin-banner.png` — 1584×396px, centered "Learning Craft AI" in cyan→violet gradient, thin divider, tagline "Building the training infrastructure the AI workforce needs."

---

## Payments

Not built into the platform. Plan is to link out to an external payment platform (Stripe or Gumroad) and email students a course access link after purchase.

---

## Future / Pending

- [ ] Connect Supabase for real auth + progress persistence (supabase.com, free tier)
- [ ] Add actual video content via admin course builder (HeyGen/Synthesia exports recommended; Vimeo free tier for hosting)
- [ ] Build demo video / walkthrough script for B2B sales calls
- [ ] First B2B target: mid-market AI data companies ($5M–$50M revenue) with active annotation programs — too small for Deloitte, big enough to have a real problem
- [ ] Corporate training licensing as third revenue stream (post first B2B client)
- [ ] Consider linking course completions to referral links for platforms like Outlier, Handshake, Snorkel (Marco's suggestion — strong differentiator)

---

## Key Context for Future Claude Sessions

- Lauren is building this largely solo to start, plans to hire once revenue comes in
- The course platform already exists and works — it is a sales asset / demo tool, not just a student product
- B2B consulting is the primary revenue driver; courses provide authority, cash flow, and a lead generation mechanism
- The business is NOT just another "AI consultant" — the moat is deep operational knowledge of how AI training pipelines actually work
- Marco (TPM friend/potential partner) has given useful pushback — his concern about technical complexity is valid in general but Lauren has already solved it
- Supabase connection is the main technical debt item remaining on the platform
