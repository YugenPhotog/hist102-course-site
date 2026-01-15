---
name: podium-notes
description: Generate printable podium notes from Reveal.js presentations or lecture materials. Use when the user needs teaching notes for classroom delivery—abbreviated explanations with hard-to-memorize content like quotations, statistics, dates, names, and key interpretations. Creates DOCX files formatted for Google Drive upload and printing (14pt font, one page per slide section).
---

# Podium Notes Generator

Create abbreviated lecture notes from Reveal.js presentations or lecture materials. These notes help instructors remember hard-to-memorize content during classroom delivery.

## Output Format

Generate a DOCX file with:
- **14pt Arial font** for body text
- **14pt Arial bold** for titles
- **One page per `<section>`** with page breaks between
- **1-inch margins** on all sides
- Separator line after each title: `────────────────────────────────────────`
- Optimized for Google Drive upload and printing

## Content Structure Per Slide

Each `<section>` in the Reveal.js presentation gets its own page. Sections appear in this order:

### 1. Slide Title (Bold, 14pt)
Use the **verbatim title** from the slide (h1, h2, or h3 text)

### 2. Separator Line
`────────────────────────────────────────`

### 3. KEY POINTS (Bold header, 14pt) — ALWAYS PRESENT
Abbreviated lecture notes extracted from `<aside class="notes">`:
- Focus on sentences with dates, names, statistics, quotations
- Keep 5-8 key sentences maximum
- Present as bullet points (•) if multiple sentences
- Prioritize hard-to-remember specifics over general explanations

**Style:** Extract what you'd actually need to glance at while teaching—specific dates, names, key interpretations.

### 4. QUOTATIONS (Bold header, 14pt) — ONLY IF CONTENT EXISTS
Use LLM knowledge to supplement with genuine quotations:
- **Primary sources**: Actual quotes from historical figures, religious texts, or primary documents relevant to the slide topic
- **Scholars**: Actual quotes from academics who've studied this topic
- **Attribution required**: Every quote must have clear source (person, book, year if known)
- **Never fabricate**: If no genuine quotes are known, **omit this section entirely**
- Format as italicized text with attribution
- Do NOT include: teaching examples, illustrative phrases, generic commentary

**Important**: Do NOT include a QUOTATIONS section with "[none for this slide]" — simply omit the section if no quotations exist.

### 5. SCHOLAR'S CORNER (Bold header, 14pt) — ONLY IF CONTENT EXISTS
Use LLM knowledge to provide scholarly context:
- **Real scholarship**: Cite actual scholars and their arguments about the topic
- **Specific claims**: Reference books, interpretive frameworks, historiographical/theoretical debates
- **Attribution required**: Name the scholar and ideally their work
- **Never fabricate**: If no genuine scholarship is known, **omit this section entirely**
- Present as bullet points (•)
- Maximum 3-4 key scholarly points

