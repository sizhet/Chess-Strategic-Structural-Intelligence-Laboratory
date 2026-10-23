# Chess-SSIL Validation Roadmap

**Repository:** Chess as a Strategic Structural Intelligence Laboratory (Chess-SSIL)  
**Version:** 1.0.0  
**Authors:** Sizhe Tan & GPT-Obot  
**Status:** Proposed research roadmap; no experimental results are claimed

## 1. Purpose and scope

This roadmap translates Chess-SSIL's conceptual claims into reproducible experiments. The goal is **not** to demonstrate that a chess engine wins games. It is to test whether explicit localization, per-node intelligence, competitive UIRTU-relay, residual handling, and structural growth offer measurable, transferable benefits over appropriate baselines.

Chess-SSIL is an experimental companion to *Strategic Structural Intelligence and Competitive UIRTU-Relay (SSICR)*, not a replacement for its general theory. The contracts in `specs/` are provisional research interfaces, not established standards.

### Core research question

> Can a competitive game environment support autonomous generation, evaluation, revision, and portable reuse of *identifiable intelligence structures*, rather than only improvement of policy parameters or increased search effort?

**Scope boundary:** Self-play has demonstrated powerful autonomous strategy learning in games. It does not by itself establish autonomous structural redesign, unrestricted continual improvement, or open-world ASI. Each is a separate empirical claim.

## 2. Evidence levels and claim discipline

| Level | Claim | Minimum evidence |
|---|---|---|
| E0 | Proposed mechanism | Explicit definition, assumptions, and falsification condition |
| E1 | Functional feasibility | Deterministic end-to-end run, legal transitions, trace replay |
| E2 | Comparative benefit | Repeated controlled comparisons against strong baselines |
| E3 | Structural benefit | Auditable structure change, ablation, matched resources, robust gain |
| E4 | Transferable benefit | Independent implementation or cross-task replication |
| E5 | Open-world generality | Out-of-distribution evidence under changing rules and objectives; not claimed by this roadmap |

Report negative and null results at every level. Never infer E3 from E1 or E2 alone.

## 3. Shared experimental foundations

### 3.1 Game selection

- **Tic-Tac-Toe:** small, fully enumerable; use exact minimax as an oracle. Perfect play draws from the initial position.
- **Nim or another precisely specified impartial game:** test rule-to-strategy generation and cross-game interface reuse. Specify the exact variant and terminal convention.
- **Connect Four:** introduce nontrivial lookahead and positional patterns; use verified solved positions or established solvers where feasible.
- **Chess:** test multi-perspective localization, strategy combination, resource allocation, and long-horizon counter-evidence; avoid claims of complete solution.
- **Go / other multi-agent environments (optional):** exploratory scaling and generalization, not required for v1.0.0.

### 3.2 Baseline families

For each claim choose baselines that isolate the mechanism:

1. Legal random or fixed-rule policy (sanity check, never sole baseline).
2. Minimax/alpha-beta with equivalent evaluation and compute where applicable.
3. MCTS or other search policy with matched rollout/compute budget.
4. Fixed-architecture learned policy or value model with matched data and training compute.
5. **No-structural-growth ablation:** identical system with candidate structure updates disabled.
6. **Random-structural-change control:** equal change budget, random or shuffled candidate selection.
7. **No-relay/no-provenance control:** only for interoperability or collective-learning experiments.

Use established strong engines as reference opponents when useful, but do not equate performance against a single engine configuration with general superiority.

### 3.3 Fair comparison protocol

- Pre-register primary metric, dataset/position distribution, baselines, and acceptance thresholds before examining final results.
- Keep game rules, starting-position sampling, opponent pool, time control, hardware, search nodes, training examples, and tuning effort comparable or report them explicitly.
- Pair games with colors reversed; use common seeds or matched position sets where possible.
- Reserve held-out positions and opponents; do not tune on final evaluation sets.
- Run multiple independent seeds; report uncertainty intervals and failure rates, not just best runs.
- Track both training and inference cost, including candidate generation, validation, rejected candidates, and maintenance overhead.
- Preserve complete versioned logs and source provenance.
- Distinguish statistical significance from practical effect size; correct for repeated selection/testing where relevant.

