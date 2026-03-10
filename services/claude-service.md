---
type: service
id: claude-service
title: Claude Service
description: "Anthropic Claude integration for academic research paper generation, providing argument analysis, literature synthesis, and academic writing assistance"
tags: [Production, Tested]
connections:
  - target: anthropic-claude
    type: runs_on
metadata:
  provider: "anthropic"
  model: "claude-sonnet"
  context_window: 200000
---

## Claude Service — Research Paper Pipeline

This service node defines how the Research Paper Pipeline uses Anthropic Claude for academic writing assistance.

### Usage Within This Skrpt

Claude serves as the primary language model for all stages of the research paper pipeline:

- **Topic Narrowing:** Evaluating the breadth of a subject area and generating focused research questions. Requires understanding of academic disciplines, feasibility assessment, and scope calibration.
- **Literature Mapping:** Classifying sources into thematic clusters, identifying relationships between authors and works, and detecting gaps in coverage. Benefits from Claude's broad knowledge of academic fields and research methodologies.
- **Thesis Construction:** Formulating defensible claims, constructing evidence chains, and anticipating counterarguments. Requires logical reasoning and familiarity with argument structures across disciplines.
- **Section Drafting:** Producing academic prose with integrated citations, appropriate hedging, disciplinary register, and proper paragraph architecture. The longest and most token-intensive stage.
- **Paper Polishing:** Multi-pass review for argument coherence, flow, citation accuracy, and stylistic consistency. Requires careful attention to detail and the ability to maintain consistency across a long document.

### Configuration Notes

- **Temperature:** Keep at 0.3-0.5 for drafting stages to ensure coherent, focused output. Raise to 0.6-0.7 for topic narrowing where creative exploration is beneficial.
- **Context window:** The polishing stage may require the full paper in context. For papers exceeding 8,000 words, consider processing in overlapping sections with a style consistency check at the end.
- **System prompt:** Each prompt node contains its own complete instructions. No additional system prompt is required.

### Important Limitations

- Claude cannot access academic databases or verify that specific papers exist. All source material must be provided by the student.
- Citation formatting follows the rules embedded in the prompts but should be cross-checked against the relevant style guide.
- Claude's knowledge has a training cutoff. Very recent publications will not be known to the model.
