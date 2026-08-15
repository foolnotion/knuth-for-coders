# Knuth for Coders

A Claude Code skill: twenty-four rules for writing prose about code
(explanations, PR descriptions, review comments, incident writeups,
docstrings), adapted from a course on mathematical exposition. Started as
thirty rules; six were trimmed as duplicates of the companion
`senior-developer-writing` skill and folded into it instead. See
[Relationship to senior-developer-writing](#relationship-to-senior-developer-writing).

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
matching the MAA's own posted copy at `maa.org/wp-content/uploads/2024/10/NTE14-1.pdf`).
The document itself is not redistributed here; only the extracted rules and
short paraphrases are, in `SKILL.md`.

**Method.** The full PDF was read section by section. Two kinds of material
were pulled out:

- The 27-point numbered list that opens the course (§1, "Notes on Technical
  Writing"), covering notation, sentence mechanics, and structure.
- The rules embedded in the later guest lectures and homework critiques
  (§12, §15, §25–43), which restate and extend the opening list from
  different angles: Wilf on getting the reader's attention, Ullman on
  keeping definitions near their use, Lamport on examples keeping you
  honest, Nilsson on modeling the reader, van Leunen on sentence rhythm,
  Stemer on precise modifier placement, Halmos on the two rules everything
  else reduces to.

Each of the 24 rules in `SKILL.md` traces to one or more specific points in
that material. The mapping below gives the section number (§) for each;
section numbers refer to the table of contents in the source PDF.

| SKILL.md rule | Source |
|---|---|
| 1–3 | §1, points 1–3 (word/symbol separation, sentence-opening symbols, logic symbols in prose) |
| 4 | §1, point 15 (subscript discipline) |
| 5 | §1, point 6 ("we" vs. passive vs. "I") |
| 6 | §1, point 7; §7 (Lamport: read at speed) |
| 7 | §1, point 9 (vary structure, use parallelism deliberately) |
| 8 | §1, point 11 (state definitions twice) |
| 9 | §1, point 12; §27 (Wilf); §34 (Nilsson) |
| 10 | §1, point 13 (readers skim formulas) |
| 11 | §1, point 16 (display and label important formulas) |
| 12 | §10–11 (WEB / literate-programming exposition order) |
| 13–14 | §1, point 26; §13 (AWK manual, writing for the novice) |
| 15 | §30 (Ullman: forbids non-referential "this") |
| 16 | §41 (Stemer: modifier placement, hedge words) |
| 17, 19 | §30 (Ullman: use lots of examples); §27 (Wilf: motivation in moderation) |
| 18 | §31 (Lamport: examples keep you honest) |
| 20 | §12 (WEB error-handling modules) |
| 21 | §5 (precision: "not nonincreasing" vs. "increasing") |
| 22 | §6 (Knuth: ship it eventually) |
| 23, 24 | §34 (Nilsson: avoid recycling; simplify, then add detail back) |

## Relationship to senior-developer-writing

This repository's rules were compared against the companion
`~/.claude/skills/senior-developer-writing` skill, which covers response
structure, debugging workflow, risk ordering, and hallucination guardrails:
material entirely outside this book's scope (Knuth's course predates that
failure mode by decades). Six rules turned out to duplicate rules already
in that skill and were removed from here on 2026-08-15, with their content
folded into `senior-developer-writing` instead:

| Removed from here | Source | Folded into senior-developer-writing |
|---|---|---|
| naming consistency, "one name per concept" | §1, point 14 | Core Rules #6 |
| don't hand the reader a bare fact list | §1, point 10 | Core Rules #8 |
| left-to-right readability (generic form) | §1, point 17 | Core Rules #9 |
| state the type of a variable before using it | Ullman §30 | Core Rules #5 |
| keep a definition next to its use | Ullman §30 | Core Rules #5 |
| review should give a complete, non-scorekeeping picture | §15 (referee's report) | Review section |

The three rules that remained closest to the code-writing craft of naming,
sentence rhythm, and examples stayed here; the four blocks with no
equivalent in `senior-developer-writing` (examples as evidence, the
boilerplate-reuse warning, the simplify-then-refine ordering, and the
read-at-speed check) were ported into it in the same pass.

**Adaptation, not transcription.** The source is about theorems and proofs;
none of its examples are about code. Every "before/after" pair in
`SKILL.md` was written for this project to illustrate the underlying rule
in a code-writing context (PR descriptions, error messages, review
comments) and does not appear in the source.

**A styled, fully-cited version** of this material, with the original
Knuth "Bad/Good" convention and per-rule source citations, is published at:
<https://claude.ai/code/artifact/f0c2eeec-0c5b-46c9-92dd-93c0231a0f89>

## Using this as a Claude Code skill

Copy or symlink this directory into your skills path, e.g.:

```sh
ln -s ~/projects/knuth-for-coders ~/.claude/skills/knuth-for-coders
```

Claude Code picks up `SKILL.md`'s frontmatter (`name`, `description`) and
lists it as an invocable skill; it is also available for Claude to select
proactively when its description matches the task.
