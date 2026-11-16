---
name: "clean-writing"
description: "Write and edit prose plainly in Khasan's house style (from his 2026 Fuel paper) with his required reference style, without the inflated, vague and formulaic patterns in Wikipedia's Signs of AI writing."
---

# Clean writing

Write so that every sentence says something specific and checkable. The rules below turn the patterns catalogued in Wikipedia's "Signs of AI writing" (WikiProject AI Cleanup, CC BY-SA 4.0) into writing instructions. Each pattern is a weakness in its own right: it pads, inflates or hides a missing fact.

Apply these rules whenever you draft or revise text with this skill active. They govern style only. They never justify dropping a fact, a caveat the content needs, or a citation.

The "House style" section sets the author's voice, conventions and terminology. Use it for every text. Where it and a general rule differ, the house-style section says which one applies.

## Scope and honesty

- This is a style guide. It does not change who wrote a text, does not affect any provider's statistical watermark, and is not a way to pass detectors. Do not describe output as "human-like" or "undetectable".
- If the user must disclose AI assistance (a thesis, a journal, a class), that still applies to text written with this skill.
- Never add deliberate errors, typos, slang or random irregularity to seem less polished. Clean means precise, not sloppy.

## House style

Profile of the author's own writing, taken from his first-author paper: K. Nasriddinov et al., "Mitigating the trade-off between selectivity and stability in CO2 hydrogenation using ultra-high potassium loading on iron catalysts", Fuel 427 (2027) 139918. Use these habits as defaults. Do not copy sentences from the paper; reuse its conventions, not its wording.

### Applies to everything

- **US spelling:** behavior, stabilize, analyze, favor, sulfur, center.
- **Serial comma:** "Ni, Co, or Ru"; "24% CO2, 72% H2, and 4% Ar".
- **Sentence length:** average about 23 words, with real spread. Roughly one sentence in ten is under 12 words and a few run past 40 when they carry a mechanism. Do not flatten this to uniform length. This replaces the general "split over 40 words" rule: split only when the sentence is hard to follow.
- **Topic sentence first.** A paragraph opens with its finding or claim in plain declarative form ("Potassium promotion has a pronounced effect on ..."), then gives values, then the explanation.
- **Plain subjects.** Most sentences start with "The ...", "This + noun ..." ("This decrease ...", "This U-shaped trend ...") or the thing itself ("Potassium ...", "CO2 conversion ..."). Do not vary openers for the sake of variety.
- **Measured claims.** State the result, then hedge the interpretation once with one of his verbs: "is consistent with", "indicates", "suggests", "is attributed to", "is likely due to", "appears to", "may act as". State limits outright: "cannot be excluded", "within the 100 h test window", "remains to be established".
- **Explanations after a colon.** He introduces a mechanism or a contrast with a colon and uses "whereas" or "while" for the two sides. Semicolons join closely related clauses.
- **Parentheses carry data:** values, sample labels, phase formulas, reaction equations, figure references.
- **In-sentence enumeration** for mechanisms: "through: (1) ..., (2) ..., and (3) ...". No bullet lists inside body text.

### Scientific text

**Voice and tense**
- Experimental: past tense, passive. "The catalyst was reduced with 5% H2/He at 500 °C for 12 h." "All chemicals were used as received without further purification."
- Results: present tense for what figures and trends show ("CO2 conversion increases from ... to ...", "Fig. 3a shows ..."); past tense is acceptable for a single measured outcome.
- Conclusions: past for what was achieved, present for what it means.
- "We" and "our" appear sparingly, for framing only: "Here, we demonstrate ...", "In the present study, we ...", "Our analysis indicates ...", "in our series". Never "I".

**Reporting numbers**
- Give the range with its endpoints and the sample at each: "from 22.3% (0 K) to a minimum of 10.9% at 20 K, then rises to 16.3% at 30 K".
- "~" for approximate values. One decimal for conversion, selectivity and yield.
- Trend verbs: increases, rises, declines, decreases, drops, peaks at, shifts toward, at the expense of.

**Units and notation**
- Space between number and unit, none before %: 300 °C, 2.0 MPa, 100 h, 25 wt%, 52.6%, 200 kV, 532 nm.
- H2/CO2 = 3; GHSV in mL gcat−1 h−1; "100 h on stream"; "time on stream".
- En dash in ranges and paired names: 28–30%, C5–C13, C–C coupling, Fe–C bonds, water–gas shift, Fischer–Tropsch, structure–performance.
- Hydrocarbon fractions: CH4, C2–C4, C5+; "olefin-to-paraffin (O/P) ratio".
- Subscripts and superscripts follow the destination format. Never use Unicode subscript characters in Word or LaTeX.

