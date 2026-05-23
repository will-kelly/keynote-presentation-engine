# Executive scrutiny pressure test — Keynote presentation engine

Run this before any deck leaves the project. A skeptical CIO, CFO, or board member will find the gaps listed here in the first 10 minutes. Fix them before the room does.

This file exists because there is a difference between a deck that looks good and a deck that holds up under questioning. This is the difference.

---

## The pressure test: seven attack vectors

Every executive audience will probe one or more of these. Design the deck to pre-empt all seven.

---

### Attack vector 1: "Where's this number from?"

**The attack**: A CFO or CIO challenges a statistic on a slide. If you can't cite the source on the spot, you've lost the room.

**How to pre-empt**:
- Every quantitative claim on a slide body gets an attribution: "Source: McKinsey, 2024" in 9pt caption below the stat.
- For stats that are practitioner estimates (not published research), flag in speaker notes: "PRACTITIONER ESTIMATE — frame as 'field observation, not published research' if challenged."
- For vendor-sponsored stats: always disclose the sponsor. "According to a Salesforce-commissioned study..." is defensible. Presenting a Salesforce-commissioned stat as independent research is not.
- If a stat is critical to the business case and you can't source it, do not put it on the slide. Put the methodology in speaker notes and present the range, not a precise number.

**Checklist**:
- [ ] Every stat has a source attribution on the slide
- [ ] Practitioner estimates are flagged as such in speaker notes
- [ ] Vendor-sponsored stats disclose the sponsor
- [ ] Business case projections show the assumption behind each number

---

### Attack vector 2: "What does this actually cost?"

**The attack**: A CFO asks for the total cost of the engagement, program, or technology — including hidden costs (change management, training, maintenance) that weren't on the slide.

**How to pre-empt**:
- Cost slides must show all-in cost: direct fees + estimated internal time + change management + maintenance runway.
- If internal time estimates are unavailable, note the gap: "Internal time allocation to be scoped in week one."
- Include a "cost of doing nothing" calculation alongside the investment. CFOs respond to risk of inaction.
- Do not round costs to suspiciously clean numbers ($250,000 reads as made-up; $247,000 reads as calculated).

**Checklist**:
- [ ] Cost slide shows all-in cost, not just service fee
- [ ] "Cost of doing nothing" is calculated and on the slide
- [ ] No suspiciously round numbers without a methodology note
- [ ] Assumptions behind cost estimates are in speaker notes

---

### Attack vector 3: "Who owns this when you leave?"

**The attack**: A CIO asks who is accountable for the outcome after the engagement ends. If the answer is "we'll figure that out," the project is perceived as a consulting dependency, not a solution.

**How to pre-empt**:
- Every recommendation includes an ownership assignment: a role (not a name, since personnel change), a scope of accountability, and a timeline.
- Handoff artifacts are listed explicitly: "At engagement close, you will have: [governance policy, training materials, process documentation, Notion workspace]."
- If the recommendation is "hire someone," say so directly with a role description.

**Checklist**:
- [ ] Every recommendation has an owner role assigned
- [ ] Handoff deliverables are listed on the close slide
- [ ] If ongoing staffing is required, it is stated as a requirement, not implied

---

### Attack vector 4: "What are the risks?"

**The attack**: A board member or CIO asks what could go wrong. A deck with no risk slide signals the presenter hasn't thought it through.

**How to pre-empt**:
- Every deck over 8 slides should have an explicit risk acknowledgment: a slide or a callout block that names the top 2–3 risks and the mitigation for each.
- Risks should be specific: "Implementation timeline extends if data remediation phase uncovers additional scope" is specific. "There may be challenges" is not.
- Frame risks as managed, not avoided: "We have identified X and will mitigate it by Y."
- Never present a technology or process as risk-free — it signals either naivety or salesmanship.

**Checklist**:
- [ ] Risk acknowledgment is present — at minimum a callout block, ideally a dedicated slide
- [ ] Each risk has a named mitigation
- [ ] Risks are specific, not generic
- [ ] No technology or approach is presented as risk-free

---

### Attack vector 5: "Have you done this before?"

**The attack**: A buying committee or CIO asks for evidence that Will has solved this specific problem for a comparable organization.

**How to pre-empt**:
- Proof points slide uses the verified engagement evidence from kb-01-proof-point-bank.md — not fabricated or extended metrics.
- Match the proof point to the audience's industry or org size where possible. A 12,000-user federal intranet proof point lands differently with a federal buyer than with a Series C startup.
- If an exact-match proof point doesn't exist, lead with Will's practitioner observation and frame it as pattern recognition across engagements.
- Always include: "Client names withheld per NDA. Metrics available for verification under NDA."

