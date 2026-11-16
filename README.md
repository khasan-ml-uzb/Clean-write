# Claude_text_humanizer: honest writing skills for thesis and paper work

Version 1.1, November 2026.

This folder holds two skills, three scripts and two guides. Despite the
folder name, nothing here is a humanizer, a detector bypass or a watermark
remover.

| Skill | Job |
|---|---|
| `thesis-prose-editor` (`SKILL.md`) | Checks drafts that you wrote: minimal-change proofreading, a writing-quality audit, reference verification, AI-use disclosure statements |
| `clean-writing` (`clean-writing/SKILL.md`) | Writing rules for any text: your house style (from your paper in Fuel 427 (2027) 139918), the required reference style, and the patterns to avoid from Wikipedia's "Signs of AI writing" |

## What changed in 1.1

- Added `clean-writing` with the house style and the required reference style.
- `references/reference-style.md`: the reference-list format for books,
  journal articles, theses and web data, with Korean and English examples.
- `check_references.py --format` and `--format-only`: print a `.bib` file in
  the required style, marking missing fields.
- `audit_draft.py`: new "house style" group (UK spelling, unit spacing,
  "As shown in Figure 3", space before %); the long-sentence limit now
  follows your own writing.
- `references/writing-signs.md`: section E, house-style conventions.
- `THESIS_GUIDE.md`: house style, reference style and a formatting step.
- All scripts print UTF-8, so Korean references display on Windows.

## What these skills are not

- Text watermarks from Claude and similar models are statistical: they live
  in which words the model chose. No clean-up pass by the same model removes
  them, and no local tool can verify removal.
- Detectors and stylistic "signs" are unreliable as proof of authorship in
  both directions. Chasing them does not make a thesis safer. A record of
  your own drafts and an accurate disclosure does.
- Text that Claude drafts in your house style is still AI-drafted and is
  disclosed as such.

`docs/AI_text_signs_detection_guide.md` explains how watermarks, detectors
and stylistic signs work, for readers who want to understand or review text.

## Layout

```
Claude_text_humanizer/
  SKILL.md                         thesis-prose-editor skill
  README.md                        this file
  THESIS_GUIDE.md                  routine for writing a thesis with both skills
  clean-writing/
    SKILL.md                       clean-writing skill (house style, reference style)
  references/
    writing-signs.md               audit checklist, with house-style conventions
    reference-style.md             required reference-list format
    disclosure-templates.md        AI-use statement templates
  scripts/
    audit_draft.py                 line-numbered writing-quality and house-style report
    change_report.py               proves a proofread kept numbers and wording
    check_references.py            DOI / ISBN verification; reference-list formatting
  docs/
    AI_text_signs_detection_guide.md
    AI_text_signs_detection_guide.pdf
```

## Install

In the Claude app, skills are saved from the review card in the chat where
they were built; the copies here are a backup. `clean-writing` is saved in
the account. `thesis-prose-editor` must be saved from its card before Claude
can use it in other chats. For Claude Code, copy each skill folder to
`~/.claude/skills/`.

## Use

In a chat with the skills enabled:

- "Proofread section 3.2" (attach or paste the text)
- "Audit this chapter draft"
- "Check my references and format the list" (attach the `.bib`)
- "Write my AI-use statement: I used Claude for proofreading chapters 2-5"
- "Use clean-writing: revise this email / report section"

Scripts need Python 3.9 or later and no extra packages:

```
python scripts/audit_draft.py chapter3.md
python scripts/audit_draft.py chapter3.docx
python scripts/change_report.py chapter3_original.md chapter3_proofread.md
python scripts/check_references.py thesis.bib --email you@university.ac.kr
python scripts/check_references.py thesis.bib --format
python scripts/check_references.py thesis.bib --format-only
```

`check_references.py` contacts `api.crossref.org` and sends only DOIs;
`--offline` and `--format-only` use no network. The other two scripts never
use the network.

## Open points in the reference style

1. English book and thesis titles: the rule says italics, its examples show
   single quotation marks. The skills and the script use italics.
2. In-text citation format, shortening of long author lists, DOIs and list
   order are not specified. The script lists all authors and sorts by author.
3. Journal articles must show page numbers; journals with article numbers
   need a decision from the graduate office.

## Sources and credit

- Audit categories adapted from Wikipedia, "Wikipedia:Signs of AI writing"
  (WikiProject AI Cleanup), CC BY-SA 4.0.
- House style profiled from K. Nasriddinov et al., Fuel 427 (2027) 139918.
- Background on text watermarking: Anthropic, "How Claude's text watermark
  works" (14 Aug 2026); Dathathri et al., Nature 634, 818-823 (2024);
  Kirchenbauer et al., arXiv:2301.10226 (2023).

## License

MIT for the code and skill text. `references/writing-signs.md` adapts
CC BY-SA 4.0 material and is shared under the same license.
