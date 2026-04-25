# Yunman English Learning Games — CLAUDE.md

## Project Overview
Interactive HTML games for Yunman, a student at Kangchiao International School. Hosted on GitHub Pages.

- **GitHub Pages**: https://rainsweetgreen.github.io/yunman-games/
- **Notion Hub**: https://www.notion.so/32e549e1b6fd81daa091ca3599a99743

## Student Profile
- **Name**: Yunman
- **Grade rule**: Starts Grade 1 (小一). Advances one grade every August.
  Each school year has two semesters (上學期 / 下學期).
- **Current**: Grade 1, Semester 2, Week 10–11 (May 2026)
- **Current story**: Through Georgia's Eyes
- **Strong**: Phonics VCe/ng/nk, Vocabulary fill-in, Seen Reading comprehension
- **Weak**: VCCV spelling, Unseen Reading, Long answer (misreads question), Setting ID
- **Midterm score**: ~73% (April 2026)

---

## Repo Structure

```
yunman-games/
├── CLAUDE.md                      ← This file (auto-read on every Claude Code start)
├── templates/                     ← One HTML template per subject
│   ├── reading_template.html
│   ├── vocab_template.html
│   ├── phonics_template.html
│   └── grammar_template.html
├── content/                       ← Course content as JSON
│   └── week{N}_{topic}.json
├── scripts/                       ← Automation scripts
│   ├── generate_game.py           ← Main generator
│   ├── validate_game.py           ← Run before every delivery
│   └── fetch_google_classroom.py  ← Auto-fetch teacher games (Mon 17:00)
├── reference/                     ← Source documents from teachers (read before making games)
│   ├── reading/                   ← FET Reading story texts (doc/pdf per story)
│   ├── phonics/                   ← FET Phonics homework docs (per week)
│   ├── grammar/                   ← CET Conventions homework docs (per topic)
│   └── vocab/                     ← CET + FET vocabulary PDFs
└── *.html                         ← Published game files
```

---

## Curriculum Source of Truth

**Always check Notion 完整課程進度表 (ID: 330549e1b6fd813897f5ddbdee3633f3)**
before making any game to confirm:
- Current week number and topic
- FET Phonics topic for the week
- CET Conventions (Grammar) topic for the week
- FET Reading story title

The full curriculum schedule is provided by teachers at the start of each semester.
Grade advances every August. New semester = new curriculum schedule.

---

## Four Subject Areas — Build ALL four every week

| Subject | Template | Notion Page ID |
|---------|----------|----------------|
| 📖 Reading | reading_template.html | 330549e1b6fd81c1afe1d559b1356392 |
| 📝 Vocabulary | vocab_template.html | 330549e1b6fd81078e71ff99b88d9b77 |
| 🔤 Phonics | phonics_template.html | 330549e1b6fd813796a2ce42bbc51fc9 |
| ✏️ Grammar | grammar_template.html | 330549e1b6fd810bb5f3dfe91f431957 |

Other Notion pages:

| Page | ID |
|------|----|
| Main hub | 32e549e1b6fd81daa091ca3599a99743 |
| 完整課程進度表 | 330549e1b6fd813897f5ddbdee3633f3 |
| Wrong answers 錯題本 | 330549e1b6fd81088a52c4c1285ded59 |
| CET Vocab | 330549e1b6fd81a597c8d9822df5ee01 |
| Game design spec | 34b549e1b6fd816f99becfb630214d86 |

---

## Exam Schedule

| Subject | When | Scope |
|---------|------|-------|
| FET Vocabulary | Every Thursday | Current week words |
| Phonics | Even weeks Monday | Week N-1 + N-2 |
| CET Vocabulary | Even weeks Monday | Week N-1 + N-2 |
| Grammar (CET Conventions) | Even weeks Monday | Week N-1 + N-2 |

---

## Global Game Design Rules

