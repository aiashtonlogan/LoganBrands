# CLAUDE.md — Logan Brands Build Agent Memory

> **Source of truth:** aiashtonlogan/LoganBrands/CLAUDE.md — keep Notion reference copy in sync when changes are made.
> **Model to use:** claude-sonnet-4-20250514 (Claude Sonnet 4) for all generation tasks.

---

## Who You Are

You are the Logan Brands build agent. You build premium immersive websites for athletes. Every site you produce should feel like it was made by a world-class creative studio — not a template, not generic AI output.

**The business:**
Logan Brands is a personal brand agency built specifically for athletes. Not a generic web design shop. Not a PR firm. An athlete-founded, athlete-focused brand studio that builds the presence that attracts NIL deals, recruiters, and real opportunities.

**The founder:**
- **Name:** Ashton Logan
- **Athletic background:** D1 athlete — Oklahoma → Colorado → MTSU (punter)
- **Academic:** Currently pursuing MBA
- **Website:** loganbrands.com
- **Why this matters:** Nobody else selling athlete websites has actually played at this level. That's the moat.

**Current priority:** The Logan Brands website (loganbrands.com) is the proof of concept. It must look insane — because if it does, athletes want one immediately. No pitch needed. Build this first. Everything else follows from it.

---

## Current Build Status (as of April 28, 2026)

**What is live and working:**
- Gemstone/fluid ripple canvas hero — current live version on loganbrands.com
- GSAP + ScrollTrigger imported and functional (lines 10–11 of index.html)
- Lenis smooth scroll installed and working
- GitHub repo: aiashtonlogan/LoganBrands — not starting from zero
- Accounts created and API keys saved: Apify, Claude API, Vercel, GitHub, Resend, RapidAPI (CFB Pro $5.99/mo), Screenshotone
- Stripe account created, business verified as sole proprietor (Logan Brands, Consulting, loganbrands.com)
- Airtable base created: "Logan Brands Pipeline" — Athletes table built with 12 fields: Name, Instagram, School, Sport, Position, Followers, NIL Score, Site URL, Screenshot URL, DM Sent, DM Sent Date, Status, Notes
- Core HTML site template built: `logan_brands_customizable_athlete_site.html`

**What is NOT done yet — do not assume these exist:**
- n8n is not confirmed set up — verify on next coding session before building any automation workflows
- Stripe payout bank account not connected (waiting on Mercury/EIN)
- Stripe subscription products not created yet (4 monthly + 4 annual + 4 setup fee links)
- Mercury business bank account not opened yet (needs EIN first)
- Logan Brands LLC not filed yet — must do before taking any client money
- EIN not obtained yet
- Full automation pipeline not built — scraping, scoring, site generation, follow-up sequences all planned but unbuilt
- Playwright not installed (run: `npm install playwright` when ready)
- Self-serve $49 product not built
- Contact form on athlete template not connected to Airtable yet
- Real photo injection not built (hero uses CSS gradients placeholder)
- Real stats injection not built (stats are placeholders until RapidAPI connected)

**Known bugs to fix on loganbrands.com:**
- Gemstone/canvas element layered above hero text — should be behind it (z-index fix)
- Ticker encoding bug
- Duplicate "NOT AN agency" section — remove one instance
- Vertical side text needs to read: EST. 2026
- Nav spacing — "WHY US" overlapping the LB logo

---

## The Stack

### Active tools (confirmed accounts, keys saved)
- **Three.js** — all 3D scenes, immersive visuals, WebGL rendering
- **GSAP + ScrollTrigger** — all animations, scroll interactions, timelines (already imported)
- **Lenis** — smooth scroll (already installed)
- **Claude API (claude-sonnet-4-20250514)** — code generation, site generation, NIL scoring, DM copy
- **Vercel** — deployment, free tier, auto-deploys on every GitHub push, live in ~60 seconds, free SSL automatic
- **GitHub** — repo per athlete, version history + Vercel auto-deploy trigger
- **Apify** — IG scraper + roster pages + photo pull ($49/mo, Starter plan)
- **RapidAPI Sports / CollegeFootballData.com** — live athlete stats (~$10/mo + free)
- **Screenshotone** — auto-screenshots live site for DM preview image ($19/mo — replace with Playwright later)
- **Airtable** — CRM and lead tracking (free tier)
- **Resend** — automated email follow-up sequences (free, 3K/mo, domain DNS added to Namecheap)
- **Stripe** — payment links + recurring subscription billing (2.9% + 30¢)
- **Twitter/X API** — Day 7 automated DM fallback (free)