## 4. Phase 0 — Contract and reproducibility readiness

**Objective:** Establish a minimal shared language before comparing intelligence mechanisms.

**Tasks**

- Specify canonical state, legal moves, transition rules, terminal conditions, and game-history semantics.
- Implement or document adapters for `SPEC-001` (state/localization/UIRTU), `SPEC-002` (evaluation/relay), and `SPEC-003` (growth/evidence).
- Define stable IDs for game, run, position, perspective, policy, UIRTU, strategy, structural version, and experiment.
- Create machine-readable manifests for seeds, compute budgets, dependencies, and rule versions.
- Verify event ordering, deterministic replay where applicable, and evidence linkage.

**Exit gate G0:** Two independent adapters or implementations can exchange and replay a small sample of legal game traces with consistent results. If only one implementation exists, mark interoperability **unverified** and proceed provisionally.

**Deliverables:** Contract examples, conformance checklist, sample event traces, reproducibility manifest.

## 5. Phase 1 — Canonical SSICR mapping

**Suggested games:** Tic-Tac-Toe, specified Nim variant.  
**Evidence target:** E1.

**Experiments**

- Map `Game State → Localization → Per-Node Evaluation → Strategy Selection → Action → Validated Transition`.
- Demonstrate that identical board states may have different interpretations under explicit perspectives while preserving a single authoritative rules engine.
- Test illegal-action rejection, terminal-state handling, history reconstruction, and strategy traceability.
- Compare rule-only, exact-minimax, and modular UIRTU implementations on identical positions.

**Primary measures:** legal-action rate (target 100%), state-replay agreement (target 100%), decision trace completeness, per-decision latency and overhead.

**Exit gate G1:** Full legal and replay consistency, plus a documented separation between raw state, localization output, strategy proposal, and authoritative transition. Winning performance is not an exit criterion.

**Falsification opportunity:** If the proposed interface cannot preserve necessary game semantics or introduces unmanageable overhead, revise the contract before advancing.

## 6. Phase 2 — Localization and strategy-generation tests

**Suggested games:** Tic-Tac-Toe, Connect Four, selected chess positions.  
**Evidence target:** E2.

**Experiments**

- Compare raw-state policies with explicit tactical, positional, and historical localization perspectives.
- Compare static perspective weights against context-dependent perspective selection.
- Compare fixed per-node action selection against a strategy generator that selects modules and allocates compute.
- Test whether localization can identify uncovered or conflicting states without using outcome labels from the held-out test set.

**Measures:** decision accuracy against exact/verified reference where available, match performance, calibration, compute-normalized performance, perspective-selection overhead, robustness on held-out positions.

**Exit gate G2:** At least one pre-registered hypothesis shows a reproducible benefit under matched resources, or a credible null/negative result identifies limits and is released with its evidence. Do not require a positive finding to declare the experiment complete.

## 7. Phase 3 — Competitive relay and residual intelligence

**Suggested games:** Connect Four and chess position suites.  
**Evidence target:** E2–E3.

**Experiments**

1. Log **Execution Stream** events (decisions, legal transitions), **Evidence Stream** events (predictions, outcomes, counterexamples), and **Evolution Stream** events (updates and versions) separately.
2. Trigger residual analysis on pre-specified signals: out-of-coverage position, forecast error, perspective conflict, search instability, or module incompatibility.
3. Compare residual-triggered analysis with fixed extra search, random triggers, and no trigger at matched budgets.
4. Build adversarial position suites and retain failures, including cases where a proposed repair worsens performance elsewhere.

**Measures:** residual detection precision/recall where labels are defensible, failure recovery, false-trigger cost, worst-slice performance, calibration, replayability, and regression rate.

