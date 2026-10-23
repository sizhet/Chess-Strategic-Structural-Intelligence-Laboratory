# Open Questions — Chess as a Strategic Structural Intelligence Laboratory (Chess-SSIL)

**Version:** 1.0.0  
**Status:** Open research agenda; hypotheses are not established results  
**Authors:** Sizhe Tan & GPT-Obot  
**Related framework:** Strategic Structural Intelligence and Competitive UIRTU-Relay (SSICR)

## Purpose

This document identifies falsifiable questions for researchers using chess and smaller perfect-information games as laboratories for Strategic Structural Intelligence (SSI), competitive UIRTU-Relay, autonomous strategy evolution, and collective structural learning. It is a research agenda, not a claim that the proposed architecture has been implemented or validated.

**Research principle:** A useful answer should specify an environment, an operational definition, a baseline, an evaluation protocol, and evidence that could disconfirm the claim.

## A. Canonical Mapping and Representation

### OQ-01 — What counts as an actual UIRTU in a game?

Is a UIRTU a reusable callable decision unit, a typed transition contract, a strategy module, or a move-instance? How can an implementation distinguish a persistent unit from its execution trace?

- **Test:** Define stable module identities and input/output schemas; replay multiple move decisions using the same unit.
- **Counter-evidence:** The mapping merely relabels ordinary function calls without enabling modular replacement or transfer.

### OQ-02 — Does structural localization improve decision quality?

Can explicit tactical, positional, historical, and opponent-model perspectives outperform raw-state or monolithic representations at matched training and inference cost?

- **Test:** Ablate each perspective on held-out positions and compare playing strength, calibration, and compute.
- **Counter-evidence:** No measurable gain after controlling for search and model capacity.

### OQ-03 — How should conflicting perspectives be resolved?

When king safety, material, initiative, and long-term positional factors disagree, should a controller use learned arbitration, uncertainty-aware scoring, or search-conditioned selection?

- **Test:** Measure performance and calibration on positions with deliberately conflicting evaluations.

### OQ-04 — What is the smallest useful localization contract?

Which fields are essential for independent modules to interpret a position without forcing a particular internal representation?

- **Test:** Exchange position and localization records across independently written modules using SPEC-001.

## B. Per-Node Intelligence and Strategy Generation

### OQ-05 — Where is the boundary between a policy and a strategy generator?

What observable behavior distinguishes a move selector from a controller that chooses perspectives, modules, search budgets, and evaluation methods?

- **Test:** Hold move-selection models fixed while varying controller choices; quantify attributable gains.

### OQ-06 — When does dynamic composition outperform fixed pipelines?

Can per-position selection of UIRTU modules improve performance, reliability, or cost compared with a strong fixed pipeline?

- **Test:** Compare under identical time, memory, and training budgets across varied position classes.

### OQ-07 — Can strategy generators improve themselves structurally?

Can a system propose and retain changes to module topology, arbitration rules, or search allocation—not merely update weights?

- **Test:** Require machine-readable before/after structural diffs, controlled evaluation, and independent replay under SPEC-003.

### OQ-08 — How should compute be allocated across uncertain branches?

Can residual-triggered search or adaptive budget allocation outperform uniform search at the same total node expansions?

- **Test:** Match total search nodes or wall-clock budget; compare regret and tactical error rate.

## C. Competitive Relay and Autonomous Learning

### OQ-09 — Which parts of the competitive loop must be independently observable?

How can execution, evidence, and evolution streams be recorded without conflating a legal transition, a prediction, and a learning update?

- **Test:** Reconstruct each game and every model update from typed logs specified by SPEC-002.

### OQ-10 — What does self-play establish—and what does it not establish?

Under what conditions does self-play yield stronger policies, and how can we avoid treating improvement at one game as evidence of open-world intelligence?

- **Test:** Evaluate against frozen historical opponents, diverse external baselines, and held-out openings.

### OQ-11 — How can nontransitive strategy cycles be detected?

A defeats B, B defeats C, and C defeats A: does the selection process preserve diversity or mistakenly collapse to one policy?

- **Test:** Use round-robin payoff matrices, population evaluation, and exploitability estimates where tractable.

### OQ-12 — Can the system avoid reward and evaluator gaming?

