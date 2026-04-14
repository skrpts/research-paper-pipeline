---
type: workflow
id: research-paper-pipeline
title: Research Paper Pipeline
description: "End-to-end workflow for producing a polished academic research paper, from topic selection through to final submission-ready draft"
tags: [Production, Tested, Academic, Research]
connections:
  - target: argument-construction
    type: uses
  - target: literature-integration
    type: uses
  - target: academic-writing-style
    type: uses
  - target: citation-extraction
    type: uses
  - target: llm-service
    type: runs_on
  - target: academic-writing-standards
    type: references
  - target: research-paper-guide
    type: references
  - target: critical-thinking-framework
    type: references
  - target: research-paper-template
    type: uses
  - target: literature-map-template
    type: uses
  - target: language-polish
    type: uses
  - target: consistency-check
    type: uses
  - target: evidence-claim-check
    type: uses
metadata:
  estimated_duration: "45-90 minutes"
  avg_tokens: 15000
  trigger: manual
output_step: "academic-writing-style"
composite_steps:
  - "argument-construction"
  - "literature-integration"
  - "academic-writing-style"
  - "citation-extraction"
  - "research-paper-template"
  - "literature-map-template"
  - "language-polish"
  - "consistency-check"
  - "evidence-claim-check"
execution:
  - skill: "argument-construction"
    step_type: "generation"
  - skill: "literature-integration"
    step_type: "synthesis"
  - skill: "academic-writing-style"
    step_type: "content"
  - skill: "citation-extraction"
    step_type: "synthesis"
  - skill: "research-paper-template"
    step_type: "generation"
  - skill: "literature-map-template"
    step_type: "synthesis"
  - skill: "language-polish"
    step_type: "content"
  - parallel:
    - skill: "evidence-claim-check"
      step_type: "review"
  - skill: "consistency-check"
    step_type: "review"
---

## Research Paper Pipeline

This workflow orchestrates the complete process of writing an academic research paper. It is designed for undergraduate and postgraduate students who need structured guidance through each phase of the writing process.

### Pipeline Stages

#### Stage 1: Topic Refinement
**Node:** `topic-narrowing-prompt`
**Input:** A broad subject area or assignment brief
**Output:** A focused, arguable research question with defined scope

The pipeline begins by taking the student's initial topic idea and systematically narrowing it. The prompt guides the student through considering feasibility, available literature, and the specificity needed for the target word count.

**Error handling:** If the generated research question is too broad or too narrow, the prompt includes self-assessment criteria. Re-run with adjusted scope parameters before proceeding.

#### Stage 2: Literature Mapping
**Node:** `literature-map-builder`
**Depends on:** Stage 1 output (research question)
**Skills used:** `literature-integration`
**Output:** A structured literature map using `literature-map-template`

With the research question established, this stage maps the scholarly landscape. The literature map identifies key authors, seminal works, theoretical frameworks, and gaps in the existing research.

**Error handling:** If the student provides fewer than five sources, the prompt will flag insufficient coverage and suggest search strategies for finding additional material.

#### Stage 3: Thesis Construction
**Node:** `thesis-statement-crafter`
**Depends on:** Stage 1 and Stage 2 outputs
**Skills used:** `argument-construction`
**Output:** A thesis statement with three supporting arguments and anticipated counterarguments

This stage synthesises the research question and literature review into a defensible thesis. The argument construction skill ensures the thesis is specific, contestable, and supported by the available evidence.

**Error handling:** The prompt includes a strength-test checklist. If the thesis fails any criterion (specificity, contestability, evidence support), it provides targeted revision guidance.

#### Stage 4: Section Drafting
**Node:** `section-drafter`
**Depends on:** Stage 3 output (thesis and argument structure)
**Skills used:** `academic-writing-style`, `literature-integration`
**Template:** `research-paper-template`
**Output:** Complete draft sections (introduction, literature review, body sections, conclusion)

The drafting stage works section by section through the paper. Each section is drafted with proper academic structure, integrated citations, and clear argumentation. The `research-paper-template` provides the structural scaffolding.

