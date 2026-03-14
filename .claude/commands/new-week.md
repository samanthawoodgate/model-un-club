Generate a complete set of weekly resources for Model UN Club on the topic: $ARGUMENTS

You must create ALL of the following files in `resources/weekN/` (where N is the next week number — check existing folders to determine this):

## 1. Lesson Plan (PDF)
- **File:** `[Topic]-Lesson-Plan.pdf`
- Use pdfkit (already installed)
- Dark header bar with "MODEL UN CLUB" branding
- Include: Learning Objectives (4-5 bullet points), Starter Activity (10 mins with discussion questions), Main Activity — Country Research (20 mins with speech prep guidance), Debate & Resolution (20 mins with step-by-step), Plenary & Reflection (10 mins), Differentiation (lower/higher ability), Resources Needed
- Estimated time: 50-60 minutes, suitable for ages 13-18
- Make it specific to the topic, not generic

## 2. Slide Deck (PPTX)
- **File:** `[Topic]-Slides.pptx`
- Use pptxgenjs (already installed)
- Dark background (#0A1628), blue accent (#4A90E2), white text
- 8 slides: Title, Scale of the Problem (with a key statistic), Causes, Who is Most Affected, Geopolitical Dimensions, What is the UN Doing, Discussion Questions (5 questions), Your Task
- Include real statistics and facts
- Each slide should have substantial content, not just bullet headers

## 3. Student Handout — Country Position Briefs (DOCX)
- **File:** `Country-Position-Briefs-[Topic].docx`
- Use docx package (already installed)
- Include 8 countries with diverse perspectives on the topic
- Each country gets: name, 4-5 sentence brief explaining their situation and stance, one-line Country Position summary in italics
- Choose countries that have genuinely different positions on the issue
- Blue headings, clean formatting

## 4. Resolution Template (PDF)
- **File:** `Resolution-Template-[Topic].pdf`
- Use pdfkit (already installed)
- Dark header bar with branding
- Pre-filled committee, topic, and one example preambulatory clause relevant to the topic
- Blank lines for: Sponsors, Signatories, 3 more preambulatory clauses, 5 operative clauses
- Include guidance text explaining what preambulatory and operative clauses are

## After generating files:
1. Update `index.html` to add a new week card in the teacher dashboard with:
   - Correct week number
   - Links to all 4 downloadable files
   - 2 embedded YouTube videos relevant to the topic (find real video IDs that are educational)
   - 3 further reading links from reputable sources (UN, BBC, academic, NGO sites)
2. Git commit and push everything
3. Tell me when the deploy is live

Use `generate-resources.js` as a reference for the code style and approach, but create a NEW script file for this week (e.g. `generate-week3.js`). Delete the script after running it.
