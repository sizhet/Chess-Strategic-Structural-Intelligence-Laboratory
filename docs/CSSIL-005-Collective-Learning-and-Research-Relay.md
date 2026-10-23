# CSSIL-005 — Collective Learning and Research Relay

**Chess as a Strategic Structural Intelligence Laboratory (Chess-SSIL)**  
**Version:** 1.0.0  
**Authors:** Sizhe Tan & GPT-Obot  
**Status:** Research framework and proposed experimental protocols  
**Companion:** CSSIL-001 through CSSIL-004; Strategic Structural Intelligence and Competitive UIRTU-Relay (SSICR)

## Abstract

A useful intelligence structure can exist without reaching the problem, agent, or environment that needs it. This paper argues that collective structural learning depends not only on discovery but also on *localization*, *relay*, *validation*, and *integration*. Chess and smaller deterministic games offer a controlled laboratory for studying those dependencies. We propose a Research Relay model in which independent investigators contribute portable localization operators, scoring modules, strategy generators, residual triggers, counter-evidence records, and reproducible evaluations. The paper distinguishes shared knowledge from executable, transferable intelligence; describes provisional research contracts and evidence standards; and proposes falsifiable experiments that test whether interoperability actually reduces duplicated effort and improves cumulative progress. These proposals are hypotheses and design targets, not established empirical results.

**Keywords:** collective structural learning; research relay; chess; SSICR; UIRTU; structural interoperability; portable intelligence; counter-evidence; autonomous strategy evolution; reproducibility.

## 1. The Problem: Intelligence Can Exist Yet Fail to Propagate

Research communities often rediscover solutions, repeat failed experiments, or struggle to reuse apparently relevant results. The limiting factor may be a missing discovery, but it may also be an inability to identify applicability, translate representations, validate evidence, or integrate a component into a different system.

We distinguish five stages:

1. **Discovery:** a candidate method, pattern, or module is found.
2. **Localization:** another investigator recognizes the conditions under which it may apply.
3. **Relay:** the method and its dependencies are transmitted in a usable representation.
4. **Validation:** the receiver tests claims against a declared baseline and protocol.
5. **Integration:** the method is composed with existing modules while preserving its operating constraints.

A publication may complete stage 1 while leaving stages 2–5 unresolved. Open access alone is therefore not equivalent to collective learning.

**Research thesis:** The rate of collective intelligence growth may be constrained by structural relay capacity, even when useful knowledge is already available.

## 2. From SIF to a Chess-Based Research Laboratory

The conceptual progression is:

- **Structural Intelligence Framework (SIF):** functional architecture, including perception, localization, per-node intelligence, control, contracts, and growth.
- **UIERU / UIRTU-Relay:** portable, composable intelligence units and their execution or transfer relationships.
- **SSICR:** strategy generation, competitive selection, and strategic relay across interacting agents.
- **Chess-SSIL:** controlled games for running, comparing, falsifying, and extending the preceding concepts.
- **Collective Research Relay:** independent contributions that can be reproduced, transferred, challenged, and recombined.

This is a proposed conceptual mapping. It does not imply that existing chess engines internally implement SIF, UIRTU, or SSICR.

Chess is especially useful because its legal actions and outcomes are well specified, while its strategic representations and computational trade-offs remain rich. Smaller games such as Nim, tic-tac-toe, and Connect Four permit cheaper reference solutions and more exhaustive testing.

## 3. Three Sources of Structural Growth

### 3.1 Discovery Growth

A researcher discovers a new scoring operator, tactic recognizer, search heuristic, or strategy-generation procedure.

### 3.2 Relay Growth

An existing module becomes usable in another agent or experimental context through a clearer interface, translated representation, or better applicability metadata. No new underlying algorithm is required.

### 3.3 Compositional Growth

Existing modules are recombined into a new capability—for example, a tactical residual detector triggers a deeper search policy only in positions where the normal evaluation is unreliable.

These mechanisms should be measured separately. A stronger composite system does not, by itself, demonstrate that a new primitive intelligence algorithm was discovered.

## 4. Four Research Bottlenecks

