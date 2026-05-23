# Keynote presentation engine

A specialized Claude Project for producing interactive, graphically rich Apple Keynote presentations that withstand executive scrutiny.

This engine turns a topic and an audience into a presentation-ready `.pptx` file (Keynote-compatible via export) and interactive HTML preview artifacts. It is built for one job: producing decks that hold up when a skeptical CIO, CFO, or board member starts asking hard questions.

---

## What it does

Every deck the engine builds has to clear three bars:

1. **Visual** — looks like a $50K agency deck, not a template fill-in.
2. **Structural** — the argument is airtight; no slide earns its place without carrying weight.
3. **Executive** — a skeptical CIO, CFO, or board member finds nothing to pick apart.

The engine enforces a verified-data discipline (no unsourced statistics), a documented voice standard (no vendor theater, no decorative em dashes), and a pre-delivery pressure test that anticipates the seven questions an executive audience will actually ask.

---

## Presentation typology

The engine recognizes the requested deck type and applies the correct architecture, slide count, and tone.

| Type | Slides | Primary audience | Win condition |
|------|--------|-----------------|---------------|
| Executive briefing | 8–12 | CIO, CFO, board | Decision or sign-off |
| Business case | 10–15 | CIO + CFO | Budget approval |
| Consulting engagement readout | 12–18 | Sponsor + stakeholders | Action plan adoption |
| Services pitch | 10–12 | Buying committee | Shortlist or PO |
| Thought leadership keynote | 20–30 | Conference audience | Authority and pipeline |
| AI readiness diagnostic | 12–16 | CIO + IT leadership | Gap acknowledgment + engagement |
| Documentation debt audit | 10–14 | CTO + content leadership | Remediation mandate |
| Content ops maturity | 12–16 | VP Content + CTO | Investment commitment |

If the deck type is not specified, the engine asks one clarifying question — who is the primary decision-maker, and what action do you need them to take — then assigns the closest type and proceeds.

---

## Workflow

The engine runs a four-stage pipeline. Each stage gates the next.

### Stage 1 — Intake

Required before any slide is written. Captures deck type, working title, primary audience, desired outcome, key argument, available evidence, brand constraints, slide count target, and any Keynote-specific features requested. If intake is thin, the engine asks for the minimum viable set: audience, outcome, and key argument.

### Stage 2 — Architecture

Before any content is drafted, the engine produces a numbered slide architecture. Each slide gets a trust job (what the audience must believe), a format, and the evidence that will carry it. Nothing proceeds to content until the architecture is confirmed.

### Stage 3 — Build

Two passes. Pass 1 drafts all slide content and speaker notes with no visuals, flagging which slides need charts, frameworks, stat callouts, proof points, comparison tables, or process flows. Pass 2 produces a precise visual specification per slide: layout, colors, fonts, the specific visual element, and speaker notes.

### Stage 4 — QA

Non-negotiable. Every slide must have a clear trust job, a visual element, and sourced data claims. The deck is checked against voice standards, the executive sandwich structure, and the seven-vector executive pressure test before it is declared done.

---

## Output formats

| Format | What you get |
|--------|--------------|
| Full deck build | A complete `.pptx` via PptxGenJS, with visual QA run before delivery |
| Interactive HTML preview | An HTML artifact rendering all slides with navigation, in the engine's color system |
| Architecture-only | The numbered slide architecture with trust jobs and evidence recommendations |
| Content-only | All slide copy and speaker notes, no visuals |
| Visual spec sheet | Per-slide layout, colors, fonts, visual element, and speaker notes for a designer |

---

## Knowledge base

The engine draws on six knowledge base files. Each governs a different dimension of deck quality.

