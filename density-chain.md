---
title: "Better Harnesses, Smaller Models: Building 90% Cheaper Agents via Automated Harness Adaptation"
authors: "Chenyang Yang, Xinran Zhao, Tongshuang Wu, Christian Kästner (Carnegie Mellon University)"
venue: "arXiv preprint (cs.SE), 2026"
source: "https://arxiv.org/abs/2607.08938 (pinned: arXiv:2607.08938v1, 2026-07-09)"
license: "CC BY 4.0 (per the arXiv record)"
date_summarized: 2026-07-18
verified_against_source: 2026-07-20
tier_budget_words: 150
tags: [llm-agents, small-language-models, agent-harness, cost-efficiency, meta-agent, software-engineering]
entity_ledger:
  - "harness adaptation thesis: shared task difficulty lifts into the harness — T1 — Abstract; §I"
  - "headline: 16/21 pairs improved, 7 close the gap, 89.7% of LLM performance at 4% cost — T1 — Abstract; §IV-D"
  - "meta-agent harness optimizer — T1 — §III"
  - "failure-mode framework: tool-use, instruction-following, knowledge, long-context, planning — T2 — §II-A; Fig. 2"
  - "adaptation strategies: add/manage contexts, create/manage tools, instrument code, orchestrate agents — T2 — §II-B; Fig. 2"
  - "seven business tasks from public benchmarks; 20/20/60 splits — T2 — §IV-A; Table I"
  - "three SLM families vs gemini-3.1-pro-preview — T2 — §IV-A"
  - "budget-approval exemplar: 75.0%→98.3% vs LLM 97.3%, 8% cost; anti-loop hook; 23 iterations — T3 — §I; §III-C; Fig. 1, 4"
  - "Table II averages: gemma 31.4→80.2, qwen 26.9→74.8, ministral 9.5→25.0 vs LLM 89.7 — T3 — Table II"
  - "$20/run optimization budget, ×3 runs/pair, $1260 total; amortized in ~13 runs — T3 — §IV-B; §IV-D"
  - "RQ2 diversity: Spearman ρ = −0.96; controlled 89.1%→68.0% — T4 — §IV-D; Fig. 5"
  - "RQ3 capability: stronger SLMs gain more (+48.8% vs +15.5%) — T4 — §I; Fig. 6"
  - "RQ4 strategy mix: instruction-following 81%, knowledge 81%, tool-use 62%, long-context 33%; contexts 86%, new tools 43%, managing tools 29%; no successful sub-agents — T4 — §IV-D"
  - "GEPA-style Pareto search over software-agent-sdk components — T4 — §III-A/B"
  - "optimizer lessons: diagnosis quality bottleneck; raw JSON beats summarized traces; diversity over iteration count — T5 — §V-A"
  - "per-SLM idiosyncrasy: no one-size-fits-all harness; re-optimize per model — T5 — §IV-D"
  - "threats: stochastic runs, one optimizer, clean environments, closed APIs — T5 — §IV-C"
  - "code released: github.com/malusamayo/migration-analysis — T5 — §I, footnote 1"
---

# T1 — Sparse

Frontier-LLM agents automate routine business work well but cost too much to
run at scale; small language models (SLMs) are cheap but fail when dropped
into a harness designed for a frontier model [Abstract; §I]. The paper's
thesis: for repetitive business tasks, much of the difficulty is shared
across task instances, so it can be lifted out of the model and into the
harness — tailored instructions, reduced tool sets, and orchestration
scaffolds — and a meta-agent can discover those adaptations automatically
from failure trajectories [Abstract; §I]. Across seven business-oriented
agentic tasks and three SLM families, optimized harnesses significantly
improve 16 of 21 task-SLM pairs, seven of which close the SLM-LLM gap
entirely; the best SLM agent recovers 89.7% of frontier-LLM performance at
4% of the cost [Abstract; §IV-D]. Adaptation works best on repetitive
workflows and on SLMs with sufficient base capability [Abstract].

# T2

