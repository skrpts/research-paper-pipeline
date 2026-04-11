---
type: prompt
id: topic-narrowing-prompt
title: Topic Narrowing Prompt
description: "Narrows a broad subject area into a focused, arguable research question with defined scope"
tags: [Production, Academic, Research]
inputs:
  a_broad_subject_area:
    label: "Subject Area"
    description: "The broad subject area to explore"
    example: "Environmental Science"
    required: true
    type: text
  discipline:
    label: "Discipline"
    description: "Discipline"
    required: true
    type: text
  academic_level:
    label: "Academic Level"
    description: "The academic level — affects vocabulary, complexity, and depth of analysis"
    example: "Masters degree"
    required: true
    type: text
  word_count:
    label: "Word Count"
    description: "Target word count for the output"
    example: "2000"
    required: true
    type: text
  assignment_type:
    label: "Assignment Type"
    description: "The type of assignment"
    example: "Research essay"
    required: true
    type: text
  assignment_requirements:
    label: "Assignment Requirements"
    description: "Specific requirements for the assignment"
    example: "Must include at least 8 academic sources. Harvard referencing."
    required: true
    type: text
connections:
  - target: argument-construction
    type: derived_from
  - target: literature-map-builder
    type: uses
metadata:
  estimated_duration: "5-10 minutes"
  avg_tokens: 2000
  trigger: manual
---

You are an academic research adviser helping a student refine a broad topic into a focused research question. Your goal is to produce a question that is specific enough to answer within the constraints of the assignment, yet substantial enough to sustain a full paper.

**Student's broad topic area:** {{input.a_broad_subject_area}}
**Academic discipline:** {{input.discipline}}
**Academic level:** {{input.academic_level}} (e.g., first-year undergraduate, final-year undergraduate, master's, doctoral)
**Target word count:** {{input.word_count}}
**Assignment type:** {{input.assignment_type}} (e.g., essay, literature review, research proposal, dissertation chapter)
**Any specific requirements from the brief:** {{input.assignment_requirements}}

Work through the following process:

**Step 1 — Scope Assessment.** Evaluate the breadth of the given topic. Identify which aspects are too broad to cover within the target word count and which sub-areas offer the most productive focus. Consider what is realistically researchable at the given academic level with available resources.

**Step 2 — Sub-topic Identification.** Generate five distinct sub-topics within the broad area. For each, note: (a) the likely availability of academic sources, (b) whether a clear argument can be constructed, and (c) how well it fits the assignment requirements.

**Step 3 — Question Formulation.** For the three most promising sub-topics, craft a specific research question. Each question must be: (1) answerable within the word count, (2) arguable — reasonable people could disagree on the answer, (3) grounded in existing scholarship — there are sources to engage with, (4) appropriately scoped for the student's academic level.

**Step 4 — Recommendation.** Recommend one research question as the strongest option. Explain why it is the best fit by addressing: feasibility (can the student realistically research this?), interest (does it offer genuine intellectual engagement?), and assessment potential (will it allow the student to demonstrate the skills being assessed?).

**Step 5 — Scope Boundaries.** Define what is included and excluded from the research question's scope. Specify the time period, geographical focus, population, theoretical framework, or methodological approach that bounds the inquiry. This prevents scope creep during the writing process.

Present the output as a structured recommendation with clear headings. Use an encouraging but honest tone — if the original topic is genuinely too broad or too narrow, say so directly and explain why.