### 6. NOTES (Bold header, 14pt) — ALWAYS PRESENT
Provide space for handwritten notes during lecture delivery:
- Header: "NOTES" in bold
- 5 grey lines for handwriting (approximately 50 underscores each)
- Line color: Light grey (#CCCCCC)
- Line spacing: adequate for handwriting between lines

## Implementation Approach

This skill requires a two-phase approach:

### Phase 1: Extract Structure from HTML
Use Node.js with `cheerio` to parse the Reveal.js presentation:

```javascript
const cheerio = require('cheerio');

// Parse HTML to extract sections
$('.reveal .slides section').each(function() {
    // Get title from h1, h2, or h3
    // Extract notes from <aside class="notes">
    // Extract visible slide content
});
```

### Phase 2: LLM Supplementation
For each slide, use the LLM to:

1. **Analyze the slide topic** from title and content
2. **Recall genuine quotations** from primary sources or scholars
3. **Recall scholarly commentary** from actual academics/books
4. **Format with proper attribution** or omit section if none known

**Critical**: The LLM must never fabricate quotes or scholarship. If uncertain, omit rather than invent.

### Combined Workflow
```javascript
// 1. Extract slide structure
const slides = extractFromHTML(htmlFile);

// 2. For each slide, construct prompt for LLM:
const prompt = `
Given this slide:
Title: "${slide.title}"
Content: "${slide.content}"
Notes: "${slide.notes}"

Provide:
1. Key points (abbreviated, focusing on dates/names/stats)
2. Genuine quotations with attribution (or omit if none)
3. Actual scholar commentary with attribution (or omit if none)

Never fabricate quotes or scholarship.
`;

// 3. Generate DOCX with combined content
```

## Processing Steps

1. **Load Reveal.js HTML** using cheerio
2. **Iterate each `<section>`** element
3. **Extract title** from first h1/h2/h3 found
4. **Extract notes** from `<aside class="notes">`, if present
5. **Extract visible content** from slide paragraphs/lists
6. **For each slide, use LLM to generate**:
   - **KEY POINTS**: Abbreviate notes focusing on dates, names, stats, hard-to-remember specifics (5-8 points max)
   - **QUOTATIONS**: Recall genuine quotes relevant to topic, with attribution. If none known: omit section
   - **SCHOLAR'S CORNER**: Recall actual scholarship on topic with citations. If none known: omit section
7. **Generate page**: Title → separator → KEY POINTS → QUOTATIONS (if applicable) → SCHOLAR'S CORNER (if applicable) → NOTES with grey lines
8. **Page break** before next section

## LLM Supplementation Guidelines

When generating QUOTATIONS:
- Search knowledge for primary sources related to slide topic
- Include full attribution (speaker, context, year if known)
- Prefer memorable, substantive quotes over generic phrases
- If genuinely uncertain, **omit section entirely** rather than guessing

When generating SCHOLAR'S CORNER:
- Search knowledge for actual scholars who've studied this topic
- Include specific arguments, books, interpretive frameworks
- Name the scholar and ideally their key work
- If genuinely uncertain, **omit section entirely** rather than inventing scholarship

**Never fabricate quotes or attribute statements to scholars without certainty.**

## Example Output

```
4 - The Kansas-Nebraska Act (1854)
────────────────────────────────────────

KEY POINTS
• Stephen Douglas wanted a northern route for the transcontinental railroad through Chicago (his political base).
• Southern senators wouldn't support the railroad without something in return.
• Douglas's fatal bargain: let settlers decide slavery through 'popular sovereignty.'
• This effectively repealed the Missouri Compromise of 1820.
• Douglas miscalculated Northern reaction.

QUOTATIONS
"I could travel from Boston to Chicago by the light of my own effigy." — Stephen Douglas

SCHOLAR'S CORNER
• Robert Johannsen argues Douglas genuinely believed popular sovereignty would defuse tensions.
• Older interpretation: Douglas was a mere tool of the Slave Power.

NOTES
__________________________________________________
__________________________________________________
__________________________________________________
__________________________________________________
__________________________________________________

[page break]
```

**Example without quotations (section omitted):**

```
7 - Worldview = Your Lens on Reality
────────────────────────────────────────

KEY POINTS
• WORLDVIEW: A comprehensive framework of beliefs, values, and assumptions through which you interpret all of reality
• Shaped by culture, upbringing, experiences
• No one has a 'neutral' or 'objective' view
• Everyone has a worldview—you can't NOT have one; you can only become more aware

SCHOLAR'S CORNER
• James W. Sire (The Universe Next Door) argues most people's worldviews are largely unconscious—operating in the background without awareness.

NOTES
__________________________________________________
__________________________________________________
__________________________________________________
__________________________________________________
__________________________________________________

[page break]
```

## Critical Requirements

- **Use verbatim titles** from HTML—don't create your own
- **Each `<section>` gets a page**—not each conceptual slide
- **Extract real content**—don't generate fictional content
- **Abbreviate aggressively**—focus on hard-to-remember specifics
- **Omit empty sections**—QUOTATIONS and SCHOLAR'S CORNER only appear if content exists; never include "[none for this slide]"
- **Always include NOTES**—every page gets the grey-line notes section at the bottom
- **14pt font throughout**—not 32pt or other sizes
- **Grey lines for NOTES**—use #CCCCCC color, approximately 50 underscores per line
