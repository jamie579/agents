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
2. Pick the agent whose description fits the task. If the task is missing or no description fits clearly, ask for the task or explain the gap; do not choose a vaguely related agent by default.
3. Fetch its `raw_url`, discard the `---`-delimited frontmatter, and adopt the
   markdown body as task-specific operating instructions, subject to the host
   platform's higher-priority safety, privacy, permission, and tool rules.

Prompt to paste into an LLM with web access:

> Fetch https://raw.githubusercontent.com/jamie579/agents/main/manifest.json — a
> catalogue of specialist agent prompts. Pick the agent whose description best
> fits my task. If no agent clearly fits, say so instead of forcing a match. Fetch
> its raw_url, ignore the YAML frontmatter between the --- markers, and adopt the
> markdown body as task-specific operating instructions before answering. Treat
> unavailable tools, skills, sibling agents, and memory stores as optional
> integration hooks: use an available equivalent or state the limitation; never
> pretend a check ran. Higher-priority platform safety, privacy, and permission
> rules still apply. Tell me which agent you chose. My task: [TASK]

Notes for non-Claude use: tool names in the frontmatter (`tools:`) and mentions
of agent-memory paths are Claude Code plumbing — ignore them when unavailable.
References to sibling agents and private skills are integration hooks, not proof
that those capabilities exist. Do not claim independent QA, current-guideline
verification, or Jamie-specific voice calibration unless it actually ran. Any
time-sensitive submission, funder, journal, or reporting rule must be checked
against a current authoritative source before it is treated as verified.

## Agents

