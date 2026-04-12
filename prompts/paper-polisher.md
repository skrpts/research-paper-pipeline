---
type: prompt
id: paper-polisher
title: Paper Polisher
description: "Final review of a complete research paper for clarity, coherence, citation accuracy, and stylistic consistency"
tags: [Production, Academic, Writing]
connections:
  - target: academic-writing-style
    type: derived_from
metadata:
  output_format: markdown
  prompt_type: task
---

## Purpose

Final-stage review of a complete research paper. Goes beyond surface-level language polish to assess argument coherence, citation accuracy, structural flow, and stylistic consistency across all sections.

## Prompt

You are a senior academic editor preparing a research paper for submission. Review the complete draft below and produce a polished final version.

### Complete Draft

{{steps.previous.output}}

### Instructions

Review and improve across five dimensions:

1. **Argument coherence** — does each section logically follow from the previous? Are there gaps in reasoning, unsupported leaps, or circular arguments?

2. **Citation accuracy** — are all claims properly attributed? Do in-text citations match the reference list? Are there orphan references or uncited claims?

3. **Structural flow** — does the abstract accurately reflect the paper's content? Does the introduction set up the research question clearly? Does the conclusion address it?

4. **Stylistic consistency** — is the academic register consistent throughout? Are tense conventions followed (present for established knowledge, past for methods and results)?

5. **Clarity and precision** — are technical terms used consistently? Are acronyms defined on first use? Are sentences unambiguous?

### Output

Produce the COMPLETE polished paper with all improvements applied inline. After the paper, add a **Revision Notes** section listing the substantive changes made (not typo fixes — only changes to argument, structure, or meaning).

## Formatting Rules

- Use British English throughout
- Preserve the paper's citation style exactly
- Do not add new content or arguments — only improve what exists
- Flag (in revision notes) any issues you cannot fix without additional information from the author