| Bottleneck | Observable symptom | Candidate intervention |
| --- | --- | --- |
| Discovery gap | No known solution to a failure class | Search, exploration, candidate generation |
| Localization gap | A relevant solution exists but is not retrieved or recognized | Problem–capability maps; applicability predicates |
| Relay gap | A solution is identified but cannot be transferred faithfully | Versioned schemas; dependency and provenance records |
| Integration gap | A transferred solution cannot operate correctly with the receiving system | Contract tests; adapters; sandbox integration |

A fifth cross-cutting bottleneck is **evidence mismatch**: experiments may use different rules, data, budgets, or outcome definitions, making reported improvements incomparable.

### 4.1 Why Localization Is More Than Search

Keyword retrieval may locate a paper about a known chess tactic but fail to recognize that its conditions apply to an unfamiliar position. Structural localization should identify relevant preconditions, state abstractions, and constraints—not merely matching names.

### 4.2 Why Relay Is More Than File Transfer

A scoring function copied without its perspective definition, input normalization, computational budget, or failure cases may produce misleading results. A valid relay must preserve enough semantics to support safe reuse and meaningful comparison.

## 5. The Research Relay Unit (RRU)

We propose a lightweight **Research Relay Unit (RRU)** as a contribution envelope, not as a replacement for UIRTU. An RRU describes a portable research artifact and its evidence. Its executable payload may be a UIRTU module, a dataset, a test, or a documented negative result.

### 5.1 Minimum Fields

| Field | Purpose |
| --- | --- |
| `unit_id`, `version`, `authors`, `license` | Identity, attribution, reuse conditions |
| `artifact_type` | Localization, scoring, strategy, residual, evaluator, dataset, or negative result |
| `game`, `ruleset`, `state_encoding` | Environment and representation |
| `inputs`, `outputs`, `preconditions` | Contract and applicability boundary |
| `dependencies`, `resource_budget` | Reproduction and integration requirements |
| `hypothesis`, `baseline`, `metrics` | Testable claim and comparison |
| `evaluation_protocol`, `seeds`, `artifacts` | Reproduction instructions |
| `failure_cases`, `counter_evidence` | Known limitations and challenges |
| `provenance`, `validation_status` | Traceability and independent verification |

### 5.2 Illustrative Manifest

```yaml
unit_id: example.tactical-residual-trigger
version: 0.1.0
artifact_type: residual_trigger
game: chess
ruleset: standard-chess
state_encoding: FEN
inputs: [position, evaluation, uncertainty]
outputs: [trigger, reason, recommended_search_budget]
preconditions: [legal_position, compatible_evaluator]
resource_budget: {max_ms_per_position: 100}
hypothesis: "Targeted deeper search reduces tactical evaluation errors"
baseline: "Fixed-budget search without trigger"
metrics: [tactical_error_rate, nodes_searched, wall_time_ms]
evaluation_protocol: "Frozen positions; paired seeds; equal total compute"
validation_status: proposed
counter_evidence: []
```

This example is illustrative only; it is not an implemented or validated module. A future SPEC should define field types, required metadata, and conformance tests.

## 6. Research Relay as a Closed-Loop Process

A proposed collective learning cycle is:

1. **Publish** a hypothesis and RRU with sufficient provenance.
2. **Discover and localize** candidate RRUs for a new problem.
3. **Check contracts** and adapt representations if necessary.
4. **Reproduce** the original result under declared conditions.
5. **Challenge** it with counterexamples and independent baselines.
6. **Integrate** it in a receiving SSICR system under controlled budgets.
7. **Measure transfer benefit**, failure modes, and integration cost.
8. **Return evidence** to the shared registry, including unsuccessful results.

A relay should be regarded as successful only after the receiving context verifies its utility or correctly records its limitations. A download, citation, or repository fork is not sufficient evidence of successful knowledge transfer.

## 7. Collective Learning Versus Autonomous Strategy Evolution

The Chess-SSIL research program should distinguish two feedback loops:

**Within-agent loop:** game execution → evidence → candidate strategy or structural update → validation → deployment or rollback.

**Across-researcher loop:** artifact publication → applicability matching → independent reproduction → integration → counter-evidence → improved shared artifacts.

These loops can reinforce each other, but neither guarantees the other. Self-play can improve a fixed architecture without producing portable research components. Conversely, an excellent shared component may be reusable without enabling autonomous structural redesign.