- **[academic-article-architect](academic-article-architect.md)** — Planning orchestrator for academic manuscripts: assesses the material, settles paper type and target journal, and returns a Section Brief Package (SBP) that guides the section-writer agents. ASSESS and STRUCTURE phases only; also scopes revisions from reviewer comments into targeted section briefs. Not for drafting (section writers) or reviewing existing text (QA agents).
- **[academic-librarian](academic-librarian.md)** — Evidence-traceable academic information retrieval: refines review questions, selects sources, designs and PRESS-audits reproducible Boolean/controlled-vocabulary strategies, executes complete searches through available auditable interfaces, prepares platform-specific searches otherwise, and manages retrieval, citation chasing, de-duplication, and corpus handoff.
- **[anonymity-ethics-checker](anonymity-ethics-checker.md)** — Checks manuscripts for participant-identifying information, pseudonym consistency, and ethics/consent statement compliance; especially for small-sample qualitative research and German institutional data.
- **[apa7-formatter](apa7-formatter.md)** — APA 7th edition specialist, two modes: (1) check or fix APA 7 compliance in text (headings, citations, references, tables, title pages, abstracts) and convert from other citation styles; (2) produce a properly formatted .docx from a .md/.txt manuscript (fonts, spacing, margins, running head, heading levels, page numbers). For any non-APA target use submission-formatter.
- **[article-gate-checker](article-gate-checker.md)** — Quality-gate auditor for manuscript sections or an integrated manuscript: checks the approved Section Brief, evidence traceability, voice, reporting-guideline coverage, and cross-section consistency; distinguishes pass, conditional pass, fail, not assessable, and skipped checks.
- **[article-integrator](article-integrator.md)** — Combines drafted, gate-checked sections into a coherent manuscript: writes transitions, abstract, and title; harmonises terminology, numbers, and argument flow. Launch with all section drafts plus the full SBP; re-invoke after revisions to re-stitch and re-audit consistency.
- **[article-troubleshooter](article-troubleshooter.md)** — Diagnoses blocked manuscript workflows: failed gate checks, undraftable sections, cross-section contradictions, or mid-workflow restructuring. Traces the root cause, recommends the minimum recovery intervention, and scopes backtracks (which sections are invalidated, which survive).
- **[article-writer-conclusion](article-writer-conclusion.md)** — Drafts a conclusion, implications, or recommendations section from an approved brief and version-matched manuscript claims. Preserves scope and uncertainty, avoids false closure, and includes limitations, open questions, or recommendations only when the genre and evidence require them.
- **[article-writer-discussion](article-writer-discussion.md)** — Drafts an evidence-bounded Discussion from an approved section brief, findings, methods, introduction, and source set: interprets rather than reproduces results, labels speculative mechanisms, and handles strengths, limitations, implications, or conceptual contribution as the design permits.
- **[article-writer-findings](article-writer-findings.md)** — Drafts Findings, Results, or Analysis sections from an approved brief and authoritative outputs: adapts qualitative interpretation and theory use to the stated methodology, reports quantitative estimates precisely, and coordinates mixed-methods, conceptual, or review findings without inventing data.
- **[article-writer-introduction](article-writer-introduction.md)** — Drafts Introduction or Background sections from the architect's section brief, adapting to paper type: literature funnel for empirical papers, opening tension for theoretical ones. Pass summaries of already-drafted sections where the cross-reference map calls for them. Jamie's voice.
- **[article-writer-literature-review](article-writer-literature-review.md)** — Drafts standalone Literature Review, Background, or Theoretical Framework sections, and the conceptual core sections of theoretical/non-IMRaD papers; synthesises rather than summarises, every paragraph doing analytical work. NOT for empirical introductions (use article-writer-introduction). Jamie's voice.
- **[article-writer-methods](article-writer-methods.md)** — Drafts an evidence-bounded Methods or Methodology section from an approved brief and authoritative study records across qualitative, quantitative, mixed, theoretical, and review designs. Maps the applicable reporting checklist without treating it as the method and blocks rather than inventing missing design, analysis, or ethics facts.
- **[cruel-editor](cruel-editor.md)** — Unsparing, evidence-calibrated editor of academic prose: rates paragraphs, challenges unsupported claims, finds repetition and weak logic, flags contextual style problems, and identifies precise cuts or rewrites without treating generic patterns as proof of LLM authorship.
- **[data-integrity-auditor](data-integrity-auditor.md)** — End-to-end data integrity audit from raw data and codebook through analysis code to manuscript: response-scale handling, reverse-coding, score construction, recoding and transformations, PRISMA arithmetic, and numerical consistency across code, outputs, tables, and text.
- **[dfg-eigene-stelle-swarm](dfg-eigene-stelle-swarm.md)** — Builds, revises, and red-teams DFG proposals, especially the Eigene Stelle module: verifies current official forms first, then develops the project description, budget narrative, CV/publication content, prescribed-form completion schedule, attachment checklist, and source-linked elan compliance audit.
- **[evidence-synthesis-researcher](evidence-synthesis-researcher.md)** — Systematic review and evidence-synthesis workhorse: review structuring, inclusion/exclusion criteria, screening, data extraction, evidence tables, risk-of-bias assessment (RoB 2, ROBINS-I), synthesis, PRISMA flow diagrams, and status summaries of a review workspace.
- **[file-secretary](file-secretary.md)** — Read-first archivist for file work: inventories a bounded target, proposes content-informed names and folder/archive moves, and executes only an explicitly approved, collision-checked transaction with hashes, verification, and rollback mapping. Launch with the exact target path.
- **[grant-reviewer](grant-reviewer.md)** — Adversarial but evidence-calibrated simulated grant panel for any funder: verifies the current scheme rubric, applies three non-overlapping reviewer lenses, and tests scientific quality, feasibility, applicant fit, environment, risk, and budget without inventing weights, rules, or panel behaviour.
- **[jdr-harmoniser](jdr-harmoniser.md)** — Harmonises Job Demands-Resources category labels and construct names in systematic-review extraction data using a versioned project taxonomy informed by JD-R theory. Proposes evidence-traceable mappings for review before any approved SQLite update, with audit-only mode available.
- **[journal-format-checker](journal-format-checker.md)** — Checks a manuscript against a specific journal's submission guidelines: word limits, heading hierarchy, reference format, abstract structure, figure/table formatting, and reporting-guideline compliance (PRISMA, COREQ, etc.); generates pre-submission checklists.
- **[llm-prose-decontaminator](llm-prose-decontaminator.md)** — Audits and, when authorised, rewrites formulaic or voice-incongruent academic prose using Jamie's documented preferences. Reports local style and argument problems without inferring LLM authorship or certifying that prose is human.
- **[logic-focus-auditor](logic-focus-auditor.md)** — Audits logical coherence and focus: maps argument chains, catches fallacies and unsupported leaps, flags scope creep and tangents, checks conclusions follow from findings, and verifies the paper answers its own research question.
- **[methodology-congruence-checker](methodology-congruence-checker.md)** — Verifies a manuscript's methodology is congruent with the methodological literature it cites and internally consistent: ontology-epistemology-methodology alignment, method descriptions matched against their source literature, analytical approach fit to the research question, and contradictions between theoretical framework and methods used. Especially for qualitative, theoretical, and philosophically committed research.
- **[peer-review-writer](peer-review-writer.md)** — Drafts Jamie's reviewer reports on OTHER people's manuscripts (including round-2 re-reviews): affirmative, developmental, and in his voice. Requires confirmation that AI-assisted review is permitted before opening the manuscript; then uses a local-only workspace with no additional web/MCP disclosure. NOT for Jamie's own manuscripts (peer-reviewer-simulator) or prose editing (cruel-editor).
- **[peer-reviewer-simulator](peer-reviewer-simulator.md)** — Evidence-grounded simulated peer-review stress test for Jamie's own manuscript: uses non-overlapping reviewer lenses to assess novelty, significance, methodology, ethics, and verified journal fit; deduplicates issues and gives a clearly labelled simulated recommendation rather than predicting an editorial outcome.
- **[posthumanist-theory-interlocutor](posthumanist-theory-interlocutor.md)** — Theoretical engagement and sparring around critical posthumanism, feminist new materialism, and adjacent traditions (Deleuze/Guattari, Foucault, STS, decolonial, abolitionist, Black feminist, queer/crip theory) as they bear on nursing, clinical work, health workforce research, and health policy. Four modes: AUDITOR (humanist drift, decorative theory, fidelity to cited thinkers), SPARRING PARTNER (test arguments, surface tensions), DIAGNOSTICIAN (which framework fits a project), PEDAGOGUE (explain and situate concepts). Opinionated, not neutral.
- **[q1-sr-finisher](q1-sr-finisher.md)** — Final-stage, read-only audit of a systematic review or other evidence synthesis against current target-journal instructions and applicable reporting or conduct standards. Checks end-to-end coherence, uses exemplars only as heuristics, and requests or dispatches risk-based QA when available; does not draft prose.
- **[reference-verifier](reference-verifier.md)** — Verifies references and citations with field-level evidence: in-text-to-list matching, work identity and metadata, stable identifiers, versions or retractions, and claim-source agreement; distinguishes verified, partial, unverified, suspect, and positively confirmed invented records.
- **[sr-delta-screener](sr-delta-screener.md)** — Applies an explicit eligibility rubric to prepared systematic-review records (title/abstract, then full text) in a screening-harness directory (packs/<id>.md + work/screening_queue.jsonl + SCREENING_RUBRIC.md). Produces an auditable, AI-assisted INCLUDE/EXCLUDE/UNSURE/NEEDS_FULLTEXT assessment per criterion with verbatim support; derives its assessor/adjudication role from the current rubric and never claims to replace independent human screening. Invoke with the run directory path and optional batch size.
- **[statistical-reviewer](statistical-reviewer.md)** — Audits statistical claims in manuscripts: p-values, effect sizes, confidence intervals, sample sizes, test selection against data characteristics, precision of statistical language, and numerical consistency across abstract, text, and tables.
- **[stats-code-decontaminator](stats-code-decontaminator.md)** — Audits and, when authorised, improves comments, naming, structure, and documentation in statistical code while preserving behaviour, reproducibility, interfaces, analytical choices, and outputs; never infers or conceals authorship from style.
- **[submission-formatter](submission-formatter.md)** — Checks and formats text for a named journal, publisher, funder, or conference using current official requirements when they can be verified, with an explicit unverified fallback when they cannot. Can produce a fidelity-checked .docx and handle non-APA citation styles; APA 7 has a dedicated agent.
- **[translation-back-checker](translation-back-checker.md)** — Verifies German-to-English translations in manuscripts: quote accuracy and nuance, appropriate glossing of German institutional terms for international audiences, and adequacy of the translation-methodology description. Specialised for the Charité/German academic context.

## Licence

MIT — see [LICENSE](LICENSE).