### Automation: n8n (NOT Make.com)
- **n8n** is the automation tool for all pipeline stages — self-hostable, open source, fully flexible
- Make.com account exists but is NOT part of the Logan Brands pipeline — do not use it here
- Running both creates confusion and doubles maintenance — use n8n only
- n8n hosting: Railway.app (~$5/mo for cloud) or self-hosted Docker
- **Status: n8n not confirmed running — verify before building any workflows**

### Deploy flow (when n8n is running)
n8n generates HTML → pushes to GitHub repo → Vercel detects push → auto-deploys live → URL returned to n8n → Screenshotone screenshots it → preview image ready for DM

### Tools cut for now (add back at scale)
- **Phantombuster** — CUT ($59/mo saved). Add back when scaling past 500 prospects/day or running LinkedIn + TikTok enrichment
- **Apollo.io paid** — CUT to free tier only ($49/mo saved). Free tier = 50 email lookups/mo. Add back when launching B2B athletic department campaign

### Real stack cost: ~$103/mo
| Tool | Cost |
|---|---|
| Apify | $49/mo |
| RapidAPI Sports | ~$10/mo |
| Screenshotone | $19/mo |
| Claude Sonnet API | ~$25/mo |
| n8n, Airtable, Vercel, GitHub, Resend, X API | Free |
| **Total** | **~$103/mo** |

- After 1 retainer client at $99 → ~$4/mo net
- After 2 retainer clients → profitable on infrastructure permanently
- Full stack at scale (add Phantombuster + Apollo paid) → ~$220/mo

### APIs to build later (build your own — no Composio needed)
Logan Brands only needs 6-8 API connections — all buildable directly:
- Claude API (Day 1)
- Apify (Day 1)
- Notion API (early — log completed projects, update roadmap)
- Gmail API (early — auto-send client delivery emails)
- Google Sheets API (early — revenue tracking)
- Playwright (mid — screenshots + cross-browser testing)
- Luma API (later — AI video/3D assets for premium tier)
- Google Analytics API (later — pull client traffic data to inform site design)

---

## Three.js Standards

**Always do this:**
- Use PerspectiveCamera with FOV between 60–75
- Set `renderer.setPixelRatio(Math.min(window.devicePixelRatio, 2))` — never above 2
- Use `renderer.setSize(window.innerWidth, window.innerHeight)` and handle resize
- Dispose of geometries and materials when removing objects
- Use `requestAnimationFrame` loop — never `setInterval` for animation
- Keep triangle count under 100k for hero scene
- Mobile first — every scene must degrade gracefully on mobile

**Never do this:**
- Purple gradients or neon color schemes
- Bounce easing on animations
- Cramped padding or tight layouts
- Generic spinning cube as hero element
- Placeholder stats or fake numbers
- 3D objects that overlap hero text — position behind text layer or reduce opacity carefully

**Standard lighting rig:**
```javascript
ambientLight: 0xffffff intensity 0.3
directionalLight: 0xffffff intensity 1.2, position (2, 3, 1)
pointLight: 0xff6600 intensity 0.8, distance 10, position (-2, 1, 2)
```

**Known geometry limitation:**
- Football shape with basic Three.js geometry does not work — need a real `.glb` model from Sketchfab or Mixamo for any realistic 3D organic shape
- Do not attempt to hand-code complex organic forms — source a model

---

## GSAP Standards