SLMs (3B–8B active parameters) fail in LLM-designed harnesses, but the
failures are systematic. The paper builds a framework mapping five
capability-indexed failure modes — tool-use, instruction-following,
knowledge, long-context, and planning/reasoning — to harness adaptation
strategies grouped by component: add or manage contexts, create or manage
tools, and adapt the agent loop via programmatic hooks or multi-agent
orchestration [§II; Fig. 2]. A meta-agent harness optimizer then searches
that space automatically: it samples a harness, runs it, diagnoses failure
trajectories, and edits harness code [§III]. The study covers seven
business tasks curated from public benchmarks (attendance auditing, budget
approval, stock alerts, anomaly detection, Playwright testing, website
management, code refactoring; 20/20/60 splits) and three open-weight SLMs
against gemini-3.1-pro-preview [§IV-A; Table I]. Optimized harnesses
significantly improve 16 of 21 pairs, close the gap on seven, and the best
SLM recovers 89.7% of LLM performance at 4% cost [§IV-D].

# T3

Harness adaptation lifts shared task difficulty from model to scaffold. The
exemplar: a budget-approval agent scores 97.3% with gemini-3.1-pro at $0.22
per query; gemma-4-26b-a4b in the same generic harness scores 75.0%, but
with an automatically discovered harness — a step-by-step plan skeleton, a
filtered tool set, and an anti-loop hook, found after 23 optimizer
iterations — reaches 98.3% at 8% of the cost [§I; §III-C; Fig. 1, 4].
Averaged across seven tasks, optimization takes gemma-4-26b-a4b from 31.4
to 80.2 (LLM: 89.7), qwen3-coder-30b-a3b from 26.9 to 74.8, and
ministral-3-8b from 9.5 to only 25.0 [Table II]. Each task-model
optimization run costs $20 (×3 runs per pair; $1,260 total), amortized
after roughly 13 deployment runs [§IV-B; §IV-D]. Gains concentrate where
instances share workflows and where the model retains enough base
capability to keep the non-offloadable core [§IV-D].

# T4

The optimizer is a meta-agent loop over software-agent-sdk components
(system prompts, skills, custom tools, hooks, context condensers,
sub-agents): GEPA-style genetic sampling from the Pareto front, trajectory
diagnosis with search memory and design-space docs, sanity checks, then
validation-gated pool updates [§III]. Results quantify the conditions.
Diversity (RQ2): task diversity, measured as mean pairwise normalized
Levenshtein distance over tool-call sequences, correlates ρ = −0.96
(Spearman) with optimized performance, and diversity-controlled variants
drop from 89.1% to 68.0% as templates grow from three to twenty [§IV-D;
Fig. 5]. Capability (RQ3): stronger SLMs gain more (+48.8% vs +15.5%);
harnesses absorb task difficulty but cannot replace missing core capability
[§I; Fig. 6]. Strategy mix (RQ4): successful adaptations target
instruction-following (81%) and knowledge (81%) failures over tool-use
(62%) and long-context (33%), via added contexts (86%), new tools (43%),
tool management (29%); no sub-agent adaptation ever succeeded [§IV-D].
Best SLM: 89.7% of LLM performance, 4% cost [Table II].

# T5 — Dense

Thesis: repetitive business tasks share difficulty across instances, so a
meta-agent can lift it into the harness — plans, filtered tools, hooks —
making SLM agents (3B–8B active) rival frontier agents [Abstract; §I]. A
failure-mode framework (tool-use, instruction-following, knowledge,
long-context, planning → context/tool/loop adaptations) grounds an
optimizer: GEPA-style Pareto sampling over software-agent-sdk components,
trajectory diagnosis, validation gating [§II–III]. Seven benchmark-derived
tasks × three SLMs vs gemini-3.1-pro: 16/21 pairs significantly improve,
seven close the gap; gemma-4-26b-a4b averages 31.4→80.2 (LLM 89.7) — 89.7%
recovery at 4% cost — qwen 26.9→74.8, ministral 9.5→25.0; budget-approval
hits 98.3% vs LLM 97.3% at 8% cost [Table II; Fig. 1]. $20/run, amortized
in ~13 runs [§IV-B/D]. Conditions: diversity ρ=−0.96 (89.1%→68.0%
controlled); stronger SLMs gain +48.8% vs +15.5% [Fig. 5–6]. Adaptations
hit instruction-following/knowledge (81%/81%) via contexts (86%), new tools
(43%); sub-agents never worked; harnesses don't transfer across SLMs —
re-optimize per model [§IV-D]. Diagnosis quality bottlenecks search:
raw-JSON traces and a frontier meta-agent beat longer, cheaper exploration
[§V-A]. Code released [§I fn. 1].