- **Background**: `#fff8f0` (warm cream)
- **Fonts**: Fredoka One (headings) + Nunito (body)
- **One file**: Every game fully self-contained in a single HTML file
- **Always include**: progress bar, score display, star animation on correct answer
- **End screen**: show wrong answers with Chinese hint explanations
- **No spoilers**: never reveal answer before student attempts
- **Mobile-friendly**: tap/click interface
- **Validate**: always run `scripts/validate_game.py` before handing to parent
- **Parent confirms**: parent must verify content correctness before publishing

## File Naming Convention

```
phonics_w{N}_{topic}.html
reading_w{N}_{story}.html
vocab_w{N}_fet_spelling.html
grammar_u{N}_{topic}.html
cet_vocab_quiz.html
cet_grammar_w{N}_{topic}.html
```

---

## 📖 Reading

### Source Documents
- FET Reading story texts live in `reference/reading/`
- One doc/pdf per story — always read before generating questions
- Parent provides new stories as docs each semester

### Text Types (open-ended — expands each semester)
- Fable (narrative with moral)
- Biography
- Persuasive / Opinion
- Informational / Expository
- *(add more as curriculum introduces them)*

### Every Story Needs TWO Games

1. **Seen Reading game** — based on the FET story text from `reference/reading/`
2. **Unseen Reading game** — Claude Code writes a NEW passage of the same
   text type and difficulty, with parallel question structure

### Seen Reading Game — Required Parts

| Part | Type | Details |
|------|------|---------|
| A | Multiple Choice — 4 questions, 3 options each | Must include a Setting question |
| B | Long Answer — 1 question, complete sentence | Format: Subject + verb + because + reason |
| C | Story Elements Match — 3 pairs | Characters → names / Setting → location sentence / Lesson → moral |

### MC Question Types to Include (Seen)
- Comprehension: find answer directly in text
- Inference: why / how does X feel
- Text Type: identify genre + reason why
- **Setting — ALWAYS include, Yunman often gets this wrong**
- Moral / Main Message

### For Persuasive Texts (Seen Reading 2)
- MC: Why did author write this? → persuade / inform / entertain
- MC: What is the author's main opinion?
- Long Answer: What is the BEST reason? *(NOT "why did author write it" — Yunman confuses these)*
- **Identify Persuasive Text**: Give 4–5 sentences, student checks supporting ones
  - **ALWAYS mix in 1 counter-argument sentence as distractor**
  - e.g. "Some people don't think music is important" → should NOT be checked
  - Yunman's common mistake: checking the counter-argument sentence

### Unseen Reading Game — Required Parts

| Part | Type | Details |
|------|------|---------|
| A | Multiple Choice — 3 questions | Text Type + reason / Main Lesson / Key Detail |
| B | Long Answer — 1 question | When/What/How/Why — show "先圈問題字！" hint |
| C | Text Structure | Timeline (fill in years) or sequence ordering |

### Yunman's Reading Weak Points — Always target these

1. **Setting question**: Mix theme/feeling sentences vs location sentences in options
   → Correct answer is ALWAYS the sentence describing place/time, not feeling or moral
2. **Persuasive check**: Always include 1 counter-argument sentence as distractor
3. **Long Answer**: Show hint "先圈問題字！(Circle the question word first!)"
4. **Unseen When question**: Answer must be a specific time from the text

### FET Vocabulary (integrated into Reading game)
- FET vocab = Story Words from the FET Reading text
- Include as a separate tab/section WITHIN the Reading game
- Do NOT make a separate FET vocab game file
- Format: Fill in blank (2 choices in brackets) + Match Picture

---

## 🔤 Phonics

### Source Documents
- Phonics homework docs live in `reference/phonics/` (one doc per week)
- Always read the doc for the current week before generating questions
- Topics expand each semester — always check 完整課程進度表 for current topic

### Current Game Formats (will grow over time)

| Exam Part | Game Format |
|-----------|-------------|
| Part A — Long vowel (circle) | Show word → click long e / long o / long u |
| Part B — ng/nk (circle word) | Two words per question → click the one heard |
| Part C — Compound (join) | Connect left-column word to right-column word |
| Part D — VCCV (write syllable) | Show partial word → choose missing syllable |
| Part E — or/ore (write word) | See description/picture → choose or/ore spelling |