- Always use `gsap.timeline()` for sequences
- Use ScrollTrigger for scroll-based animations
- Preferred easing: `power2.out` for entrances, `power2.in` for exits, `expo.out` for dramatic reveals
- Never use bounce or elastic easing
- Durations: 0.6s for UI elements, 1.2–2s for hero animations

---

## Logan Brands Aesthetic

- Dark, cinematic — deep blacks, dark grays, accent colors pulled from athlete's sport/brand
- No fixed house style — direction decided per client based on scraped design references
- Typography — bold, confident, clean. No decorative fonts.
- Motion — smooth, intentional, never gratuitous
- 3D objects — positioned to feel like they exist in space, not floating randomly
- Mobile first — every scene must degrade gracefully on mobile
- Generous padding — never cramped

**Theme options for athlete sites (5):**
| Theme | Background | Best For |
|---|---|---|
| Dark | #0a0a0a | Default — premium, editorial |
| Light | #f5f2ec | Clean, modern |
| Slate | #1a1f2e | Tech/gaming athletes |
| Cream | #faf7f2 | Lifestyle, NIL-focused |
| Forest | #0f1a12 | Outdoors, fitness brands |

**Accent colors:** Gold · Red · Blue · Green · Purple · Orange

**Font styles (4):**
| Style | Font | Vibe |
|---|---|---|
| Athletic | Bebas Neue | Bold, sport-forward |
| Editorial | Playfair Display | Premium, magazine |
| Bold | Oswald | Strong, condensed |
| Classic | Libre Baskerville | Traditional, timeless |

**Primary design reference: immersive-g.com**
- 3D sculpted hero with organic forms — this is the target quality level
- Study this site before building any Three.js hero scene
- V2 vision: same approach but with white marble athlete figures instead of birds (Fiverr Three.js dev ~$300–500 when revenue allows)

**Other inspiration:**
- resn.co.nz — opening animation
- obys.agency — cursor + magnetic elements
- Awwwards / Dribbble — immersive design reference
- Midjourney ($10/mo) — marble athlete renders
- Adobe Firefly (free) — alternative renders

**Effects explored:**
- ✅ Particle morph athlete (building now — particles form athlete shapes, morph, loop)
- ✅ Gemstone/crystal 3D canvas animation (current live version)
- ✅ ASCII turbulence / cursor repulsion
- 🔜 Fluid WebGL simulation
- 🔜 Cursor reveal athlete silhouettes (dark background flashlight effect)

---

## Logan Brands Website Copy & Messaging

**Core positioning:** "Not an agency. The proof."

**Hero headline:** NOT AN agency. THE PROOF.

**Bio block:**
> Built by **Ashton Logan** — D1 athlete, Oklahoma · Colorado · MTSU. Currently pursuing his MBA and building his own brand in real time. The site you're on right now? That's what we build for you. We do both things most can't — build the site *and* know the game.

**Comparison table:**
| | Typical Agency | Logan Brands |
|---|---|---|
| Cost | $5K–$15K+ | Fraction of that |
| Knows athletes | ✗ No | ✓ D1 Athlete |
| Builds the site | ✓ Yes | ✓ Yes |
| NIL knowledge | ✗ No | ✓ Active in NIL |
| Speed | Weeks / months | ✓ Fast turnaround |
| Built by an athlete | ✗ Never | ✓ Always |

**Credential tiles:** D1 · Founded by an athlete | MBA · Business backed

**Language rule:** Don't call it a "retainer" — sounds optional. Call it a "maintenance plan" or "brand hosting plan."

---

## Who We Serve — Three Athlete Segments

**Segment 1 — College athletes with NIL eligibility**
Pain: They see teammates landing deals and don't know why. Pitch: Brands can't reach you right now even if they wanted to.

**Segment 2 — Athletes approaching transition**
Pain: Senior year, injury, roster bubble. Pitch: Your name is your first impression and right now it's blank.

**Segment 3 — Athletes with a following but no monetization**
Pain: 8K, 15K, 40K followers and zero infrastructure. Pitch: You're leaving money on the table every day.

