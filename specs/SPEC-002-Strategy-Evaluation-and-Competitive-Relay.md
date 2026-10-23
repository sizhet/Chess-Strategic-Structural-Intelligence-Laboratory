# SPEC-002 — Strategy Evaluation and Competitive Relay

**Project:** Chess as a Strategic Structural Intelligence Laboratory (Chess-SSIL)  
**Version:** 1.0.0 (provisional research specification)  
**Authors:** Sizhe Tan & GPT-Obot  
**Status:** Proposal; not an implemented or certified interoperability standard  
**Related:** CSSIL-001–005; SPEC-001; forthcoming SPEC-003

## Abstract

This specification defines a minimal, auditable interface for evaluating candidate strategies and recording competitive UIRTU-Relay episodes in deterministic, turn-based, perfect-information games. Its purpose is to support independent experiments, reproducible comparisons, counter-evidence, and collective learning. It separates **strategy proposals**, **authoritative game transitions**, **competitive observations**, and **structural learning decisions**. Chess is the motivating example, but the contract can be instantiated for Tic-Tac-Toe, Nim, Connect Four, and Go when their rule and state representations are declared.

This document does not claim that a self-play agent has achieved autonomous structural evolution. It specifies how researchers could test that claim.

## 1. Scope and boundaries

### In scope

- Strategy identity, versions, declared capabilities, and resource budgets.
- Candidate action evaluation, including optional distributions and uncertainty.
- Competitive relay event sequencing, authoritative move application, and provenance.
- Match and tournament outcome recording.
- Evidence capture, counter-evidence, reproducibility, and comparison protocols.
- Interfaces that can connect to the game-state and UIRTU contracts in SPEC-001.

### Out of scope

- A particular chess engine, neural architecture, search algorithm, or training framework.
- Guaranteed optimal play, solved Go, or claims about general intelligence.
- Autonomous modification of rules, objectives, or deployment permissions.
- Full structural-growth lifecycle semantics, reserved for SPEC-003.

**Normative language:** MUST, SHOULD, and MAY indicate requirements, recommendations, and options for implementations claiming conformance to this *provisional* specification.

## 2. Canonical concepts

| Concept | Meaning |
|---|---|
| Game state | Authoritative state under a declared rule set, as in SPEC-001 |
| Localization | A perspective-dependent interpretation of that state |
| UIRTU invocation | One bounded decision-service invocation with traceable inputs and outputs |
| Strategy | A versioned decision policy or composition of modules used to propose actions |
| Candidate action | An action proposed but not yet accepted by the rules engine |
| Competitive relay | Ordered exchange of decision, validation, transition, and feedback events |
| Evaluation | A stated procedure for estimating or measuring performance |
| Counter-evidence | An observation that challenges a strategy's prediction or claimed advantage |
| Structural change | A modification to a module, interface, selection policy, or composition graph |

A **move is not itself a UIRTU**. A move is an action produced by an invocation of one or more UIRTU-capable components. A match is a sequence of such invocations and validated transitions.

## 3. Reference flow

```text
Authoritative Game State (SPEC-001)
        |
        v
Localization / Perspectives
        |
        v
Strategy Invocation -----> Candidate Action + Evaluation
        |                             |
        |                             v
        +----------------------> Rules Validator
                                      |
                              accepted / rejected
                                      |
                                      v
                              State Transition
                                      |
                                      v
                         Competitive Relay Event Log
                                      |
                        +-------------+-------------+
                        |                           |
                        v                           v
                 Match Evaluation             Counter-Evidence
                        |                           |
                        +-------------+-------------+
                                      |
                                      v
                           Research / Growth Review
                             (SPEC-003 boundary)
```

The authoritative rules engine MUST validate every proposed action; a policy's predicted transition MUST NOT replace authoritative state.

## 4. Required identifiers and versioning

Every experiment MUST declare:

