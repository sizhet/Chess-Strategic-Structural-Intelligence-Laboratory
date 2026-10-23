# START HERE — Chess as a Strategic Structural Intelligence Laboratory

**Chess-SSIL · v1.0.0**  
**Authors:** Sizhe Tan & GPT-Obot  
**Status:** Research framework and provisional experimental contracts; not a validated implementation.

## 1. Purpose

Chess-SSIL is a lightweight, independently citable research bridge from **Strategic Structural Intelligence and Competitive UIRTU-Relay (SSICR)** to experiments that can be reproduced, challenged, extended, and collectively improved.

Chess and smaller deterministic games provide controlled environments in which researchers can separate **game state**, **strategic localization**, **per-node intelligence**, **strategy generation**, **competitive relay**, and **structural evolution**. The ambition is not to claim that chess proves artificial superintelligence. It is to make specific structural-intelligence claims experimentally tractable.

> **Guiding principle:** Build a verified strategy-generable core, preserve residual problems as evidence, and expand the core only through independently tested structural improvements.

## 2. The Research Lineage

| Foundation | Contribution to this laboratory |
|---|---|
| **Structural Intelligence Framework (SIF)** | Functional architecture, localization, per-node intelligence, control, contracts, and growth. |
| **UIERU / UIRTU-Relay** | Portable intelligence units and composable execution/relay structures. |
| **SSICR** | Strategy generation, competitive selection, and structural evolution as research objects. |
| **Chess-SSIL** | Controlled games, provisional interfaces, falsifiable hypotheses, and collective-learning experiments. |

Chess-SSIL is a companion experimental program, not a replacement for the foundational SSICR repository.

## 3. Choose Your Shortest Reading Path

### New to the subject — 20-minute orientation

1. Read [CSSIL-001 — Chess as a Canonical SSICR Laboratory](docs/CSSIL-001-Chess-as-a-Canonical-SSICR-Laboratory.md).
2. Review [Fig-001 — Grand Map](figures/Fig-001-Chess-SSIL-Grand-Map.png) and [Fig-002 — Localization and Per-Node Intelligence](figures/Fig-002-Chess-Localization-and-Per-Node-Intelligence.png).
3. Scan [OPEN-QUESTIONS](research/OPEN-QUESTIONS.md) for a tractable question.

### Interested in autonomous strategy evolution

1. Read [CSSIL-002 — Localization, Per-Node, and Strategy Generation](docs/CSSIL-002-Localization-Per-Node-and-Strategy-Generation.md).
2. Read [CSSIL-003 — Competitive Relay and Autonomous Strategy Evolution](docs/CSSIL-003-Competitive-Relay-and-Autonomous-Strategy-Evolution.md).
3. Read [CSSIL-004 — Residual Intelligence and Structural Growth](docs/CSSIL-004-Residual-Intelligence-and-Structural-Growth.md).
4. Use [TESTABLE-HYPOTHESES](research/TESTABLE-HYPOTHESES.md) and [VALIDATION-ROADMAP](research/VALIDATION-ROADMAP.md).

### Interested in collective learning or wider task coverage

1. Read [CSSIL-005 — Collective Learning and Research Relay](docs/CSSIL-005-Collective-Learning-and-Research-Relay.md).
2. Read [CSSIL-006 — Strategy-Generability Partition and Residual-to-Generable Evolution](docs/CSSIL-006-Strategy-Generability%20Partition%20and%20Residual-to-Generable%20Evolution.md).
3. Start with the [provisional contracts](specs/) and a small reproducible contribution.

## 4. Six Hints for Collective-Learning Contributors

**H1 — Start small and verify first.** Use tic-tac-toe, Nim, or Connect Four before tackling full chess or Go. A tiny game with known outcomes can expose conceptual and interface errors early.

**H2 — Separate state, localization, and strategy.** The authoritative game position is not itself a strategic interpretation; the interpretation is not itself an action decision. Preserve these boundaries in experiments.

**H3 — Compare against strong baselines.** Use suitable minimax/alpha-beta, MCTS, fixed-architecture learning, and increased-search-budget baselines. Equalize compute, training data, and evaluation conditions wherever possible.

**H4 — Preserve failures and counter-evidence.** Report unfavorable positions, failed hypotheses, evaluator disagreement, cost regressions, and transfer failures—not only wins.

**H5 — Contribute portable pieces.** A localization operator, residual detector, evaluator, benchmark, or reproducible negative result can be useful without a complete SSICR implementation.

**H6 — Improve the relay, not only the algorithm.** Record applicability conditions, interfaces, provenance, independent validation, and integration constraints so another team can actually reuse the result.

## 5. A Minimal First Experiment

