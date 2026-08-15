# Knuth for Coders

A Claude Code and OpenCode skill for writing, reviewing, explaining, and
debugging technical material for senior software developers. It applies the
reader-first discipline of mathematical exposition to LLM-assisted work on
code, architecture, incidents, tests, patches, and documentation.

The skill covers two complementary concerns:

- How to say it: precise naming, readable sentence structure, motivation,
  worked examples, careful scope, and revision.
- What an engineering response must establish: evidence, assumptions,
  verification, risk ordering, debugging workflow, and actionable review
  findings.

The first concern is a direct adaptation of the source's prose discipline.
The second applies its reader-first standard to risks and workflows that arise
when an LLM operates in a contemporary codebase.

## Provenance

**Source.** Donald E. Knuth, Tracy Larrabee, and Paul M. Roberts,
*Mathematical Writing*, MAA Notes Number 14 (Mathematical Association of
America, 1989). The report is the edited transcript of Stanford CS 209,
"Mathematical Writing," taught by Knuth in autumn quarter 1987, plus guest
lectures by Herb Wilf, Jeff Ullman, Leslie Lamport, Nils Nilsson,
Mary-Claire van Leunen, Rosalie Stemer, and Paul Halmos. 119 pages.

**Copy consulted.** PDF retrieved 2026-08-15 from
`https://jmlr.csail.mit.edu/reviewing-papers/knuth_mathematical_writing.pdf`
(a scan used by the Journal of Machine Learning Research to train reviewers,
matching the MAA's posted copy at
`maa.org/wp-content/uploads/2024/10/NTE14-1.pdf`). The document itself is not
redistributed here; the skill contains extracted rules and paraphrases.

**Adaptation.** The source is about mathematical exposition, not software
engineering. Its reader-modeling, notation, sentence, motivation, example,
precision, and revision guidance is adapted here for code-facing prose. The
rules on evidence, verification, risk, debugging, and review extend the same
reader-first discipline to modern LLM-assisted development; they are not
claimed as rules from Knuth's course.

The skill's prose guidance principally draws on:

- The 27-point list in §1, "Notes on Technical Writing," covering notation,
  sentence mechanics, and structure.
- §10-11 on exposition order in WEB and literate programming.
- §27 on reader motivation and examples.
- §30-31 on definitions, types, examples, and using examples to test prose.
- §34 on modeling the reader, avoiding boilerplate reuse, and simplifying
  before refining.
- §41 on exact modifier placement and hedging.
- §15 on complete, constructive review.

## Installation

Claude Code discovers skills in `~/.claude/skills/`; OpenCode also discovers
external Claude skills there. Clone the repository, then create a symlink:

```sh
ln -s ~/projects/knuth-for-coders ~/.claude/skills/knuth-for-coders
```

Restart Claude Code or OpenCode after installation so it discovers the new
skill.
