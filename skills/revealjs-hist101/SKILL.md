---
name: revealjs-hist102
description: Create Reveal.js presentation decks specifically designed for HIST 101 and HIST 102 community college history courses. Use when the user needs to create interactive HTML slide presentations for teaching U.S. history topics including Colonial era, Revolution, Early Republic, Antebellum period, Civil War, Reconstruction, Gilded Age, Progressive Era, and 20th century. Optimized for HD TV display (16:9), small classroom settings (4 rows), with high-contrast design using Pantone 2026 Atmospheric color palette. Always includes presenter notes plugin, interactive pop-ups, image placeholders with search terms, and student-facing educational notes.
---

# Reveal.js for HIST 101/102

Create professional, interactive Reveal.js presentations tailored for community college U.S. history survey courses.

## Design Specifications

### Display & Format
- **Aspect ratio**: 16:9 (optimized for HD TV)
- **Classroom size**: Small (4 rows), allows slightly smaller fonts than standard
- **Navigation**: Horizontal slides only (no vertical slides)
- **Output**: Single standalone HTML file with CDN links

### Color Palette (Pantone 2026 Atmospheric Harmonies)

Based on the Pantone Color of the Year 2026 "Cloud Dancer" and its Atmospheric palette. This palette evokes "misty skies, breezy blues, and deep watery greens" with a mood that is "uplifting, ethereal, and introspective."

**Primary Colors:**
- **Cloud Dancer** (billowy white): `#F0EEE9` - Headers, highlighted text, key terms
- **Pale Sunlight** (misted yellow): `#E8DFB8` - Warm accents, quotes, attention items
- **Atmospheric Slate** (dark blue-gray): `#2A3540` - Primary background

**Accent Colors:**
- **Misty Sky** (soft gray-blue): `#B8C5D0` - Secondary text, subtle highlights
- **Sterling Blue** (deeper atmospheric blue): `#6B8FAD` - Interactive elements, links
- **Quiet Wave** (oceanic blue-green): `#5D8A8C` - Secondary accent, borders
- **Aventurine** (deep teal-green): `#4A7C72` - Key terms, important concepts

**Supporting Colors:**
- **Morning Mist** (warm gray): `#C5C0B8` - Captions, attribution text
- **Deep Current** (dark teal): `#2D4A4A` - Pop-up backgrounds, contrast elements

**Background Strategy**: Use dark Atmospheric Slate `#2A3540` as the primary background. This reduces eye strain on HDTV displays, provides excellent contrast, and allows Cloud Dancer and accent colors to "glow" as the visual focus. The dark background evokes the "breaking through gray skies" feeling of the Atmospheric palette.

### Typography
- **Headers**: Bold sans-serif (Montserrat or similar from CDN), size range 2.5em-3.5em for h1, 1.8em-2.2em for h2
- **Body text**: Clean sans-serif (Open Sans or similar from CDN), size range 1.1em-1.3em
- **Captions**: Italic, 0.9em-1em
- **Line height**: 1.4-1.6 for readability

## Required Plugins

Always include these Reveal.js plugins:
```html
<script src="https://cdn.jsdelivr.net/npm/reveal.js@5/plugin/notes/notes.js"></script>
<script src="https://cdn.jsdelivr.net/npm/reveal.js@5/plugin/highlight/highlight.js"></script>
<script src="https://cdn.jsdelivr.net/npm/reveal.js@5/plugin/zoom/zoom.js"></script>
```

Configure plugins in initialization:
```javascript
Reveal.initialize({
    plugins: [ RevealNotes, RevealHighlight, RevealZoom ],
    // ... other config
});
```

## Standard HTML Structure

Create a complete standalone HTML file with this structure:

```html
<!doctype html>
<html lang="en">
<head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>[Lecture Topic] - HIST 101</title>
    
    <!-- Reveal.js CSS from CDN -->
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/reveal.js@5/dist/reveal.css">
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/reveal.js@5/dist/theme/black.css">
    
    <!-- Google Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@700&family=Open+Sans:wght@400;600&display=swap" rel="stylesheet">
    
    <style>
        /* Custom styling goes here - see Styling Patterns section */
    </style>
</head>
<body>
    <div class="reveal">
        <div class="slides">
            <!-- Slides go here -->
        </div>
    </div>
    
    <!-- Reveal.js and plugins from CDN -->
    <script src="https://cdn.jsdelivr.net/npm/reveal.js@5/dist/reveal.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/reveal.js@5/plugin/notes/notes.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/reveal.js@5/plugin/highlight/highlight.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/reveal.js@5/plugin/zoom/zoom.js"></script>
    
    <script>
        Reveal.initialize({
            width: 1920,
            height: 1080,
            margin: 0.1,
            minScale: 0.2,
            maxScale: 2.0,
            controls: true,
            progress: true,
            center: true,
            hash: true,
            transition: 'slide',
            plugins: [ RevealNotes, RevealHighlight, RevealZoom ]
        });
    </script>
</body>
</html>
```

## Styling Patterns

### Custom CSS Template
Include this CSS in the `<style>` block with customizations:

```css
:root {
    /* Pantone 2026 Atmospheric Palette */
    --cloud-dancer: #F0EEE9;
    --pale-sunlight: #E8DFB8;
    --atmospheric-slate: #2A3540;
    --misty-sky: #B8C5D0;
    --sterling-blue: #6B8FAD;
    --quiet-wave: #5D8A8C;
    --aventurine: #4A7C72;
    --morning-mist: #C5C0B8;
    --deep-current: #2D4A4A;
}

.reveal {
    font-family: 'Open Sans', sans-serif;
    font-size: 32px;
    background-color: var(--atmospheric-slate);
}

.reveal .slides section {
    color: var(--cloud-dancer);
}

.reveal h1, .reveal h2, .reveal h3 {
    font-family: 'Montserrat', sans-serif;
    font-weight: 700;
    color: var(--cloud-dancer);
    text-transform: none;
    text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
}

.reveal h1 { font-size: 3em; }
.reveal h2 { font-size: 2em; color: var(--pale-sunlight); }
.reveal h3 { font-size: 1.5em; color: var(--misty-sky); }

.reveal p, .reveal li {
    color: var(--cloud-dancer);
}

.reveal a {
    color: var(--sterling-blue);
    text-decoration: underline;
}

.reveal a:hover {
    color: var(--pale-sunlight);
}

/* Pop-up/Modal styling */
.popup {
    display: none;
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    background: var(--deep-current);
    color: var(--cloud-dancer);
    padding: 2em;
    border-radius: 15px;
    box-shadow: 0 10px 40px rgba(0,0,0,0.5);
    max-width: 70%;
    max-height: 70%;
    overflow-y: auto;
    z-index: 1000;
    border: 3px solid var(--quiet-wave);
}

.popup.active { display: block; }

.popup h3 {
    color: var(--pale-sunlight);
    margin-top: 0;
}

.popup-close {
    position: absolute;
    top: 10px;
    right: 20px;
    font-size: 2em;
    cursor: pointer;
    color: var(--misty-sky);
}

.popup-close:hover {
    color: var(--cloud-dancer);
}

.popup-trigger {
    color: var(--sterling-blue);
    text-decoration: underline dotted;
    cursor: pointer;
    border-bottom: 2px dotted var(--sterling-blue);
}

.popup-trigger:hover {
    color: var(--pale-sunlight);
    border-bottom-color: var(--pale-sunlight);
}

/* Image placeholder styling */
.img-placeholder {
    background: var(--deep-current);
    border: 3px dashed var(--quiet-wave);
    padding: 3em;
    text-align: center;
    color: var(--misty-sky);
    font-style: italic;
    border-radius: 10px;
}

/* Key term styling */
.key-term {
    color: var(--aventurine);
    font-weight: 600;
    text-shadow: 1px 1px 2px rgba(0,0,0,0.3);
}

/* Primary source styling */
.primary-source {
    background: rgba(232, 223, 184, 0.15);
    border-left: 5px solid var(--pale-sunlight);
    padding: 1em;
    margin: 1em 0;
    font-style: italic;
    color: var(--cloud-dancer);
}

.primary-source-attribution {
    text-align: right;
    font-size: 0.9em;
    color: var(--morning-mist);
    margin-top: 0.5em;
    font-style: normal;
}

/* Timeline styling */
.timeline-item {
    display: flex;
    align-items: center;
    margin: 0.8em 0;
    padding: 0.5em;
    border-left: 4px solid var(--sterling-blue);
    background: rgba(107, 143, 173, 0.1);
}

.timeline-date {
    color: var(--pale-sunlight);
    font-weight: bold;
    min-width: 120px;
}

/* Historian quote styling */
.historian-quote {
    border-left: 5px solid var(--quiet-wave);
    padding-left: 1.5em;
    font-style: italic;
    color: var(--misty-sky);
}

.historian-attribution {
    text-align: right;
    font-size: 0.9em;
    color: var(--morning-mist);
    margin-top: 0.5em;
}

/* Comparison boxes */
.comparison-box {
    border: 3px solid var(--quiet-wave);
    padding: 1.5em;
    border-radius: 10px;
    background: rgba(93, 138, 140, 0.1);
}

.comparison-box.alt {
    border-color: var(--sterling-blue);
    background: rgba(107, 143, 173, 0.1);
}

/* Section divider styling */
.section-divider {
    background: linear-gradient(135deg, var(--deep-current) 0%, var(--atmospheric-slate) 100%);
}

.section-divider h2 {
    color: var(--cloud-dancer);
    font-size: 2.5em;
}

/* Assessment/quiz styling */
.assessment-box {
    background: var(--deep-current);
    border: 2px solid var(--aventurine);
    border-radius: 10px;
    padding: 1.5em;
    margin: 1em 0;
}

.assessment-box h3 {
    color: var(--aventurine);
    margin-top: 0;
}

/* Emphasis/callout box */
.callout {
    background: rgba(232, 223, 184, 0.1);
    border: 2px solid var(--pale-sunlight);
    border-radius: 8px;
    padding: 1em;
    margin: 1em 0;
}

.callout-title {
    color: var(--pale-sunlight);
    font-weight: bold;
    margin-bottom: 0.5em;
}

/* Progress/slide counter styling */
.reveal .progress {
    background: var(--deep-current);
}

.reveal .progress span {
    background: var(--sterling-blue);
}
```

