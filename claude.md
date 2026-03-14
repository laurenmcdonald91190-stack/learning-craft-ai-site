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
- **Fonts:** DM Sans (all weights including 700, 800) — loaded from Google Fonts
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
| Marketing site | `learning-craft-ai-site` | `learningcraftai.com` |
| Course platform | `courses-learning-craft-ai` | `courses.learningcraftai.com` |

- Both repos on GitHub under `laurenmcdonald91190-stack`
- Both connected to Vercel — auto-deploys on every push
- Edit files directly in GitHub browser → Vercel deploys in ~30 seconds
- Domain on Squarespace DNS

### DNS (Squarespace) — Confirmed Working
- `@` A record: `216.198.79.1`
- `www` CNAME: `0bb88df4f5456fe5.vercel-dns-017.com`
- `courses` CNAME: `ff685089e345633e.vercel-dns-017.com`

---

## Course Platform — Key Details

### Admin Credentials (ALL use password `lcai2026@dmin`)

| Email |
|---|
| `admin@learningcraftai.com` |
| `arpmcdonald86@gmail.com` |
| `bloomjs@lafayette.edu` |
| `lauren.mcdonald@learningcraftai.com` |
| `lauren.mcdonald91190@gmail.com` |

### Other Credentials
| Role | Email | Password |
|---|---|---|
| Demo (B2B prospects) | `demo@learningcraftai.com` | `lcaidemo2026` |
| Student | any email | any password (mock auth — accepts anything) |

### Admin Login Flow
- Login screen has 3 tabs: Sign In, Create Account, Admin (gold)
- Admin tab has its own email + password fields — completely separate from student flow
- All password fields have Show/Hide toggle
- Admin emails checked case-insensitively
- On successful admin login → goes directly to admin panel (course builder backend)

### Demo Mode
- Accessed via `demo@learningcraftai.com` / `lcaidemo2026` OR clicking "View demo" on login screen
- Shows ONLY the demo course — real courses are hidden
- Purple "Business Demo Mode" banner appears at top
- Demo course: "AI Contributor Training — Sample Module" (id: `course-demo`, marked `isDemo: true`)

### Courses (Pre-loaded)
1. **Intro to AI Model Training Platforms** — Introductory, 5 lessons, 3 quiz questions
2. **Prompt Evaluation Fundamentals** — Intermediate, 4 lessons, 2 quiz questions
3. **AI Training Reviewer Fundamentals** — Advanced, 5 lessons, 2 quiz questions
4. **AI Contributor Training — Sample Module** — Demo only, 3 lessons, 2 quiz questions

### Video Placeholders
- All lesson video placeholders show 🎬 "Coming Soon / This video lesson is on its way." — NOT admin instructions

### Platform Features
- XP system (+50 per lesson, +25 per correct quiz answer)
- Level progression (500 XP per level)
- 8 badges with unlock conditions
- Streak tracking, confetti, level-up modal
- Leaderboard (shows name + XP only, no private data)
- **Notifications dropdown** — bell icon in topbar, auto-generates notifications from toasts (badge earned, lesson complete etc.), clears on open, "Clear all" option
- **Profile modal** — clicking avatar opens modal showing name, email, level, XP, lessons completed, streak, earned badges, Sign Out button
- Admin course builder (create/edit courses, lessons, quiz questions)
- Video support: YouTube, Vimeo, Google Drive, generic iframe (HeyGen/Synthesia)

### Student Privacy
- Each student only sees their own dashboard, XP, progress, badges, streak
- No student can see another student's data
- Leaderboard shows first name only

---

## Marketing Site — Key Details

### Pages & Navigation (hash routing)
- `/#home` — Home
- `/#about` — About
- `/#services` — Business Services (also has demo section)
- `/#courses` — Individual Courses ← HeyGen intro video embedded here
- `/#demo` — Try Demo
- `/#contact` — Contact

### HeyGen Video Embeds
- **Home/hero area:** `https://app.heygen.com/embeds/03ffce067d034517a448b2c46ccc15da`
- **Individual Courses page:** `https://app.heygen.com/embeds/f09030e6741d4729b4be199760c7e056` (intro video — "Is This For You?", shown above coming-soon banner)

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
- **No DM Mono** — replaced with DM Sans throughout
- **No grid lines on favicon/LinkedIn assets** — removed per Lauren's preference
- **No credential/certification language** on Course 3 — removed deliberately
- **No "Each course earns you a credential" line** — removed from courses intro
- **Favicon** — inline SVG data URI, dark bg, gradient LC lettermark (cyan→violet), glowing cyan dot top-right

---

## Favicon (Inline SVG — use this everywhere)