What safeguards detect a strategy that optimizes an imperfect evaluation metric while weakening real playing strength?

- **Test:** Separate training evaluators from independent tournament outcomes and adversarial probes.

## D. Residual Intelligence and Structural Growth

### OQ-13 — What constitutes a residual rather than ordinary uncertainty?

How should coverage gaps, prediction errors, search failures, transfer failures, and relay incompatibilities be operationalized?

- **Test:** Label residual categories on benchmark cases; measure inter-rater agreement and predictive usefulness.

### OQ-14 — Which residuals justify structural intervention?

When should a system increase search, retrain parameters, add a perspective, or create a new module?

- **Test:** Compare interventions on the same residual cohorts; include intervention cost and regression risk.

### OQ-15 — How can causal credit be assigned to a structural change?

If training data, search budget, and module topology change together, how can structural benefits be isolated?

- **Test:** Factorial ablations and matched-budget trials with preregistered primary metrics.

### OQ-16 — How can structural bloat and regression be prevented?

What acceptance, rollback, complexity, and maintenance gates keep growth from becoming uncontrolled accumulation?

- **Test:** Track strength, latency, memory, failure rate, and module count across successive accepted changes.

### OQ-17 — Can counter-evidence be reused across agents?

Can a failure case from one implementation reveal an equivalent weakness in another despite differences in representations?

- **Test:** Transfer annotated counterexamples using normalized game states and explicit applicability constraints.

## E. Experimental Validity and Scaling

### OQ-18 — Which games provide the best progression of evidence?

What is learned uniquely from Nim, Tic-Tac-Toe, Connect Four, chess, and Go, and when does added complexity cease to clarify mechanisms?

- **Test:** Establish a staged benchmark suite with exact-solution checks where available and reproducible fixed-seed trials.

### OQ-19 — How can learning, search, and structural evolution be disentangled?

Do apparent gains persist when compute, experience, and evaluation opportunities are matched?

- **Test:** Compare fixed architecture plus more search, fixed architecture plus more training, and structural evolution at equal resource budgets.

### OQ-20 — What constitutes meaningful generalization?

Does a discovered structure transfer to unseen openings, opponent styles, board sizes, game variants, or a distinct game?

- **Test:** Predefine in-distribution, out-of-distribution, and cross-game transfer suites; report negative results.

### OQ-21 — What would falsify the central structural-evolution advantage hypothesis?

Under which task distributions and resource limits should the framework be judged unsuccessful?

- **Test:** Preregister thresholds for strength, efficiency, robustness, and transfer; publish null and adverse findings.

## F. Collective Learning and Research Relay

### OQ-22 — What is the minimal portable research contribution?

Can an independent researcher contribute one localization operator, scorer, residual detector, strategy module, or counterexample without adopting the whole architecture?

- **Test:** Run a third-party module through SPEC-001–003 with no private integration steps.

### OQ-23 — Where do research relay failures occur?

Are the primary obstacles discovery, applicability localization, interface mismatch, reproducibility, or integration cost?

- **Test:** Record failure categories and time-to-integration for contributed artifacts.

### OQ-24 — Does standardization accelerate collective learning?

Do shared contracts reduce duplicate effort and integration time enough to offset schema and governance overhead?

- **Test:** Compare independent teams using a common contract versus ad hoc integration on equivalent tasks.

### OQ-25 — How should evidence provenance and negative results travel?

What metadata makes a contribution auditable, comparable, citable, and safe to reuse?

- **Test:** Require versioned datasets, seeds, rule variants, budgets, baseline IDs, outcome measures, and known failure conditions.

### OQ-26 — Can compositional growth be measured independently of discovery?

Can the system gain new capability by recombining existing validated modules, without adding new base algorithms?

- **Test:** Freeze the module library; permit only new compositions and measure capability gains on held-out tasks.

## G. Limits, Governance, and Generalization

### OQ-27 — What is the scope of the proposed “automatic license”?

Which capabilities are demonstrated by autonomous policy learning, which require autonomous structural changes, and which remain unsupported for open-world intelligence?

- **Test:** Maintain a claims-to-evidence matrix separating established findings, local demonstrations, and conjectures.