**Execution order:**
1. Introduction (contextualises the research question and previews the argument)
2. Literature review (synthesises sources identified in Stage 2)
3. Body sections (one per supporting argument from Stage 3)
4. Conclusion (synthesises findings and identifies future research directions)

**Error handling:** Each section draft is checked against the `academic-writing-standards` source for disciplinary conventions. If a section is under the expected word count or lacks sufficient citations, the drafter flags it for expansion.

#### Stage 5: Polish and Review
**Node:** `paper-polisher`
**Depends on:** Stage 4 output (complete draft)
**Skills used:** `academic-writing-style`
**Output:** Submission-ready paper with revision notes

The final stage reviews the complete draft for clarity, argument coherence, citation accuracy, stylistic consistency, and adherence to the target style guide. It produces both a polished version and a set of revision notes explaining each change.

**Error handling:** If the polisher identifies structural problems (e.g., an argument that contradicts the thesis, a missing section, or a citation that does not appear in the reference list), it escalates these as critical issues requiring the student's attention before submission.

### Parallel Execution Notes
Stages 1-3 are strictly sequential — each depends on the previous output. Stage 4 sections can be drafted in parallel once the thesis and argument structure are established. Stage 5 must wait for all sections to be complete.

### Quality Gates
- After Stage 1: Research question must pass the specificity test
- After Stage 2: Literature map must contain a minimum of eight sources
- After Stage 3: Thesis must pass all five strength-test criteria
- After Stage 4: Each section must meet minimum word count and citation density
- After Stage 5: Final paper must pass the holistic quality checklist

## Inputs

| Name | Required | Description | Example |
|------|----------|-------------|---------|
| `{{input.a_broad_subject_area}}` | Yes | A broad subject area or assignment brief | `The impact of social media on political polarisation` |
| `{{input.discipline}}` | Yes | Academic discipline | `Political Science` |
| `{{input.academic_level}}` | Yes | Academic level of the student | `Final-year undergraduate` |
| `{{input.word_count}}` | Yes | Target word count for the paper | `5000` |
| `{{input.assignment_type}}` | No | Type of assignment | `Essay` |
| `{{input.assignment_requirements}}` | No | Specific requirements from the assignment brief | `Must include at least 15 sources, APA format` |
| `{{input.referencing_style}}` | No | Referencing style to use | `APA` |
| `{{input.existing_sources}}` | No | Sources the student has already identified | `Smith (2023), Jones & Brown (2024)` |
| `{{input.target_source_count}}` | No | Number of sources to aim for | `20` |
| `{{input.preliminary_position}}` | No | Student's preliminary position on the topic | `I think social media increases polarisation through echo chambers` |
| `{{input.section_name}}` | No | Which section to draft | `Introduction` |
| `{{input.section_word_count}}` | No | Target word count for the section being drafted | `800` |
| `{{input.student_concerns}}` | No | Any specific concerns about the draft | `I'm not sure my conclusion is strong enough` |

## Outputs

| Name | Description |
|------|-------------|
| A focused, arguable research question | A focused, arguable research question with defined scope |
| A structured literature map using literature-map-template | A structured literature map using literature-map-template |
| A thesis statement | A thesis statement with three supporting arguments and anticipated counterarguments |
| Complete draft sections | Complete draft sections |
| Submission-ready paper | Submission-ready paper with revision notes |

## Setup

Before running this workflow:

1. No external services required — paste your content directly and provide any supporting context as inputs or source nodes.
2. Review the included documents, assets, or source nodes and customise them to match your team, brand, or domain conventions where needed.
3. No specific AI provider or API key is required beyond your configured skrptiq LLM provider.

## Provider Notes

- The longer synthesis stages benefit from a model with strong reasoning and a generous context window.
- Extraction, classification, and formatting steps generally run well on smaller or faster models.
- Because there are no vendor-specific integrations here, provider choice is mostly a trade-off between speed, quality, and cost.

## Example Input

To test this workflow immediately after import:

```
A Broad Subject Area: "Paste the relevant brief, notes, source material, or dataset here."
```