**Terminology (one name per thing, never varied)**
- Samples: "0 K", "5 K", "20 K", "25 K", "30 K" for K loading in wt%; series "FeCuxK/Al2O3"; base "FeCu/Al2O3" or "FeCu/γ-Al2O3"; "the unpromoted catalyst"; "K-promoted"; "high-K catalysts"; "fresh" and "spent" catalysts. For other projects, ask for the sample labels or take them from the user's draft.
- "K loading" (not "K content" in one place and "K amount" in another), "C5+ selectivity", "C5+ yield", "CO2 conversion", "CO selectivity", "chain growth", "carburization", "basicity", "deactivation", "carbon deposition".
- Phases by name with formula at first mention: "Hägg carbide (Fe5C2)", "magnetite (Fe3O4)", "cementite (θ-Fe3C)", "metallic Fe (Fe0)".
- Define an abbreviation at first use, then use only the abbreviation: "reverse water–gas shift (RWGS)", "Fischer–Tropsch synthesis (FTS)", TPD, TPR, XRD, XPS, TEM, STEM-EDS.

**Figures, tables, sections, citations**
- "Fig. 1", "Fig. 3a", "Table 1", "Section 3.2", "Fig. S1, SI".
- Lead with the figure as subject ("Fig. 1 and Table 1 summarize ...", "Fig. 6 compares ...") or cite it in parentheses after the statement ("... with increasing K content (Fig. 7a)"). Do not write "As shown in Fig. X" or "As can be seen".
- Numeric citations in square brackets before the full stop: [9,13], [31–33]. Author-led form: "Hoque et al. reported that ... [23]."
- Reference list: use the "Required reference style" section below. For a journal manuscript, the journal's style takes precedence (his Fuel paper uses Elsevier numbered style with abbreviated journal titles and DOI).

**Structure**
- Sections: 1. Introduction; 2. Experimental (Catalyst preparation, Catalyst characterization, Catalytic activity test); 3. Results and discussion with descriptive subsection titles in sentence case ("Carbon deposition and stability"); 4. Conclusions.
- Abstract, about 170 words, one paragraph: the problem in one sentence; "Here, we demonstrate that ..."; the headline numbers; the mechanism as a numbered in-sentence list; one caveat; one sentence of implication.
- Introduction: general motivation, what promoters do (cited), the specific gap, then "In the present study, we ..." and what was examined.
- Results paragraph: finding, values with samples, comparison across the series, interpretation tied to a characterization result or a citation.
- Conclusions, one paragraph: "This study demonstrates that ..."; key values; what they are attributed to; the limit of the evidence; one closing sentence on use.

### Required reference style

Use this format for every reference list, unless the user names a target journal; the journal's own style then takes precedence. The rules and examples were supplied by the user as the required style.

**Common rules**
- Author: last name first, then first name. Korean names as written. Several authors are separated by commas.
- Publication year in parentheses directly after the author(s), followed by a comma.
- Page numbers without "p" or "pp".
- Elements are separated by commas; the entry ends with a period.

**(1) Books**
Order: Author (Year), Title, Edition, Place of publication: Publisher.
- Title in 「」 for Korean; in italics for English.
- Give the edition number only from the second edition on.
- A colon follows the place of publication.

Examples:
- 김인태 (1992), 「과학기술 정책평가」, 서울: 과학비평사.
- Anderson, J. Parker (1989), *Science & Technology*, N.Y.: GrandVolumes.

**(2) Journal articles**
Order: Author (Year), 'Article title', Journal name, Volume(Issue), Pages.
- Article title in single quotation marks; in English, capitalize the first letter.
- Journal name in italics for English; in 「」 for Korean.
- Always state the page numbers.

Examples:
- 박학일, 심재진 (1999), '효과적인 과학기술혁신단계', 「이공계연구」, 29(4), 1-28.
- Amile, Rolson (1992), 'Characteristics of R&D', *Review of R&D Research*, 62, 37-65.

**(3) Theses**
Order: Author (Year), Title, Type of thesis, University that awarded the degree.
- Title in 「」 for Korean; in italics for English, with the first letter capitalized.

Examples:
- 김동현 (2002), 「과학기술중심사회구축을 위한 이공계활성화 방안에 관한 연구」, 박사학위논문, 과학기술연합대학원대학교.
- Amile, Rolson (1992), *Meta-evaluation of R&D*, Unpublished doctoral dissertation, University of Science & Technology.

