# Brand and visual decision guide — Keynote presentation engine

Governs every visual decision in Will's decks. Use this to resolve ambiguity on color, typography, layout, icon use, chart type selection, and when to apply client branding vs. Will's defaults.

---

## When to use which palette

### Will's default executive palette
Apply when: No client brand is specified, or this is a thought leadership / speaking deck.

| Role | Name | Hex | Use |
|------|------|-----|-----|
| Dark background | Midnight navy | `1E2761` | Title, divider, close slides |
| Light background | White | `FFFFFF` | Content slides |
| Content card fill | Ice gray | `F4F6FB` | Card backgrounds, table alternates |
| Primary accent | Coral | `F96167` | CTAs, data highlights, risk flags |
| Secondary accent | Teal | `028090` | Icons, chart bars, phase labels |
| Tertiary accent | Gold | `C9A84C` | Business case stats, dollar figures |
| Success/positive | Green | `2A9D8F` | Passing scores, positive outcomes |
| Warning/medium | Amber | `F4A261` | Medium-risk items, caution signals |
| Text on dark | White | `FFFFFF` | All body and heading text on dark slides |
| Text on light | Charcoal | `2D2D2D` | Body text on white/light slides |
| Muted text | Mid-gray | `666666` | Captions, attribution, footnotes |
| Eyebrow/accent text on dark | Ice blue | `CADCFC` | Spaced-caps eyebrow lines on dark slides |

### Alternate palettes (for visual variety or specific deck types)

**Cherry red (documentation debt, risk-heavy executive briefings)**
- Primary dark: `990011` (cherry)
- Secondary dark: `21295C` (navy)
- Accent: `C9A84C` (gold)
- Light bg: `FCF6F5` (off-white)
- Use for: High-stakes risk decks where urgency needs to be felt visually

**Teal trust (services pitch, AI readiness, content ops)**
- Primary dark: `021F30` (deep navy)
- Accent 1: `028090` (teal)
- Accent 2: `02C39A` (mint)
- Light bg: `F0F7F8` (pale teal-white)
- Use for: Services pitches and diagnostic decks where trust and competence are the visual message

**Never use these palettes**: Generic blue gradients, purple/violet schemes, warm beige defaults (`F5F5DC`, `FAF0E6`, `FAEBD7`), or any palette that would work equally well for a completely unrelated topic.

---

## Color application rules

**The executive sandwich**: Dark title slide → light content slides → dark close slide. This creates rhythm and signals premium production.

**Dominant color discipline**: One color takes 60–70% of the visual weight. Two supporting tones. One sharp accent. Never give four colors equal weight — it looks undesigned.

**Semantic color use**:
- Coral / red tones: risk, urgency, problem framing
- Green / teal tones: positive outcomes, validated scores, success metrics
- Gold / amber tones: financial figures, warnings, medium-risk items
- White on dark: authority and clarity
- Color-code consistently across the entire deck — don't use coral for risk on slide 3 and for a CTA on slide 7

**Backgrounds**:
- Dark slides: navy `1E2761` or `021F30` — never black (`000000`) unless client brand specifies
- Light slides: white `FFFFFF` — never cream or warm-toned defaults
- Card fills: `F4F6FB` or the palette-appropriate light variant

---

## Typography rules

### Default font stack

| Element | Font | Size | Weight |
|---------|------|------|--------|
| Title slide heading | Georgia | 36–54pt | Bold |
| Content slide heading | Georgia | 26–32pt | Bold |
| Section headers / card titles | Trebuchet MS | 13–18pt | Bold |
| Body text | Calibri | 12–14pt | Regular |
| Eyebrow / spaced caps | Calibri or Trebuchet MS | 10–12pt | Bold + charSpacing: 5–6 |
| Captions / attribution | Calibri | 9–11pt | Regular, muted gray |
| Stat callout number | Georgia or Calibri | 64–120pt | Bold |
| Stat label | Calibri | 14–18pt | Regular |

### Font availability check
These fonts render correctly on macOS (Keynote) and Windows (PowerPoint) without substitution:
- Georgia ✓
- Trebuchet MS ✓
- Calibri ✓ (Windows default; installed on Mac via Office)
- Cambria ✓
- Arial Black ✓ (fallback if Georgia unavailable)

If building for a client who may not have Office installed on Mac: use Georgia + Arial Black as the safe pairing.

### Font rules
- Never mix more than two font families in one deck
- Heading font must be visually distinct from body font — size alone is not enough contrast
- Eyebrow text always: uppercase + charSpacing 5–6 + smaller size (10–12pt)
- Never use italic for more than one sentence at a time — reserve italic for stat labels and attribution

---

## Layout selection guide

Use this to pick the right layout for the content type. Never use the same layout on consecutive slides.

| Content type | Best layout | Component |
|---|---|---|
| Opening impact statement | Full-bleed stat callout | Component 2 |
| Three parallel points | Three-column card grid | Component 3 |
| Sequential steps or phases | Horizontal timeline | Component 5 |
| Prioritized actions | Numbered intervention list | Component 4 |
| Scored results | Bar chart + side panel | Component 6 |
| Problem vs. cost | Two-column split | Component 7 |
| Single major insight | Full-bleed stat or quote slide | Component 2 |
| Service or capability overview | Icon grid (2x2 or 2x3) | Custom |
| Risk matrix | Color-coded table | Custom |
| Case study | Logo + three columns + stat callout | Custom |
| Comparison | Side-by-side columns | Custom |

