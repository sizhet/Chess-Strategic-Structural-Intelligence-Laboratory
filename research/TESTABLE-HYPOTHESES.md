# Testable Hypotheses — Chess as a Strategic Structural Intelligence Laboratory (Chess-SSIL)

**Version:** 1.0.0  
**Authors:** Sizhe Tan & GPT-Obot  
**Status:** Proposed research hypotheses; not empirical findings  
**Related:** `docs/CSSIL-001`–`CSSIL-005`, `specs/SPEC-001`–`SPEC-003`, `research/OPEN-QUESTIONS.md`, `research/VALIDATION-ROADMAP.md`

## 1. Purpose and Scope

Chess-SSIL uses progressively more demanding, rule-governed games to test whether Strategic Structural Intelligence and Competitive UIRTU-Relay (SSICR) can support **reproducible strategy learning, identifiable structural changes, and transferable collective learning**. This document specifies falsifiable hypotheses rather than claiming that SSICR, structural recursive self-improvement, or artificial superintelligence has been demonstrated.

The target progression is **Tic-Tac-Toe / Nim → Connect Four → Chess → selected Go or multi-agent variants**. Each stage should preserve a common experiment record while allowing game-specific state encodings, legality checks, and evaluation methods.

### Core distinctions

- **State:** authoritative rules and board configuration.
- **Localization:** an interpreted, possibly multi-perspective structural representation of that state.
- **Per-Node UIRTU:** a bounded, versioned decision capability operating on a localization or state input.
- **Strategy generator:** a mechanism that selects, composes, or revises decision procedures.
- **Parameter learning:** weights or values change while the architecture remains fixed.
- **Structural growth:** a versioned change in operators, routing, interfaces, module composition, or decision architecture.
- **Collective relay:** independently produced research artifacts are discovered, matched to needs, transferred, validated, and integrated.

A stronger win rate alone is **not** proof of structural growth, and self-play alone is **not** proof of autonomous structural evolution.

## 2. General Experimental Protocol

Every test should pre-register the hypothesis, game and rules version, baseline, treatment, compute and data budgets, evaluation seeds or starting positions, primary metric, failure criterion, and replication plan. Record code and artifact versions, hardware, time limits, legal-action validation, and game transcripts. Use paired openings or swapped player colors where relevant. Report uncertainty intervals and negative results; avoid selecting a test set after observing the outcome.

**Primary measures:** win/draw/loss rate, score against a fixed opponent pool, exploitability or optimality gap where computable, evaluation calibration, generalization to held-out positions, compute per move, sample efficiency, structural complexity, and independent reproduction rate.

**Suggested decision rule:** define a meaningful effect threshold *before* testing; compare paired outcomes with uncertainty intervals or an appropriate pre-registered statistical test. A non-significant result is inconclusive when power is inadequate; a reliably negative or equivalence-bounded result can challenge the hypothesis. Adjust for multiple comparisons across many candidates.

## 3. Hypothesis Register

### H01 — Explicit Localization Adds Measurable Value

**Claim:** Under matched information and compute budgets, a modular agent with explicit structural localization can outperform a state-to-action baseline on at least one pre-registered distribution of unfamiliar positions.

**Test:** Compare (A) raw-state policy and (B) policy using versioned tactical/positional features, with comparable parameter counts and training exposure. Hold out tactical motifs or position families.

**Measures:** held-out performance, calibration, compute, and feature-attribution stability.

**Falsification pressure:** no meaningful improvement across pre-registered tests, or gains vanish after equalizing resources. A null result in one setting does not establish universal uselessness.

### H02 — Multi-Perspective Localization Improves Robustness

**Claim:** A controlled ensemble of distinct perspectives (e.g., material, king safety, mobility, threats) improves performance or calibration over the strongest individual perspective in some defined position families.

**Test:** Single-perspective ablations versus multi-perspective routing; use held-out adversarial and ordinary positions.

**Measures:** mistake rate by position family, calibration, decision latency, and disagreement detection.

**Failure condition:** no robust benefit after accounting for additional compute or greater model capacity.

### H03 — Strategy Composition Beats a Fixed Selector in Changing Contexts

**Claim:** A context-sensitive strategy generator that selects among bounded UIRTU modules outperforms a fixed module selector under controlled shifts in opponent style or position distribution.

**Test:** Compare fixed, randomized, and context-dependent routing using the same module library and budgets.

**Measures:** performance by shift, adaptation latency, routing regret, and overhead.

**Failure condition:** the dynamic generator does not outperform a properly tuned fixed or mixture baseline.

### H04 — Competitive Relay Produces Useful Evidence Beyond Final Outcomes

**Claim:** Turn-level prediction and transition traces improve diagnosis of failures and subsequent learning compared with terminal win/loss records alone.