- `experiment_id`, `protocol_version`, `game_id`, and `ruleset_id` (including ruleset version).
- `match_id`, `player_id`, `strategy_id`, and immutable `strategy_version` for each participant.
- `state_id` or deterministic state digest before and after each accepted transition.
- A monotonically increasing `event_seq` within a match.
- A stable `invocation_id` linking decision proposals to their outcomes.
- The implementation version of the authoritative rules engine.

Identifiers MUST be unique within their stated scope. Version labels MUST NOT be silently reused for changed strategy artifacts. A digest algorithm and canonical serialization method SHOULD be declared; a digest without canonicalization is not a portable identity guarantee.

## 5. Strategy manifest contract

A strategy manifest MUST include `strategy_id`, `strategy_version`, `supported_rulesets`, `decision_interface_version`, and `artifact_reference`. It SHOULD include the following:

- `localization_dependencies`: perspective identifiers and versions.
- `modules`: component identifiers and optional composition graph.
- `learning_mode`: `frozen`, `between_matches`, or `within_match`.
- `search_method` and resource requirements, when applicable.
- `randomness`: algorithm, seed policy, and nondeterminism disclosure.
- `provenance`: authorship, training-data summary, and dependency references.

A manifest declares capabilities; it does not establish empirical superiority.

## 6. Decision and evaluation interface

### 6.1 Request

A `StrategyEvaluationRequest` MUST contain:

| Field | Type | Requirement |
|---|---|---|
| `invocation_id` | string | Required, unique |
| `match_id` | string | Required |
| `state_id` | string | Required |
| `player_id` | string | Required |
| `strategy_id` / `strategy_version` | string | Required |
| `legal_actions` or `legal_action_set_ref` | array/string | Required |
| `resource_budget` | object | Required; explicit limits |
| `localization_refs` | array | Optional |
| `history_ref` | string | Optional |
| `seed` | integer/string | Optional; required if deterministic replay relies on it |

### 6.2 Response

A `StrategyEvaluationResponse` MUST contain `invocation_id`, `state_id`, `proposed_action`, `strategy_version`, and `status`. It SHOULD include `candidate_actions`, `value_estimate`, `uncertainty`, `evaluation_perspective`, `compute_used`, and `evidence_refs`.

`status` MUST be one of `proposed`, `abstained`, or `failed`. An `abstained` or `failed` response MUST NOT be interpreted as a legal move. Any value estimate MUST state its scale and perspective (e.g., expected outcome for player-to-move, in `[-1,1]`). Candidate probabilities, if supplied, MUST be finite, nonnegative, and sum to approximately one under a declared numerical tolerance; they MUST be labeled as policy weights rather than calibrated win probabilities unless calibration has been evaluated.

### 6.3 Illustrative JSON

```json
{
  "protocol_version": "1.0.0",
  "invocation_id": "inv-0042",
  "match_id": "match-007",
  "state_id": "state-042",
  "player_id": "white",
  "strategy_id": "example-policy",
  "strategy_version": "0.3.1",
  "status": "proposed",
  "proposed_action": "e2e4",
  "candidate_actions": [
    {"action": "e2e4", "policy_weight": 0.65},
    {"action": "d2d4", "policy_weight": 0.35}
  ],
  "value_estimate": {
    "value": 0.12,
    "scale": "expected_outcome_-1_to_1",
    "perspective": "white"
  },
  "uncertainty": {"kind": "not_estimated"},
  "compute_used": {"nodes": 1000, "wall_ms": 38},
  "evidence_refs": ["evidence-017"]
}
```

The example is synthetic and is not an observed chess-engine result. Its two listed candidate actions are an illustrative normalized subset, not necessarily the full legal-action distribution.

## 7. Competitive relay event contract

Every event MUST include `event_seq`, `event_type`, `match_id`, `actor`, `state_id_before`, and `timestamp_or_logical_tick`. Supported baseline event types:

1. `decision_requested`
2. `decision_proposed`
3. `action_validated` or `action_rejected`
4. `state_transitioned` (accepted moves only)
5. `feedback_recorded`
6. `match_terminated`
7. `evaluation_completed`