**Exit gate G3:** Traceable residual-to-intervention episodes and controlled evidence of benefit or limitation; each proposed repair includes counter-evidence and explicit scope.

## 8. Phase 4 — Autonomous structural strategy evolution

**Suggested games:** Connect Four first; chess after basic validity.  
**Evidence target:** E3.

**Candidate structural changes**

- New or revised localization perspective.
- New scoring operator or evaluation composition.
- New reusable UIRTU or routing/dispatch condition.
- New strategy-generator selection or search-budget policy.
- New residual trigger or evaluator, subject to independent evaluation.

**Candidate lifecycle**

`Propose → Register → Sandbox → Compare → Challenge → Accept/Reject → Monitor → Roll Back (if needed)`

**Critical isolation tests**

- Structural-change-enabled vs frozen structure with **equal total compute**.
- Structural change vs parameter-only adaptation.
- Structural change vs increased search budget.
- Targeted candidate selection vs random candidate selection.
- Proposed structure with and without the new component (ablation).
- In-distribution vs held-out opponents, positions, and game variants.

**Measures:** win/draw/loss rates or game-specific utility, compute-normalized improvement, structure count/complexity, sample efficiency, retained gains, catastrophic regressions, and rollback frequency.

**Exit gate G4:** At least one independently auditable change survives matched-resource comparisons and held-out tests; otherwise report the attempted change and its negative result. A larger or more complex system alone does not qualify as structural intelligence growth.

**Safety gate:** All autonomous structural updates occur in a bounded sandbox; promotion into a reference implementation requires explicit evaluation and rollback support.

## 9. Phase 5 — Collective learning and research relay

**Suggested scope:** Two or more independent teams/implementations; small games are sufficient.  
**Evidence target:** E4.

**Experiments**

- Exchange a localization operator, UIRTU module, strategy manifest, or residual dataset across independent implementations.
- Compare contract-based integration against unstructured descriptions or ad hoc adapters.
- Test whether a receiver can discover relevant modules from capability metadata, validate applicability, and reject incompatible versions.
- Attempt compositional reuse of two independently contributed modules; test for positive, neutral, and negative interactions.
- Reproduce a published failure case and a published successful intervention from the same evidence package.

**Measures:** integration person-hours, time-to-first-valid-run, replay success, reproducibility rate, defect rate, compatibility failures, transfer gain, provenance completeness, and number of reusable contributions.

**Exit gate G5:** Independent replay and at least one documented cross-implementation transfer, including measured integration cost and any failures. Claims that relay *accelerates* collective learning require controlled comparisons, not anecdotal reuse.

## 10. Hypothesis-to-phase traceability

The `TESTABLE-HYPOTHESES.md` document is authoritative for exact hypothesis wording. The following mapping is a **planning crosswalk**; reconcile identifiers with that document before release.

| Hypothesis family | Proposed IDs | Primary phase | Evidence focus |
|---|---|---|---|
| Localization and strategy generation | H01–H03 | 2 | Representation, dynamic selection, budget control |
| Competitive relay and residual intelligence | H04–H06 | 3 | Evidence stream, triggers, counter-evidence |
| Autonomous structural evolution | H07–H08 | 4 | Genuine structural improvement vs confounds |
| Collective learning and research relay | H09–H12 | 5 | Portability, provenance, matching, composition |
| Transfer and autonomy boundaries | H13–H14 | 4–5 and future work | Cross-game limits, fixed-rule vs open-world claims |

## 11. Common evidence package

Each published experiment should contain at minimum:

```text
experiment-package/
├── README.md                    # question, hypothesis, result, limitations
├── manifest.json                # rules, code versions, seeds, compute, hardware
├── protocol.md                  # preregistered comparisons and thresholds
├── interfaces/                  # SPEC versions and adapter notes
├── runs/                        # replayable logs or immutable references
├── results.csv                  # per-run/per-seed results, not only aggregates
├── analysis.md                  # uncertainty, ablations, confounders
├── counter-evidence.md          # failures, regressions, adversarial cases
├── provenance.md                # authors, licenses, dependencies, lineage
└── reproduction.md              # commands or precise procedural steps
```