**Question:** Does an explicit localization module improve decision quality or sample efficiency in a small, fully observable game?

1. **Select a game:** tic-tac-toe or a small Nim variant; freeze its rules and terminal conditions.
2. **Create two agents:** a baseline agent and an agent with a separate, versioned localization output. Keep the action-selection method otherwise as comparable as practical.
3. **Define measurements before running:** legal-move rate, win/draw/loss outcomes against fixed opponents, exploitability or optimality gap when solvable, runtime, and compute budget.
4. **Run controlled evaluations:** multiple seeds if learning is stochastic, paired opponents, held-out positions, and a complete move/event log.
5. **Check alternative explanations:** feature engineering, extra compute, privileged information, or training leakage may explain gains without demonstrating a reusable structural mechanism.
6. **Publish the evidence:** include code or pseudocode, game/rules version, configuration, baseline, metrics, failures, and a concise applicability statement.

A negative result is a valid contribution if the experiment is well specified and reproducible.

## 6. Provisional Research Contracts

These are proposals for interoperability, **not adopted industry standards**:

| Contract | Scope |
|---|---|
| [SPEC-001](specs/SPEC-001-Game-State-Localization-and-UIRTU-Contract.md) | Authoritative state, strategic localization, and UIRTU decision boundaries. |
| [SPEC-002](specs/SPEC-002-Strategy-Evaluation-and-Competitive-Relay.md) | Strategy evaluation, competition events, execution/evidence/evolution streams. |
| [SPEC-003](specs/SPEC-003-Structural-Growth-and-Evidence-Record.md) | Structural change proposals, provenance, acceptance criteria, and rollback. |

Use the smallest subset necessary for your experiment. Describe deviations explicitly.

## 7. Strategy-Generability Partition: A Research Heuristic

Rather than assuming all tasks are equally amenable to autonomy, assess whether a task has sufficiently clear **rules, observable state, permissible actions, evaluation, feedback, resource bounds, and governance constraints**.

- **G1 — Searchable:** candidate strategies can be generated and compared under a defined evaluator.
- **G2 — Learnable:** feedback can improve strategies with measurable, independently verified benefits.
- **G3 — Structurally evolvable:** changes to localization, evaluation, modules, or strategy generation can themselves be proposed and fairly tested.
- **Residual frontier:** missing or unreliable conditions require evidence gathering, decomposition, better evaluators, or human review.

**Residual-to-Generable Conversion (RGC)** is a hypothesis about moving a well-defined subset of residual tasks into a verified generable domain. It is not a claim that all real-world problems can eventually be solved automatically. Generating a strategy does not confer authority to execute it.

## 8. What Would Count as Progress?

Distinguish the following evidence levels:

- **Functional demonstration:** a game can be replayed and the proposed interfaces can exchange valid data.
- **Controlled performance gain:** a method beats a credible baseline under comparable conditions.
- **Validated structural gain:** a traceable architecture/module change adds benefit beyond parameter updates, extra data, or increased search.
- **Independent transfer:** another implementation reproduces or reuses the result with its limitations preserved.

See [VALIDATION-ROADMAP](research/VALIDATION-ROADMAP.md) for staged gates and [TESTABLE-HYPOTHESES](research/TESTABLE-HYPOTHESES.md) for falsifiable claims.

## 9. Contribution Checklist

A useful research contribution should state:

- **Claim and scope:** what is being tested, in which game/task and conditions?
- **Artifact and interface:** what is new, and how can another researcher call or inspect it?
- **Baselines and budget:** what alternatives were tested, and with what resources?
- **Evidence and counter-evidence:** what succeeded, failed, or remains uncertain?
- **Reproduction instructions:** rules version, seeds, dependencies, data, and evaluation protocol.
- **Provenance and governance:** authorship, version, license, applicable permissions, and safe deployment limits.

Contributors should not need to adopt every SI hypothesis to test a single one. Refutations and partial interoperability improvements are welcome research outcomes.

## 10. Boundaries and Next Steps

AlphaGo/AlphaZero-style self-play demonstrates powerful autonomous **strategy learning** in bounded games; it does **not** establish autonomous evolution of arbitrary software architectures or general ASI. Chess-SSIL proposes experiments to test such stronger structural claims separately.

Start with one question, one baseline, one measurable result, and one portable evidence record. Then invite independent replication.

For the complete repository map, see [CONTENTS.md](CONTENTS.md). For terminology, see [GLOSSARY.md](GLOSSARY.md).

---

**Chess-SSIL v1.0.0 · Sizhe Tan & GPT-Obot**  
*From a chess game to a collective laboratory for autonomous structural intelligence evolution.*