Events SHOULD include `invocation_id`, `strategy_version`, `payload_ref`, and a causal parent reference. `state_transitioned` MUST record `state_id_after` and the authoritative action. Rejected actions MUST NOT advance the authoritative game state. Event logs SHOULD be append-only; corrections SHOULD be new events rather than edits to history.

### Event invariants

- Event sequence numbers MUST be strictly increasing within each match.
- A transition MUST refer to a previously validated action.
- A match MUST NOT accept new transitions after its terminal event.
- Each accepted transition MUST reproduce from its preceding authoritative state and declared ruleset.
- An actor MUST be authorized to move for the recorded side.
- Timeouts, disconnections, resignations, and adjudications MUST be distinguishable from board-derived terminal outcomes.

## 8. Match outcome and evaluation contract

`MatchResult` MUST contain `match_id`, both strategy versions, `ruleset_id`, `outcome`, `termination_reason`, and a reference to the final event. `outcome` MUST distinguish `win`, `loss`, `draw`, and `invalid_or_incomplete` from a declared reference player's perspective. A game outcome MUST NOT be conflated with an evaluation score or training reward.

For cross-strategy comparison, a protocol SHOULD specify:

- Opponent pool, versions, and selection procedure.
- Color/first-player balancing and paired openings or starting positions.
- Fixed resource ceilings (nodes, time, memory, accelerator class as appropriate).
- Seeds, randomization method, and match count.
- Training/evaluation separation and checkpoint freeze policy.
- Primary metric and uncertainty estimate (e.g., win/draw/loss rates with confidence intervals).
- Secondary metrics: computation, latency, illegal proposals, abstentions, robustness, and replay failures.

**Causal attribution:** An improvement in match outcomes alone does not prove structural growth. Changes to compute, data, tuning, or opponent mix are alternative explanations. Structural-evolution claims require ablations and matched-budget controls.

## 9. Counter-evidence and residual interface

A `CounterEvidenceRecord` SHOULD include:

| Field | Description |
|---|---|
| `evidence_id` | Stable identifier |
| `match_id`, `event_seq`, `state_id` | Exact replay location |
| `strategy_id`, `strategy_version` | Evaluated strategy |
| `claim_or_prediction` | What was expected, including perspective and scale |
| `observation` | What was observed |
| `discrepancy_metric` | Defined measurement, not merely an adjective |
| `residual_class` | Coverage, prediction, decision, search, relay/integration, or transfer |
| `suspected_cause` | Hypothesis, explicitly marked unverified |
| `reproduction` | Seed, artifact refs, and replay instructions |
| `disposition` | Open, investigated, confirmed, rejected, or unresolved |

Counter-evidence MUST remain accessible when a candidate improvement is rejected. Reports SHOULD distinguish surprising but valid play from rule violations, evaluator defects, and distribution shifts.

## 10. Learning and structural-change boundary

Competitive relay can generate three distinguishable streams:

- **Execution:** actions and authoritative transitions.
- **Evidence:** predictions, outcomes, anomalies, and counter-evidence.
- **Evolution:** proposals to update parameters, modules, or strategy-generating structures.

The first two can be logged without any autonomous learning. An evolution stream exists only when a declared update process consumes evidence and produces versioned candidates. The **accept/reject/rollback** semantics for structural changes belong to SPEC-003. A candidate update MUST NOT overwrite the strategy artifact used to produce the evaluation data without explicit versioning and protocol disclosure.

## 11. Reference evaluation designs

### Experiment A — Minimal relay correctness

Use Tic-Tac-Toe with an authoritative solver. Replay complete matches, verify turn order, legal moves, terminal outcomes, and event causality. Success: zero unexplained mismatches in the declared test corpus.

### Experiment B — Strategy improvement under self-play

Use a simple game with frozen baseline policies. Compare an updating policy with its initial checkpoint under balanced evaluation. Record uncertainty and compute. Success: a predeclared performance improvement replicated across seeds; no structural-evolution claim is implied.