## Interactive Pop-ups

Create clickable terms that open detailed pop-ups:

```html
<section>
    <h2>The Second Great Awakening</h2>
    <p>The <span class="popup-trigger" onclick="togglePopup('awakening-popup')">Second Great Awakening</span> 
    transformed American religious life.</p>
    
    <div id="awakening-popup" class="popup">
        <span class="popup-close" onclick="togglePopup('awakening-popup')">&times;</span>
        <h3>Second Great Awakening (1790s-1840s)</h3>
        <p>A Protestant religious revival that emphasized personal salvation, emotional worship, 
        and social reform. Key features included:</p>
        <ul>
            <li>Camp meetings and revival gatherings</li>
            <li>Democratization of religion</li>
            <li>Rise of new denominations (Methodists, Baptists)</li>
            <li>Connection to reform movements</li>
        </ul>
    </div>
</section>

<script>
    function togglePopup(id) {
        document.getElementById(id).classList.toggle('active');
    }
    
    // Close popup when clicking outside
    document.addEventListener('click', function(e) {
        if (e.target.classList.contains('popup')) {
            e.target.classList.remove('active');
        }
    });
    
    // Close popup with Escape key
    document.addEventListener('keydown', function(e) {
        if (e.key === 'Escape') {
            document.querySelectorAll('.popup.active').forEach(p => p.classList.remove('active'));
        }
    });
</script>
```

## Image Placeholders

Always create descriptive placeholders with search terms:

```html
<div class="img-placeholder" style="width: 800px; height: 600px; margin: 1em auto;">
    <strong>IMAGE PLACEHOLDER</strong><br>
    <em>Dimensions: 800x600px</em><br><br>
    <strong>Search terms:</strong> "Seneca Falls Convention 1848 historical photograph"<br>
    "Elizabeth Cady Stanton women's rights convention"<br><br>
    <strong>Suggested sources:</strong> Library of Congress, National Archives
</div>
```