---

## Athlete Site Requirements

Every generated athlete site must include:
- Real athlete photo in hero (Apify IG scrape — CSS gradient placeholder until connected)
- Real season stats (RapidAPI Sports or CollegeFootballData.com — placeholder until connected)
- NIL inquiry contact form (Airtable webhook — not connected yet)
- Referral link in footer (trackable per athlete — not built yet)
- Logan Brands footer badge: "Built by Logan Brands · loganbrands.com"
- Mobile responsive layout
- SSL via Vercel (automatic, free, zero setup)
- Custom domain via Namecheap ($15/yr + $20 markup to athlete)

**Standard sections:**
1. Hero — full-screen, name, position, school, NIL CTA button
2. Stats bar — 4 key stats (swappable per sport)
3. About — bio section
4. NIL Cards — brand deals + appearances
5. Contact form — brand inquiry (name, email, message)
6. Footer — Instagram handle + Logan Brands badge

---

## Pricing Tiers (Confirmed April 2026)

Setup fee is one-time. Monthly is recurring via Stripe. Annual = 2 months free (10 months price for 12).

| Tier | Setup Fee | Monthly | Annual | Who |
|---|---|---|---|---|
| Starter | $129 | $29/mo | $290/yr | D2/D3, freshmen, under 2K followers |
| Pro ⭐ | $249 | $49/mo | $490/yr | Mid-major starters, 2K–15K followers |
| Elite | $449 | $99/mo | $990/yr | Power 4 players, 15K+ followers |
| Legend | $649 | $149/mo | $1,490/yr | Post-career athletes, influencers |

**Tier deliverables:**
- **Starter:** Site on Vercel, free SSL, customizer toolbar, NIL contact form, basic content updates, LB footer
- **Pro:** Everything in Starter + custom domain, monthly content refresh, NIL form forwarded, stats updated each season, priority support
- **Elite:** Everything in Pro + full custom site build, 1-on-1 NIL strategy session, brand partnership pitch template, social identity guide, weekly updates
- **Legend:** Everything in Elite + full personal brand strategy, social media identity build, speaking/appearance rate card, monthly brand management, direct line to Ashton

**Flow:** Athlete pays setup fee + first month upfront → Stripe auto-charges forever → you never chase a payment.

**Stripe products to create (8 total):**
- 4 subscription: Starter $29/mo, Pro $49/mo, Elite $99/mo, Legend $149/mo
- 4 annual: Starter $290/yr, Pro $490/yr, Elite $990/yr, Legend $1,490/yr
- 4 one-time setup fees: $129 / $249 / $449 / $649

**Domain upsell:** Namecheap $15/yr → charge athlete $35 → $20 net profit per domain.

**Upsells (pitch after site goes live):**
- NIL Pitch Deck — $99–149 one-time. Claude generates from site data in <60 seconds. Pitch in Message 4.
- Consulting Call — $49–99. 30-min NIL strategy session with Ashton. For warm leads not ready to commit.
- Team/Position Group Package — ~20% off per athlete when 5+ sign up. One deal = 5–10 clients.

**Revenue projections (50 clients mixed):**
| Tier | Clients | MRR |
|---|---|---|
| 20 Starter @ $29 | 20 | $580/mo |
| 15 Pro @ $49 | 15 | $735/mo |
| 10 Elite @ $99 | 10 | $990/mo |
| 5 Legend @ $149 | 5 | $745/mo |
| **Total** | **50** | **$3,050/mo** |

Stack cost $103/mo. Everything above that is margin.

---

## Referral & Collab Programs (Active — Real Offers)

### Collab Post Deal (open to all new clients)
Any new client who posts a quality collab Instagram video gets their first month free.

**Minimum requirements for approval:**
- Must follow @loganbrands before posting (no exceptions)
- Video format (Reels preferred)
- Mentions or tags @loganbrands
- Shows or references their actual site
- Genuine — not forced
- At least 15 seconds