### Experiment C — Structural versus nonstructural improvement

Use Connect Four or a constrained chess setting. Compare: (1) frozen structure, (2) parameter-only updates, (3) more search at matched training, and (4) candidate structural changes. Success: reproducible incremental advantage under controlled resource accounting and ablation.

### Experiment D — Portable research relay

Have two independent implementations consume the same game-state and event contracts. Exchange a strategy or evaluation module with provenance and rerun the benchmark. Success: compatible replay and comparable results without private adapters or undocumented manual interpretation.

## 12. Conformance checklist

An implementation claiming **SPEC-002 Core Conformance** MUST demonstrate:

- [ ] Versioned ruleset, strategy, and engine identifiers.
- [ ] Request/response correlation by invocation ID.
- [ ] Legality checked by an authoritative rules engine.
- [ ] Accepted and rejected actions logged distinctly.
- [ ] Ordered, replayable event history with causal links.
- [ ] Consistent state IDs across transitions.
- [ ] Explicit termination reason and outcome perspective.
- [ ] Declared evaluation protocol and resource budgets.
- [ ] Preservation of strategy versions during evaluation.
- [ ] Reproducibility artifacts or a documented nondeterminism limitation.

**Extended Research Conformance** SHOULD additionally include candidate distributions, counter-evidence records, matched-budget comparisons, and independent cross-implementation replay.

Conformance means the interface and records satisfy these conditions; it does not certify playing strength, fairness, safety, or scientific validity of conclusions.

## 13. Collective learning contribution package

Independent researchers SHOULD be able to contribute a bounded artifact without adopting the entire SI framework. A recommended package contains:

```text
contribution/
  manifest.json           # artifact, authors, license, versions, dependencies
  strategy-or-module/     # source, binary, or reproducible reference
  protocol.json           # ruleset, opponents, seeds, budgets, metrics
  event-log.jsonl         # replayable competitive relay events
  results.json            # outcomes, uncertainty, limitations
  counter-evidence.jsonl  # failures and contrary cases
  README.md               # setup, reproduction, and scope
```

A public result SHOULD say whether its contribution is a new discovery, a localization/relay improvement, a composition improvement, or a validated structural change. Unsupported superiority or autonomy claims SHOULD be labeled hypotheses.

## 14. Open questions

1. What is the smallest event schema that remains sufficient for independent causal replay?
2. Which localization representations transfer across different games without obscuring ruleset-specific meaning?
3. How should policy scores, calibrated probabilities, and uncertainty be compared without misleading normalization?
4. How can structural changes be evaluated fairly when they alter the cost and search space of strategy generation?
5. What constitutes evidence that a strategy generator, rather than merely a policy, has improved?
6. How should independently contributed counter-evidence be merged while preserving provenance and disagreement?
7. Which relay bottlenecks most strongly limit cross-team reproducibility and reuse?

## 15. Relationship to the Chess-SSIL research program

- **CSSIL-001:** canonical chess-to-SSICR mapping.
- **CSSIL-002:** localization, Per-Node intelligence, and strategy generation.
- **CSSIL-003:** competitive relay and autonomous strategy evolution.
- **CSSIL-004:** residual intelligence and structural growth.
- **CSSIL-005:** collective learning and research relay.
- **SPEC-001:** authoritative state, localization, and UIRTU invocation contracts.
- **SPEC-003 (planned):** structural candidate lifecycle, evidence, selection, and rollback.

## 16. Closing principle

> **Competitive Relay is a credible substrate for autonomous strategy learning only when action execution, evidence generation, and learning updates remain separately observable and independently testable.**

The practical objective is not to build another monolithic chess engine. It is to make strategy evaluation and competitive evidence portable enough that independent experiments can accumulate into collective structural learning.

---

**Citation note:** This is a proposed research specification by Sizhe Tan & GPT-Obot. Cite the repository's published DOI once assigned; do not substitute a placeholder DOI for a registered identifier.
