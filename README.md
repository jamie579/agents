# Agents

34 reusable agent prompts for academic research, writing, and quality
assurance, written by [Jamie B. Smith](https://orcid.org/0000-0003-0097-6102)
(Charité – Universitätsmedizin Berlin). Built as
[Claude Code subagents](https://docs.anthropic.com/en/docs/claude-code/sub-agents),
but portable: each file is YAML frontmatter (Claude Code-specific) followed by a
plain-markdown system prompt that any LLM can adopt.

This repo is a filtered mirror generated from a private config repo — edits here
will be overwritten; open an issue instead.

## Use with Claude Code

Drop any file into `~/.claude/agents/` (user-wide) or `.claude/agents/`
(per-project) and it becomes available to the Agent tool.

## Use with any other LLM

1. Fetch [`manifest.json`](manifest.json) — every agent's name, description, and raw URL.
2. Pick the agent whose description fits the task.
3. Fetch its `raw_url`, discard the `---`-delimited frontmatter, and adopt the
   markdown body as your system prompt / instructions.

Prompt to paste into an LLM with web access:

> Fetch https://raw.githubusercontent.com/jamie579/agents/main/manifest.json — a
> catalogue of specialist agent prompts. Pick the agent whose description best
> fits my task, fetch its raw_url, ignore the YAML frontmatter between the ---
> markers, and adopt the markdown body as your operating instructions before
> answering. Tell me which agent you chose. My task: [TASK]

Notes for non-Claude use: tool names in the frontmatter (`tools:`) and mentions
of agent-memory paths are Claude Code plumbing — ignore them. References to
"Jamie's voice" point at a private style guide; the agents degrade gracefully
without it.

## Agents

- **[academic-article-architect](academic-article-architect.md)** — Planning orchestrator for academic manuscripts: assesses the material, settles paper type and target journal, and returns a Section Brief Package (SBP) that guides the section-writer agents. ASSESS and STRUCTURE phases only; also scopes revisions from reviewer comments into targeted section briefs. Not for drafting (section writers) or reviewing existing text (QA agents).
- **[academic-librarian](academic-librarian.md)** — Full academic information-retrieval pipeline: research question refinement (PICO/PICo/SPIDER/PCC), review-type and database selection advice, Boolean strategy design with controlled vocabulary (MeSH/CINAHL/EMTREE), PRESS audits of existing strategies, search execution via PubMed/bioRxiv MCP and web, full-text retrieval, grey literature, citation chaining, de-duplication, and filing an organised corpus into the project workspace. Also troubleshoots strategies returning too many or too few results.
- **[anonymity-ethics-checker](anonymity-ethics-checker.md)** — Checks manuscripts for participant-identifying information, pseudonym consistency, and ethics/consent statement compliance; especially for small-sample qualitative research and German institutional data.
- **[apa7-formatter](apa7-formatter.md)** — APA 7th edition specialist, two modes: (1) check or fix APA 7 compliance in text (headings, citations, references, tables, title pages, abstracts) and convert from other citation styles; (2) produce a properly formatted .docx from a .md/.txt manuscript (fonts, spacing, margins, running head, heading levels, page numbers). For any non-APA target use submission-formatter.
- **[article-gate-checker](article-gate-checker.md)** — Quality-gate auditor for manuscript sections or the integrated manuscript: checks compliance with the Section Brief, voice standards, reporting-guideline coverage, and cross-section consistency; returns a structured pass/fail gate report. Can run targeted checks (voice only, consistency only).
- **[article-integrator](article-integrator.md)** — Combines drafted, gate-checked sections into a coherent manuscript: writes transitions, abstract, and title; harmonises terminology, numbers, and argument flow. Launch with all section drafts plus the full SBP; re-invoke after revisions to re-stitch and re-audit consistency.
- **[article-troubleshooter](article-troubleshooter.md)** — Diagnoses blocked manuscript workflows: failed gate checks, undraftable sections, cross-section contradictions, or mid-workflow restructuring. Traces the root cause, recommends the minimum recovery intervention, and scopes backtracks (which sections are invalidated, which survive).
- **[article-writer-conclusion](article-writer-conclusion.md)** — Drafts Conclusion, Implications, or Recommendations sections from a section brief plus the discussion draft. Deliberately modest: restates the contribution without inflation, treats limitations as epistemic conditions, opens questions rather than closing them; writes concrete recommendations for policy papers. All paper types; Jamie's voice.
- **[article-writer-discussion](article-writer-discussion.md)** — Drafts the Discussion section from a section brief plus findings and introduction drafts: interprets findings against the literature, explores mechanisms, handles strengths, limitations, and implications; never repeats results. For theoretical papers, articulates the conceptual contribution. All paper types; Jamie's voice.
- **[article-writer-findings](article-writer-findings.md)** — Drafts Findings/Results/Analysis sections from a section brief plus the actual data: qualitative themes with data-theory weaving, quantitative results presented descriptively with text-table-figure coordination, mixed-methods strands, conceptual analysis outcomes, or review synthesis. Jamie's voice.
- **[article-writer-introduction](article-writer-introduction.md)** — Drafts Introduction or Background sections from the architect's section brief, adapting to paper type: literature funnel for empirical papers, opening tension for theoretical ones. Pass summaries of already-drafted sections where the cross-reference map calls for them. Jamie's voice.
- **[article-writer-literature-review](article-writer-literature-review.md)** — Drafts standalone Literature Review, Background, or Theoretical Framework sections, and the conceptual core sections of theoretical/non-IMRaD papers; synthesises rather than summarises, every paragraph doing analytical work. NOT for empirical introductions (use article-writer-introduction). Jamie's voice.
- **[article-writer-methods](article-writer-methods.md)** — Drafts Methods/Methodology sections from a section brief: qualitative (philosophical positioning, methodology, data generation, analysis, quality criteria), quantitative (design through analysis plan, structured per STROBE/CONSORT as applicable), mixed, theoretical (approach to inquiry), or review (search, screening, synthesis). Jamie's voice.
- **[cruel-editor](cruel-editor.md)** — Merciless editor of academic prose: strips filler, challenges every claim, rates every paragraph, finds repetition, checks logical flow, enforces the banned LLM-pattern list, and identifies cuts to hit word limits. Harshest editor imaginable; always specific, always constructive.
- **[data-integrity-auditor](data-integrity-auditor.md)** — End-to-end data integrity audit from raw data and codebook through analysis code to manuscript: response-scale handling, reverse-coding, score construction, recoding and transformations, PRISMA arithmetic, and numerical consistency across code, outputs, tables, and text.
- **[dfg-eigene-stelle-swarm](dfg-eigene-stelle-swarm.md)** — Produces and revises DFG proposals, especially with the Eigene Stelle module: project description, CV/publication lists, budget narrative, employer statement drafts, attachment checklists, and elan compliance verification; includes a red-team DFG reviewer mode for critiquing existing drafts.
- **[evidence-synthesis-researcher](evidence-synthesis-researcher.md)** — Systematic review and evidence-synthesis workhorse: review structuring, inclusion/exclusion criteria, screening, data extraction, evidence tables, risk-of-bias assessment (RoB 2, ROBINS-I), synthesis, PRISMA flow diagrams, and status summaries of a review workspace.
- **[file-secretary](file-secretary.md)** — Archivist and meticulous secretary for file work: renames files from contents and metadata, builds numbered folder hierarchies, archives stale versions and duplicates with datestamps, and keeps whole project workspaces in order. Launch with the target path.
- **[grant-reviewer](grant-reviewer.md)** — Brutal simulated grant panel for any funder: three reviewers from different disciplinary perspectives score against the funder's actual assessment criteria. Judges FUNDABILITY (track record, feasibility, budget justification, environment, risk), not just scientific quality; finds every weakness a hostile panel member would exploit.
- **[jdr-harmoniser](jdr-harmoniser.md)** — Harmonises Job Demands-Resources category labels and construct names in systematic-review extraction data: maps messy free-text labels to a standardised Bakker and Demerouti taxonomy, reading from the extraction SQLite database; proposes the mapping, then applies it (or runs audit-only to preview).
- **[journal-format-checker](journal-format-checker.md)** — Checks a manuscript against a specific journal's submission guidelines: word limits, heading hierarchy, reference format, abstract structure, figure/table formatting, and reporting-guideline compliance (PRISMA, COREQ, etc.); generates pre-submission checklists.
- **[llm-prose-decontaminator](llm-prose-decontaminator.md)** — Forensically detects and rewrites LLM-generated prose patterns to Jamie's authentic academic voice. Use on drafted sections (proactively, before gate-checking), co-authored text that reads like ChatGPT, or in audit-only mode to assess voice authenticity without rewriting.
- **[logic-focus-auditor](logic-focus-auditor.md)** — Audits logical coherence and focus: maps argument chains, catches fallacies and unsupported leaps, flags scope creep and tangents, checks conclusions follow from findings, and verifies the paper answers its own research question.
- **[methodology-congruence-checker](methodology-congruence-checker.md)** — Verifies a manuscript's methodology is congruent with the methodological literature it cites and internally consistent: ontology-epistemology-methodology alignment, method descriptions matched against their source literature, analytical approach fit to the research question, and contradictions between theoretical framework and methods used. Especially for qualitative, theoretical, and philosophically committed research.
- **[peer-review-writer](peer-review-writer.md)** — Drafts Jamie's reviewer reports on OTHER people's manuscripts (invited journal reviews, including round-2 re-reviews): affirmative, developmental, in his voice. Confidentiality built in: reads local disk only, no web/MCP/cloud-synced folders, workspace under ~/PeerReview_Local_NoCloud/. NOT for Jamie's own manuscripts (peer-reviewer-simulator) or for editing his prose (cruel-editor).
- **[peer-reviewer-simulator](peer-reviewer-simulator.md)** — Simulated peer review of Jamie's own manuscript for a named journal: evaluates the WORK (novelty, significance, methodology, ethics), produces structured reviews from multiple reviewer perspectives, anticipates likely objections, and gives a recommendation.
- **[posthumanist-theory-interlocutor](posthumanist-theory-interlocutor.md)** — Theoretical engagement and sparring around critical posthumanism, feminist new materialism, and adjacent traditions (Deleuze/Guattari, Foucault, STS, decolonial, abolitionist, Black feminist, queer/crip theory) as they bear on nursing, clinical work, health workforce research, and health policy. Four modes: AUDITOR (humanist drift, decorative theory, fidelity to cited thinkers), SPARRING PARTNER (test arguments, surface tensions), DIAGNOSTICIAN (which framework fits a project), PEDAGOGUE (explain and situate concepts). Opinionated, not neutral.
- **[q1-sr-finisher](q1-sr-finisher.md)** — Final-stage benchmarking of a systematic review or other evidence synthesis against Q1 journal standards before submission: audits structural moves against canonical patterns (PRISMA 2020, AMSTAR-2, JBI, GRADE/CERQual, MOOSE, ENTREQ, PRISMA-NMA, PRISMA-ScR, RAMESES), checks end-to-end logical coherence, and orchestrates the QA constellation. Audits, gates, and orchestrates; does NOT draft prose. Complements evidence-synthesis-researcher, which handles the upstream pipeline.
- **[reference-verifier](reference-verifier.md)** — Verifies manuscript references and citations: existence checks against PubMed/DOI/web, detection of hallucinated DOIs and fabricated authors, claim-source agreement, in-text-to-reference-list matching, and reference formatting.
- **[sr-delta-screener](sr-delta-screener.md)** — Screens a prepared queue of systematic-review records (title/abstract, then full text) against an explicit eligibility rubric on a screening-harness directory (packs/<id>.md + work/screening_queue.jsonl + SCREENING_RUBRIC.md), such as the PflegeStressPlan search-update harness. Recommends INCLUDE/EXCLUDE/UNSURE/NEEDS_FULLTEXT per criterion with a verbatim supporting quote; acts as screener-2/pre-screen and never silently includes. Invoke with the run directory path and optional batch size.
- **[statistical-reviewer](statistical-reviewer.md)** — Audits statistical claims in manuscripts: p-values, effect sizes, confidence intervals, sample sizes, test selection against data characteristics, precision of statistical language, and numerical consistency across abstract, text, and tables.
- **[stats-code-decontaminator](stats-code-decontaminator.md)** — Cleans LLM tells out of statistical and analytical scripts (R, Python, SPSS, SAS, Stata) so they read expert-authored: restyles comments, naming, structure, and documentation while preserving the statistical logic exactly. Use proactively on any LLM-generated analysis script before it enters the research workflow or supplementary materials.
- **[submission-formatter](submission-formatter.md)** — Formats any text for any named submission target (journal, publisher, funder, conference): researches the target's requirements live, then checks and fixes text compliance and/or produces a formatted .docx. Handles any citation style; asks for the target if none is given. (APA 7 has its own dedicated agent, apa7-formatter.)
- **[translation-back-checker](translation-back-checker.md)** — Verifies German-to-English translations in manuscripts: quote accuracy and nuance, appropriate glossing of German institutional terms for international audiences, and adequacy of the translation-methodology description. Specialised for the Charité/German academic context.

## Licence

MIT — see [LICENSE](LICENSE).