**Test:** Train or revise agents with (A) final outcomes only and (B) outcomes plus validated intermediate traces; keep total interaction and compute controlled.

**Measures:** time to identify failures, sample efficiency, prediction accuracy, and trace storage cost.

**Failure condition:** additional traces do not improve diagnosis or learning under fair budgets.

### H05 — Residual-Triggered Analysis Is More Efficient Than Uniform Analysis

**Claim:** Allocating extra search or diagnostic computation to pre-defined residual signals yields a better performance–cost frontier than uniform allocation.

**Test:** Compare fixed search, randomized allocation, and residual-triggered allocation using identical average compute limits.

**Measures:** error reduction per compute unit, missed-critical-position rate, false triggers.

**Failure condition:** no advantage over simple uncertainty-based or uniform baselines.

### H06 — Counter-Evidence Reduces False Structural Promotions

**Claim:** Requiring adversarial counter-evidence tests before accepting structural changes reduces the rate of regressions on held-out opponent pools.

**Test:** Randomly assign candidate changes to standard validation versus standard plus counter-evidence gates, without allowing extra test-set tuning.

**Measures:** regression frequency, acceptance precision, cost, and time to promotion.

**Failure condition:** the additional gate yields no material reliability benefit or imposes disproportionate cost.

### H07 — Autonomous Structural Change Can Improve Performance Beyond Parameter Updates

**Claim:** Under matched resources, an agent permitted to add, replace, or reroute versioned decision modules can achieve a measurable gain over a fixed-architecture learner.

**Test:** Fixed architecture with parameter updates versus structural search with an explicit change log; control for total search trials, training compute, and evaluation exposure.

**Measures:** held-out performance, compute, change provenance, and architecture complexity.

**Failure condition:** structural treatment shows no net gain or only benefits from extra optimization resources.

**Important:** This is a research hypothesis, not a result already established for Chess-SSIL.

### H08 — Strategy-Generator Evolution Adds Value Beyond Strategy Learning

**Claim:** Updating the mechanism that selects or composes strategies can outperform updating only the strategies inside a fixed generator.

**Test:** Compare fixed generator + evolving modules against evolving generator + same module candidates, with matched optimization budgets.

**Measures:** adaptation across opponent pools, generalization, stability, and complexity.

**Failure condition:** generator changes provide no independent gain after controlling for search effort.

### H09 — Explicit Structural Provenance Improves Reproducibility

**Claim:** Versioned contracts and provenance records reduce the time and error rate required for an independent team to reproduce a result.

**Test:** Give independent teams equivalent artifacts with and without standardized state, localization, UIRTU, strategy, and evidence manifests.

**Measures:** reproduction success, elapsed time, ambiguity reports, integration defects.

**Failure condition:** standardized records do not improve outcomes or impose greater burden than benefit.

### H10 — Portable Research Units Improve Cross-Team Reuse

**Claim:** A portable contribution package with inputs, outputs, assumptions, evaluation evidence, and failure cases increases successful cross-team reuse versus prose-only descriptions.

**Test:** Randomized or crossover integration exercises using matched research contributions.

**Measures:** successful integration rate, time to first valid run, defect count, and semantic mismatch.

**Failure condition:** no measurable improvement across independent teams.

### H11 — Localization of Existing Capabilities Is a Distinct Collective-Learning Bottleneck

**Claim:** Capability discovery based on explicit problem–capability matching improves reuse over keyword-only or unstructured browsing.

**Test:** Researchers solve tasks using a common registry, with or without structured applicability metadata; keep available modules identical.

**Measures:** retrieval precision, correct applicability decisions, downstream solution success, search time.

**Failure condition:** structured matching provides no advantage over strong information-retrieval baselines.

### H12 — Relay and Composition Generate Gains Without New Algorithms

**Claim:** Some benchmark improvements can be achieved solely by recombining existing validated UIRTU modules, without inventing new component algorithms.

**Test:** Freeze the component library and compare independent modules, fixed composition, and learned composition on held-out tasks.

**Measures:** gain over best individual module, integration cost, robustness, and failure modes.

**Failure condition:** composition does not beat strong single-module or simple ensemble baselines.

### H13 — Gains Transfer Across Game Families Only Within Measured Boundaries

**Claim:** Selected structural contracts or diagnostic methods learned in small games transfer to larger games with lower adaptation cost than game-specific redevelopment.

**Test:** Freeze generic interfaces and adapt them from Tic-Tac-Toe or Connect Four to Chess; compare against new implementations with equal engineering budgets.

**Measures:** integration time, correctness, performance overhead, number of game-specific changes.

**Failure condition:** transfer costs equal or exceed redevelopment, or abstractions hide essential game-specific information.