## Student-Facing Presenter Notes

Create comprehensive, friendly notes in `<aside class="notes">` tags:

```html
<aside class="notes">
    <h4>📚 What You Need to Know</h4>
    <p>The Market Revolution transformed how Americans worked and lived. Think of it as the 
    1800s version of the Internet Revolution - it changed EVERYTHING about daily life.</p>
    
    <h4>📖 Key Definitions</h4>
    <ul>
        <li><strong>Market Revolution</strong>: The shift from a self-sufficient agricultural 
        economy to a market-based economy where people bought and sold goods</li>
        <li><strong>Transportation Revolution</strong>: Building of canals, roads, and 
        railroads that connected regions</li>
    </ul>
    
    <h4>💭 Context & Connections</h4>
    <p>This happened roughly 1815-1860. Before this, most Americans lived on farms and made 
    most of what they needed. After, they worked for wages and bought goods at stores. 
    This connects to: industrialization, urbanization, immigration, and slavery expansion.</p>
    
    <h4>🎓 Senior Historians' Corner</h4>
    <p><strong>Charles Sellers</strong> argues the Market Revolution created deep anxieties 
    about losing independence and traditional ways of life. <strong>Daniel Walker Howe</strong> 
    emphasizes how new communication technologies (like the telegraph) changed American culture. 
    These historians debate whether the changes were mostly positive (progress, opportunity) 
    or negative (exploitation, inequality).</p>
    
    <h4>🤔 Discussion Prompts</h4>
    <ul>
        <li>How would your daily life be different without a market economy?</li>
        <li>What modern technology has had a similar transformative effect?</li>
    </ul>
</aside>
```

## Special Slide Layouts for History

### Timeline Slide
```html
<section>
    <h2>Road to Civil War Timeline</h2>
    <div class="timeline-item">
        <span class="timeline-date">1820</span>
        <span>Missouri Compromise - Attempts to balance free/slave states</span>
    </div>
    <div class="timeline-item">
        <span class="timeline-date">1850</span>
        <span>Compromise of 1850 - Includes Fugitive Slave Act</span>
    </div>
    <div class="timeline-item">
        <span class="timeline-date">1854</span>
        <span>Kansas-Nebraska Act - Popular sovereignty leads to violence</span>
    </div>
</section>
```

### Primary Source Slide
```html
<section>
    <h2>Frederick Douglass on Slavery</h2>
    <div class="primary-source">
        "I have often been utterly astonished, since I came to the north, to find persons 
        who could speak of the singing, among slaves, as evidence of their contentment 
        and happiness. It is impossible to conceive of a greater mistake."
        <div class="primary-source-attribution">
            — <em>Narrative of the Life of Frederick Douglass</em>, 1845
        </div>
    </div>
</section>
```

### Comparison Slide (Before/After or Two Systems)
```html
<section>
    <h2>Two Prison Systems Compared</h2>
    <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 2em;">
        <div class="comparison-box">
            <h3>Auburn System</h3>
            <ul>
                <li>Silent congregation</li>
                <li>Work in groups</li>
                <li>Night isolation</li>
                <li>Cost effective</li>
            </ul>
        </div>
        <div class="comparison-box alt">
            <h3>Pennsylvania System</h3>
            <ul>
                <li>Complete isolation</li>
                <li>Individual cells</li>
                <li>24/7 solitude</li>
                <li>Expensive</li>
            </ul>
        </div>
    </div>
</section>
```

### Biographical Info Box
```html
<section>
    <h2>Harriet Tubman</h2>
    <div style="display: flex; gap: 2em; align-items: start;">
        <div class="img-placeholder" style="width: 400px; height: 500px; flex-shrink: 0;">
            <strong>IMAGE PLACEHOLDER</strong><br>
            <em>400x500px portrait</em><br><br>
            <strong>Search:</strong> "Harriet Tubman portrait photograph"<br>
            "Harriet Tubman carte de visite"
        </div>
        <div style="text-align: left;">
            <p><strong style="color: var(--pale-sunlight);">Born:</strong> c. 1822, Dorchester County, Maryland</p>
            <p><strong style="color: var(--pale-sunlight);">Key Role:</strong> Underground Railroad conductor, Union spy, 
            abolitionist, women's rights activist</p>
            <p><strong style="color: var(--pale-sunlight);">Major Achievement:</strong> Made 13 missions to rescue ~70 enslaved people</p>
            <p class="key-term">"I never ran my train off the track, and I never lost a passenger."</p>
        </div>
    </div>
</section>
```

