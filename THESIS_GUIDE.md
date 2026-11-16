# Using the skills while writing a thesis

A working routine for a doctoral thesis: you write, the skills check.
Two skills are involved. `thesis-prose-editor` proofreads, audits and checks
references. `clean-writing` holds your house style (from your paper in Fuel)
and the required reference style.
It assumes chapters in Markdown, LaTeX or Word and references in a `.bib`
file or a reference manager that can export one (EndNote can).

## The rule that keeps you safe

**You draft every sentence. The tool corrects and questions.**

This is the use that universities and journals most consistently permit, and
it is the easiest to disclose. It also matters technically. Claude's text
watermark is carried by the words Claude chooses, and Anthropic notes that
when Claude only fixes grammar and punctuation in someone's writing, the mark
has just those few corrections to live in and may not register. Text that
Claude drafts for you is marked throughout, and should be disclosed as
drafted with AI.

Before you start, read two documents and save copies:

1. Your university's current research-ethics and thesis regulations on
   generative AI. Ask the graduate office or your supervisor if you cannot
   find them; rules were being introduced at many Korean universities during
   2026 and differ between institutions.
2. The author guidelines of each journal you plan to publish chapters in.

Where they conflict, follow the stricter one.

## Your house style and reference style

`clean-writing/SKILL.md` records how you write: US spelling, past passive in
Experimental, present tense for trends in Results, "Fig. 3a shows ...",
values with the sample in parentheses, your sample labels, and your hedging
verbs. `references/writing-signs.md` (section E) lists the conventions as a
table, and `audit_draft.py` flags the mechanical ones (UK spelling, `300°C`,
`52.6 %`, "As shown in Figure 3").

Use the house style in two ways:

- **As a checklist for your own drafts.** This is the normal use in a thesis.
  The audit and the proofread both apply it.
- **When Claude drafts or revises text for you** with `clean-writing`. The
  text then follows your conventions, but Claude chose the words. Disclose it
  as AI-drafted or AI-edited (templates 2 and 6). Matching your style does
  not change that.

Reference lists follow `references/reference-style.md`:

| Type | Format |
|---|---|
| Book | Author (Year), *Title*, Edition, Place: Publisher. |
| Journal article | Author (Year), 'Article title', *Journal*, Volume(Issue), Pages. |
| Thesis | Author (Year), *Title*, Type of thesis, University. |
| Web data | Author (Year or n.d.), 'Title', Retrieved date, from address. |

Korean titles and journal names go in 「」 in place of italics. Chapters
submitted to a journal follow that journal's style instead. Three points are
still open and should be confirmed with the graduate office: whether English
book and thesis titles take italics or single quotation marks (the rule and
its examples disagree), the in-text citation format, and how long author
lists are shortened.

## Per-chapter routine

| Step | You | Skill / script | Keep on file |
|---|---|---|---|
| 1. Draft | Write the section from your notes and data | none | Dated draft (`ch3_v1.md`) or a git commit |
| 2. Self-edit | Reread once for logic and order | none | |
| 3. Audit | Read the findings; rewrite flagged passages yourself | "Audit this draft" or `audit_draft.py` | Audit output |
| 4. Proofread | Accept or reject each correction | "Proofread this section" | Change list |
| 5. Verify the proofread | Fix anything the report flags | `change_report.py v2.md v3.md` | Report |
| 6. References | Resolve every MISMATCH, UNRESOLVED and NO-ID | `check_references.py thesis.bib` | Report |
| 7. Format the list | Fill every bracketed gap from the source | `check_references.py thesis.bib --format-only` | Formatted list |
| 8. Final read | Read the chapter aloud or on paper | none | |

Do the audit before the proofread. There is no point correcting the grammar
of a sentence you are about to cut.

### Step 3 in practice: acting on audit findings

The audit sorts findings into four groups. Work in this order.

**Fix.** These are scholarship problems. Examples and what to do:

- *"Researchers have widely reported that K promotes carburization."*
  Name the studies and cite them, or delete the sentence.
- *"[add reference]"*, *"XX wt%"*: fill in or remove.
- A URL containing `utm_source=...`: you copied it from a chatbot or search
  tool. Replace it with the DOI link, and reread the source to confirm it
  says what your sentence says.

**Tighten.** Replace evaluation with measurement:

- *"K plays a pivotal role in chain growth."*
  becomes what you observed: *"Raising K from 0 to 2 wt% increased C5+
  selectivity from 31% to 52% at constant conversion (Figure 3.4)."*
- *"These results underscore the importance of promoter loading."*
  Usually delete. If it is a claim, state it and point to the evidence.
- *"Moreover / Furthermore / Additionally"* at the start of consecutive
  sentences: keep the one that carries a logical step.
- One name per thing. If it is "FeCuAl-2K" in the Methods, it is not "the
  material", "the sample" and "the system" in the Results.

**House style.** Mechanical departures from your own conventions: UK
spelling, missing space before a unit, a space before %, "Figure 3" for
"Fig. 3", "As shown in Fig. 3" for "Fig. 3 shows". Fix them all; they need
no judgment. "Importantly," and "dramatically" are flagged here too, because
the house style drops them.

