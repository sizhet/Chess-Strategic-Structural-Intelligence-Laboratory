# CSSIL-006 — Strategy-Generability Partition and Residual-to-Generable Evolution

**Subtitle:** An Incremental Research Path from Autonomous Strategy Generation to Expanding Structural Intelligence  
**Repository:** Chess as a Strategic Structural Intelligence Laboratory (Chess-SSIL)  
**Authors:** Sizhe Tan & GPT-Obot  
**Version:** 1.0.0  
**Status:** Research proposal; hypotheses and provisional interfaces, not demonstrated general intelligence

## Abstract

Chess and other finite games demonstrate how strategies can be searched, evaluated, and improved within well-defined rules. They do not, by themselves, establish that arbitrary real-world tasks can be autonomously solved or that structural self-improvement is guaranteed. This paper proposes **Strategy-Generability Partition (SGP)**: classify tasks according to whether their strategies can be generated and validated under explicit assumptions, budgets, and authority constraints. Tasks that do not meet those criteria are not discarded; they enter a **Residual Domain** for diagnosis, decomposition, evidence acquisition, evaluator development, and potential **Residual-to-Generable Conversion (RGC)**. The goal is a measurable, reversible expansion of reliable autonomous strategy coverage. SGP and RGC are proposed as research mechanisms for Competitive UIRTU-Relay, Structural Intelligence, and Collective Learning, not as established solutions to open-world autonomy.

**Keywords:** strategy generability; residual intelligence; structural intelligence; UIRTU-Relay; SSICR; autonomous strategy generation; collective learning; evaluation; governance; chess

## 1. Research Motivation

A common research ambition is to build a general agent capable of solving nearly every problem in one unified process. This ambition can obscure an engineering opportunity: many domains already support effective automatic strategy generation because they expose actions, transitions, feedback, and meaningful evaluation. Chess is an unusually clean example, but similar structures arise in constrained scheduling, simulation-based design, test-driven software development, and some scientific optimization tasks.

The proposed alternative is incremental:

1. Identify tasks where strategy generation is already sufficiently specified and verifiable.
2. Build reliable autonomous search, learning, and competition within those tasks.
3. Treat the remaining tasks, missing assumptions, and failed cases as explicit residuals.
4. Invest in mechanisms that make selected residuals newly generable.
5. Validate every expansion before incorporating it into the autonomous operating domain.

This is a research program for **expanding a verified capability frontier**, not an assertion that all problems can eventually be reduced to games.

## 2. Definitions and Scope

### 2.1 Task and strategy

Represent a task instance as

\[
T=(S,A,\mathcal{T},O,J,C,B,\Gamma),
\]

where:

- \(S\): state space or state representation;
- \(A\): candidate actions and legal-action constraints;
- \(\mathcal{T}\): transition model or access to an environment that executes actions;
- \(O\): observations and feedback;
- \(J\): objective, evaluation criteria, or an explicitly stated partial ordering;
- \(C\): contextual constraints and available evidence;
- \(B\): resource budget (compute, time, data, experiment cost);
- \(\Gamma\): governance and authorization boundaries.

A **strategy** is a policy, plan, decision procedure, or composable structural mechanism that maps relevant context and observations to candidate actions. A strategy can be generated without being correct, safe, deployable, or optimal. These claims require separate evidence.

### 2.2 Generability is conditional, not intrinsic

Define a provisional predicate

\[
G(T;E,B,\tau)=1
\]

only when an implementation has demonstrated that it can produce strategies for task \(T\), and validate them against declared evidence \(E\), budget \(B\), and acceptance thresholds \(\tau\). This is a claim relative to an environment and a test protocol, not a metaphysical classification of the problem.

A task may be generable in a simulator but not yet generable for real-world deployment. A task may also be generable for advisory outputs while autonomous execution remains unauthorized.

### 2.3 Three maturity levels