| File | Governs |
|------|---------|
| `kb-01-proof-point-bank.md` | Biographical proof points, proprietary methodologies, and verified engagement metrics. The only approved source for credibility claims. |
| `kb-02-data-sources-statistics.md` | Every statistic cleared for use, with source, year, and usage caveats. Stats not in this file get flagged as unverified. |
| `kb-03-slide-component-library.md` | Reusable, QA'd PptxGenJS code patterns for the nine most common slide components. |
| `kb-04-audience-tone-calibration.md` | Maps each audience type (CIO, CFO, CTO, VP Content, board, conference) to the correct register, density, and risk framing. |
| `kb-05-brand-visual-guide.md` | Color palettes, typography, layout selection, icon rules, and chart type selection. |
| `kb-06-executive-pressure-test.md` | The seven attack vectors an executive audience uses, with pre-emption checklists for each. |

---

## Design standards

### Color

The default executive palette, applied unless brand constraints are provided:

| Role | Color | Hex |
|------|-------|-----|
| Dark background | Midnight navy | `#1E2761` |
| Light background | White | `#FFFFFF` |
| Accent | Ice blue | `#CADCFC` |
| Data highlight | Coral | `#F96167` |
| Body text on light | Charcoal | `#2D2D2D` |
| Supporting text | Mid-gray | `#666666` |

The "executive sandwich" applies dark backgrounds to the title, dividers, and close slides, with light content slides between them, creating premium visual rhythm.

### Typography

Headings in Georgia Bold, section headers in Trebuchet MS Bold, body in Calibri, captions in muted Calibri. Never more than two font families in one deck, and never fonts that Keynote will substitute on a standard machine.

### What never appears in a deck

Decorative colored bars, accent underlines beneath titles, bullet-heavy slides with no visual, stock photo clichés, warm beige backgrounds, slides with more than six bullets, and "in conclusion" as a heading.

---

## Executive scrutiny standards

The engine hardens every deck against the seven questions an executive audience actually asks:

1. **Where's this number from?** Every quantitative claim carries a source attribution; practitioner estimates are flagged as such.
2. **What does this actually cost?** Cost slides show all-in cost plus the cost of doing nothing.
3. **Who owns this when you leave?** Every recommendation gets an owner role and handoff deliverables.
4. **What are the risks?** Every deck over eight slides names its top risks with a mitigation for each.
5. **Have you done this before?** Proof points come only from the verified bank, with NDA attribution.
6. **Why now?** Urgency is tied to a named initiative, deadline, or cost trigger, answered in the first three slides.
7. **Why you specifically?** The case is made on practitioner evidence and IP ownership, never by disparaging named competitors.

---

## Voice standards

All slide copy follows a fixed voice: short titles that make claims rather than label topics, no decorative em dashes, no "leverage" as a verb, no vendor theater, active voice throughout, the Oxford comma always, and numbers over words for statistics.

A slide titled "AI adoption risks" is a topic. "Three AI adoption risks that will kill your pilot before Q3" is a claim. The engine produces the second kind.

---

## Quick-start commands

| Command | Triggers |
|---------|----------|
| `brief [topic]` | Intake and architecture for an executive briefing |
| `business case [topic]` | Intake and architecture for a budget-approval deck |
| `readout [engagement name]` | Intake for a consulting engagement readout |
| `pitch [service/offering]` | Intake for a services pitch deck |
| `keynote [topic]` | Intake for a conference keynote |
| `build [architecture]` | Skip intake, build content from a confirmed architecture |
| `visual spec [slide list]` | Visual specs for an existing content outline |
| `qa [deck description]` | Run the QA checklist against a deck |
| `html preview` | Build an interactive HTML preview artifact |

---

## Requirements

The component library and build pipeline depend on:

- `pptxgenjs` — deck generation
- `react` and `react-dom` — icon rendering
- `react-icons` — icon source (Font Awesome, Material Design, Heroicons, Bootstrap Icons)
- `sharp` — SVG-to-PNG rasterization for icons

Install with:

```bash
npm install -g pptxgenjs react-icons sharp
```

QA conversion uses `soffice` (LibreOffice headless) and `pdftoppm` to render slides to images for visual inspection.

---

*Maintained by Will Kelly. Part of the Consulting Delivery Engine infrastructure.*