### Section Divider Slide
```html
<section class="section-divider" data-background="linear-gradient(135deg, #2D4A4A 0%, #2A3540 100%)">
    <h2>Part II</h2>
    <h3 style="color: var(--misty-sky);">The Counterrevolution</h3>
    <p style="color: var(--morning-mist); font-style: italic;">Why violence succeeded in overthrowing Reconstruction</p>
</section>
```

### Assessment Break Slide
```html
<section>
    <h2>📝 Check Your Understanding</h2>
    <div class="assessment-box">
        <h3>Quick Question</h3>
        <p>Which organization was primarily responsible for placing Confederate monuments 
        in Southern courthouse squares during the 1890s-1920s?</p>
        <ol style="list-style-type: upper-alpha;">
            <li>United Confederate Veterans (UCV)</li>
            <li>United Daughters of the Confederacy (UDC)</li>
            <li>Sons of Confederate Veterans (SCV)</li>
            <li>Ku Klux Klan</li>
        </ol>
    </div>
    <aside class="notes">
        <p><strong>Answer: B</strong> - The UDC was the primary organization behind the first wave 
        of Confederate monument construction, particularly in prominent public spaces.</p>
    </aside>
</section>
```

### Callout/Emphasis Box
```html
<section>
    <h2>Key Insight</h2>
    <div class="callout">
        <div class="callout-title">🔑 Why This Matters</div>
        <p>The timing of Confederate monument construction—peaking during Jim Crow, 
        not immediately after the war—reveals their true purpose: reinforcing white 
        supremacy during a period of active racial oppression.</p>
    </div>
</section>
```

## Output Instructions

1. **Always create a complete, functional HTML file** that can be opened directly in a browser
2. **Use CDN links** for all Reveal.js resources (CSS, JS, plugins)
3. **Include comprehensive presenter notes** for every substantive slide
4. **Create descriptive image placeholders** with specific search terms
5. **Use pop-ups liberally** for terms, concepts, or additional context
6. **Apply the Pantone 2026 Atmospheric palette** consistently throughout
7. **Maintain high contrast** for classroom visibility (dark background, light text)
8. **Keep slides uncluttered** - use pop-ups for detail rather than cramming content

## Best Practices

- **One main idea per slide** - use pop-ups for elaboration
- **Large, clear fonts** - remember the 4-row classroom
- **Strong color contrast** - Cloud Dancer text on Atmospheric Slate background
- **Interactive elements** - make learning engaging with clickable terms
- **Student-centered notes** - write for your students, not yourself
- **Visual hierarchy** - use Pale Sunlight for h2, Aventurine for key terms
- **Historical accuracy** - cite sources in notes when referencing scholars
- **Accessibility** - the blue-green palette works well for most colorblind students
- **Dark background** - reduces eye strain on HDTV displays during 50-minute lectures

## Color Usage Quick Reference

| Element | Color | Hex |
|---------|-------|-----|
| Background | Atmospheric Slate | `#2A3540` |
| H1 Headers | Cloud Dancer | `#F0EEE9` |
| H2 Headers | Pale Sunlight | `#E8DFB8` |
| H3 Headers | Misty Sky | `#B8C5D0` |
| Body Text | Cloud Dancer | `#F0EEE9` |
| Key Terms | Aventurine | `#4A7C72` |
| Links/Interactive | Sterling Blue | `#6B8FAD` |
| Borders/Accents | Quiet Wave | `#5D8A8C` |
| Quotes/Emphasis | Pale Sunlight | `#E8DFB8` |
| Captions/Attribution | Morning Mist | `#C5C0B8` |
| Pop-up Background | Deep Current | `#2D4A4A` |
