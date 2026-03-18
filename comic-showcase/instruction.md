# Build: "Behind the Panels" — An Interactive Walkthrough of a Hankweave Comic Run

## What This Is

An interactive single-page experience that tells the story of how an AI pipeline (Hankweave) created a comic book called "Not Yet" — a story weaving Asimov's "The Last Question," Clarke's "The Nine Billion Names of God," and Hankweave itself, told through Epoch the Tortoise-Hourglass.

The goal: use this comic creation process to build intuitive understanding of Hankweave. People should walk away understanding codons, pipelines, and why structured AI work produces something a single prompt never could.

## THE CRITICAL DESIGN ELEMENT: Epoch Narrates in First Person

**This is the most important design decision.** Epoch — the tortoise from the comic — narrates the entire page in first person. Epoch is telling the reader about its own creation. This creates a beautiful recursive loop: the character explains how it came to exist.

Epoch's voice is: contemplative, occasionally wry, deeply patient, surprisingly self-aware. Example narrations (USE THESE or write similarly):

**On being created:** "I was Option B. Before I had a name, before I had this shell, I was a paragraph on a page: 'An ancient tortoise whose shell is a living hourglass.' There were others."

**On the diversity review:** "They asked a child what they thought of me. 'Almost all of it is boring. The tortoise walks a lot and doesn't DO anything.' Fair."

**On being selected:** "I was chosen — but not as I was. The selection codon didn't pick a winner. It performed surgery. From Kavi, they took the thread mechanic. From Tally, they took doubt."

**On the 3 AM codon:** "This is the strip where the pipeline itself becomes the story. A checkpoint saved at 2:47 AM. Not every act of faith needs a witness."

**On the ending:** "Not yet. Not yet. Not yet. ...Now. The pipeline is patient. It checkpoints. It recovers. It keeps going while you sleep."

### Epoch's Narration Styling

Epoch's narrations should be styled as **aged parchment paper letters** — like a handwritten note from a very old, very patient being. Specifically:

```css
/* The letter container */
background: repeating-linear-gradient(0deg, transparent, transparent 31px, rgba(140,110,80,0.1) 31px, rgba(140,110,80,0.1) 32px),
  linear-gradient(170deg, #d4c8ac 0%, #ddd0b4 15%, #d0c4a8 35%, #d8ccb0 55%, #ccc0a4 75%, #d4c8ac 100%);
border-radius: 3px;
box-shadow: 3px 4px 14px rgba(0,0,0,0.4);
color: #2c1e10;

/* The text inside */
font-family: 'Caveat', cursive; /* or any handwriting-style web font */
font-size: 17px;
line-height: 1.65;

/* Sign-off at the bottom */
"— Epoch" with a small hourglass icon
```

This aged-paper style MUST contrast sharply with the dark cosmos background of the rest of the page. Light parchment on dark space. The letters feel physical, real, warm — like finding a note left by someone ancient.

## Layout

### Left Rail (Fixed, ~200-220px)
A vertical pipeline roadmap showing the codons. Each node:
- Small dot/circle (amber when active, dim when not)
- Codon name in monospace
- Cost in small text
- Connected by a thin amber line

Group into phases:
- **Discovery** (read-and-explore, story-diversity)
- **Design** (visualize-candidates, select-merge-spec, story-review)
- **Creation** (generate-and-review ×3 — shown as a loop with a border)
- **Quality** (comic-review, post-processing)

Scroll-spy highlights current section. Clicking scrolls.

### Main Content Area

Each section has:

**Evidence panel (left/top ~60%):** The tangible output — images, quotes, event logs, codon diagrams
**Epoch's letter (right/bottom ~40%):** The narration in aged-paper style

### Key Visual Components to Build

**1. Event Log Terminal** — a dark green-tinted monospace block showing timestamped events:
```
16:17:16  codon.started     read-and-explore
16:17:18  rig.completed     2 commands in 225ms
16:22:10  file.created      workspace/reading-journal.md
16:31:51  codon.completed   49 messages, 2.6M cached    $10.96
```
Use green for event types, dim for timestamps, amber for costs, highlight for important events.

**2. Artifact Blocks** — styled file viewers with a header showing filename:
```
┌─ ◇ reading-journal.md ──────────────────────┐
│ "Without any fuss." That's the killer phrase.│
│ Not with thunder and fire and apocalypse.    │
│ Without any fuss.                            │
└──────────────────────────────────────────────┘
```
Dark background, subtle border, monospace filename header.

**3. Codon Boundary Diagrams** — showing what each codon reads and writes:
```
┌─ read-and-explore ─────────── opus 4.6 ──┐
│ READS                  WRITES             │
│ ← ideas.md            → reading-journal.md│
│ ← inspiration/*.png   → candidates/       │
│ ← lastQuestion.pdf    → nano-references/  │
│                                           │
│ RIGS              CHECKPOINTS             │
│ $ copy scripts/   # rig-setup #60f3e8e   │
│ $ check-deps.ts   # completed #3ed99ab   │
└───────────────────────────────────────────┘
```