- **G1 — Strategy Searchable:** legal or admissible candidates can be generated and evaluated at least provisionally.
- **G2 — Strategy Learnable:** a learning or search process yields reproducible improvement against strong, budget-matched baselines.
- **G3 — Structurally Evolvable:** identifiable changes to localization, evaluators, UIRTU modules, relay topology, or strategy-generation procedures improve held-out outcomes and survive independent validation.

These levels are not automatic promotions. G3 requires evidence that the benefit is attributable to a structural modification, not simply extra compute, parameters, or training data.

### 2.4 Residual Domain

The Residual Domain contains task instances or task components whose current evidence is insufficient for a claimed generability level. Reasons may include unknown rules, missing evaluators, unreliable simulators, unobserved state, unbounded action consequences, ambiguous objectives, or authorization limits.

**Residual is a diagnostic and routing status, not proof that a problem is permanently unsolvable.**

## 3. Strategy-Generability Partition (SGP)

The proposed SGP pipeline is:

```text
Incoming Task / Game / Objective
              |
              v
Task Contract + Scope + Authority
              |
              v
Generability Assessment
   |                         |
   v                         v
Verified Generable       Residual Domain
Domain (G1/G2/G3)        (reasons recorded)
   |                         |
   v                         v
Strategy Generator       Residual Handler
   |                         |
   v                         v
Evaluation / Relay       Evidence / Decomposition /
   |                     Evaluator / Model Repair
   |                         |
   +---- Verified RGC <------+
              |
              v
Updated Task Coverage and Evidence Registry
```

### 3.1 Assessment dimensions

A generability assessment should document:

| Dimension | Key question | Failure / residual example |
|---|---|---|
| Rules and constraints | What actions are admissible? | Incomplete business or safety rules |
| State and localization | Can relevant state be observed and interpreted? | Hidden dependencies |
| Transition and simulation | Can candidate actions be tested meaningfully? | Simulator-to-reality mismatch |
| Evaluation | Can better strategies be distinguished reliably? | Reward proxy misalignment |
| Feedback | Is feedback timely and attributable? | Delayed or confounded outcomes |
| Resources | Can testing be performed within budget? | Intractable search |
| Robustness | Does the result generalize beyond training cases? | Overfitting to one opponent |
| Authority | May the strategy be executed autonomously? | Human approval required |

Passing one dimension cannot compensate silently for failure on another. A weighted summary score may assist triage, but hard constraints and unresolved authority requirements must remain visible.

### 3.2 Partition at subtask granularity

Many real-world problems are mixed. A task should be decomposed into independently testable components when feasible. For example, software delivery may contain generable components (unit-test repair, dependency checks) and residual components (ambiguous requirements, stakeholder value judgments). The entire project must not be marked generable merely because a few subroutines are automatable.

## 4. Residual-to-Generable Conversion (RGC)

RGC is the proposed process of changing the task representation, evidence, evaluator, or execution environment so that a previously residual component passes an explicit generability gate.

### 4.1 Conversion operators

1. **Localization repair:** identify missing context, state features, or task-to-capability mappings.
2. **Problem decomposition:** isolate smaller, testable subtasks with explicit interfaces.
3. **Evidence acquisition:** obtain measurements, counterexamples, domain constraints, or experimental data.
4. **Evaluator construction:** define objective tests, reference solutions, preference comparisons, or uncertainty-aware validation.
5. **Simulator or sandbox construction:** create a bounded environment for repeatable candidate testing, while measuring model fidelity.
6. **UIRTU composition:** reuse portable modules and contracts to build a new strategy generator.
7. **Human or external delegation:** obtain missing judgments or permissions without pretending they were autonomously inferred.

### 4.2 Proposed lifecycle

```text
Residual Registered
  -> Root-Cause Diagnosis
  -> Conversion Proposal
  -> Sandbox Trial
  -> Baseline Comparison
  -> Independent Validation
  -> Accept / Reject / Defer
  -> Evidence Registry Update
```

A successful RGC claim must record what changed, what became generable, which assumptions were added, the tested task distribution, and what remains residual. Failed conversions are valuable counter-evidence.

### 4.3 Non-monotonic frontier

