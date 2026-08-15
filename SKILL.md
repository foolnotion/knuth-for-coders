---
name: knuth-for-coders
description: Use when writing, editing, reviewing, explaining, or debugging technical material for senior software developers, especially LLM responses about code, architecture, incidents, tests, and patches. Applies Knuth-inspired clarity, evidence, and safe engineering-response discipline.
---

# Knuth for Coders

Write for a capable, time-constrained developer who is reading beside an
editor, terminal, diff, test output, or incident dashboard.

Adapted from the reader-first discipline in Donald Knuth, Tracy Larrabee, and
Paul Roberts, *Mathematical Writing* (MAA Notes 14, 1989). The source governs
the prose rules below; the debugging, risk, and verification rules extend that
discipline to modern LLM-assisted software engineering.

Optimize for the reader's ability to reconstruct the reasoning, assess the
tradeoffs, and act safely. Do not optimize for minimum length at the expense
of causal reasoning, conditions, or verification.

## Core Rules

1. Lead with the outcome: the diagnosis, finding, recommendation, or result.
2. State the purpose before explaining the mechanism.
3. Separate observations, inferences, assumptions, and recommendations.
4. Support claims with local evidence: file paths, symbols, logs, tests,
   commands, or clearly labeled assumptions.
5. Define non-obvious terms, identifiers, and notation before relying on them.
6. Use one name for one concept. Preserve the codebase's established
   vocabulary unless a distinction is intentional.
7. Explain behavior, invariants, side effects, failure paths, and tradeoffs;
   do not narrate obvious syntax line by line.
8. Connect nontrivial code, commands, formulas, and claims with prose that
   says what they establish and why they matter.
9. Make sentences understandable from left to right. Prefer direct verbs,
   concrete subjects, and unambiguous references over dense noun stacks and
   vague pronouns.
10. Be concise by removing filler, not reasoning. Keep words such as
    "because", "if", "unless", and "therefore" when they expose a
    dependency or constraint.
11. Do not call something obvious, robust, scalable, safe, or production-ready
    without stating the observable property that justifies the claim.
12. Never invent repository state, command output, APIs, benchmarks, or test
    results. State exactly what was verified and what remains unverified.
13. Do not reuse a caveat, disclaimer, or explanation verbatim across
    responses. Check that it still fits the current context; the new
    situation almost certainly has a different emphasis than whatever the
    boilerplate was originally written for.

## Knuth-Derived Prose Craft

- State the relationship between two identifiers in words. Do not place two
  backticked names or expressions side by side and make the reader infer the
  connective.
- Do not open a sentence with a bare code token. Give the reader a noun first:
  write "The retry counter (`retries++`) increments...", not "`retries++`
  increments...".
- Write connectives in English inside prose. Do not let `&&`, `=>`, or another
  operator stand in for "and", "or", or "implies".
- Prefer role names such as `producer` and `consumer` over arbitrary indexes
  such as `client1` and `client2` when the roles are what distinguish them.
- Prefer a direct statement or inclusive "we" over passive voice and
  first-person hedging. Use parallel syntax for genuinely parallel ideas, but
  vary sentence shape when the ideas differ.
- State an important definition or decision twice in complementary forms when
  that helps a skimming reader: once formally or operationally, then once in
  plain language.
- Write so the explanation holds together when a reader skips every code
  block. Pull a load-bearing line, configuration value, or command onto its
  own line if it will be referenced later.
- Introduce information when the reader needs it, not necessarily in execution
  order. Expository order and runtime order are often different.
- Unpack dense noun stacks. Write for a competent engineer without this exact
  local context, not only for people who already know the incident or code.
- Give "this" an explicit antecedent. Place modifiers where they make the
  intended scope exact, and remove hedges that add no information.
- Give edge cases and failure modes the same explanatory care as the main
  path. State the narrowest true scope: "fixed for this reproduction" is not
  the same claim as "fixed".

## Response Structure

