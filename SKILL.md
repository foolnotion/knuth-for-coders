---
name: knuth-for-coders
description: Use when writing or reviewing prose about code for a senior developer audience (explanations, PR descriptions, review comments, incident writeups, docstrings) and a precise, source-grounded discipline on naming, structure, and claims is wanted. Complements general senior-developer writing guidance with rules adapted from Knuth's course on mathematical exposition.
---

# Knuth for Coders

Thirty rules adapted from Donald Knuth, Tracy Larrabee, and Paul Roberts,
*Mathematical Writing* (MAA Notes 14, 1989): the transcript of a Stanford
course on mathematical exposition, including guest lectures by Herb Wilf,
Jeff Ullman, Leslie Lamport, Nils Nilsson, Mary-Claire van Leunen, Paul
Halmos, and Rosalie Stemer. Mathematics and code both traffic in objects
that must be named precisely and claims that must be justified precisely;
these rules carry that discipline over.

Full source citations and provenance: see README.md in this repository.
A styled version of this material lives at:
https://claude.ai/code/artifact/f0c2eeec-0c5b-46c9-92dd-93c0231a0f89

The two rules everything below is a special case of (Halmos): organize the
material. Do not distract the reader.

## Naming and notation

1. State the relationship between two identifiers in words. Two backticked
   names placed side by side force the reader to guess the connective.
2. Don't open a sentence with a bare code token. Give the reader a noun to
   hang it on first: "The retry counter (`retries++`) increments before..."
   not "`retries++` happens before...".
3. Write the connective in English inside prose; don't let `&&`, `=>`, or
   other operator symbols stand in for "and", "or", "implies".
4. Use one name per concept for the whole response, and use it for that
   concept only. Renaming something mid-explanation (counter, then tally,
   then running total) forces a re-verification that should have been free.
5. Stop indexing and start naming once there's something to distinguish.
   `producer`/`consumer` carries the distinction the name needs; `client1`/
   `client2` makes the reader keep re-deriving it.

## Sentence and paragraph mechanics

6. Prefer a direct statement or "we" over passive voice, and skip
   first-person hedging. "Moving the lock outside the loop removes the
   contention," not "it was determined that the lock should be moved."
7. Read a nontrivial explanation once at normal reading speed before
   sending it. Rhythm problems surface at speed, not while composing.
8. Use matching sentence templates for genuinely parallel items (three
   renamed functions described the same way signals they're the same kind
   of change). Vary the template when the items actually differ.
9. Don't hand the reader a bare list of facts and let them do the
   connecting. A bullet list of "changed X, changed Y, changed Z" with no
   commentary is the homework-proof failure mode: complete, unusable.
10. State an important definition or decision twice, in different words.
    Restating it reinforces it for a reader who is skimming, which is most
    readers most of the time.

## Structure, order, and motivation

11. Before the diff or the fix, say what problem it solves and why it
    matters now. Keep the reader uppermost in mind: what do they know
    already, what do they expect next, and why?
12. Write so the explanation holds together if the reader skips every code
    block. Most readers skim past anything that looks like a snippet on
    the first pass; if the surrounding prose doesn't carry the argument
    alone, the code isn't carrying it either.
13. Pull the load-bearing line, config value, or command onto its own
    line if it will be referred back to later in the same response.
14. Write sentences that resolve left to right without a re-read. "Fix the
    bug in the payment retry logic that only manifests under load" forces
    a backtrack; "Fix the payment retry bug; it only manifests under load"
    doesn't.
15. Introduce a piece of the explanation at the moment the reader needs
    it, not necessarily the order the code executes in. The best order for
    exposition and the best order for a machine to run something are
    frequently different orders.

## Audience and precision

16. Unpack a stacked noun-modifier before it reaches three deep.
    "Distributed multi-tenant async job queue rebalancing timeout" is
    precise and unreadable; say what modifies what.
17. Write for a competent engineer who doesn't already have this specific
    context, not for someone who was already in the incident channel.
    Writing for the novice ends up serving the expert too; jargon
    calibrated to insiders serves nobody who wasn't already there.
18. Say what a variable is before using its bare name: "the retry counter
    `attempts`," not just "`attempts`." The type or role is often the
    information the reader actually needed.
19. Give "this" an explicit antecedent. "This ordering assumption breaks
    under concurrent writes," not "this breaks under concurrent writes."
20. Keep a definition next to its use. If a term was defined earlier in a
    long response, restate it briefly where it's actually used rather than
    trusting the reader to remember it from several paragraphs back.
21. Place modifiers where they belong, and say precisely what's true.
    "Only the service retries on 5xx" and "the service only retries on
    5xx" are different claims. "Idempotent" and "safe to retry under this
    one condition" are different claims. Cut hedges that add no
    information: "basically", "essentially", "in the context of", an
    unearned "really".

## Examples

22. Show one worked example instead of describing behavior abstractly. A
    reader generalizes from a good example faster than they specialize
    from an abstraction.
23. Test the explanation against the example before sending it. If the
    stated reasoning doesn't survive contact with the concrete case being
    discussed, the reasoning is wrong.
24. Use several examples, including ones that don't produce the
    interesting result. A single cherry-picked success case reads as
    staged; the boundary where a fix stops applying is often more
    convincing than the happy path.

## Equal billing for edge cases

25. Give edge cases and failure modes the same expository care as the main
    path. A perfunctory bullet list of caveats at the very end reads the
    way error-handling code written last usually reads: bolted on.
26. State a claim's actual scope instead of a stronger one that sounds
    cleaner. "Fixed" and "fixed for this reproduction" are different
    claims; say the narrower true thing.

## Revision and review

27. Give a nontrivial explanation one self-check pass, then send it. Any
    writing can be improved; at some point it has to go out the door.
28. Don't paste the same boilerplate caveat into a new context without
    checking it still fits. The new situation almost certainly has a
    different emphasis than the one the boilerplate was written for.
29. It's fine to give the simplified model first and add the precise
    caveats after, as long as the caveats actually arrive. Front-loading
    every exception before the reader has the shape of the idea loses them
    before the idea lands.
30. When reviewing someone else's code, deliver a complete picture: is it
    correct, is it a genuine improvement, and what are its limits. Deliver
    it as help for the author's next piece of work, not a scored complaint
    list.
