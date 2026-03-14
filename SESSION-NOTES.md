# Model UN Club Website — Session Notes

## What We Built (14 March 2026)

This was a test run to explore what Claude Code can do. Everything below was built from scratch in a single session.

### Setup & Tooling
- **Node.js v24 + npm** — installed via winget
- **GitHub CLI** — installed via winget, logged in as `samanthawoodgate`
- **Git** — was already installed, configured with samantha.woodgate@gmail.com
- **Project folder:** `C:\Users\saman\projects\model-un-club`
- **GitHub repo:** https://github.com/samanthawoodgate/model-un-club (public)
- **Live site:** https://samanthawoodgate.github.io/model-un-club/
- **Hosting:** GitHub Pages (free, auto-deploys on push)
- **Password:** `modelunclub` (client-side gate — not bank-level security, just keeps casual visitors out)

### Website Features
- Dark blue theme with animated pulsing globe background
- Floating country placard animations (UK, US, France, Japan, etc.)
- Glowing logo with gradient title
- Four pillar cards: Public Speaking, Global Issues, Conferences, Leadership
- Tagline: "Saving the World Every Week"
- Mobile responsive
- Password gate on the public site
- **Teacher Portal** — mock login (just click Log In) leading to weekly resources dashboard

### Teacher Portal — What's In It
Three weeks of content, organised as expandable cards:

| Week | Topic | Status |
|------|-------|--------|
| 1 | Water Scarcity & the Global Water Crisis | **Fully built** — all resources downloadable |
| 2 | The Conflict in Iran & Middle East Geopolitics | **Partially built** — country profiles done, other resources placeholder |
| 3 | Global Oil Trade & Energy Politics | **Placeholder only** — no real resources yet |

### Downloadable Resources Created

**Week 1 — Water Scarcity:**
- Lesson Plan (PDF) — 50-60 min, starter/main/debate/reflection structure
- Slide Deck (PPTX) — 8 slides, dark theme, stats & discussion questions
- Country Position Briefs (DOCX) — 8 countries for debate (Egypt, Ethiopia, India, Brazil, Somalia, US, China, Netherlands)
- Resolution Template (PDF) — fill-in UN resolution format with guidance
- Water Bankruptcies Briefing Pack (DOCX) — 12 detailed country profiles (US/LA, China/Beijing, UK/London, Brazil/São Paulo, India/Chennai, Egypt/Cairo, Indonesia/Jakarta, Iran/Tehran, Mexico/Mexico City, South Africa/Cape Town, Spain/Madrid, Thailand/Bangkok). **Fact-checked and corrected.**

**Week 2 — Iran Conflict:**
- Country Profiles Briefing Pack (DOCX) — 10 countries (Iran, US, Israel, Saudi Arabia, Russia, China, UK, Iraq, Germany, Turkey) with world maps embedded. Each has key facts, conflict stats, diplomatic strategy, risk factors, and a specific negotiation task.

### Country Profile Template Structure
Based on `MUN - Water Bankrupties.docx` from Downloads. Each country follows:
1. **Country name** (large heading)
2. **World map** — small map in top-right with red dot on the country
3. **Key facts box:** Capital, Area, Population, Language(s), Religions (with %), Life expectancy (men/women), GDP per capita
4. **City focus** — a specific city relevant to the topic
5. **Key [Topic] Statistics** — 4-6 bullet points with specific sourced data
6. **[Topic] Sustainability and Management** — 2-3 points about current efforts
7. **Climate and Risk Factors** — 3-4 forward-looking risk points
8. **Your task** — A specific funding ask or diplomatic objective with concrete targets

Each doc covers 10-12 countries with diverse geographic representation. All stats should be recent and fact-checked.

### Logo Assets
Downloaded from `UN MODEL CLUB.zip`. Stored in project root:
- `logo.png` / `1.png` — Main logo (wreath + "Model UN Club") — **this is the site logo**
- `2.png` — Bronze Award badge
- `3.png` — Silver Award badge
- `4.png` — Gold Award badge
- `5.png` — Gavel icon
- `6.png` — Ballot box icon

### Custom Slash Commands
Saved in `.claude/commands/`:

