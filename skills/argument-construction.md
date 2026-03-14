---
type: skill
id: argument-construction
title: Argument Construction
description: "Builds logically sound academic arguments with clear claims, evidence chains, and counterargument handling"
tags: [Production, Tested]
connections:
  - target: llm-service
    type: runs_on
  - target: academic-writing-standards
    type: references
metadata:
  estimated_duration: "5 minutes per argument"
  avg_tokens: 3000
  trigger: manual
---

## Argument Construction

This skill enables the construction of rigorous academic arguments suitable for research papers, dissertations, and scholarly essays. It operates on the Toulmin model of argumentation, adapted for academic writing contexts.

### Core Capabilities

**Claim Formulation:** Given a research question and preliminary evidence, this skill formulates clear, specific, and contestable claims. Each claim is tested against three criteria: (1) it makes a substantive assertion rather than stating a fact, (2) it is specific enough to be supported within the available word count, and (3) it engages meaningfully with the existing literature.

**Evidence Chain Construction:** For each claim, this skill builds an evidence chain that links the claim to supporting data through warrants (reasoning that connects evidence to claim). It identifies the strongest available evidence from the student's source material, ranks evidence by relevance and strength, and flags any claims that lack sufficient evidential support.

**Counterargument Mapping:** Every strong argument anticipates objections. This skill identifies the two or three most likely counterarguments to each claim, evaluates their strength, and constructs appropriate rebuttals. It distinguishes between counterarguments that can be refuted, those that require concession, and those that necessitate qualification of the original claim.

**Argument Sequencing:** Academic papers require arguments to build upon one another. This skill determines the optimal ordering of arguments within a paper, considering logical dependency (does argument B rely on accepting argument A?), rhetorical impact (which ordering is most persuasive?), and disciplinary conventions (does the field expect a particular structure?).

### Constraints

- All arguments must be grounded in cited evidence. This skill will not construct arguments from assertion alone.
- Counterarguments are treated seriously, not as straw men. If a counterargument is genuinely strong, the skill will recommend qualifying the claim rather than offering a weak rebuttal.
- The skill respects disciplinary differences. An argument in philosophy follows different conventions from one in sociology or natural science. The student's discipline and the `academic-writing-standards` source inform the argument's structure.
- Arguments are constructed at the level appropriate to the student's stated academic level (undergraduate, postgraduate taught, postgraduate research). A first-year undergraduate is not expected to produce the same depth of argumentation as a doctoral candidate.

### Output Format

Each constructed argument is returned as a structured block:

- **Claim:** The specific assertion being made
- **Evidence:** Numbered list of supporting evidence with source references
- **Warrant:** The reasoning connecting the evidence to the claim
- **Counterarguments:** Anticipated objections with rebuttals or concessions
- **Strength rating:** High / Medium / Low, with justification
- **Position in sequence:** Where this argument sits in the overall paper structure
