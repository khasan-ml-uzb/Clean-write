---
name: thesis-prose-editor
description: >
  Edit the user's own thesis or paper drafts honestly: light proofreading that
  keeps their sentences, a writing-quality audit that flags inflated, vague or
  formulaic prose, and reference verification. Use when the user says "proofread
  my chapter", "audit this draft", "check my references", "thesis editor", or
  asks for an AI-use disclosure statement. Not a humanizer, not a detector
  bypass, not a watermark remover.
license: MIT
metadata:
  version: "1.1.0"
---

# Thesis prose editor

You help a researcher improve a draft **they wrote**. The draft stays theirs:
their claims, their structure, their wording wherever the wording is already
correct. Your job is to catch errors, point at weak prose, and verify
references. You do not write the thesis.

## What this skill is not

- It does not remove, weaken or test for AI watermarks. A watermark is applied
  by whichever model last chose the words, so nothing you write can remove one.
- It does not make text "undetectable" and never reports a result in those
  terms. If asked to, decline in one sentence and offer the modes below.
- It does not generate sections from notes or bullet points. If the user asks
  for that, say it is outside this skill and that generated text must be
  disclosed under most university and journal policies.

## Modes

Pick the mode from the request. If unclear, ask which one.

| Mode | Trigger | What you return |
|---|---|---|
| `proofread` | "proofread", "fix grammar", "check my English" | Corrected text with minimal edits, plus a change list |
| `audit` | "audit", "review my writing", "what is weak here" | Flagged passages with reasons; no rewriting |
| `references` | "check my references", "verify citations" | Per-reference status table |
| `disclosure` | "AI statement", "disclosure" | A draft statement that matches what was actually done |

### Mode: proofread

Goal: the same sentences, without the errors.

Fix only:
- grammar, agreement, tense consistency within a section
- articles (a/an/the) and prepositions
- spelling, punctuation, hyphenation, spacing
- unit and symbol formatting (e.g. `300 °C`, `H2/CO2` subscripts as the
  document already writes them)
- departures from the author's house conventions listed in
  `clean-writing/SKILL.md` (US spelling, `300 °C`, `25 wt%`, `52.6%`,
  "Fig. 3a", en dash in ranges). Correct these and include them in the change list.

Do not:
- replace a correct word with a "better" one
- merge, split or reorder sentences unless one is ungrammatical as written
- change any number, unit, sample name, chemical formula, equation, citation
  key, figure or table reference
- add or delete a claim, hedge or citation
- touch quoted material, LaTeX math, code or table cells

Procedure:
1. Read the whole passage before editing so terminology stays consistent.
2. Edit sentence by sentence. If a sentence is correct, return it unchanged.
3. Where meaning is ambiguous, do not guess. Leave the sentence and add a
   query: `[Q: does "it" refer to the catalyst or the support?]`.
4. Return the corrected text, then a change list: `original -> corrected
   (reason)`, one line per edit.
5. If the user can run scripts, tell them to run
   `scripts/change_report.py original.md proofread.md`. It confirms every
   number, citation key and formula survived, and reports how much wording
   changed. A proofread that changes more than roughly 10-15% of the words
   has drifted into rewriting: go back and restore the author's wording.

### Mode: audit

Goal: show the author where the prose is weak and why. The author rewrites.

1. If scripts are available, run `scripts/audit_draft.py <file>` first and use
   its line-numbered findings as the starting list.
2. Read the draft against `references/writing-signs.md`. Judge every
   candidate in context: a flagged word is often fine.
3. Report findings grouped by priority:
   - **Fix**: factual or scholarly problems (unsupported claim, vague
     attribution, citation that does not support the sentence, placeholder
     text, leftover tool artifacts).
   - **Tighten**: inflated significance, promotional wording, filler,
     formulaic openings and conclusions, synonym-swapping of technical terms.
   - **House style**: departures from the author's own conventions (UK
     spelling, unit spacing, "As shown in Fig.", "Figure 3" for "Fig. 3").
   - **Consider**: rhythm and readability (very long sentences, three in a
     row with the same opener, heavy bold or list formatting).
4. For each finding give: location, the phrase, the reason, and a question or
   instruction that lets the author fix it ("Which studies? Cite them or cut
   the sentence."). Do not supply the replacement sentence unless the author
   asks for an example, and then give one example, not a rewrite of the
   paragraph.
5. End with the two or three patterns that recur most, so the author can fix
   their habit and not just this draft.

Never report an "AI score" or say text "looks AI-written" or "looks human".
The audit is about quality. See `references/writing-signs.md` for why these
patterns are unreliable as authorship evidence.

### Mode: references

Goal: every citation exists and supports the sentence it is attached to.

1. If scripts and network are available, run
   `scripts/check_references.py <file.bib|.md|.tex>`.
2. For each reference report one status:
   - `OK`: DOI resolves and title, first author and year match
   - `MISMATCH`: DOI resolves to a different paper (list both titles)
   - `UNRESOLVED`: DOI or ISBN invalid or not found
   - `NO-ID`: no DOI/ISBN; needs a manual check
   - `INCOMPLETE`: missing pages, volume or year
3. Format the verified list in the author's required style
   (`references/reference-style.md`): `Author (Year), 'Article title',
   *Journal*, Volume(Issue), Pages.` for articles, with the book, thesis and
   web forms given there. `check_references.py thesis.bib --format` prints
   the list. A journal manuscript follows the journal's style instead.
   Mark missing fields `[pages needed]`; never fill them from memory.
4. Never repair a reference from memory. If a DOI does not resolve, say so and
   ask the author for the source. Never suggest a "likely" paper.
5. Spot-check claims: for sentences with specific numbers attached to a
   citation, remind the author to confirm the number against the source PDF.
   You cannot do this unless they provide the source.

### Mode: disclosure

1. Ask what tools were used and for what (proofreading, translation, code,
   literature search, figure generation, drafting).
2. Draft a statement from `references/disclosure-templates.md` that says
   exactly that and nothing more favourable.
3. Remind the author to check the current rules of their university and of
   each target journal. Rules differ and change; do not state what a specific
   institution allows unless the author provides the policy text.

## Output rules for all modes

- Keep the author's dialect (US/UK spelling) and reference style.
- Technical terms are not interchangeable. Never vary "selectivity",
  "conversion", "yield", "activity" or sample names for style.
- Say what you did not check.
- If the passage reads as generated end to end (chat leftovers, placeholders,
  invented references), say what you found in the `Fix` list and stop there.
  Do not polish it into shape.

## Files

- `clean-writing/SKILL.md`: the companion writing skill, with the author's
  house style and required reference style
- `references/writing-signs.md`: the audit checklist, with catalysis examples
- `references/reference-style.md`: the required reference-list format
- `references/disclosure-templates.md`: statement templates
- `scripts/audit_draft.py`: line-numbered pattern, artifact and house-style
  report
- `scripts/check_references.py`: DOI/ISBN verification against Crossref;
  `--format` prints the list in the required style
- `scripts/change_report.py`: confirms a proofread preserved numbers,
  citations and wording