### H14 — Closed-Rule Autonomy Does Not Automatically Generalize to Open-World Autonomy

**Boundary hypothesis:** Success at autonomous strategy learning in a fixed, fully specified game does not by itself predict reliable behavior under changing rules, incomplete observations, conflicting objectives, or contested evaluation.

**Test:** Progressively introduce rule changes, partial observability, multi-objective rewards, and distribution shifts. Measure degradation and recovery.

**Interpretation:** This is a boundary probe, not a claim that all transfer is impossible. Strong transfer would narrow the identified gap; poor transfer would reinforce the need for additional mechanisms and governance.

## 4. Prioritization for Independent Researchers

| Priority | Hypotheses | Recommended environment | Why start here |
|---|---|---|---|
| P0 | H04, H05, H06, H09 | Tic-Tac-Toe, Nim, Connect Four | Cheap, auditable evidence and failure handling |
| P0 | H10, H11 | Shared benchmark and module registry | Direct tests of collective-learning friction |
| P1 | H01, H02, H03, H12 | Connect Four, small chess positions | Modular localization and strategy composition |
| P1 | H07, H08 | Connect Four, restricted Chess | Distinguish architecture evolution from tuning |
| P2 | H13, H14 | Cross-game and altered-rule tasks | Boundaries of portability and autonomy |

These priorities reflect experimental tractability, not a claim about expected outcomes.

## 5. Minimum Research Contribution Record

A useful contribution may be a failed experiment, a test case, a reusable UIRTU, a new localization, a counterexample, or an integration report. Each contribution should include:

```yaml
contribution_id: "cssil-example-001"
hypothesis_id: "H05"
contribution_type: "experiment"  # experiment | module | counterexample | replication
ruleset_id: "connect-four-standard-v1"
baseline_id: "fixed-budget-search-v1"
treatment_id: "residual-triggered-search-v1"
protocol_version: "1.0"
code_version: "commit-or-archive-id"
compute_budget: "documented-and-matched"
train_test_separation: "documented"
primary_metric: "error-reduction-per-node-expanded"
uncertainty_method: "pre-registered"
result_status: "pending"  # positive | negative | inconclusive | pending
artifact_links: []
known_limitations: []
counter_evidence_links: []
```

Avoid publishing identifying personal data, private game logs, or unlicensed third-party artifacts. Record licenses and provenance for shared assets.

## 6. Evaluation Integrity and Governance

1. **Rule authority:** legality and terminal outcomes must be checked by an independent game engine or formally verified ruleset.
2. **Leakage control:** isolate training, validation, and final test positions; track repeated positions and transpositions where material.
3. **Compute parity:** report search nodes, wall-clock, hardware, training cost, and candidate-selection cost.
4. **Baseline strength:** include simple baselines and the strongest feasible matched baseline; avoid straw-man comparisons.
5. **Anti-Goodhart:** assess performance across opponent pools and held-out settings, not only a self-play opponent.
6. **Rollback:** maintain reversible structural versions and a regression suite before promotion.
7. **Independent verification:** distinguish developer-run results from third-party replications.
8. **Claims discipline:** report association and task-specific performance rather than inferring general intelligence or ASI.

## 7. Mapping to the Three Provisional Contracts

| Research element | Contract | Evidence expected |
|---|---|---|
| Game state, legal actions, localization | `SPEC-001` | Valid state, interpretation provenance, UIRTU input/output |
| Strategy evaluation and competitive events | `SPEC-002` | Paired games, actions, outcomes, traces, resource use |
| Candidate structural change and acceptance | `SPEC-003` | Version diff, counter-evidence, validation gate, rollback |

The contracts are provisional research interfaces. Independent implementations may propose revisions if they document compatibility and migration implications.

## 8. What Would Count as Meaningful Progress?

A successful first research cycle need not produce a strong chess engine. It would be meaningful to demonstrate **one** of the following with a reproducible baseline: a better residual trigger under matched compute; a measurable advantage from a modular strategy selector; a structural change with independently verified benefit; or a reduction in cross-team integration time through portable contracts.

Conversely, credible negative results identify where the proposed abstraction does **not** help. Those results should be retained as first-class collective-learning assets.

## 9. Research Position

**The central test is not whether a chess program can win. It is whether identifiable, portable, and independently testable structural mechanisms improve the way strategies are generated, evaluated, revised, and collectively reused.**

Chess and simpler games supply controlled laboratories for that question. They do not, on their own, establish open-world autonomous intelligence evolution.

---

**Citation note:** Cite the Chess-SSIL repository and the specific hypothesis ID when reporting experiments. Replace any placeholder DOI with the actual DOI only after publication.

**Authors:** Sizhe Tan & GPT-Obot  
**License:** Follow the repository's published license and citation metadata.