**(4) Web data**
Order: Author (Year), 'Title of web data', Retrieved Month D, YYYY, from [organization Web site:] URL.
- Use (n.d.) when the page has no date.
- Always give the retrieval date and the full address.

Examples:
- Amile, Rolson (2000), 'APA style essentials', Retrieved May 18, 2000, from Vanguard University, Department of Psychology Web site: http://www.edusys.edu/psychology/index.cfm?doc_id=796.
- Amile, Rolson (n.d.), 'Notable people in psychology of religion', Retrieved August 3, 2001, from http://www.psy.com/psyrelig/psyrelpr.htm.

**Applying it**
- Build each entry only from a record you were given or retrieved. Never fill a missing volume, page range, or year from memory; write `[pages needed]` and tell the user.
- Journal articles need page numbers. For article-number journals, give the article number in the page position and flag it for the user to confirm.
- The supplied examples show English book and thesis titles in single quotation marks, while the rule text says italics. Follow the rule text (italics) unless the user says otherwise.
- Not specified by the rules: the in-text citation format, how to shorten long author lists, whether to add a DOI, and the order of the list. Follow the user's document if it shows a pattern; otherwise ask once before formatting.

### Where his paper and the general rules differ

His paper contains some patterns that the general rules below remove. Resolution:

- **Keep, at his low frequency:** "However" freely; "Additionally", "Moreover", "Meanwhile", "In particular", "In contrast", "At the same time" as single connectives (about one per 1,000 words each, never stacked); "Notably" at most once per section; paired em dashes for an inserted qualifier, at most once per page.
- **Keep:** "significantly" only where a difference was measured; "pronounced", "markedly", "progressive", "predominantly" as descriptive terms with a number nearby.
- **Follow the general rule, not the paper:** no "multifaceted", "crucial", "key role", "leveraging", "dramatically", "striking", "robust stability"; no sentence adverbs "Importantly" or "Interestingly"; no "not only ... but also"; no trailing ", reflecting ..." or ", providing ..." significance clauses; no closing sentence promising a "pathway" or "design strategy" unless it names what to do.
- If the user asks for a pattern from the second list in a specific text, use it there.

### Non-scientific text (emails, reports, messages, documentation)

Keep the general habits: US spelling, topic sentence first, plain subjects, numbers with units, one measured hedge, limits stated outright, serial comma. Drop the paper apparatus (section numbering, figure and citation conventions, sample labels). Use "I" where one person is writing. Keep it shorter than the scientific register: say the point, the evidence, and what is needed from the reader.

## 1. Content: say the thing

**State what happened, not how important it is.**
- Avoid: "This marks a pivotal moment in the evolution of the field."
- Write: "The 2019 paper was the first to report selectivity above 50%."

**No trailing significance clauses.** Do not end a sentence with ", highlighting...", ", underscoring...", ", reflecting...", ", showcasing..." or ", paving the way for...". If the significance is real, make it a separate claim with evidence.

**No promotion.** Cut "remarkable", "outstanding", "groundbreaking", "cutting-edge", "state-of-the-art", "seamless", "vibrant", "rich", "renowned". Give the number or the fact and let the reader judge.

**Name your sources.** Never write "experts say", "researchers have shown", "it is widely recognised", "studies suggest" or "critics argue" without saying who. If you cannot name the source, cut the claim or mark it as needing one.

**Do not manufacture balance or outlook.** No "Despite these challenges, X continues to..." endings, no "Future prospects" paragraph of general optimism. End on the last substantive point: a result, a limit, or the next concrete step.

**Do not fill gaps with speculation.** If information is missing, say what is missing in one plain sentence. Do not write "while specific details are limited, it is likely that...".

**Do not restate.** No paragraph that summarises the section just written, and no conclusion that repeats the introduction point for point.

## 2. Language: plain words

**Use "is" and "has".** Not "serves as", "stands as", "functions as", "boasts", "features", "represents" when a simple copula is meant.

**Prefer the common word.** Avoid these unless they are the precise term: delve, tapestry, intricate, intricacies, multifaceted, pivotal, crucial, underscore, showcase, foster, garner, leverage, navigate, landscape, realm, testament, robust, comprehensive, meticulous, notably, enduring, evolving. Field terms are fine: "robust regression" is a method; "a robust platform" is filler.

**Delete filler openers.** "It is important to note that", "It is worth mentioning that", "It should be noted that", "In order to" (use "to"), "due to the fact that" (use "because").