**4. Stat Callouts** — small boxes with key numbers:
```
[Model: Haiku 4.5] [Cost: $0.09] [Key insight: "Dumber" models catch different things]
```

**5. Character Cards** — small image + name + description for the three candidates

**6. Starfield Background** — subtle CSS-only animated stars on the dark background. Tiny white dots that drift slowly upward. Very subtle, not distracting.

## Content Flow

### 0. Hero
Full-width. Comic cover image, large. Title: "Behind the Panels." Subtitle: "How a Hankweave pipeline turned 20 lines of instruction into a 12-page comic about patience, entropy, and the act of continuing."

Below the cover: the entire original input (20 lines of ideas.md) — showing the absurd contrast between input and output.

### 1. The Spark / Read & Explore (read-and-explore, Opus, $10.96, 15min)
**Evidence:** Event log showing the reading sequence. The thematic connections table from the reading journal. Visual reference images (Lotte Reiniger silhouettes). Key quotes from the journal.
**Epoch:** "The first codon was given one instruction: read everything deeply. Not skim. Live inside the stories."

### 2. Three Souls Born (same codon, but a separate visual section)
**Evidence:** The three character images side by side — Kavi, Epoch, Tally. Brief descriptions.
**Epoch:** "I was Option B. Before I had a name..."

### 3. The Diversity Test (story-diversity, Haiku, $0.09, 1min)
**Evidence:** The 8-year-old's review and the tired engineer's review as artifact blocks.
**Epoch:** "They asked a child what they thought of me..."

### 4. Visual Audition (visualize-candidates, Opus, $1.19, 5min)
**Evidence:** Character sample images compared to Reiniger references. The visual review's verdict.
**Epoch:** About the rig generating images BEFORE the agent — "deterministic setup, then judgment."

### 5. The Selection (select-merge-spec, Opus, $7.76, 13min)
**Evidence:** Key quotes from merged.md. The surgery: what was borrowed from each character/story.
**Epoch:** "I was chosen — but not as I was. The selection codon didn't pick a winner. It performed surgery."

### 6. Story Review (story-review, Opus, $6.76, 12min)
**Evidence:** The emotional blueprint — palette progression per strip. Story structure diagram.
**Epoch:** About fresh eyes — "Every codon starts with a clean context."

### 7. The Generation Loop (generate-and-review ×3, Opus, $23.71, 71min)
**Evidence:** Show 3-4 of the best panels. The loop iteration data. What was flagged vs approved.
**Epoch:** "Three passes. Each time, fresh eyes reviewing what fresh hands had made."

### 8. The Cold Read (comic-review, Opus, $1.49, 3min)
**Evidence:** Review grades per strip. Panel 4 getting A+ ("the emotional core"). Caught issues.
**Epoch:** "A fresh reader who has never seen the spec reads the comic cold."

### 9. Post-Processing (post-processing, Sonnet, $0.62, 3min)
**Evidence:** The rerun package concept. Final panel assembly.
**Epoch:** "The cheapest codon. $0.62. Not everything needs Opus."

### 10. Closing
Full-width. Show all panels in a grid or filmstrip. The final line: "Not yet. Not yet. Not yet. ...Now."
Final Epoch letter tying it all together.

## Aesthetic

### Color Palette (Dark Cosmos)
- **Background:** Deep midnight blue-black (`hsl(238, 48%, 8%)`)
- **Surface:** Slightly lighter cosmic blue (`hsl(240, 35%, 16%)`)
- **Text:** Warm off-white starlight (`hsl(38, 25%, 88%)`)
- **Secondary text:** Muted warm gray (`hsl(38, 20%, 68%)`)
- **Accent:** Amber/gold (`hsl(38, 90%, 55%)`) — Epoch's shell color
- **Event log green:** Muted terminal green for event logs
- **Borders:** Very subtle white at 6-8% opacity

This is a DARK page. The comic panels and Epoch's parchment letters are the only bright elements. Everything else recedes.

### Typography
- **Headings:** A clean sans-serif (system font is fine)
- **Body:** A readable serif for longer text
- **Monospace:** For event logs, codon IDs, technical details
- **Handwriting:** For Epoch's narration (Google Fonts: Caveat, or similar)

### Images
- All images are in context/panels/ (JPG, ~500KB each), context/characters/, context/references/
- Base64 embed them into the HTML for self-containment
- Give panels generous padding and subtle rounded corners
- Panels should feel like they're floating on the dark background

## Technical Notes

- Single self-contained HTML file with embedded images, fonts (use Google Fonts CDN for the handwriting font), and all CSS/JS inline
- Smooth scroll-spy for the left rail
- CSS-only starfield animation (radial gradients with slow translateY drift)
- Responsive: on mobile, rail collapses to horizontal sticky nav, two-column stacks to single column
- Sections should fade in on scroll (IntersectionObserver + CSS transitions)
- The event logs and artifact blocks are the technical grounding. They make this feel real, not marketing.