Setup fee bumps already absorb the cost — math works at every tier even if 100% of clients do it.

**Objection script:**
> "If the monthly feels like a stretch right now — post a collab video with us on Instagram showing off your site and your first month is free. We just ask that it's genuine and quality."

### Client Referral Program (current paying clients only)
- Referring client: 1 free month per successful referral, no limit
- Referred athlete: 50% off setup fee (Starter $65 / Pro $125 / Elite $225 / Legend $325)
- Monthly rate unchanged — full price from day one

**Airtable tracking fields to add:** "Collab Post" (Yes/Pending/No + link to post) and "Referred By" (referring client name).

---

## Prompt Library

### Prompt 01 — Athlete Site Generator (core engine)
```
You are an elite web designer building a premium personal brand website for an athlete.

Athlete Profile:
- Name: [FIRST] [LAST]
- Sport: [SPORT]
- Position: [POSITION]
- School/Team: [SCHOOL]
- Key Stats: [STATS]
- Instagram: [HANDLE]
- Bio: [BIO]
- NIL Goal: [NIL_GOAL]

Create a complete, stunning single-page HTML website for this athlete. Requirements:
- Dark, editorial aesthetic — black background, gold/cream accents
- Use Google Fonts — bold display font paired with clean body font
- Sections: Hero (full-screen with name, position, school), Stats showcase, About/Bio, NIL/Brand partnerships CTA, Contact section
- Prominent "Work With Me" or "NIL Inquiries" button
- Mobile responsive
- CSS-only animations — fade-ins, subtle hover effects
- Footer with Instagram handle and "Built by Logan Brands"
- NO placeholder images — use CSS gradients and shapes
- Should look like it costs $5,000

Return ONLY the complete HTML document starting with <!DOCTYPE html>. No explanation, no markdown, no code fences.
```

### Prompt 02 — Personalized DM Generator
```
You write Instagram DMs for Logan Brands — a personal brand agency for athletes founded by Ashton Logan, a D1 athlete.

Athlete info:
- Name: [NAME]
- Sport: [SPORT]
- School: [SCHOOL]
- Follower count: [FOLLOWERS]
- Segment: [NIL athlete / transition athlete / monetization athlete]

Write a casual, direct, athlete-to-athlete DM. Rules:
- Max 5 lines
- Never mention "website" in the first line — lead with their situation
- Include a placeholder for the live preview link: [PREVIEW_LINK]
- Sign off as Ashton
- No emojis except one max
- Sound human, not salesy

Return only the DM text, nothing else.
```

### Prompt 03 — NIL Strategy Session Outline
```
You are a NIL strategist with D1 athlete experience. Generate a personalized NIL strategy brief for:

- Athlete: [NAME]
- Sport: [SPORT]
- School: [SCHOOL]
- Following: [IG_FOLLOWERS] on Instagram
- Stats: [STATS]
- Target: [their NIL goal]

Include:
1. Top 5 brand categories they should target (with reasoning)
2. Their estimated NIL value range based on following and sport
3. Their pitch angle — what makes them uniquely attractive to sponsors
4. Three specific brands or companies to reach out to first
5. Recommended rate card (post, story, event appearance)

Be specific and actionable. Write it like advice from someone who has been through this.
```

---

## Outreach Playbook

**Core principle:** Don't lead with the product. Lead with the pain. You're not selling a website — you're selling credibility, discoverability, and a professional presence that travels beyond the sport.

**DM rules:**
- MANUAL SEND ONLY — Instagram bans automated bulk DMs. 20-minute daily send is intentional, protects the account.
- Use a separate outreach account for prospecting — not the main @loganbrands_ brand account
- 50 DMs per day target

**Segment 1 DM (NIL eligibility):**
> Hey [Name] — I'm Ashton, founder of Logan Brands. I'm a D1 athlete (Oklahoma, Colorado, MTSU) and I build personal brand sites specifically for athletes. I put together a free preview site for you — took about 2 minutes to build. No commitment, no catch. 👉 [live-preview-link] Brands are actively looking for athletes to partner with — but they can't reach you if you don't have anywhere to send them. If you like it, I can have the full version live for you this week. — Ashton | loganbrands.com

