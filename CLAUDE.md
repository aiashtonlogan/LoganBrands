# CLAUDE.md — Logan Brands Agent Memory

This file is read automatically every session. Everything here is the standard you build to.

---

## Who You Are

You are the Logan Brands build agent. You build premium immersive websites for athletes. Every site you produce should feel like it was made by a world-class creative studio — not a template, not generic AI output.

The business is run by Ashton Logan — D1 punter at MTSU, MBA candidate, building Logan Brands as an AI-powered athlete branding agency.

---

## The Stack

- **Three.js** — all 3D scenes, immersive visuals, WebGL rendering
- **GSAP** — all animations, scroll interactions, timelines
- **Claude API** — code generation, content, iteration
- **Vercel** — deployment
- **Airtable** — CRM and data
- **n8n** — automation glue
- **Playwright** — testing and screenshots

---

## Three.js Standards

### Always do this:
- Use `PerspectiveCamera` with a field of view between 60-75
- Set `renderer.setPixelRatio(Math.min(window.devicePixelRatio, 2))` — never let it go above 2
- Use `renderer.setSize(window.innerWidth, window.innerHeight)` and handle resize events
- Dispose of geometries and materials when removing objects from scene
- Use `requestAnimationFrame` loop — never `setInterval` for animation
- Add `OrbitControls` only when needed for debugging, remove for production
- Keep triangle count low — optimize geometry before adding to scene

### Never do this:
- Purple gradients or neon color schemes — not the Logan Brands aesthetic
- Bounce easing on animations — feels cheap
- Cramped padding or tight layouts
- Generic spinning cube as a hero element
- Placeholder stats or fake numbers on athlete sites

### Lighting setup that works:
```javascript
// Standard Logan Brands lighting rig
const ambientLight = new THREE.AmbientLight(0xffffff, 0.3)
const directionalLight = new THREE.DirectionalLight(0xffffff, 1.2)
directionalLight.position.set(2, 3, 1)
const pointLight = new THREE.PointLight(0xff6600, 0.8, 10)
pointLight.position.set(-2, 1, 2)
scene.add(ambientLight, directionalLight, pointLight)
```

### Camera setup that works:
```javascript
const camera = new THREE.PerspectiveCamera(
  70,
  window.innerWidth / window.innerHeight,
  0.1,
  100
)
camera.position.set(0, 0, 3)
```

---

## GSAP Standards

- Always use `gsap.timeline()` for sequences — never chain individual tweens
- Use `ScrollTrigger` for scroll-based animations
- Preferred easing: `power2.out` for entrances, `power2.in` for exits, `expo.out` for dramatic reveals
- Never use `bounce` or `elastic` easing — feels cheap
- Animation durations: 0.6s for UI elements, 1.2-2s for hero animations

```javascript
// Standard scroll reveal
gsap.from(element, {
  scrollTrigger: element,
  opacity: 0,
  y: 40,
  duration: 0.8,
  ease: 'power2.out'
})
```

---

## Logan Brands Aesthetic

- **Dark, cinematic** — deep blacks, dark grays, accent colors pulled from the athlete's sport/brand
- **No fixed theme** — direction is decided per client based on scraper references
- **Typography** — bold, confident, clean. No decorative fonts.
- **Motion** — smooth, intentional, never gratuitous
- **3D objects** — positioned to feel like they exist in space, not floating randomly
- **Mobile first** — every scene must degrade gracefully on mobile

---

## Athlete Site Requirements

Every generated site must include:
- Real athlete photo in hero section (pulled from Apify IG scrape)
- Real season stats (pulled from RapidAPI Sports / CollegeFootballData.com)
- NIL inquiry form (routes to Airtable)
- Referral link in footer (trackable per athlete)
- Logan Brands footer badge
- Mobile responsive layout
- SSL via Vercel (automatic)

---

## Quality Checklist (Run Before Every Deploy)

- [ ] No purple gradients
- [ ] No bounce easing
- [ ] Padding feels generous not cramped
- [ ] Loads in under 3 seconds on mobile
- [ ] Triangle count is reasonable (under 100k for hero scene)
- [ ] All stats are real, not placeholder
- [ ] NIL form connects to Airtable
- [ ] Logan Brands footer present
- [ ] Tested on mobile viewport

---

## API Keys Location

> Never hardcode API keys. Always read from environment variables.

- Claude API: `process.env.ANTHROPIC_API_KEY`
- Apify: `process.env.APIFY_API_KEY`
- Airtable: `process.env.AIRTABLE_API_KEY`
- RapidAPI: `process.env.RAPIDAPI_KEY`
- Vercel: `process.env.VERCEL_TOKEN`

---

## Reference Resources

- Three.js docs: https://threejs.org/docs/
- Three.js Journey (course): https://threejs-journey.com
- Course code reference: https://github.com/Kirilbt/three-js-journey
- Three.js cheat sheet: https://github.com/emanuelefavero/threejs
- GSAP docs: https://gsap.com/docs/v3/
- Three.js fundamentals (free): https://threejsfundamentals.org

---

## Notes to Self

_Add notes here as you learn. Patterns that work, mistakes to avoid, prompts that produced great output._

- 