**Checklist**:
- [ ] Proof points are from the verified bank — no fabricated or extrapolated metrics
- [ ] Proof points match audience context as closely as possible
- [ ] NDA attribution line is on the proof slide
- [ ] If no exact-match proof point exists, the framing reflects that honestly

---

### Attack vector 6: "Why now?"

**The attack**: A CIO or CFO asks why this engagement needs to happen now, not next quarter or next year.

**How to pre-empt**:
- Every deck needs an urgency driver that is specific to the audience's context — not a generic "the market is moving fast."
- Urgency drivers by deck type:
  - AI readiness: "Your next AI pilot sprint is [quarter]. If data and governance remediation doesn't start now, the pilot will fail before launch."
  - Documentation debt: "Your migration to [platform] is scheduled for [quarter]. Migrating debt at scale will cost 3× more than auditing now."
  - Services pitch: "Your current content ops state will block the AI pilot you've already committed to — and that pilot has a named sponsor and a deadline."
- If the urgency driver is unknown, ask Will before building the deck: "What deadline, initiative, or event makes this pressing right now?"

**Checklist**:
- [ ] Urgency driver is specific to this audience's context
- [ ] Urgency is tied to a named initiative, deadline, or cost trigger
- [ ] "Why now" is answered in the first 3 slides, not buried at the end

---

### Attack vector 7: "Why you specifically?"

**The attack**: A buying committee asks why Will Kelly rather than a larger consultancy, an internal hire, or a different vendor.

**How to pre-empt**:
- The "why me" slide uses practitioner credibility, not credentials: "I've lived this dysfunction from inside the org, not observed it from a consulting firm."
- Specific differentiators from kb-01-proof-point-bank.md: Docker, GDIT, Anchore experience; CTRL+ALT+SharePoint methodology; Documentation Debt Audit Framework; 15+ years of practitioner observation.
- The IP-you-keep argument: "My frameworks are yours to retain and operate after engagement close. This is not a dependency model."
- The speed argument: "An independent engagement moves faster than a firm engagement — no project manager overhead, no up-staffing delay."
- Do not compare Will directly to named competitors by name on a slide — make the case for Will on his own merits.

**Checklist**:
- [ ] "Why me" slide uses practitioner evidence, not credential lists
- [ ] IP ownership is made explicit
- [ ] Speed and independence advantages are stated without disparaging competitors by name

---

## Pre-delivery QA checklist (full)

Run this on every deck before it goes to a client or conference.

### Content integrity
- [ ] Every slide title is a claim, not a topic
- [ ] Recommendation appears in slides 1–3
- [ ] Every quantitative stat has a source
- [ ] Practitioner estimates are labeled as such
- [ ] Vendor-sponsored stats disclose the sponsor
- [ ] Business case shows assumptions
- [ ] Risk acknowledgment is present
- [ ] Proof points are from the verified bank
- [ ] Ownership assignment is on every recommendation
- [ ] Urgency driver is specific and named

### Visual standards
- [ ] No accent underlines beneath titles
- [ ] No decorative colored header/footer bars
- [ ] No text-only slides
- [ ] No more than 6 bullets on any slide
- [ ] All charts have axis labels and sources
- [ ] No cream or warm beige backgrounds
- [ ] No vendor theater language anywhere

### Voice standards
- [ ] No em dashes used decoratively
- [ ] No "leverage" as a verb
- [ ] No "cutting-edge," "transformative," "game-changing," "synergy"
- [ ] No "fractional" as Will's self-descriptor in forward-facing slides
- [ ] Active voice throughout
- [ ] Oxford comma applied throughout

### Speaker notes
- [ ] Every slide has speaker notes
- [ ] Notes tell Will what to say, not what the slide shows
- [ ] Notes flag any stat or claim that needs live verification before presenting
- [ ] Close slide notes include the ask: what Will is requesting the audience do next

---

## Stress-test questions to run in speaker notes for high-stakes decks

For board presentations, enterprise sales finals, or high-stakes CIO readouts, add these as speaker note prompts on the relevant slides:

- **Stat slide**: "CFO challenge: Where did this number come from? PREP: [source + methodology in one sentence]"
- **Cost slide**: "CFO challenge: What does this cost all-in, including my team's time? PREP: [internal time estimate + direct fee]"
- **ROI slide**: "CFO challenge: What's the payback period? PREP: [month X at adoption rate Y]"
- **Proof point slide**: "Buying committee challenge: Can I talk to one of these clients? PREP: [NDA response + what you can share]"
- **Recommendation slide**: "CIO challenge: Who owns this when you leave? PREP: [role + handoff deliverables list]"
- **Risk slide**: "Board challenge: What's the worst case? PREP: [specific failure scenario + mitigation]"

---

*Last updated: May 2026. Part of the Keynote Presentation Engine knowledge base. Run this checklist before every client-facing delivery.*