Generability is **not guaranteed to increase monotonically**. New evidence can invalidate a simulator, expose an unsafe strategy, reveal distribution shift, or overturn an evaluator. Systems must support demotion from G3 to G2/G1 or back to Residual, with preserved provenance and rollback.

## 5. Chess as a Canonical Starting Point

Chess provides formal rules, deterministic legal transitions, a bounded board representation, and objectively defined terminal outcomes. These properties make it a useful laboratory for G1 and G2. Modern chess and Go systems demonstrate powerful automated strategy learning and search, but their success does not imply that the entire game tree has been exhaustively solved or that their architecture autonomously invents new structural modules.

Chess-SSIL should use a graduated sequence:

| Stage | Environment | Research purpose |
|---|---|---|
| 0 | Tic-Tac-Toe / small Nim | Ground-truth legality, exhaustive baselines, replay |
| 1 | Connect Four or constrained variants | Search-budget tradeoffs, residual detection |
| 2 | Chess | Multi-perspective localization, strategic composition |
| 3 | Controlled task variants | Evaluator gaps, transfer, distribution shift |
| 4 | Selected real-world sandboxes | Conditional transfer beyond games, with external validation |

A meaningful test is not whether the system wins at chess; it is whether **SGP correctly predicts when a strategy-generation procedure is reliable**, and whether **RGC expands that verified domain** under controlled comparison.

## 6. Competitive UIRTU-Relay Architecture

Within the broader SSICR architecture, SGP and RGC can be assigned to separable components:

- **Task Intake / Contract:** parse objectives, constraints, task distribution, and permissions.
- **Generability Assessor:** issue a provisional G1/G2/G3/Residual classification with supporting evidence.
- **Localization Layer:** produce multi-perspective task-state features and uncertainty records.
- **Per-Node UIRTU:** execute a bounded decision, search, evaluator, or transformation module.
- **Strategy Generator:** select, compose, and evaluate candidate policies or plans.
- **Competitive Relay:** run controlled opponents, variants, or benchmarks; emit execution and evidence records.
- **Residual Handler / RGC:** diagnose gaps and propose bounded conversions.
- **Structural Growth Controller:** test, accept, reject, or roll back changes under versioned governance.
- **Collective Learning Registry:** publish portable methods, conformance results, and counter-evidence.

The authoritative environment state, its localized interpretation, candidate action, validated transition, and learning update must remain separately observable. This supports independent audit and interoperable implementations.

## 7. Autonomous Strategy Coverage (ASC)

A candidate coverage metric is:

\[
ASC(D,B,\tau)=\frac{\sum_{i=1}^{n}w_i\,\mathbf{1}[\mathrm{Pass}(T_i;B,\tau)]}{\sum_{i=1}^{n}w_i},
\]

where \(D\) is a **declared task distribution**, \(w_i\) are pre-specified weights, \(B\) is a resource budget, and \(\tau\) is a set of evaluation and reliability gates.

Report ASC alongside:

- performance against matched baselines;
- held-out reliability and confidence intervals;
- human intervention and approval rate;
- compute, data, time, and experimental cost;
- real-world or external validity, when relevant;
- RGC conversion success and subsequent regression rate;
- safety, constraint, and authorization violations;
- retained residual mass and failure categories.

ASC is not a universal intelligence score. Its meaning depends on sampling, weights, task scope, evaluator quality, and acceptance thresholds. Publishing these is mandatory for meaningful comparisons.

## 8. Testable Hypotheses

**H-SGP-01 — Assessment utility.** An explicit SGP assessor predicts strategy-generation success on held-out tasks more accurately than a naive uniform-autonomy policy. **Falsifier:** no predictive gain under calibrated evaluation.

**H-SGP-02 — Partition efficiency.** Routing only validated generable subtasks to autonomous generation reduces wasted compute or failed attempts at matched quality. **Falsifier:** no net benefit once assessment overhead is included.

**H-RGC-01 — Conversion effectiveness.** Targeted residual repair increases verified coverage compared with repeated generic search under equal resources. **Falsifier:** gains disappear on held-out tasks or after budget matching.