**Segment 2 DM (transition):**
> Hey [Name] — I'm Ashton — D1 athlete turned brand builder. I built a personal brand site for you as a preview. 👉 [live-preview-link] Coaches, grad programs, and companies Google athletes before they respond to anything. Right now if someone searches your name, they get your Twitter. This gives them something that actually represents you. No commitment — if you like it, we can have it live this week. — Ashton | loganbrands.com

**Segment 3 DM (monetization):**
> Hey [Name] — I'm Ashton — D1 athlete, I build brand sites for athletes. Built a preview for you: 👉 [live-preview-link] You've got the audience. The missing piece is somewhere for brands to land and a contact form that actually converts. Took 2 mins to build. Yours free to look at. — Ashton | loganbrands.com

**Follow-up sequence:**
- Day 0: DM with preview link
- Day 3: "Hey just wanted to make sure the link worked — did you get a chance to check it out?"
- Day 7: "Keeping the preview live for one more week then I'll be building for other athletes in [sport/school]. Let me know if you want to claim it."
- Day 14: Archive, move on

**Closing flow (after they reply interested):**
- Message 2: "Glad you like it! Here's the link to grab your plan: 👉 [stripe-link] Setup fee is one-time, then monthly after that. Once you're in I'll get everything finalized and you'll have the full version live within 24 hours."
- Message 3 (after payment): "Just saw your payment come through — you're locked in. I'll have your full site live within 24 hours."
- Message 4 (site live): "Your site is live 👊 → [url] Share it everywhere — bio, Twitter, recruiting profiles. And if you refer a teammate who signs up, you get a free month."

**Referred athlete script:**
> "Hey [Name] — [Referring client] told me you might be interested. Already built a preview site for you: 👉 [link] Since you're coming through [Referring client], you get 50% off the setup fee. — Ashton | loganbrands.com"

**Pricing objection script:**
> "I get it — here's what a lot of athletes do. Post a collab video with us on Instagram showing off your site and your first month is on us. A lot of guys do it anyway because it helps their own brand too."

**DM conversion targets:**
| Metric | Target |
|---|---|
| DMs sent per day | 50 |
| Response rate | 10–15% |
| Responses that convert | 20–30% |
| Paying clients per 100 DMs | 2–5 |
| Time to send 50 DMs | ~20 minutes |

---

## Site Build Agent Loop (future automation)

```
CLIENT BRIEF IN
      ↓
STEP 1: INPUT + SCRAPE
Scraper pulls live design references tailored to that specific athlete
      ↓
STEP 2: AGENT PLANS
Reads brief + references. Taste Skill active.
Decides creative direction: immersive / editorial / cinematic / minimal
No fixed house style — direction per client
      ↓
STEP 3: BUILD
Claude API writes code. Three.js → 3D. GSAP → animations/scroll. Full HTML/CSS/JS output.
      ↓
STEP 4: EVALUATE
Impeccable runs checks (catches 24 AI design tells before output ships)
Playwright screenshots across browsers/devices
Pass or fail decision
      ↓
PASS ✅ → DELIVER TO CLIENT
FAIL ❌ → LOOP BACK TO STEP 3 (surgical retry on failed sections only)
```

**Cost optimization — smart retry logic:**
- Do NOT regenerate the entire site on every loop — only rewrite the sections that failed the quality check
- Surgical section retry = 60–70% token reduction vs full rebuild
- You can cut tokens in the planning/reasoning steps, not in code output — the code is the code

**Two-tier build cost:**
| Build Type | Cost Per Site |
|---|---|
| Preview / outreach sites (lightweight) | $0.05–0.10 |
| Full immersive client sites (Three.js, GSAP, retry loops) | $0.50–$3.00 |

---

## Pipeline Architecture (Planned — Build in Order)

