# Knuth for Coders

A Claude Code skill: thirty rules for writing prose about code (explanations,
PR descriptions, review comments, incident writeups, docstrings), adapted
from a course on mathematical exposition.

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

Each of the 30 rules in `SKILL.md` traces to one or more specific points in
that material. The mapping below gives the section number (§) for each;
section numbers refer to the table of contents in the source PDF.

| SKILL.md rule | Source |
|---|---|
| 1–3 | §1, points 1–3 (word/symbol separation, sentence-opening symbols, logic symbols in prose) |
| 4 | §1, point 14 (consistent notation) |
| 5 | §1, point 15 (subscript discipline) |
| 6 | §1, point 6 ("we" vs. passive vs. "I") |
| 7 | §1, point 7; §7 (Lamport: read at speed) |
| 8 | §1, point 9 (vary structure, use parallelism deliberately) |
| 9 | §1, point 10 (homework-list style vs. running commentary) |
| 10 | §1, point 11 (state definitions twice) |
| 11 | §1, point 12; §27 (Wilf); §34 (Nilsson) |
| 12 | §1, point 13 (readers skim formulas) |
| 13 | §1, point 16 (display and label important formulas) |
| 14 | §1, point 17 (left-to-right readability) |
| 15 | §10–11 (WEB / literate-programming exposition order) |
| 16–17 | §1, point 26; §13 (AWK manual, writing for the novice) |
| 18 | §30 (Ullman: state the types of your variables) |
| 19 | §30 (Ullman: forbids non-referential "this") |
| 20 | §30 (Ullman: keep definitions and uses close together) |
| 21 | §41 (Stemer: modifier placement, hedge words) |
| 22, 24 | §30 (Ullman: use lots of examples); §27 (Wilf: motivation in moderation) |
| 23 | §31 (Lamport: examples keep you honest) |
| 25 | §12 (WEB error-handling modules) |
| 26 | §5 (precision: "not nonincreasing" vs. "increasing") |
| 27 | §6 (Knuth: ship it eventually) |
| 28, 29 | §34 (Nilsson: avoid recycling; simplify, then add detail back) |
| 30 | §15 (referee's report: complete algorithm, proof, limitations) |

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