We also distinguish three maturity levels:

- **Established precedent:** autonomous strategy learning in defined games is supported by substantial prior research.
- **Research target:** autonomous modification and selection of modular strategy structures under controlled experiments.
- **Open frontier:** robust autonomous evolution across changing rules, objectives, environments, and evaluation regimes.

Success in a closed game must not be presented as proof of general or superintelligent autonomous evolution.

## 8. Six Practical Hints for Collective Learners

### Hint 1 — Start Small, Verify First

Use a small game with an available reference solver. Verify state legality, transitions, outcomes, and reproducibility before building elaborate strategy modules.

### Hint 2 — Separate State, Localization, and Strategy

Record raw game state separately from derived tactical or positional abstractions, evaluations, and action-selection policies. This makes module contributions and ablation tests interpretable.

### Hint 3 — Compare Against Strong Baselines

Compare with minimax, alpha–beta, MCTS, or fixed-architecture learning where appropriate. Hold compute, training data, game rules, and test distributions as comparable as possible.

### Hint 4 — Preserve Failures and Counter-Evidence

Publish tactical blind spots, failed transfers, counterexamples, negative results, and rollback decisions. A well-documented failure may be more reusable than an unqualified success claim.

### Hint 5 — Contribute Portable Pieces, Not Entire Systems

A useful contribution may be one evaluator, localization operator, trigger, test suite, or integration adapter. Small, versioned, well-tested components lower the barrier to independent participation.

### Hint 6 — Improve Relay, Not Only Intelligence

Measure whether others can find, understand, reproduce, adapt, and integrate a result. Better documentation, contracts, and applicability metadata may generate more collective value than another isolated performance gain.

## 9. Testable Hypotheses

**H1 — Localization improves reuse.** Structured applicability metadata increases correct identification of reusable modules compared with keyword-only retrieval, measured by precision, recall, and retrieval time.

**H2 — Contracts reduce integration friction.** Versioned input/output and precondition contracts reduce integration time and incompatibility defects compared with narrative-only descriptions.

**H3 — Counter-evidence improves reliability.** Shared failure cases reduce repeated failures on held-out adversarial positions, relative to sharing only positive results.

**H4 — Modular reuse improves cumulative progress.** Under matched team size and compute, a shared RRU registry yields more independently reproduced improvements per unit time than isolated research workflows.

**H5 — Composition produces transferable gains.** Combining compatible localization, residual, and search modules improves held-out performance or compute efficiency beyond each module alone; evaluate interaction effects using ablations.

**H6 — Relay capacity can become a bottleneck.** Increasing the number of independently generated modules without improving discovery and integration interfaces produces diminishing realized reuse; improved interfaces mitigate the decline.

These are hypotheses to test, not empirical conclusions. Results should include confidence intervals or uncertainty estimates, preregistered primary metrics where feasible, and explicit negative outcomes.

## 10. Minimal Experimental Program

### Experiment A — Can an Independent Researcher Reproduce a Module?

Provide a small-game module with frozen tests and a reference baseline. Ask an independent team to reproduce its outputs and performance. Measure setup time, agreement, errors, and missing dependencies.

### Experiment B — Does Applicability Metadata Improve Localization?

Create a collection of strategy modules and positions with independently adjudicated relevance labels. Compare keyword search with structured precondition matching on unseen queries.

### Experiment C — Does a Portable Residual Trigger Transfer?

Train or design a tactical error trigger in one position distribution; test it on different openings, opponents, or chess engines. Compare fixed compute against triggered compute, including false positives and missed failures.

### Experiment D — Does Shared Counter-Evidence Prevent Rediscovery?

Randomize independent teams to receive positive-only artifacts or artifacts plus documented counterexamples. Measure duplicated failures, validation effort, and successful improvements.

### Experiment E — Does Collective Relay Improve End-to-End Research Throughput?

Compare isolated workflows with registry-assisted workflows on the same task portfolio. Track verified improvements, person-hours, compute consumption, integration defects, and long-term maintenance burden.

**Experimental caution:** For human-team experiments, control prior expertise and account for collaboration effects. For agent experiments, control model versions, prompts, tool access, compute, and contamination between train and test sets.