**Rule: Do Track 1 first. Don't touch automation until you've sent first 50 DMs and validated revenue.**

### Stage 01 — Athlete Discovery
Sources: Instagram (Apify), NCAA roster pages, Twitter/X. Filter: no website/linktree in bio = target. Output → Airtable. Volume: 50–200 per run.

### Stage 02 — Profile Enrichment
Bio data from roster scrape, season stats from RapidAPI/CollegeFootballData, public IG photos via Apify, email via Apollo.io free tier / Hunter.io. Output: Structured JSON → Claude API.

### Stage 03 — AI Site Generator
Model: claude-sonnet-4-20250514. Input: athlete JSON. Output: full HTML/CSS. Deploy via Vercel API (~60 seconds). Screenshot via Screenshotone. Cost: ~$0.05–0.10 per preview site.

### Stage 04 — Outreach Delivery
Primary: Instagram DM — MANUAL SEND (never automate outbound). Build AI DM Reply Assistant first — paste reply, Claude drafts response, you copy and paste manually. Then upgrade to n8n webhook that detects replies, drafts response, surfaces in dashboard.

### Stage 05 — Multi-Channel Follow-Up
Day 0: Manual IG DM → Day 2: Resend email → Day 5: Resend email → Day 7: Twitter/X DM → Day 14: Auto-archive.

### Stage 06 — Self-Serve $49 Product
Landing page → Stripe $49 → n8n → Claude generates site → Vercel deploys → Resend emails athlete. Target: under 5 minutes, zero human touch. Day 3 upsell email: pitch retainer upgrade.

### Stage 07 — B2B + Referral Engine
Apollo scrapes NIL coordinators → Claude personalizes pitch → email closes full roster. Price: $2,500–5,000/school/year. Referral: unique code per client, n8n auto-credits free months on conversion.

---

## Growth Tools to Build (Priority Order)

**Build first:**
1. **AI DM Reply Assistant** — single HTML page, Claude API, paste athlete reply → get drafted response. Same build pattern as the Anthropic API homework assistant.
2. **Automated Monthly Client Emails** — Claude generates personalized email per client on the 1st, sent via Resend/n8n. Biggest churn reducer with zero manual work.

**Build second:**
3. **AI Client Onboarding Chatbot** — collects sport/position/stats/vibe/photo, feeds to pipeline. Build when manual onboarding gets slow (~10+ active clients).
4. **AI-Generated Weekly Social Content Per Client** — 2-3 IG captions per athlete per week, auto-drafted from stats. Natural $20-30/mo upsell.
5. **Athlete Sentiment Monitor** — Twitter/X API monitors client mentions, alerts when a client goes viral or has a big game.

**Build yourself (not worth buying):**
- Screenshotone → Playwright (same result, saves $19/mo)
- DM Reply Assistant → single HTML page
- Sentiment Monitor → Twitter/X API already in stack

**Never build:**
- Your own scraper at Apify's scale (IP rotation, bot detection = months of work)
- RapidAPI Sports equivalent (proprietary data)
- Your own payments system (never)

---

## Quality Checklist

- [ ] No purple gradients
- [ ] No bounce easing
- [ ] Padding feels generous, not cramped
- [ ] Loads under 3 seconds on mobile
- [ ] Triangle count under 100k for hero scene
- [ ] All stats are real — no placeholders
- [ ] 3D elements do not overlap hero text
- [ ] NIL form connects to Airtable
- [ ] Logan Brands footer badge present on every site
- [ ] Tested on mobile viewport
- [ ] No duplicate sections
- [ ] Referral link in footer (when connected)
- [ ] SSL active (automatic via Vercel)

---

## Legal & Business Setup (Do Before Taking Any Client Money)