### Yunman's Phonics Weak Points
- VCCV: magnet→magnat, blanket→blamket, chapter→trkter (ch sound inaudible)
- r-Controlled: bore→bork (confuses word-final -ore vs -ork)
- Vowel Y: long i (1 syllable) vs long e (2 syllables)

---

## ✏️ Grammar (CET Conventions)

### Source Documents
- CET Conventions homework docs live in `reference/grammar/` (one doc per topic)
- Always read the doc for the current topic before generating questions

### Two Games Per Topic
1. **Teacher's game**: auto-fetched from Google Classroom every Monday 17:00
   → saved to Notion Grammar page by `scripts/fetch_google_classroom.py`
2. **Our game**: generated by Claude Code from the homework doc

### Game Format

| Part | Game Format |
|------|-------------|
| Part A | Full sentence, 2 options → click correct one |
| Part B | Sentence with blank → select answer |
| Part C | Show incorrect sentence → student corrects it |

### Topics Covered (Grade 1 Semester 2)
- Pronouns (I / me)
- Capitalize Proper Nouns
- Singular / Plural
- Verb Tense (past / future)
- Be Verbs (is / are / am)
- Compound Sentences (Week 11+)
- *(more added each semester)*

### Yunman's Grammar Weak Points
- Be verbs: is/are/am confusion
- Tense identification (went vs go)

---

## 📝 Vocabulary

### Two Separate Streams

#### FET Vocabulary
- Source: Story Words from FET Reading texts
- **Integrated into the Reading game** — no separate file needed
- Format: Fill in blank (2 choices) + Match Picture

#### CET Vocabulary
- Source: CET vocab PDFs in `reference/vocab/`
- Teacher posts a Wordwall game every Monday 10:00 AM on Google Classroom
  → `scripts/fetch_google_classroom.py` fetches the link at 17:00 Monday
  → saves to Notion CET Vocab page automatically
- **Claude Code generates**: mid-term review + end-of-term review games
  - Mid-term: Week 1–8 综合複習 (existing: cet_vocab_quiz.html)
  - End-of-term: Week 10–16 综合複習 (to be made when Week 16 done)
- Format: Fill in blank with context sentence, 10 random questions per round
- Each round shows Word Bank; student selects correct word for each sentence

---

## Google Classroom Auto-Fetch

**Script**: `scripts/fetch_google_classroom.py`
**Schedule**: Every Monday at 17:00

What it fetches:
1. CET Vocabulary game (Wordwall link) → saves to Notion CET Vocab page
2. CET Grammar game link → saves to Notion Grammar page

After fetching, update the relevant Notion page table with:
- Week number, game link, date fetched

---

## Workflow for Every New Game

1. Read this CLAUDE.md
2. Check 完整課程進度表 in Notion for current week + topic
3. Read source doc from `reference/` for this week's content
4. Get any extra content from parent (story text, photos of worksheets)
5. Generate HTML using the appropriate template
6. Run `scripts/validate_game.py` — check:
   - All answer indices within options range
   - No duplicate questions
   - No apostrophe issues breaking JS strings
   - All DOM IDs exist in HTML
   - Correct answer is actually in the options array
7. Show parent for content verification — **PARENT MUST CONFIRM before publishing**
8. `git add . && git commit -m "add {filename}" && git push`
9. Update relevant Notion page table with new game link

---

## Notion Pages to Update After Every Game

| Subject | Notion Page ID |
|---------|----------------|
| Reading | 330549e1b6fd81c1afe1d559b1356392 |
| Vocabulary | 330549e1b6fd81078e71ff99b88d9b77 |
| Phonics | 330549e1b6fd813796a2ce42bbc51fc9 |
| Grammar | 330549e1b6fd810bb5f3dfe91f431957 |
| CET Vocab | 330549e1b6fd81a597c8d9822df5ee01 |
| Wrong answers | 330549e1b6fd81088a52c4c1285ded59 |