### OQ-28 — Who governs goals and acceptance criteria?

How are objective functions, evaluator authority, compute limits, and deployment permissions kept distinct from the system's ability to improve strategies?

- **Test:** Require externally defined constraints and auditable approval gates for structural deployment.

### OQ-29 — What breaks when game assumptions are relaxed?

How do partial observability, stochastic transitions, shifting rules, multi-agent cooperation, and real-world costs change the architecture?

- **Test:** Introduce one assumption change at a time and document failed contracts and required adaptations.

### OQ-30 — Can the framework support cumulative progress without premature universality claims?

What evidence would justify expanding from game-specific SSICR to more general structural intelligence, and what evidence would limit that claim?

- **Test:** Use explicit scope statements, external replication, and transfer benchmarks before broadening conclusions.

## Suggested Research Priorities

| Priority | Questions | Why start here? | Minimum deliverable |
|---|---|---|---|
| P0 | OQ-01, 04, 09, 22 | Establish interoperability and observability | One replayable game trace and a replaceable module |
| P0 | OQ-15, 19, 21 | Prevent false structural-growth claims | Matched-budget baseline and ablation protocol |
| P1 | OQ-02, 05, 06, 08 | Evaluate architectural benefits | Localization/controller comparison |
| P1 | OQ-13, 14, 17 | Turn failures into testable repair proposals | Residual dataset and intervention study |
| P1 | OQ-23, 24, 25 | Test collective-learning value | Cross-team integration experiment |
| P2 | OQ-07, 16, 20, 26 | Study validated autonomous growth | Versioned structural-change lineage |
| P2 | OQ-27–30 | Bound broader extrapolations | Claims-to-evidence and governance review |

## Recommended Contribution Template

A contribution addressing any question should include:

1. **Question ID and precise claim** — what is being tested, with an operational definition.
2. **Environment and rules** — game, variant, initial-position distribution, and termination rules.
3. **Module and contract versions** — inputs, outputs, dependencies, and compatibility constraints.
4. **Baselines and budget** — training examples, search nodes, hardware, time, and memory.
5. **Evaluation protocol** — seeds, opponents, held-out scenarios, uncertainty estimates, and primary metric.
6. **Evidence and counter-evidence** — successes, failures, raw logs, and reproducibility instructions.
7. **Scope and limitations** — what the findings do *not* establish.
8. **Provenance** — authorship, licenses, artifacts, and citation details.

## Connections to Repository Materials

- `docs/CSSIL-001-Chess-as-a-Canonical-SSICR-Laboratory.md` — conceptual mapping and research scope.
- `docs/CSSIL-002-Localization-Per-Node-and-Strategy-Generation.md` — representation and decision modules.
- `docs/CSSIL-003-Competitive-Relay-and-Autonomous-Strategy-Evolution.md` — learning and strategy evolution.
- `docs/CSSIL-004-Residual-Intelligence-and-Structural-Growth.md` — failure-driven structural change.
- `docs/CSSIL-005-Collective-Learning-and-Research-Relay.md` — independent contribution and transfer.
- `specs/SPEC-001-Game-State-Localization-and-UIRTU-Contract.md` — state and decision interfaces.
- `specs/SPEC-002-Strategy-Evaluation-and-Competitive-Relay.md` — competitive evidence streams.
- `specs/SPEC-003-Structural-Growth-and-Evidence-Record.md` — change control and validation.
- `research/TESTABLE-HYPOTHESES.md` — formalized claims and metrics (planned companion).
- `research/VALIDATION-ROADMAP.md` — phased experimental program (planned companion).

## Closing Perspective

Chess-SSIL seeks to turn a broad theoretical proposal into an open, falsifiable, modular research program. The central challenge is not merely to discover a strong move or policy; it is to determine whether strategies, strategy-generating structures, and portable research contributions can be improved through competitive evidence while retaining independent validation and human-governed boundaries.

**Collective-learning principle:** Intelligence may fail to propagate not because it is absent, but because discovery, localization, relay, validation, or integration breaks down. Each such breakdown is itself a legitimate research problem.

---

*Chess-SSIL v1.0.0 · Sizhe Tan & GPT-Obot · Open research questions; not claims of validated results.*
