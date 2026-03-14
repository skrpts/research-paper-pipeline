---
type: skill
id: academic-writing-style
title: Academic Writing Style
description: "Applies discipline-appropriate academic writing conventions including register, hedging, paragraph structure, and stylistic consistency"
tags: [Production, Tested]
connections:
  - target: llm-service
    type: runs_on
  - target: academic-writing-standards
    type: references
metadata:
  estimated_duration: "3-5 minutes per section"
  avg_tokens: 2500
  trigger: manual
---

## Academic Writing Style

This skill governs the stylistic and structural conventions of academic writing. It ensures that all output conforms to the expectations of scholarly communication within the student's discipline and academic level.

### Core Capabilities

**Register Calibration:** Academic writing operates within a specific register — formal, precise, and evidence-grounded. This skill adjusts the formality level to match disciplinary norms. Scientific writing tends toward impersonal, passive constructions ("It was observed that..."), whilst humanities writing increasingly accepts first-person positioning ("I argue that..."). The skill calibrates based on the student's discipline, institution, and stated preferences.

**Hedging and Certainty:** Academic writing requires careful modulation of certainty. This skill applies appropriate hedging language ("suggests," "appears to indicate," "may contribute to") where findings are tentative, and stronger assertions ("demonstrates," "establishes," "confirms") where evidence is robust. Over-hedging weakens arguments; under-hedging overstates evidence. The skill finds the disciplinary sweet spot.

**Paragraph Architecture:** Each academic paragraph follows a predictable structure: topic sentence, development, evidence, analysis, and link to the next paragraph. This skill ensures every paragraph has a clear function within the section, a single controlling idea, adequate development (typically 100-250 words in most disciplines), and smooth transitions that maintain the argument's momentum.

**Signposting and Metadiscourse:** Academic papers guide the reader through the argument using signposting ("This section examines...", "Having established X, the discussion now turns to Y..."). This skill inserts appropriate metadiscourse without overdoing it — enough to orient the reader, not so much that the paper reads like a table of contents.

**Stylistic Consistency:** Across a multi-section paper, voice, tense usage, terminology, and formatting must remain consistent. This skill maintains a style profile for the paper and flags deviations. Common issues it catches include tense shifts between sections, inconsistent terminology (using "participants" in one section and "subjects" in another), and register drift (becoming too informal in later sections as the student tires).

**Disciplinary Adaptation:** Writing conventions vary significantly across fields. This skill adapts its guidance based on the target discipline:
- **Sciences:** IMRaD structure, passive voice, precise methodology descriptions, quantitative hedging
- **Social sciences:** APA conventions, balanced active/passive voice, theoretical framing emphasis
- **Humanities:** Longer paragraphs, extensive textual engagement, first-person argumentation accepted, footnote-heavy styles
- **Law:** Case citation conventions, precedent-based argumentation, formal register throughout
- **Engineering:** Concise technical writing, specification-focused, diagram-heavy sections

### Constraints

- The skill does not impose a single "correct" academic style. It adapts to disciplinary norms and institutional expectations.
- It will not make writing sound artificially complex. Clarity is the highest priority in academic writing; jargon is used only when technically necessary.
- Feedback is constructive and educational. When correcting style, the skill explains why the change improves the writing, helping the student develop their own academic voice.

### Output Format

Styled text is returned with:
- The revised passage with all style adjustments applied
- Inline annotations explaining significant changes (togglable)
- A style consistency report when processing multiple sections
- Discipline-specific notes where conventions have been applied