**Layout variety enforcement**: If slides N and N+1 would use the same layout, override one. The deck should feel like it has visual momentum, not repetition.

---

## Icon usage rules

**Source**: react-icons library (Font Awesome `fa`, Material Design `md`, Heroicons `hi`, Bootstrap Icons `bi`)

**Sizing for rasterization**: Always render at 256px minimum. Display size on slide is set by `w` and `h` in inches — rasterization size determines crispness.

**Color**: Always match icon color to the accent color of its section or card. Never use default black icons on a colored background without a contrasting circle behind them.

**Icon-on-dark backgrounds**: Wrap icon in a colored circle if using on a dark slide — the icon alone will disappear.

**Icon-on-light backgrounds**: Colored icons on white/light gray backgrounds work without a wrapper circle IF the icon color has enough contrast. Test visually.

**Icon scale on slides**:
- Standalone icons (one per slide): 0.8"–1.2" display size
- Card icons (one per card in a grid): 0.4"–0.6" display size
- Inline icons (next to text): 0.3"–0.4" display size

**Icon selection**: Match icon to meaning precisely. Do not use generic icons (gears, lightbulbs, magnifying glasses) when a more specific icon is available. Examples:
- Documentation → `FaFileAlt`, `FaBook`, `FaClipboard`
- Data → `FaDatabase`, `FaTable`, `FaChartBar`
- AI/technology → `FaMicrochip`, `FaRobot`, `FaBrain`
- Risk → `FaExclamationTriangle`, `FaShieldAlt`, `FaTimesCircle`
- Success → `FaCheckCircle`, `FaStar`, `FaTrophy`
- People/talent → `FaUsers`, `FaUserCog`, `FaHandshake`

---

## Chart type selection guide

| Data type | Chart type | Notes |
|---|---|---|
| Domain scores (5 categories) | Horizontal bar | Sorted ascending or descending by score |
| Trend over time | Line chart | Smooth lines; label key inflection points |
| Part-to-whole | Pie or donut | Only if fewer than 5 segments; label segments |
| Category comparison | Vertical bar (column) | Group by category, not by series |
| Before/after single metric | Side-by-side columns | Color-code: red for before, green for after |
| Distribution | Horizontal bar or scatter | Scatter only for genuinely bivariate data |
| Maturity stages | Horizontal bar with max = 4 | Always set valAxisMaxVal: 4 for consistency |

**Chart styling rules** (apply to every chart):
- `chartColors`: Match deck palette — never use PptxGenJS defaults (generic blue)
- `chartArea`: White fill, no border, `roundedCorners: false`
- `catGridLine`: `style: "none"` — hide category grid lines
- `valGridLine`: Light gray `E0E4EE`, size 0.5 — subtle only
- `dataLabelColor`: Readable against bar color — white on dark bars, charcoal on light bars
- `showLegend`: Only if multiple series are plotted
- Axis labels: Always include units in the axis title or chart title

---

## What executive decks never contain

These are hard stops — if any of these appear, remove before delivering:

**Visual AI tells**:
- Accent underlines beneath slide titles
- Decorative full-width colored bars (header bars, footer stripes)
- Equally-weighted rainbow color palettes
- Cream or warm beige backgrounds
- Generic stock photo metaphors: handshakes, lightbulbs, puzzle pieces, gears floating in space

**Content tells**:
- "In conclusion..." as a heading
- "Thank you" as a final slide (use a CTA or a challenge instead)
- Bullet lists with more than 6 items (if you have 7+, it's two slides or a table)
- Slide titles that are topics, not claims ("AI adoption" → "Three AI adoption risks that will derail your pilot")
- Data points without sources
- Projections without stated assumptions
- Appendices that contain material that should be in the main deck

**Voice tells**:
- Em dashes used decoratively (use commas, colons, or sentence breaks)
- "Leverage" as a verb
- Vendor theater language (cutting-edge, transformative, game-changing, synergy, holistic)
- "Fractional" as Will's self-descriptor in forward-facing slides

---

## Client brand override protocol

When a client provides brand guidelines, apply in this order:

1. **Colors**: Replace Will's palette with client primary, secondary, and accent. Keep semantic mapping (risk = warm/red tone, success = green/teal tone) even if specific hex values change.
2. **Fonts**: Replace Georgia + Calibri with client-specified fonts. If client fonts are non-standard, note that Keynote may substitute on machines without the font installed.
3. **Logo placement**: Title slide only, unless client specifies all slides. Bottom-right at 0.8"–1.0" width. Do not place on dark slides unless logo has a light variant.
4. **Layout vocabulary**: Keep the same component structures — dark title, content slides, numbered lists, stat callouts. The layout is not branded; only colors, fonts, and logo are.
5. **Will's voice**: Keep. Brand guidelines govern visuals, not argument structure or editorial voice.

---

*Last updated: May 2026. Part of the Keynote Presentation Engine knowledge base.*