```html
<link rel="icon" type="image/svg+xml" href="data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 32 32'%3E%3Cdefs%3E%3ClinearGradient id='g' x1='0%25' y1='0%25' x2='100%25' y2='100%25'%3E%3Cstop offset='0%25' stop-color='%2300e5c8'/%3E%3Cstop offset='100%25' stop-color='%239b5de5'/%3E%3C/linearGradient%3E%3C/defs%3E%3Crect width='32' height='32' rx='7' fill='%23080b10'/%3E%3Cline x1='10.5' y1='4' x2='10.5' y2='28' stroke='%2300e5c8' stroke-width='0.4' stroke-opacity='0.2'/%3E%3Cline x1='21.5' y1='4' x2='21.5' y2='28' stroke='%2300e5c8' stroke-width='0.4' stroke-opacity='0.2'/%3E%3Cline x1='4' y1='10.5' x2='28' y2='10.5' stroke='%2300e5c8' stroke-width='0.4' stroke-opacity='0.2'/%3E%3Cline x1='4' y1='21.5' x2='28' y2='21.5' stroke='%2300e5c8' stroke-width='0.4' stroke-opacity='0.2'/%3E%3Ctext x='5' y='23' font-family='sans-serif' font-weight='900' font-size='18' fill='url(%23g)' letter-spacing='-1'%3ELC%3C/text%3E%3Ccircle cx='26' cy='7' r='3' fill='%2300e5c8' opacity='0.9'/%3E%3Ccircle cx='26' cy='7' r='5' fill='%2300e5c8' opacity='0.15'/%3E%3C/svg%3E">
```

---

## LinkedIn Assets (Already Created)

- **Profile picture / logo:** `learningcraftai-favicon.png` — 400×400px
- **Banner:** `learningcraftai-linkedin-banner.png` — 1584×396px

---

## HeyGen Assets

- **Intro video deck (Facebook/individual audience):** `learningcraftai-intro-video-deck.pptx`
  - 5 slides, ~60 seconds, energetic tone
  - Slide 1: Hook — "Model Training. Data Labeling. AI Annotation."
  - Slide 2: "AI doesn't train itself" — 3 cards (real people / data / companies pay)
  - Slide 3: The problem — without training vs. with Learning Craft AI
  - Slide 4: Brand reveal — "Learning Craft AI"
  - Slide 5: CTA — explore site / join waitlist / follow along
  - Speaker notes = clean voiceover script, HeyGen-ready (no labels or timing markers)
- **B2B promo deck:** `learningcraftai-heygen-deck.pptx` (v2, broader B2B + individual positioning)

---

## Supabase — Set Up But Not Yet Wired In

**Project details:**
- Project URL: `https://eayhhviiyxyarjxnjndi.supabase.co`
- Publishable key: `sb_publishable_0QZ04Lct_xCc2BzvYm_orw_5LBmBDjd`
- Region: East US (North Virginia)

**Tables created (RLS enabled on all):**
- `profiles` (id, email, role: student/admin/demo, created_at)
- `course_progress` (id, user_id, course_id, lesson_id, completed, completed_at)
- `user_xp` (user_id, xp, level, streak, last_active)

**Status:** Tables and RLS policies set up. Auth not yet wired into courses.html — still using mock auth.

---

## Payments

Not built yet. Plan: link out to Stripe or Gumroad, email students a course access link after purchase.

---

## Pending / Next Steps

- [ ] Wire Supabase auth into courses.html — replace mock auth with real login/register
- [ ] Persist XP/progress to Supabase (course_progress and user_xp tables)
- [ ] Add Google + Facebook OAuth (future)
- [ ] Create OG image (`og-image.png`, 1200×630px) and upload to both repos
- [ ] Add actual video content via admin course builder (HeyGen → Vimeo free tier)
- [ ] First B2B outreach to mid-market AI data companies ($5M–$50M revenue)
- [ ] Corporate training licensing as third revenue stream (post first B2B client)
- [ ] Consider linking course completions to referral links for Outlier, Handshake, Snorkel (Marco's suggestion)

---

## Key Context for Future Claude Sessions

- Lauren is building this largely solo to start, plans to hire once revenue comes in
- The course platform is a sales asset / demo tool as much as a student product
- B2B consulting is the primary revenue driver; courses provide authority, cash flow, and lead gen
- The business moat is deep operational knowledge of how AI training pipelines actually work
- Supabase connection is the main technical debt item remaining
- **When editing large single-file HTML files (index.html, courses.html): make minimal targeted changes only, use Python str.replace, verify file completeness after every edit, never run automated replacement scripts on the full file**