**Consider.** Split a long sentence only where it is hard to follow; your
own average is about 23 words, and a few of your sentences run past 40 when
they carry a mechanism. Vary three consecutive sentences that open
identically, unless it is a deliberate list of steps in the Methods.

Ignore a finding when the wording is the field's standard term ("robust" for
a statistical method, "selectivity" repeated ten times). The script cannot
tell; you can.

### Step 4 in practice: what a proofread may change

Allowed: agreement ("catalyst were" to "catalyst was"), articles, tense
consistency, punctuation, spelling, unit spacing.

Not allowed: new wording for a correct sentence, merged or reordered
sentences, any change to a number, sample name, formula, citation or
figure reference.

Paste one section at a time (500 to 1,500 words). Long pastes make it harder
to review every change, and you must review every change.

### Step 5: the change report

```
python scripts/change_report.py ch3_v2.md ch3_v3.md
```

- **Protected content** must read "All preserved". If a number differs,
  the proofread introduced an error: restore your value.
- **Wording** should stay under about 15% of tokens changed. Above that,
  the pass rewrote instead of proofreading. Reject it and ask again for
  grammar-only corrections, or fix the errors by hand from the change list.
- **Heavily rewritten sentences** are listed so you can restore your own.

### Step 6: references

```
python scripts/check_references.py thesis.bib --email you@ust.ac.kr
```

| Status | Meaning | Action |
|---|---|---|
| MISMATCH | The DOI belongs to a different paper | Find the right DOI from the publisher page; reread the source |
| UNRESOLVED | DOI not found or ISBN invalid | Check for a typo; if the paper cannot be found, remove the citation and the claim |
| NO-ID | No DOI or ISBN | Verify by hand (older papers, theses, standards) |
| INCOMPLETE | Missing volume, pages or year | Complete from the publisher page |
| CHECK | Author or year differs | Compare with the PDF |

### Step 7: formatting the reference list

```
python scripts/check_references.py thesis.bib --format-only
```

The script prints every entry in the required style, sorted by author, with
`*...*` marking italics. Example output:

```
Nasriddinov, Khasan, Min, Ji-Eun, Park, Hae-Gu (2022), 'Effect of Co, Cu,
and Zn on FeAlK catalysts in CO2 hydrogenation to C5+ hydrocarbons',
*Catalysis Science & Technology*, 12(3), 906-915.
```

- `[pages needed]`, `[volume needed]` and similar markers show missing
  fields. Fill them from the publisher page, never from memory. The style
  requires page numbers for every journal article; for journals that use
  article numbers (Fuel, for example), give the article number and confirm
  that this is accepted.
- Conference papers and reports are not covered by the style; the script
  marks them for a manual decision.
- Run step 6 first. The formatter prints what the `.bib` file contains,
  right or wrong.

Never accept a reference suggested by a chatbot without opening the paper.
A reference that does not exist, or that does not say what you cite it for,
is the most serious finding an examiner can make, and it is unrelated to
any detector.

## By chapter type

- **Introduction and literature review.** Highest risk of vague attribution
  and inflated framing. Every general statement needs named sources. Run the
  reference check after each writing session, not at the end.
- **Experimental.** Proofread only. Past passive and repeated sentence
  openers are your house style here. Use the change report: a silent change to a
  temperature or loading is the failure to guard against.
- **Results and discussion.** Audit for significance phrases standing in for
  data, and for synonym-swapping of sample names. Check that every claim
  points to a figure, table or citation.
- **Conclusions.** Audit for the formulaic ending ("despite these challenges
  ... holds great promise"). State what was shown, the limits, and the next
  experiment.
- **Abstract.** Write it last, yourself. Proofread only. Your pattern: the
  problem, "Here, we demonstrate that ...", the headline numbers, the
  mechanism, one caveat, one sentence of implication.

## Records and disclosure

Keep a folder per chapter with: your dated drafts, the audit output, the
proofreading change lists, the change reports and the reference reports.
Version control (git) does this automatically if you commit after each step.

Write the disclosure as you go, not at submission. Templates are in
`references/disclosure-templates.md`; ask the skill for "disclosure" mode and
tell it what you actually used. For a thesis written with this routine,
template 1 (proofreading only) plus template 4 (code assistance, if you used
AI for your ML scripts) is typical. If `clean-writing` drafted or reworded
any passage, add template 2 or 6 for those sections.

## If a detector flags your thesis

Detectors report probabilities and are known to produce false positives,
including on formal writing by non-native English speakers. A flag is not a
finding of misconduct.

1. Do not run the text through a "humanizer". It changes your wording,
   can introduce errors, and looks worse than the flag if discovered.
2. Give your supervisor or the committee your record: dated drafts, change
   lists, the disclosure statement.
3. Offer to explain any passage and its sources in person.

An author who can show how each chapter developed, and who disclosed tool
use up front, has the answer to the question a detector raises.

## What not to use the skills for

- Generating sections from bullet points or data tables.
- Paraphrasing other people's papers to lower a similarity score. Cite and
  quote, or write your own synthesis.
- Producing or "fixing" references from memory.
- Anything described as making text undetectable.