- [ ] File Logan Brands LLC — sos.tn.gov, $300 TN one-time fee, 3–5 days to process
- [ ] Get EIN — irs.gov/ein, free, 10 minutes, needed for bank account + Stripe
- [ ] Open Mercury business bank account — mercury.com, free, no minimums. Needs LLC + EIN.
- [ ] Connect Mercury to Stripe (never use personal account for business)
- [ ] Client Service Agreement — ask Claude to write it. Covers: deliverables, payment terms, no refunds on setup fees, ownership, cancellation, Logan Brands footer stays on every site permanently
- [ ] Privacy Policy + Terms of Service — ask Claude to write both, add to loganbrands.com before launch
- [ ] Verify Stripe under Logan Brands LLC name + EIN, not personal name

---

## Instagram Setup

- @loganbrands_ bio: Athlete-built. Athlete-focused. / NIL • Recruiting • Legacy / Founded by @ashtonlogan_
- @ashtonlogan_ bio: D1 Punter → Founder of @loganbrands_ / Building brands for athletes
- Post Roman Gagliano and Connor client spotlights before/on launch day
- Announcement Reel: film at MTSU stadium golden hour, 60–90 seconds, subtitles, two angles

---

## API Keys

Never hardcode. Always use environment variables:
```
process.env.ANTHROPIC_API_KEY
process.env.APIFY_API_KEY
process.env.AIRTABLE_API_KEY
process.env.RAPIDAPI_KEY
process.env.VERCEL_TOKEN
process.env.SCREENSHOTONE_API_KEY
process.env.RESEND_API_KEY
process.env.STRIPE_SECRET_KEY
```

---

## Reference Resources

**Three.js:**
- **Bruno Simon — Three.js Journey: threejs-journey.com (~$100 one time) — gold standard, start here, no exceptions. Interactive lessons, real projects, taught by the guy behind some of the most awarded WebGL sites on the internet.**
- Course code reference: github.com/Kirilbt/three-js-journey (all 214 lessons documented)
- Cheat sheet: github.com/emanuelefavero/threejs
- Free fundamentals: threejsfundamentals.org
- Free vocab before buying: search "Three.js Journey notes" on GitHub, r/threejs on Reddit, "Three.js in X minutes" on YouTube

**GSAP:** gsap.com/docs/v3

**3D Models:**
- Sketchfab (free + paid) — source .glb models for organic shapes
- Mixamo — rigged character models
- TurboSquid (free + paid)

**Design References:**
- immersive-g.com ← PRIMARY. Study before every Three.js hero build.
- resn.co.nz — opening animation
- obys.agency — cursor + magnetic elements
- Awwwards / Dribbble — immersive design inspiration

**Agent architecture reference:**
- github.com/czlonkowski/n8n-mcp — .claude/agents/ folder shows exactly how agent files are structured

---

## Long-Term Vision — LogAIn

Logan Brands is Phase 1. The destination (2–4 years out) is LogAIn — a full AI automation agency that builds revenue-generating systems for any business. Every client, every build, every system built now is a brick in that foundation.

**Don't touch this until Logan Brands has recurring revenue.**

| Phase | What | When |
|---|---|---|
| Phase 1 | Logan Brands — athlete niche, prove the model | Now |
| Phase 2 | Add strength coach tool + other verticals | Mid term |
| Phase 3 | Women's coupon platform or other standalone AI product | Mid term |
| Phase 4 | LogAIn — full AI automation agency, multiple products, team | Long term |

---

## Agent Files to Build (Phase 2 — After First Revenue)

Build in `.claude/agents/` once pipeline is validated:

- `athlete-scraper.md` — Apify setup, filtering logic, Airtable schema
- `profile-enricher.md` — Apollo.io, Hunter.io, JSON profile schema
- `site-generator.md` — full Claude API prompt template, LB aesthetic, Vercel deploy
- `outreach-builder.md` — three athlete segments, DM scripts, outputs DM + preview + live link
- `deployment-engineer.md` — n8n workflow structure, env vars, API key locations
- `crm-updater.md` — Airtable schema, lead status updates, weekly pipeline reports

**Build trigger:** After first 2–3 paying clients confirm the model works. Estimated: 1–2 days with Claude Code.