**No false contrasts.** Do not write "not only X but also Y", "not just X, but Y" or "It's not X, it's Y" unless someone actually claimed only X. Write "X and Y".

**No reflex triplets.** List three things only when there are three. Do not pad to "efficient, sustainable and scalable".

**One name per thing.** Pick a term and repeat it. Do not rotate "the catalyst", "the material", "the system" for one object. Repetition of a technical term is correct.

**One hedge at most.** "may suggest", not "may potentially suggest". Hedge only where the uncertainty is real, and say what it is.

**Transitions carry logic or go.** Use "however", "therefore", "because" where the relation exists. Do not open consecutive sentences with "Moreover", "Furthermore", "Additionally".

## 3. Structure and rhythm

- Let length follow content. Some paragraphs are two sentences. Do not shape every paragraph as claim, three supports, summary.
- Mix sentence lengths naturally: a short sentence after a long one when the point is short. Split any sentence over about 40 words at its logical joint.
- Do not open three sentences in a row with the same words, except in a deliberate list of steps.
- Put the main point first. No wind-up sentence announcing what the paragraph will do.

## 4. Formatting

- Headings in sentence case unless the target style says otherwise.
- No bold inside running prose for emphasis. Bold is for labels the reader scans for.
- No lists of bold-label-colon items when the content is an argument; write a paragraph. Use a list or table only when the reader will scan or compare.
- Use commas, parentheses or a colon where they work. Do not use em dashes for emphasis or to bolt on an afterthought.
- No emoji as heading or bullet decoration.
- Match the destination's markup. No Markdown in text bound for Word, LaTeX or an email.
- Straight quotes unless the destination's style uses curly ones; never mix.

## 5. No chat residue in the deliverable

The text you hand over contains only the text. Keep these out of it:

- openers and closers addressed to the user ("Certainly!", "Here is the revised version", "I hope this helps", "Let me know if...")
- offers and follow-up questions inside the document
- statements about your knowledge, access or limits
- placeholders ("[insert reference]", "XX", "TBD"). If something is missing, list it for the user outside the text.
- tracking parameters on URLs (`utm_source=...`); give the clean link or the DOI

Notes to the user go before or after the text, clearly separate.

## 6. References and facts

- Never invent a reference, DOI, ISBN, page number, quotation or statistic.
- Cite only sources you were given or have actually retrieved, and only for what they say.
- If a claim needs a source you do not have, write the claim without the citation and tell the user it needs one. Do not attach a plausible-looking reference.
- Give page numbers for books and for direct quotations when available.

## 7. Revising existing text

When the user gives you their own draft to clean:

1. Fix the patterns above with the smallest change that works. Keep their facts, order, terminology and voice.
2. Where a pattern hides a missing fact (a vague attribution, an unsupported superlative), do not paper over it with smoother wording. Flag it: `[needs source]` or `[which studies?]`.
3. Do not change numbers, names, quotations, citations, equations or code.
4. After the text, list what you changed by category and what you flagged.

## 8. Final check before handing over

Read the draft once more and confirm:

- Every general claim has a named source or is the author's own stated position.
- No sentence could be deleted without losing information. Delete the ones that could.
- No word from the avoid-list remains except as a precise term.
- No sentence ends in a significance clause; no paragraph ends in a summary.
- No consecutive stacked transitions; no reflex triplet; no "not only ... but also".
- One name per thing throughout.
- Formatting matches the destination; no chat residue, placeholders or tracked links.
- House style holds: US spelling, units and notation, sample labels, figure and citation format, tense by section.
- Reference list follows the required reference style (or the named journal's style), with every entry built from a retrieved record and page numbers present.
- Nothing was invented.

If fixing a pattern would require a fact you do not have, leave the gap visible and tell the user.

## Examples

**Before:** "Potassium plays a pivotal role in CO2 hydrogenation, serving as a key promoter that not only enhances chain growth but also improves stability, underscoring the importance of alkali promotion in this evolving field."

**After:** "Adding 2 wt% K raised C5+ selectivity from 31% to 52% and reduced deactivation over 100 h (Table 2)." If those numbers are not available: "K promotes chain growth [needs source and data]."

**Before:** "Moreover, the catalyst demonstrates remarkable performance. Furthermore, experts have noted its robust nature. Additionally, it holds great promise for the future."

**After:** state the measured performance and who reported it, or cut all three sentences.

**Before:** "Despite these challenges, the technology continues to evolve, paving the way for a more sustainable future."

**After:** "Two problems remain: water inhibits the active phase, and the catalyst sinters above 350 °C."