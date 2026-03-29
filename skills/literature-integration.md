---
type: skill
id: literature-integration
title: Literature Integration
description: "Synthesises academic sources into coherent literature reviews with proper citation integration and critical analysis"
tags: [Production, Tested, Academic, Citations, Research]
connections:
  - target: llm-service
    type: runs_on
  - target: academic-writing-standards
    type: references
metadata:
  estimated_duration: "5-10 minutes per section"
  avg_tokens: 3500
  trigger: manual
---

## Literature Integration

This skill handles the synthesis of academic sources into coherent, critically engaged prose. It moves beyond simple summarisation to produce genuine literature integration — identifying patterns, tensions, and gaps across multiple sources.

### Core Capabilities

**Source Synthesis:** Given a set of academic sources (provided as summaries, abstracts, or key findings), this skill identifies thematic connections, methodological patterns, and points of disagreement. It groups sources into coherent thematic clusters and determines the narrative thread that connects them to the student's research question.

**Citation Weaving:** This skill integrates citations naturally into academic prose. It employs a mix of integral citations (where the author's name forms part of the sentence, e.g., "Smith (2023) argues that...") and non-integral citations (where the citation appears parenthetically, e.g., "Recent findings suggest... (Smith, 2023)"). The balance is adjusted based on disciplinary norms and the rhetorical purpose of each passage.

**Critical Engagement:** Rather than simply reporting what each source says, this skill evaluates sources critically. It identifies methodological strengths and limitations, assesses the relevance of findings to the current research question, notes where findings conflict or converge, and positions each source within the broader scholarly conversation.

**Gap Identification:** A strong literature review does more than summarise — it identifies what is missing. This skill analyses the collected sources to find underexplored questions, methodological approaches not yet tried, populations or contexts not yet studied, and theoretical tensions not yet resolved. These gaps provide the justification for the student's own research.

**Narrative Structure:** Literature reviews require a clear organisational logic. This skill can structure reviews thematically (grouped by topic or concept), chronologically (tracing the development of an idea over time), methodologically (grouped by research approach), or theoretically (organised around competing frameworks). The choice depends on the discipline, the research question, and the sources available.

### Constraints

- Sources must be properly attributed. This skill will not present ideas without citation.
- Direct quotation is used sparingly and only when the original wording is significant. Paraphrase is the default mode.
- The skill distinguishes between primary and secondary sources and handles each appropriately.
- It does not fabricate sources or citations. All referenced works must come from the student's provided source list.
- Integration density varies by section: a dedicated literature review chapter is denser than a contextualising paragraph in the introduction.

### Output Format

Integrated literature passages are returned with:
- Inline citations in the student's chosen referencing style (APA, Harvard, Chicago, MLA, or Vancouver)
- A list of all sources cited in the passage, for cross-referencing
- Notes on which sources are central versus peripheral to the argument
- Flagged gaps or tensions that the student may wish to address