| Command | What It Does |
|---------|-------------|
| `/new-week [topic]` | Generates a full week: lesson plan (PDF), slides (PPTX), country briefs (DOCX), resolution template (PDF), updates website, pushes to GitHub |
| `/update-week [week - changes]` | Modifies an existing week's resources |
| `/add-videos [week - request]` | Adds YouTube videos to a week |
| `/add-reading [week - request]` | Adds further reading links to a week |

### Fact-Checker
Ran a full fact-check on the water scarcity doc (12 countries, 60+ claims). Results:
- ~80% accurate
- 8 corrections applied (Egypt desalination numbers, Brazil hydropower %, Mexico timeline, South Africa threshold clarification, Spain contamination stats, Bangkok sea level, Egypt WHO claim removed)
- **TODO:** Define constraints/conditions for the fact-checker agent (sources to trust, recency requirements, confidence ratings, sensitivity for school context, etc.)

---

## What's NOT Done Yet / Next Steps

### Website
- [ ] Decide what the website should actually do beyond the teacher portal
- [ ] Get a custom domain (currently using samanthawoodgate.github.io/model-un-club)
- [ ] Decide whether to keep GitHub Pages or move to Vercel/Netlify (Vercel needs a paid plan for password protection)
- [ ] Make the repo private (requires GitHub Pro for Pages, or switch hosting)
- [ ] Replace mock teacher login with real authentication (if needed)
- [ ] Build out the design — current version is a test/proof of concept

### Content
- [ ] Complete Week 2 (Iran) — still needs: lesson plan, slide deck, resolution template
- [ ] Complete Week 3 (Oil Trade) — needs everything
- [ ] Decide on more weekly topics
- [ ] Decide if the Water Bankruptcies briefing pack template should be the standard for all weeks
- [ ] Consider what other resource types teachers might need

### Fact-Checker Configuration
- [ ] Which sources to trust (UN agencies, BBC, WHO, academic journals?)
- [ ] How recent stats need to be (last 2 years? 5 years?)
- [ ] Whether to flag politically sensitive / one-sided claims
- [ ] Whether to flag government self-reported stats that might be biased
- [ ] Auto-correct vs. flag-only mode
- [ ] Confidence ratings (high / moderate / unverifiable)
- [ ] Whether to check age-appropriateness and debate balance
- [ ] Scope: numbers only, or also historical claims, dates, treaty names?
- [ ] Time/cost budget for the checker

### Integrations to Explore
- [ ] Canva API — for auto-generating visual content (currently no video support via API)
- [ ] Google Docs integration — could set up MCP server for direct access
- [ ] Consider video generation tools (Creatomate, Shotstack) if needed

---

## Technical Notes

### How the Site Deploys
1. Edit files in `C:\Users\saman\projects\model-un-club`
2. Git commit and push
3. GitHub Actions workflow (`.github/workflows/deploy.yml`) auto-deploys to GitHub Pages
4. Live in ~30 seconds at https://samanthawoodgate.github.io/model-un-club/

### How Resources Are Generated
Node.js scripts using:
- `pdfkit` — for PDF generation (lesson plans, resolution templates)
- `pptxgenjs` — for PowerPoint slide decks
- `docx` — for Word documents (country briefs)
- `sharp` — for PNG image generation (world maps)
- `adm-zip` / `jszip` — for reading/modifying existing .docx files

Scripts are written as one-off generators, run with `node scriptname.js`, then deleted after use. The `generate-resources.js` file is kept as a reference template.

### npm Packages Installed
```
pdfkit, docx, pptxgenjs, sharp, adm-zip, jszip
```

### File Structure
```
model-un-club/
├── .claude/commands/       ← custom slash commands
├── .github/workflows/      ← GitHub Pages deploy
├── resources/
│   ├── maps/               ← world map PNGs for each country
│   ├── week1/              ← water scarcity resources
│   └── week2/              ← Iran conflict resources
├── index.html              ← the entire website (single file)
├── logo.png                ← main logo
├── 1-6.png                 ← logo variants and icons
├── package.json
├── generate-resources.js   ← reference script for resource generation
└── .gitignore
```

---

## Preferences & Style Notes
- Keep it simple — I'm new to dev, Claude does the heavy lifting
- Just do things rather than explaining steps and asking me to do them
- Use cockney rhyming slang occasionally to keep things lively
- Don't ask for permission on every tool call — allowlist is set up
- All commits and pushes can happen without asking