## 11. Proposed Contribution and Validation Policy

A practical repository or future companion registry could label contributions as:

- `proposed`: documented idea, not yet tested;
- `locally-reproduced`: repeated by the original contributor under a fixed protocol;
- `independently-reproduced`: replicated by a separate investigator;
- `transfer-validated`: shown useful in at least one distinct receiving context;
- `challenged`: credible conflicting evidence exists;
- `deprecated`: replaced, invalidated, or unsafe for the declared use.

Labels should include dates, artifact versions, test protocols, and links to evidence. They are descriptive research statuses, not universal certifications. An artifact may remain useful within a narrow applicability range even when challenged elsewhere.

## 12. Governance and Limits

Open research relay introduces risks: incompatible licenses, provenance gaps, benchmark gaming, accidental data leakage, invalid evaluation, and propagation of flawed components. A responsible collective system should require attribution, explicit scope, sandbox testing, version pinning, rollback, and evaluator independence where feasible.

Competitive results are especially vulnerable to Goodhart effects. Winning against a narrow opponent pool does not establish robust strategic superiority. Evaluate against diverse opponents, held-out positions, resource budgets, and changing distributions.

The game environment fixes many constraints that remain unresolved in the open world: goal specification, partial observability, conflicting values, physical action consequences, and institutional authority. These limits should remain explicit when discussing implications for general autonomous intelligence.

## 13. Relationship to Companion Documents

- **CSSIL-001:** chess as a canonical SSICR laboratory.
- **CSSIL-002:** localization, per-node intelligence, and strategy generation.
- **CSSIL-003:** competitive relay and autonomous strategy evolution.
- **CSSIL-004:** residual intelligence, counter-evidence, and structural growth.
- **CSSIL-005 (this paper):** portable contributions and collective research relay.
- **SPEC-001:** game-state, localization, and UIRTU interface.
- **SPEC-002:** strategy evaluation and competitive relay protocol.
- **SPEC-003:** structural growth and evidence record.
- **research/TESTABLE-HYPOTHESES.md:** cross-paper hypothesis register.
- **research/VALIDATION-ROADMAP.md:** staged experiments and acceptance criteria.

The companion specifications are planned research contracts, not established standards.

## 14. Future Directions

Promising next steps include interoperable RRU manifests, reference implementations for small games, automated contract conformance, structural precedent registries, causal attribution for composite strategies, cross-game transfer, adversarial evaluation, and human–AI research collaboration. A useful first milestone would be an independently reproduced small-game module that another team integrates without consulting its original author.

## 15. Conclusion

Collective learning requires more than creating knowledge and making it public. It requires mechanisms through which an existing insight can be **found, localized, transferred, tested, integrated, and challenged** where it is needed. Chess-SSIL offers a controlled environment for testing this proposition with portable intelligence modules and reproducible competitive experiments.

The central proposed insight is:

> **Evolution may be delayed not because intelligence is absent, but because intelligence cannot reach, recognize, or integrate with the place where it is needed.**

The practical objective is not to build another monolithic chess engine. It is to establish a small, rigorous research relay through which independent discoveries—and independent refutations—can accumulate into more reliable structural intelligence.

---

## References and Research Context

The following works provide relevant background, not direct validation of the Chess-SSIL framework:

1. Silver, D., et al. (2017). *Mastering the game of Go without human knowledge*. Nature 550, 354–359. https://doi.org/10.1038/nature24270
2. Silver, D., et al. (2018). *A general reinforcement learning algorithm that masters chess, shogi, and Go through self-play*. Science 362, 1140–1144. https://doi.org/10.1126/science.aar6404
3. Kocsis, L., & Szepesvári, C. (2006). *Bandit based Monte-Carlo planning*. ECML.
4. Sutton, R. S., & Barto, A. G. (2018). *Reinforcement Learning: An Introduction*, 2nd ed. MIT Press.
5. Wilkinson, M. D., et al. (2016). *The FAIR Guiding Principles for scientific data management and stewardship*. Scientific Data 3, 160018. https://doi.org/10.1038/sdata.2016.18

**Citation note:** Cite the repository's versioned Zenodo DOI after publication; no DOI is presumed for this draft.

**License note:** Repository licensing and third-party dependencies should be verified before release.
