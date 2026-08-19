# Field notes

Notes from using this skill on real documents. Added in this fork, not upstream.

Writing craft only. Nothing about the documents themselves.

---

## 2026-08-19 — first pass, a vendor-facing technical question list

About 2,400 words, drafted by an AI assistant over several sessions, then audited against the skill's pattern list.

**Measured before and after rather than reading and judging.** A short script counted the tells, and the count is what showed the scale of the problem.

| | Before | After |
| --- | --- | --- |
| Em-dashes | 36 | 0 |
| Bold spans | 36 | 18 |
| "load-bearing" | 1 | 0 |
| "genuinely" | 2 | 0 |
| "exactly" | 4 | 0 |
| Sentences in the 15–25 word band | 36% | 31% |

### What the pass taught

**Density is the signal, not the count.** Thirty-six em-dashes sounds bad but means little on its own. One every 65 words is the number that made it obvious. Worth normalising any count against document length before deciding whether it matters.

**Rewrite, do not substitute.** Swapping an em-dash for a comma keeps the sentence shape that wanted the em-dash in the first place. Several sentences had to be broken in two. The em-dash was often hiding a run-on, so removing it improved the argument rather than just the punctuation, and the questions in the document read more directly afterwards.

**Bold overuse tracked em-dash overuse exactly, 36 each.** That is unlikely to be coincidence. Both look like reaching for emphasis instead of using sentence structure to carry it. Worth checking them together, and suspecting a common cause when both are high.

**Keep the false positives.** "Worth confirming it cannot reach production" and "That is a good position to be in" both tripped pattern checks and both are ordinary English. Stripping every flagged phrase produces stilted prose, which is its own tell. The list is a prompt to look at a sentence, not a find-and-replace.

**Counting and reading catch different things.** After the rewrite the counts were clean, so it was tempting to stop. Reading the document end to end then found three defects from earlier programmatic edits: an introduction saying "these four questions" above six of them, two sections that read as duplicates without saying how they differed, and a missing section separator. Heading-sequence checks and cross-reference checks had both passed while the prose was wrong.

That last one generalises. **Structural edits break prose invisibly.** Any renumbering, section insertion or find-and-replace across a document needs a read-through afterwards, not just a structural validation. The validators confirm the skeleton and say nothing about whether the sentences still make sense.

### Additions worth considering upstream

- A density metric rather than a raw count, normalised per thousand words.
- Bold-span density as a companion check to em-dash density, given how closely they tracked here.
- A note that mechanical edits to a document warrant a full read afterwards. This is adjacent to the skill's "over-polishing" category but distinct: the failure is not polish, it is a structural edit leaving stale prose behind.