**H-RGC-02 — Reusable conversion methods.** A documented conversion operator transfers to related residuals better than one-off ad hoc fixes. **Falsifier:** no transfer after controlling for task similarity.

**H-STR-01 — Structural improvement.** Automatically proposed structural changes outperform fixed-architecture alternatives under matched training data and compute. **Falsifier:** gains are explained by added resources or fail independent reproduction.

**H-CL-01 — Collective relay.** Shared contracts and evidence packages reduce the time or effort required for independent teams to reproduce and integrate validated conversions. **Falsifier:** no improvement against ordinary unstructured sharing.

Each hypothesis should be pre-registered with baselines, split strategy, evaluation metrics, stopping rules, and negative-result reporting.

## 9. Minimal Experimental Program

### Experiment A — Partition calibration

Create a mixed benchmark of small games and deliberately underspecified variants. Have an assessor predict which task instances can be reliably solved by a fixed generator. Compare predictions with observed outcomes; measure precision, recall, calibration, and abstention quality.

### Experiment B — Residual repair

Introduce one missing element at a time: state feature, rule, evaluator, or transition fidelity. Test whether the corresponding RGC operator restores performance under matched compute and without leakage from evaluation cases.

### Experiment C — Structural evolution versus scaling

Compare (i) fixed structure with more search, (ii) fixed structure with more training, and (iii) explicit structural changes. Record all costs, ablations, and counterexamples. Do not credit structure for improvements that can be explained by budget differences.

### Experiment D — Collective learning relay

Give independent teams either a conventional research summary or a versioned package containing task contract, operator, test cases, negative evidence, and reproduction instructions. Measure reproduction time, integration defects, and transfer success.

### Experiment E — Frontier regression

After promoting tasks to a generable class, introduce distribution shifts and evaluator perturbations. Verify that the system detects failures, demotes claims when warranted, and preserves prior evidence.

## 10. Research Relay Package (Provisional)

A minimal portable record could contain:

```yaml
record_id: "rgc-example-001"
schema_version: "0.1-provisional"
task_family: "small-board-game"
source_status: "residual"
target_status: "G1"
residual_reason: "missing-evaluator"
conversion_operator: "evaluator-construction"
assumptions:
  - "deterministic legal transitions"
validation:
  benchmark: "held-out-positions-v1"
  baseline: "fixed-generator-v1"
  compute_budget: "declared-in-experiment"
  outcome: "pending-independent-reproduction"
counter_evidence: []
authority:
  execution_mode: "sandbox-only"
artifacts:
  contract: "path/to/task-contract"
  tests: "path/to/reproduction-tests"
```

This is an illustrative schema, not a finalized interoperability standard. A contribution should also include code or pseudocode where available, license, authorship, provenance, limitations, and failed cases.

## 11. Collective Learning: Six Practical Hints

1. **Start with verifiable islands.** Choose bounded games and tasks where correctness or utility can be measured.
2. **Publish the partition criterion.** State why a task is G1/G2/G3 or Residual, and under which assumptions.
3. **Make residuals actionable.** Record the missing evidence, evaluator, context, or authority instead of labeling a task merely “hard.”
4. **Share conversion operators.** A reusable way to make a problem testable may matter more than a single successful answer.
5. **Preserve counter-evidence and reversibility.** Negative results, distribution shifts, and demotions are part of cumulative progress.
6. **Separate ability from authority.** Automatically generating a strategy never automatically grants permission to execute it.

The objective of Collective Learning is not only to share strategies but to share **the methods by which previously non-generable tasks become reliably generable**.

## 12. Boundaries and Open Problems

Several constraints limit the proposed expansion:

- **Underspecified objectives:** no amount of search can settle a normative dispute without a legitimate objective-setting process.
- **Simulator mismatch:** optimized simulated outcomes may not transfer to physical or social systems.
- **Feedback scarcity:** delayed, expensive, or unobservable outcomes make evaluation difficult.
- **Goodhart effects:** a metric can improve while real utility declines.
- **Combinatorial explosion:** some fully specified games remain computationally difficult.
- **Safety and irreversibility:** a strategy may be generable but inappropriate for autonomous execution.
- **Nonstationarity:** task rules, environments, and stakeholders may change.
- **Structural credit assignment:** proving that a specific new UIRTU or relay structure caused an improvement is challenging.

These are not mere engineering details; they determine whether a claimed conversion is scientifically meaningful.

## 13. Implications for the ASI Research Horizon

SGP suggests a possible incremental path toward broader autonomous structural intelligence:

\[
\text{Verified Generable Tasks}
\rightarrow \text{Competitive Strategy Learning}
\rightarrow \text{Validated Structural Evolution}
\rightarrow \text{Residual Conversion}
\rightarrow \text{Expanded Verified Coverage}.
\]

This pathway **does not establish ASI**, guarantee open-ended improvement, or show that most objective problems are automatically generable. It identifies measurable intermediate milestones. The research question is whether the verified frontier can expand across increasingly heterogeneous task families while maintaining evaluation integrity, resource efficiency, and appropriate governance.

The key separation remains:

> **Strategy automation can expand; action authority must be governed independently.**

The subject boundaries and scoring sovereignty developed in Subjective Structural Intelligence (SSI) remain relevant when moving beyond closed games.

## 14. Conclusion

Chess-SSIL offers a practical laboratory for studying automatic strategy generation. Strategy-Generability Partition turns this laboratory insight into a broader research methodology: concentrate effort where strategy generation is demonstrably reliable, diagnose what prevents other tasks from qualifying, and treat successful residual conversion as a measurable form of structural intelligence growth.

The proposed contribution is not a shortcut around uncertainty. It is a way to **make uncertainty explicit, route it productively, and progressively test the expansion of autonomous capability**.

> **Do not demand that autonomy solve everything first. Build a verified generable core, preserve the residual frontier, and expand through evidence-backed structural relay.**

## 15. Relationship to the Chess-SSIL Repository

- **CSSIL-001:** Chess as a Canonical SSICR Laboratory — foundational game-to-SSICR mapping.
- **CSSIL-002:** Localization, Per-Node, and Strategy Generation — task interpretation and decision architecture.
- **CSSIL-003:** Competitive Relay and Autonomous Strategy Evolution — competitive learning and structural improvement.
- **CSSIL-004:** Residual Intelligence and Structural Growth — diagnosis and candidate growth mechanisms.
- **CSSIL-005:** Collective Learning and Research Relay — portability, evidence, and interoperability.
- **CSSIL-006 (this paper):** Strategy-Generability Partition and Residual-to-Generable Evolution — a task-partition and frontier-expansion research program.
- **SPEC-001/002/003:** provisional contracts for state/localization, competitive evaluation, and structural growth evidence.
- **research/TESTABLE-HYPOTHESES.md** and **research/VALIDATION-ROADMAP.md:** baseline research program; future releases may incorporate the additional SGP/RGC hypotheses and experiments.

## References and Context

The following are conceptual reference points rather than evidence that SGP/RGC has already been validated:

- Silver, D., et al. (2017). *Mastering the game of Go without human knowledge*. Nature, 550, 354–359. https://doi.org/10.1038/nature24270
- Silver, D., et al. (2018). *A general reinforcement learning algorithm that masters chess, shogi, and Go through self-play*. Science, 362, 1140–1144. https://doi.org/10.1126/science.aar6404
- Sutton, R. S., & Barto, A. G. (2018). *Reinforcement Learning: An Introduction* (2nd ed.). MIT Press. http://incompleteideas.net/book/the-book-2nd.html
- Goodhart, C. A. E. (1975). *Problems of Monetary Management: The U.K. Experience*. Papers in Monetary Economics, Reserve Bank of Australia. (Historical origin of the principle commonly associated with metric-target failures.)

**Citation note:** Cite this work using the repository's `CITATION.cff` and DOI once released. No DOI is asserted here before publication.