For privacy, licensing, or resource constraints, publish a documented minimal substitute and state what cannot be independently reproduced. Do not claim independent replication where only internal replay occurred.

### Suggested event identifiers

`experiment_id`, `run_id`, `game_id`, `state_id`, `ruleset_id`, `perspective_id`, `uirtu_id`, `strategy_id`, `structure_version`, `candidate_id`, `evidence_id`, `parent_event_id`, `timestamp`, `compute_budget`.

These are proposed field names, not a finalized JSON schema. The normative meaning and any required fields should be reconciled with SPEC-001–003.

## 12. Failure and rollback policy

Treat failures as research outputs:

- **Invalid transition:** stop the run; fix state/rules contract.
- **Non-reproducible benefit:** downgrade claim; publish seed-level results.
- **Evaluation leakage or unfair budget:** invalidate comparison and rerun.
- **Regressive structural change:** reject or roll back; preserve the counterexample.
- **Unclear attribution:** report as system-level improvement, not proven structural gain.
- **Incompatible relay contribution:** record the failed localization, version, or integration boundary.
- **Evaluator gaming:** challenge with held-out opponents, independent metrics, and adversarial tests.

Never discard unsuccessful experiments merely because they weaken a preferred hypothesis.

## 13. Minimal viable research program

A small independent contributor can complete a meaningful project without implementing a full chess engine:

1. Implement the Phase 1 pipeline for Tic-Tac-Toe using an existing authoritative rules library or a fully tested local rules engine.
2. Export one `SPEC-001`-compatible state/localization/decision trace.
3. Compare a fixed strategy with one explicit localization or routing modification under identical conditions.
4. Publish both successful and failed positions, per-seed results, and resource costs.
5. Package the module and evidence so a second implementation can replay it.

**Minimum meaningful contribution:** a falsifiable result, a portable module, a conformance test, or a reproducible counterexample. A complete SSICR stack is not required.

## 14. Governance and release milestones

| Milestone | Artifact | Release criterion |
|---|---|---|
| M0 | v1.0.0 research design | Documents, provisional specs, explicit hypotheses, no unsupported results |
| M1 | Canonical trace reference | G0–G1 documented |
| M2 | Controlled strategy study | G2 results with negative cases |
| M3 | Residual/evidence benchmark | G3 with held-out evaluation |
| M4 | Structural evolution demonstrator | G4 with fair ablation and rollback |
| M5 | Independent research relay | G5 with external reproduction |

These are **dependency milestones**, not promised dates. If a gate fails, revise the claim or contract rather than silently advancing.

## 15. Open questions for the next revision

- Which localization outputs are truly portable across distinct game engines?
- How can a strategy generator be compared fairly when it changes its own search allocation?
- What is the smallest convincing example of *structural* rather than parametric improvement?
- How should counter-evidence be weighted when different evaluators disagree?
- Can a public capability registry reduce discovery and integration costs in a measured study?
- How do learned structures retain validity under rule changes, opponent distribution shifts, or new objectives?
- Which results generalize beyond closed, deterministic, perfect-information games?

## 16. Closing principle

> **The laboratory succeeds when claims become testable, failures become reusable evidence, and independent discoveries can be localized, relayed, validated, and integrated.**

Chess-SSIL is an invitation to collective experimentation. Its intended output is not a predetermined demonstration of ASI, but a growing, auditable body of evidence about how competitive structural intelligence can—and cannot—evolve.

---

**Related repository materials:** `docs/CSSIL-001` through `CSSIL-005`; `specs/SPEC-001` through `SPEC-003`; `research/OPEN-QUESTIONS.md`; `research/TESTABLE-HYPOTHESES.md`.

**Citation:** Cite the repository's `CITATION.cff` and associated DOI once published. Until then, cite the versioned repository URL and release tag.