# Key results

| Claim or metric | Exact value | Locator |
|---|---|---|
| Pairs significantly improved / gap closed | 16 of 21 task-SLM pairs; 7 close the SLM-LLM gap | Abstract; §IV-D |
| Best SLM recovery | 89.7% of LLM performance at 4% of cost, 25% latency reduction (gemma-4-26b-a4b) | Abstract; §IV-D; Table II |
| Budget-approval exemplar | LLM 97.3% @ $0.219; SLM generic 75.0% → adapted 98.3% at 8% cost; 23 optimizer iterations | §I; §III-C; Table II |
| Task-suite averages (accuracy, generic → optimized) | gemma-4-26b-a4b 31.4→80.2; qwen3-coder-30b-a3b 26.9→74.8; ministral-3-8b 9.5→25.0; gemini-3.1-pro 89.7 | Table II |
| Average cost per instance | gemini-3.1-pro $1.735; optimized gemma $0.071 | Table II |
| Optimization budget | $20 per run; 3 runs per pair; $1,260 total; amortized after ~13 runs | §IV-B (fn. 3); §IV-D |
| Diversity correlation (RQ2) | Spearman ρ = −0.96 (diversity vs optimized score); 89.1% → 68.0% from 3 to 20 templates | §IV-D; Fig. 5 |
| Capability effect (RQ3) | +48.8% (more capable SLMs) vs +15.5% (less capable) | §I; §IV-D; Fig. 6 |
| Failure modes addressed (RQ4) | instruction-following 81%; knowledge 81%; tool-use 62%; long-context 33% | §IV-D |
| Strategies used (RQ4) | adding contexts 86%; creating tools 43%; managing tools 29%; sub-agent creation: zero successes | §IV-D |
| Tasks and splits | 7 tasks (100 instances each; website-management 50); 20/20/60 train/val/test | Table I; §IV-A |
| Meta-agent | gemini-3.1-pro-preview; cheaper gemini-3-flash-preview yields worse harnesses despite more iterations | §IV-B; §V-A |
| Code | github.com/malusamayo/migration-analysis | §I, footnote 1 |

# Our take

This paper says out loud something our own doctrine arrived at from the
other direction: close failure classes with tooling shape, not with prayer
at the prompt. Their harness absorbs what our house rules call the
model-shaped risk — plans, filtered tools, hooks that programmatically
refuse the failure — and their RQ4 numbers put weight behind it:
instruction-following and knowledge failures dominate, and deterministic
scaffold beats model heroics for both. The result we find most
decision-relevant is the pairing of ρ = −0.96 (repetitiveness is almost
the whole ballgame) with the capability floor (+48.8% vs +15.5%): harnesses
amplify competence, they don't mint it. The lesson we starred: diagnosis
quality bottlenecks the whole search, and raw JSON trajectories beat
prettified summaries as meta-agent food — a warning against over-curating
what you show your tools. We registered this paper as a primary-verified
source in our research map; nothing in our repos exists *because of* it
yet, so it earns no inspirations entry — that's the receipts rule working
as intended.

# Provenance

- Canonical source: https://arxiv.org/abs/2607.08938
- Version studied: arXiv:2607.08938v1 (submitted 2026-07-09; v1 is the
  latest as of verification)
- Verified against source: 2026-07-18, studied from the arXiv v1 PDF fetched
  fresh from the versioned endpoint; section, table, and figure numbering
  follows that PDF
- Re-verified against source: 2026-07-20 — re-fetched arXiv:2607.08938v1 from
  the versioned PDF endpoint and re-checked every T1–T5 claim, key-results
  row, and locator (§II–VII, Fig. 1–6, Table I–II, footnotes 1–3) against it;
  no discrepancies found, verification date refreshed only
- Source license: CC BY 4.0, per the arXiv record
- Authors' code: https://github.com/malusamayo/migration-analysis [§I,
  footnote 1]
- Revisions or errata noticed since: none
