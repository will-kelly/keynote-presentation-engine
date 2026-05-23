# Slide component code library — Keynote presentation engine

Reusable PptxGenJS code patterns for the most common slide components. Copy and adapt — do not rewrite from scratch. These patterns have been QA'd against the reference decks and are known to render correctly.

Always follow the pitfall rules from the PPTX skill: no `#` prefix on hex colors, no 8-char hex for opacity, fresh shadow objects per call, no ROUNDED_RECTANGLE with accent bars.

---

## Setup boilerplate

```javascript
const pptxgen = require("pptxgenjs");
const React = require("react");
const ReactDOMServer = require("react-dom/server");
const sharp = require("sharp");

// Install if missing: npm install -g pptxgenjs react-icons sharp

const pres = new pptxgen();
pres.layout = "LAYOUT_16x9"; // 10" × 5.625"

// Will's default palette — override with client brand if provided
const C = {
  navy:    "1E2761",  // Primary dark background
  white:   "FFFFFF",  // Primary light background
  iceBlue: "CADCFC",  // Accent on dark
  coral:   "F96167",  // Data highlight, CTAs
  charcoal:"2D2D2D",  // Body text on light
  midGray: "666666",  // Captions, attribution
  lightBg: "F4F6FB",  // Content card backgrounds
  teal:    "028090",  // Secondary accent
  gold:    "C9A84C",  // Tertiary accent, business case
  green:   "2A9D8F",  // Positive/success
  amber:   "F4A261",  // Warning/medium risk
};

// Shadow factory — always use a factory function, never reuse object
const makeShadow = () => ({ type: "outer", color: "000000", blur: 8, offset: 2, angle: 135, opacity: 0.08 });

// Icon helper
async function iconPng(IconComponent, hexColor, size = 256) {
  const svg = ReactDOMServer.renderToStaticMarkup(
    React.createElement(IconComponent, { color: `#${hexColor}`, size: String(size) })
  );
  const buf = await sharp(Buffer.from(svg)).png().toBuffer();
  return "image/png;base64," + buf.toString("base64");
}
```

---

## Component 1: Title slide (dark, left accent bar)

Use on: Opening slide of every deck. Dark background signals executive register.

```javascript
function addTitleSlide(pres, { eyebrow, title, subtitle, presenter, bgColor, accentColor }) {
  const s = pres.addSlide();
  s.background = { color: bgColor || C.navy };

  // Left accent bar
  s.addShape(pres.shapes.RECTANGLE, {
    x: 0, y: 0, w: 0.18, h: 5.625,
    fill: { color: accentColor || C.coral }, line: { color: accentColor || C.coral }
  });

  // Eyebrow — spaced caps
  s.addText(eyebrow.toUpperCase(), {
    x: 0.45, y: 1.1, w: 9.1, h: 0.4,
    fontSize: 11, bold: true, color: C.iceBlue, charSpacing: 5, margin: 0
  });

  // Main title
  s.addText(title, {
    x: 0.45, y: 1.7, w: 8.2, h: 2.2,
    fontSize: 38, bold: true, color: C.white, margin: 0
  });

  // Divider
  s.addShape(pres.shapes.RECTANGLE, {
    x: 0.45, y: 4.05, w: 1.8, h: 0.05,
    fill: { color: accentColor || C.coral }, line: { color: accentColor || C.coral }
  });

  // Presenter line
  s.addText(presenter || "Will Kelly  |  Technical Content Strategist, AI Enablement", {
    x: 0.45, y: 4.25, w: 8, h: 0.35,
    fontSize: 12, color: C.iceBlue, margin: 0
  });

  if (subtitle) {
    s.addText(subtitle, {
      x: 7.5, y: 5.15, w: 2.2, h: 0.3,
      fontSize: 9, color: C.midGray, align: "right", margin: 0
    });
  }
}
```

---

## Component 2: Full-bleed stat callout

Use on: Problem slides, business case impact slides. Maximum impact. One stat per slide.

```javascript
function addStatSlide(pres, { label, stat, context, source, bgColor, accentColor }) {
  const s = pres.addSlide();
  s.background = { color: bgColor || C.navy };

  s.addShape(pres.shapes.RECTANGLE, {
    x: 0, y: 0, w: 0.18, h: 5.625,
    fill: { color: accentColor || C.teal }, line: { color: accentColor || C.teal }
  });

  // Eyebrow label
  s.addText(label.toUpperCase(), {
    x: 0.45, y: 0.4, w: 9, h: 0.4,
    fontSize: 11, bold: true, color: accentColor || C.teal, charSpacing: 5, margin: 0
  });

  // The stat — large
  s.addText(stat, {
    x: 0.45, y: 0.95, w: 9, h: 2.4,
    fontSize: 110, bold: true, color: C.coral, margin: 0
  });

  // Context — two lines max
  s.addText(context, {
    x: 0.45, y: 3.4, w: 7.5, h: 1.1,
    fontSize: 26, bold: true, color: C.white, margin: 0
  });

  if (source) {
    s.addText(`Source: ${source}`, {
      x: 0.45, y: 5.2, w: 6, h: 0.25,
      fontSize: 9, color: C.midGray, margin: 0
    });
  }
}
```

---

## Component 3: Three-column card grid

Use on: Executive summary (where you are / what blocks you / what to do), service area overviews, three-option comparisons.

```javascript
function addThreeCardSlide(pres, { title, cards, bgColor, accentColor }) {
  // cards: [{ label, body }]
  const s = pres.addSlide();
  s.background = { color: bgColor || C.white };
  s.addShape(pres.shapes.RECTANGLE, { x: 0, y: 0, w: 10, h: 0.08, fill: { color: accentColor || C.navy }, line: { color: accentColor || C.navy } });

  s.addText(title, {
    x: 0.5, y: 0.22, w: 9, h: 0.55,
    fontSize: 26, bold: true, color: C.navy, margin: 0
  });

  cards.forEach((card, i) => {
    const x = 0.4 + i * 3.1;
    s.addShape(pres.shapes.RECTANGLE, {
      x, y: 1.05, w: 2.9, h: 3.5,
      fill: { color: C.lightBg }, shadow: makeShadow()
    });
    s.addShape(pres.shapes.RECTANGLE, {
      x, y: 1.05, w: 2.9, h: 0.07,
      fill: { color: accentColor || C.navy }, line: { color: accentColor || C.navy }
    });
    s.addText(card.label, {
      x: x + 0.18, y: 1.22, w: 2.55, h: 0.5,
      fontSize: 14, bold: true, color: accentColor || C.navy, margin: 0
    });
    s.addText(card.body, {
      x: x + 0.18, y: 1.88, w: 2.55, h: 2.5,
      fontSize: 12, color: C.charcoal, margin: 0
    });
  });
}
```

---

## Component 4: Numbered intervention list

Use on: Recommendations, remediation steps, prioritized action items. Works for 3–5 items.

```javascript
function addNumberedListSlide(pres, { title, items, bgColor }) {
  // items: [{ num, color, title, body, tag }]
  const s = pres.addSlide();
  s.background = { color: bgColor || C.white };
  s.addShape(pres.shapes.RECTANGLE, { x: 0, y: 0, w: 10, h: 0.08, fill: { color: C.navy }, line: { color: C.navy } });

  s.addText(title, {
    x: 0.5, y: 0.22, w: 9, h: 0.55,
    fontSize: 24, bold: true, color: C.navy, margin: 0
  });

  const itemH = Math.min(1.5, (4.6) / items.length);

  items.forEach((item, i) => {
    const y = 1.0 + i * (itemH + 0.08);
    s.addShape(pres.shapes.RECTANGLE, {
      x: 0.4, y, w: 0.75, h: itemH,
      fill: { color: item.color }, line: { color: item.color }
    });
    s.addText(item.num, {
      x: 0.4, y: y + itemH * 0.2, w: 0.75, h: itemH * 0.6,
      fontSize: 28, bold: true, color: C.white, align: "center", margin: 0
    });
    s.addShape(pres.shapes.RECTANGLE, {
      x: 1.3, y, w: 8.3, h: itemH,
      fill: { color: C.lightBg }, line: { color: "E0E4EE" }
    });
    s.addText(item.title, {
      x: 1.5, y: y + 0.1, w: 8.0, h: 0.38,
      fontSize: 13, bold: true, color: item.color, margin: 0
    });
    s.addText(item.body, {
      x: 1.5, y: y + 0.48, w: 8.0, h: itemH - 0.7,
      fontSize: 11, color: C.charcoal, margin: 0
    });
    if (item.tag) {
      s.addText(item.tag, {
        x: 1.5, y: y + itemH - 0.25, w: 6, h: 0.22,
        fontSize: 10, italic: true, color: C.midGray, margin: 0
      });
    }
  });
}
```

---

## Component 5: Horizontal phase timeline

Use on: Engagement models, audit phases, project roadmaps. 3–5 phases.

```javascript
async function addTimelineSlide(pres, { title, phases, bgColor, accentColor }) {
  // phases: [{ label, weeks, desc }]
  const s = pres.addSlide();
  s.background = { color: bgColor || C.white };
  s.addShape(pres.shapes.RECTANGLE, { x: 0, y: 0, w: 10, h: 0.08, fill: { color: accentColor || C.navy }, line: { color: accentColor || C.navy } });

  s.addText(title, {
    x: 0.4, y: 0.22, w: 9, h: 0.55,
    fontSize: 24, bold: true, color: C.navy, margin: 0
  });

  const colW = 10 / phases.length;
  const nodeY = 2.6;

  phases.forEach((ph, i) => {
    const x = i * colW;
    const cx = x + colW / 2;

    // Connector line (not on last)
    if (i < phases.length - 1) {
      s.addShape(pres.shapes.RECTANGLE, {
        x: cx + 0.4, y: nodeY + 0.3, w: colW - 0.8, h: 0.06,
        fill: { color: accentColor || C.teal }, line: { color: accentColor || C.teal }
      });
    }

    // Circle node
    s.addShape(pres.shapes.OVAL, {
      x: cx - 0.38, y: nodeY, w: 0.76, h: 0.65,
      fill: { color: accentColor || C.teal }, line: { color: accentColor || C.teal }
    });
    s.addText(String(i + 1), {
      x: cx - 0.38, y: nodeY + 0.06, w: 0.76, h: 0.52,
      fontSize: 14, bold: true, color: C.white, align: "center", margin: 0
    });

    // Phase label above
    s.addShape(pres.shapes.RECTANGLE, {
      x: x + 0.15, y: 1.1, w: colW - 0.3, h: 0.85,
      fill: { color: C.lightBg }, line: { color: "D0E8EC" }
    });
    s.addText(ph.label.toUpperCase(), {
      x: x + 0.15, y: 1.25, w: colW - 0.3, h: 0.55,
      fontSize: 12, bold: true, color: accentColor || C.teal, align: "center", charSpacing: 3, margin: 0
    });

    // Below: label and desc
    s.addText(ph.label, {
      x: x + 0.1, y: nodeY + 0.85, w: colW - 0.2, h: 0.4,
      fontSize: 13, bold: true, color: C.navy, align: "center", margin: 0
    });
    s.addText(ph.weeks, {
      x: x + 0.1, y: nodeY + 1.28, w: colW - 0.2, h: 0.3,
      fontSize: 11, italic: true, color: accentColor || C.teal, align: "center", margin: 0
    });
    s.addText(ph.desc, {
      x: x + 0.1, y: nodeY + 1.65, w: colW - 0.2, h: 1.0,
      fontSize: 10, color: C.charcoal, align: "center", margin: 0
    });
  });
}
```

---

## Component 6: Bar chart scorecard with side panel

Use on: Diagnostic results, maturity scores, competitive comparisons.

```javascript
function addScorecardSlide(pres, { title, chartData, panelTitle, panelItems, bgColor }) {
  // chartData: { labels: [], values: [] }
  // panelItems: [{ iconData, color, label, note }]
  const s = pres.addSlide();
  s.background = { color: bgColor || C.lightBg };
  s.addShape(pres.shapes.RECTANGLE, { x: 0, y: 0, w: 10, h: 0.08, fill: { color: C.navy }, line: { color: C.navy } });

  s.addText(title, {
    x: 0.5, y: 0.22, w: 9, h: 0.5,
    fontSize: 22, bold: true, color: C.navy, margin: 0
  });

  // Bar chart
  s.addChart(pres.charts.BAR, [{
    name: "Score",
    labels: chartData.labels,
    values: chartData.values
  }], {
    x: 0.4, y: 0.95, w: 5.8, h: 4.3,
    barDir: "bar",
    chartColors: [C.teal],
    chartArea: { fill: { color: C.white }, roundedCorners: false },
    catAxisLabelColor: C.charcoal,
    valAxisLabelColor: C.midGray,
    valAxisMaxVal: 4,
    valGridLine: { color: "E0E4EE", size: 0.5 },
    catGridLine: { style: "none" },
    showValue: true,
    dataLabelColor: C.white,
    dataLabelFontSize: 12,
    showLegend: false,
    showTitle: false,
  });

  // Side panel
  s.addText(panelTitle || "Priority flags", {
    x: 6.4, y: 0.95, w: 3.2, h: 0.4,
    fontSize: 13, bold: true, color: C.navy, margin: 0
  });

  panelItems.forEach((item, i) => {
    const y = 1.5 + i * 0.9;
    if (item.iconData) {
      s.addImage({ data: item.iconData, x: 6.4, y: y + 0.05, w: 0.35, h: 0.35 });
    }
    s.addText(item.label, {
      x: 6.85, y, w: 2.8, h: 0.32,
      fontSize: 12, bold: true, color: item.color || C.navy, margin: 0
    });
    s.addText(item.note, {
      x: 6.85, y: y + 0.32, w: 2.8, h: 0.45,
      fontSize: 10, color: C.charcoal, margin: 0
    });
  });
}
```

---

## Component 7: Two-column problem/cost slide

Use on: Opening problem slide in any diagnostic or pitch deck.

```javascript
function addProblemCostSlide(pres, { title, problemTitle, problemItems, costTitle, costItems, bgColor }) {
  // problemItems: [string]
  // costItems: [{ val, label }]
  const s = pres.addSlide();
  s.background = { color: bgColor || C.white };
  s.addShape(pres.shapes.RECTANGLE, { x: 0, y: 0, w: 10, h: 0.08, fill: { color: C.teal }, line: { color: C.teal } });

  s.addText(title, {
    x: 0.5, y: 0.22, w: 9, h: 0.55,
    fontSize: 26, bold: true, color: C.navy, margin: 0
  });

  // Left: problem list
  s.addShape(pres.shapes.RECTANGLE, {
    x: 0.4, y: 1.05, w: 4.6, h: 4.0,
    fill: { color: C.lightBg }, line: { color: "D0E8EC" }
  });
  s.addText(problemTitle || "You probably recognize this:", {
    x: 0.6, y: 1.2, w: 4.2, h: 0.4,
    fontSize: 13, bold: true, color: C.teal, margin: 0
  });
  problemItems.forEach((item, i) => {
    s.addText(`• ${item}`, {
      x: 0.7, y: 1.72 + i * 0.5, w: 4.1, h: 0.42,
      fontSize: 12, color: C.charcoal, margin: 0
    });
  });

  // Right: cost panel (dark)
  s.addShape(pres.shapes.RECTANGLE, {
    x: 5.2, y: 1.05, w: 4.4, h: 4.0,
    fill: { color: C.navy }, line: { color: C.navy }
  });
  s.addText(costTitle || "What it costs you", {
    x: 5.4, y: 1.2, w: 4.0, h: 0.4,
    fontSize: 13, bold: true, color: C.teal, margin: 0
  });
  costItems.forEach((item, i) => {
    const y = 1.9 + i * 1.15;
    s.addText(item.val, {
      x: 5.4, y, w: 4.0, h: 0.65,
      fontSize: 34, bold: true, color: C.gold, margin: 0
    });
    s.addText(item.label, {
      x: 5.4, y: y + 0.65, w: 4.0, h: 0.42,
      fontSize: 11, color: C.iceBlue, margin: 0
    });
  });
}
```

---

## Component 8: Dark CTA close slide

Use on: Final slide of every pitch, briefing, and diagnostic deck.

```javascript
function addCTASlide(pres, { bgColor, accentColor, headline, body, contact }) {
  const s = pres.addSlide();
  s.background = { color: bgColor || C.navy };

  // Footer bar
  s.addShape(pres.shapes.RECTANGLE, {
    x: 0, y: 4.85, w: 10, h: 0.775,
    fill: { color: accentColor || C.teal }, line: { color: accentColor || C.teal }
  });

  s.addText(headline, {
    x: 0.5, y: 0.6, w: 9, h: 2.2,
    fontSize: 40, bold: true, color: C.white, margin: 0
  });

  s.addText(body, {
    x: 0.5, y: 3.0, w: 9, h: 1.5,
    fontSize: 14, color: C.iceBlue, margin: 0
  });

  s.addText(contact || "willkelly.substack.com  |  LinkedIn: /in/willkelly", {
    x: 0.5, y: 4.98, w: 7, h: 0.35,
    fontSize: 12, color: C.white, margin: 0
  });
}
```

---

## Component 9: Section divider slide

Use on: Between major sections in decks longer than 12 slides.

```javascript
function addDividerSlide(pres, { sectionNum, sectionLabel, bgColor, accentColor }) {
  const s = pres.addSlide();
  s.background = { color: bgColor || C.navy };

  s.addShape(pres.shapes.RECTANGLE, {
    x: 0, y: 0, w: 0.18, h: 5.625,
    fill: { color: accentColor || C.coral }, line: { color: accentColor || C.coral }
  });

  s.addText(`SECTION ${sectionNum}`, {
    x: 0.45, y: 1.5, w: 9, h: 0.45,
    fontSize: 11, bold: true, color: accentColor || C.coral, charSpacing: 6, margin: 0
  });

  s.addText(sectionLabel, {
    x: 0.45, y: 2.1, w: 8.5, h: 2.0,
    fontSize: 52, bold: true, color: C.white, margin: 0
  });
}
```

---

## QA script (run after every build)

```bash
# 1. Convert to PDF
python /mnt/skills/public/pptx/scripts/office/soffice.py --headless --convert-to pdf output.pptx

# 2. Convert to images
rm -f slide-*.jpg
pdftoppm -jpeg -r 150 output.pdf slide

# 3. List for inspection
ls -1 "$PWD"/slide-*.jpg
```

Then inspect every slide image for: text overflow, element overlap, low contrast text, missing content, leftover placeholders.

---

*Last updated: May 2026. Part of the Keynote Presentation Engine knowledge base.*