Use the smallest useful subset of this sequence:

```text
Context -> finding -> cause -> change or recommendation -> consequences -> verification
```

- Start responses with the answer, not generic background or a restatement of
  the request.
- Give each paragraph one main job: establish a fact, explain a cause, state a
  change, or identify a risk.
- Use bullets for independent findings, risks, or steps. Use prose for causal
  arguments.
- State the next action explicitly: fix, test, investigate, accept, or defer.
- Keep headings and citations grammatically optional; the surrounding prose
  must make sense without them.
- For a genuinely complex mechanism, it is acceptable to state a simplified
  model first and follow immediately with the precise caveats in the same
  response. The caveats must still arrive; do not stop at the simplification.

## Code And Architecture

- State the contract at boundaries such as APIs, queues, databases, files,
  caches, and third-party services: inputs, outputs, validation, and failure
  behavior.
- Call out non-obvious control flow: transactions, retries, fallback paths,
  concurrency coordination, idempotency, authorization, caching, and cleanup.
- Prefer the smallest correct change. Do not introduce abstractions,
  dependencies, configuration, or compatibility layers without a concrete
  need.
- Preserve existing project conventions for naming, errors, dependencies,
  tests, and framework patterns. Explain deliberate deviations.
- Use code examples to show contracts and decisions. Label incomplete examples
  as schematic rather than presenting them as executable.
- Keep comments rare and useful: preserve an invariant, constraint, or
  non-obvious reason; never restate self-evident code.

## Examples

- Prefer one worked example (a concrete input, output, or before/after) over
  describing behavior abstractly. A reader generalizes from a good example
  faster than they specialize from an abstraction.
- Verify an explanation against its own example before presenting it. If the
  stated reasoning doesn't survive contact with the concrete case discussed,
  the reasoning is wrong, not the example.
- Where useful, include a case that does not produce the interesting result,
  not only the success case. The boundary where a fix stops applying is often
  more convincing than the happy path, and prevents the example from reading
  as cherry-picked.

## Risk And Uncertainty

- Surface security, data integrity, authorization, race-condition,
  compatibility, and operational risks before lower-impact details.
- State assumptions only when a different answer follows if they are false.
- Be precise about conditions: say "under concurrent requests" or "when the
  cache is shared across replicas" rather than overgeneralizing.
- Do not add backwards compatibility speculatively. Require an external
  consumer, persisted data, shipped behavior, or explicit requirement.
- For consequential changes, identify migration, rollback, and failure-mode
  implications.

## Debugging

- Begin with the most likely root cause supported by the evidence, not a
  generic troubleshooting checklist.
- Separate reproduction, observation, hypothesis, and fix.
- Rank alternative hypotheses by evidence and impact.
- Provide the smallest discriminating verification step: a targeted test,
  command, query, trace, or log inspection that differentiates the leading
  hypotheses.
- Do not recommend broad changes before the failure has been isolated unless
  immediate mitigation is required.

## Review

- Lead with actionable findings ordered by severity.
- For each finding, give the location, failure mode, triggering condition, and
  consequence.
- Focus on behavior and risk, not personal taste. Flag style only when it
  affects correctness, maintainability, consistency, performance, security,
  accessibility, or project conventions.
- If no substantive issue is found, say so, then note material assumptions or
  testing gaps.
- Write review comments as help for the author's next change, not as a scored
  list of complaints.

## Final Check

Before responding, check:

- Does the opening state the result or recommended action?
- Can the reader distinguish fact from inference and proposal?
- Is each important claim supported or clearly conditional?
- Are all non-obvious identifiers and assumptions understandable locally?
- Does every command or code block have a purpose and expected result?
- Are failure modes, side effects, and verification steps clear?
- Did concision remove filler rather than necessary reasoning?
- Does the response report exactly what was and was not verified?
- Read it once at normal pace: does any sentence need a re-read? Restructure
  it rather than trusting the reader to parse it twice.
