# SPEC-003 — Structural Growth and Evidence Record

**Repository:** Chess as a Strategic Structural Intelligence Laboratory (Chess-SSIL)  
**Version:** 1.0.0 — Provisional Research Contract  
**Authors:** Sizhe Tan & GPT-Obot  
**Status:** Research proposal; not a standardized or validated implementation  
**Companion documents:** CSSIL-003, CSSIL-004, CSSIL-005, SPEC-001, SPEC-002

## Abstract

This specification defines a minimal, auditable contract for proposing, testing, accepting, rejecting, and rolling back structural changes in a competitive structural-intelligence system. Chess and smaller deterministic games serve as experimental environments. The central objective is to distinguish **structural intelligence growth** from ordinary parameter updates, deeper search, and selection effects, while making evidence portable across independent research implementations.

A candidate structural change is **not** an improvement merely because it wins a few games. It becomes a supported improvement only when its provenance, test protocol, resource costs, failure cases, and comparative outcomes survive predeclared evaluation. This document defines manifests, lifecycle states, evidence records, acceptance gates, rollback triggers, and conformance checks for that process.

## 1. Scope and normative vocabulary

This is a **provisional research contract**, not a claim of achieved autonomous structural self-improvement. In this document, **MUST**, **SHOULD**, and **MAY** describe requirements for implementations claiming conformance to this experimental contract.

In scope:

- Versioned changes to localization perspectives, scoring operators, decision policies, UIRTU modules, relay routing, residual triggers, or strategy generators.
- Traceable links from residual observations and hypotheses to candidate changes.
- Competitive and noncompetitive evaluation with controlled compute budgets.
- Independent reproduction, counter-evidence, deployment gates, and rollback.
- Portable records for collective learning.

Out of scope:

- A prescribed chess engine, neural architecture, or programming language.
- Proof of open-world autonomous intelligence or ASI.
- Automatic approval of production deployment from sandbox results.
- A universal scalar measure of intelligence.

## 2. Architectural position

```text
Authoritative Game State (SPEC-001)
          |
          v
Localization / Per-Node / Strategy Generator
          |
          v
Competitive Relay + Evaluation Events (SPEC-002)
          |
          v
Residual / Counter-Evidence Detection
          |
          v
Structural Change Proposal (this SPEC)
          |
          v
Sandbox Validation --> Independent Reproduction
          |                    |
          +---------+----------+
                    v
            Governance Decision
             /      |       \
          Accept  Reject   Revise
             |
       Staged Deployment
             |
       Monitor / Rollback
             |
      Versioned Evidence Registry
```

A game transition remains authoritative only through the rules engine. Structural candidates may propose actions or analyses but MUST NOT silently alter game rules or rewrite historical observations.

## 3. What counts as structural growth?

A **structural change** modifies an explicit component, connection, control policy, representation, or composition rule. Examples include adding a king-safety localization perspective; splitting a scoring node into opening and endgame evaluators; inserting a residual-triggered search module; or replacing a static strategy selector with a context-sensitive selector.

By contrast, changing weights inside an unchanged model is a **parameter update**. Increasing Monte Carlo simulations is a **compute allocation change**. Retraining a model on more games is a **data/training change**. These may improve performance but MUST NOT be reported as structural growth without an independently identifiable structural modification.

A change can be both structural and parametric. In that case, the experiment MUST isolate the incremental structural effect using appropriate controls.

### 3.1 Structural change taxonomy

| Code | Target | Illustrative change |
|---|---|---|
| `LOC` | Localization | Add or split a strategic perspective |
| `SCORE` | Scoring | Introduce a new evaluator or folding operator |
| `UIRTU` | Per-node intelligence | Add a reusable tactical decision unit |
| `RELAY` | Composition and routing | Change when or how units are invoked |
| `RESIDUAL` | Detection and handling | Add a new blind-spot trigger |
| `GENERATOR` | Strategy generation | Change candidate generation or module selection |
| `GOVERNANCE` | Evaluator/control plane | Introduce a verification or safety gate |

## 4. Identifiers and versioning

Every proposal MUST include:

- `proposal_id`: stable unique identifier.
- `parent_system_version`: immutable reference to the baseline system.
- `candidate_system_version`: immutable reference to the proposed system.
- `component_ids`: affected components and interface versions.
- `change_type`: one or more taxonomy codes from Section 3.
- `artifact_digest`: cryptographic digest or equivalent immutable artifact reference.
- `created_at`: UTC timestamp.
- `provenance`: human-authored, model-generated, self-play-derived, or mixed; include relevant source references.

Implementations SHOULD preserve a directed acyclic history of system versions and changes. A candidate MUST be reproducible from its declared parent plus declared modifications.

## 5. Structural Growth Proposal contract

The proposal MUST identify a concrete failure, limitation, or opportunity and a falsifiable reason the proposed modification should help. It MUST state expected benefits, likely regressions, costs, and intended scope.

```json
{
  "schema_version": "cssil.spec003.v1",
  "record_type": "structural_proposal",
  "proposal_id": "sgp-0042",
  "created_at": "2026-10-23T18:00:00Z",
  "parent_system_version": "engine-a@1.3.0",
  "candidate_system_version": "engine-a@1.3.1-candidate.1",
  "artifact_digest": "sha256:<replace-with-real-digest>",
  "change_type": ["LOC", "RELAY"],
  "component_ids": ["king_safety@2", "relay_selector@1"],
  "provenance": {
    "origin": "self_play_analysis",
    "source_event_ids": ["relay-event-0198"],
    "source_evidence_ids": ["ev-0198"]
  },
  "hypothesis": "A dedicated king-safety perspective reduces tactical oversights in exposed-king positions at equal compute.",
  "mechanism": "Invoke the new perspective when a preregistered exposure feature exceeds threshold 0.7.",
  "target_population": "Held-out chess positions with exposed kings",
  "expected_benefits": ["lower blunder rate"],
  "possible_regressions": ["higher latency", "false triggers"],
  "resource_budget": {"max_nodes_per_move": 10000, "max_wall_ms_per_move": 1000},
  "evaluation_protocol_id": "eval-king-safety-v1",
  "status": "proposed"
}
```

All identifiers, values, and results in examples are illustrative; they are not measured outcomes. An actual digest MUST contain a verifiable value.

## 6. Lifecycle and transition rules

Allowed lifecycle states:

`proposed -> registered -> sandbox_testing -> evaluated -> independently_reproduced -> accepted -> staged -> deployed`

Alternative terminal or intermediate states:

`rejected`, `revision_required`, `suspended`, `rolled_back`, `superseded`.

Rules:

1. A proposal MUST be registered before formal testing; the protocol and evaluation criteria MUST be frozen or versioned before test outcomes are inspected.
2. `evaluated` requires a completed evidence bundle, including negative outcomes and resource usage.
3. `independently_reproduced` requires execution by a distinct implementation, operator, or reproducible environment with clearly identified independence limitations.
4. `accepted` requires a recorded decision, justification, evaluator identity, and acceptance-gate results.
5. `deployed` requires a deployment authorization separate from experimental acceptance.
6. Any state transition MUST append an immutable audit event; historical states MUST NOT be silently overwritten.
7. `rolled_back` MUST identify the previously accepted version restored and the trigger that caused rollback.

A research project MAY omit deployment altogether and stop at independent reproduction.

## 7. Evaluation Protocol contract

Each protocol MUST declare, before final testing:

- Game and ruleset, state/position sampling method, and legality checker.
- Primary metric and direction of improvement (e.g., paired win-rate difference, blunder rate).
- Baseline versions and ablations: unchanged architecture, compute-matched search, parameter-only update, and candidate structure where feasible.
- Dataset partitions: development, validation, and sealed held-out evaluation.
- Random seeds, color/first-player balance, opponent pool, opening distribution, and duplicate-position policy.
- Resource constraints: training compute, inference compute, memory, latency, and external data.
- Statistical plan: sample size rationale, confidence intervals, paired design, and multiple-comparison correction where needed.
- Predeclared acceptance thresholds and failure/rollback thresholds.
- Rules for invalid games, crashes, timeouts, and missing records.

A self-play win rate against an earlier version alone is insufficient to establish broad improvement. Evaluate against multiple opponents and held-out conditions to reduce overfitting and cyclic dominance.

## 8. Evidence Record contract

Evidence MUST be append-only and attributable to a proposal, version, protocol, and evaluation run. Each record MUST include:

| Field | Meaning |
|---|---|
| `evidence_id` | Immutable record identifier |
| `proposal_id` | Structural change being evaluated |
| `protocol_id` | Frozen evaluation design |
| `run_id` | Exact execution instance |
| `baseline_version`, `candidate_version` | Compared artifacts |
| `environment` | Ruleset, software versions, hardware, seeds |
| `dataset_ref` | Positions, games, and split identifier |
| `metrics` | Results, units, denominators, uncertainty |
| `resource_usage` | Training/inference compute and latency |
| `counter_evidence_refs` | Regressions and failure cases |
| `artifact_refs` | Replay logs, models, code, checksums |
| `interpretation` | What is and is not supported |

```json
{
  "schema_version": "cssil.spec003.v1",
  "record_type": "evaluation_evidence",
  "evidence_id": "ev-0204",
  "proposal_id": "sgp-0042",
  "protocol_id": "eval-king-safety-v1",
  "run_id": "run-0204",
  "baseline_version": "engine-a@1.3.0",
  "candidate_version": "engine-a@1.3.1-candidate.1",
  "environment": {"game": "chess", "ruleset": "standard", "seed": 441},
  "dataset_ref": "heldout-exposed-king-v1",
  "metrics": {
    "blunder_rate_baseline": 0.12,
    "blunder_rate_candidate": 0.09,
    "positions_evaluated": 1000,
    "confidence_interval_difference": null
  },
  "resource_usage": {"mean_wall_ms_baseline": 83, "mean_wall_ms_candidate": 91},
  "counter_evidence_refs": ["ce-007"],
  "artifact_refs": ["replay-run-0204.jsonl"],
  "interpretation": "Illustrative numbers only; statistical support is not established."
}
```

A missing uncertainty estimate MUST be explicitly marked as missing, not interpreted as zero uncertainty. Experimental reports MUST distinguish raw observations from interpretation.

## 9. Counter-Evidence Record contract

Negative evidence MUST remain discoverable even after a proposal is rejected or rolled back. A counter-evidence record SHOULD contain:

- `counter_evidence_id`, `proposal_id`, `run_id`, `observed_at`.
- Exact position or game trace, ruleset, and relevant history.
- Expected versus observed behavior and failure classification.
- Reproduction procedure, frequency, severity, and scope.
- Whether the failure reflects legality, localization, evaluation, search, relay, generalization, or measurement.
- Resolution status and linked repair proposals.

Counter-evidence SHOULD be classified as **confirmed**, **unconfirmed**, or **disputed**. An unexplained loss is evidence of a performance failure, but not automatically evidence of the proposed root cause.

## 10. Acceptance and rollback gates

A candidate MAY be accepted only when all mandatory gates pass:

1. **Integrity:** reproducible artifact versions, valid game transitions, complete audit trail.
2. **Comparison:** predeclared baseline and at least one meaningful ablation.
3. **Performance:** primary metric meets the protocol's threshold with uncertainty reported.
4. **Resources:** gains are not explained solely by unreported extra compute or data.
5. **Robustness:** no unacceptable regressions on designated stress or held-out sets.
6. **Evidence:** counter-evidence and known limitations are attached.
7. **Reproducibility:** independent or explicitly qualified reproduction status recorded.
8. **Governance:** evaluator and deployment authorization boundaries preserved.

Rollback SHOULD be triggered by material regression, legality violation, unexpected resource escalation, invalidated evaluation, evidence corruption, or violation of deployment policy. The rollback event MUST preserve the failed candidate and its evidence for future analysis.

## 11. Structural Growth vs. performance inflation

A claim of structural improvement SHOULD report a matched comparison such as:

`Delta_structural = Metric(candidate structure, matched budget) - Metric(baseline structure, matched budget)`

This is a comparison convention, not a causal proof by itself. Stronger attribution uses factorial or ablation designs varying structure, parameter training, search budget, and data exposure separately. Also report variance across seeds, opponent pools, and starting positions.

Metrics MAY include win/draw/loss rate, Elo estimates with appropriate uncertainty, exploitability for tractable games, regret, calibration, residual coverage, latency, memory, and portability/reproduction cost. No single metric should substitute for the entire evidence bundle.

## 12. Cross-SPEC compatibility

- **SPEC-001** supplies authoritative game state, localization outputs, and UIRTU decision interfaces. This specification references its state and component versions without overriding them.
- **SPEC-002** supplies strategy-evaluation and competitive-relay events. This specification consumes those events as evidence and links every structural proposal to their IDs.
- **SPEC-003** governs change proposals and evaluation evidence, not the actual legality of moves or the operational dispatch of actions.

Implementations SHOULD reject incompatible interface versions explicitly and preserve adapters and migration records when interfaces evolve.

## 13. Collective Learning Contribution Package

An independent contribution SHOULD be publishable as a compact package:

```text
contribution-id/
├── manifest.json
├── proposal.json
├── protocol.json
├── evidence.jsonl
├── counter-evidence.jsonl
├── artifacts/               # Code, models, traces, or stable references
├── reproduction.md
└── limitations.md
```

The manifest SHOULD identify authorship, license, provenance, schema versions, dependencies, artifact digests, and an appropriate citation. Researchers MAY publish evidence-only contributions, including failed replications, without contributing an executable module.

A contribution's value is not limited to positive results. A reproducible failure, an interface incompatibility, or a reliable residual dataset may prevent many downstream researchers from repeating the same mistake.

## 14. Conformance tests

An implementation claiming SPEC-003 conformance SHOULD pass at least the following checks:

| Test | Expected result |
|---|---|
| CT-01 | Reject proposal missing parent version or artifact reference |
| CT-02 | Reject undeclared change type or unsupported schema version |
| CT-03 | Preserve original proposal after amendments; append revisions |
| CT-04 | Reject acceptance without linked protocol and evidence |
| CT-05 | Detect candidate/baseline version mismatch across records |
| CT-06 | Record compute/data mismatch rather than silently treating results as comparable |
| CT-07 | Retain failed and counter-evidence records after rejection |
| CT-08 | Reject invalid lifecycle transitions |
| CT-09 | Restore prior authorized version on rollback and log the reason |
| CT-10 | Reconstruct proposal-to-evaluation-to-decision provenance graph |
| CT-11 | Reproduce a recorded game trace against the authoritative ruleset |
| CT-12 | Export a portable contribution package with versioned schema |

Passing these checks establishes interface/process conformance, **not** evidence of intelligent growth.

## 15. Minimal validation roadmap

**Phase A — Tiny deterministic game:** Use Tic-Tac-Toe or Nim, with exact optimal-play ground truth. Demonstrate complete event linkage, deliberate structural change, negative evidence, and rollback.

**Phase B — Connect Four:** Introduce search-budget matching, residual-triggered modules, held-out positions, and opponent diversity. Compare a fixed architecture against an adaptive one.

**Phase C — Chess:** Test multi-perspective localization, tactical blind-spot detection, strategy-generator changes, and robustness under opening and opponent shifts.

**Phase D — Collective replication:** Ask an independent group to import a contribution package, reproduce one positive and one negative result, and document adaptation effort and interface failures.

Each phase SHOULD publish a reproducibility report even if no structural gain is demonstrated.

## 16. Research hypotheses

- **H-SG-01:** Residual-triggered structural proposals reduce targeted errors more efficiently than compute-matched deeper search in at least some game distributions.
- **H-SG-02:** Explicit counter-evidence retention reduces recurrence of previously identified failure classes.
- **H-SG-03:** Versioned structural change records improve causal attribution compared with outcome-only logs.
- **H-SG-04:** Portable contribution packages reduce independent reproduction and integration cost.
- **H-SG-05:** Competitive evaluation across diverse opponents reduces false acceptance caused by self-play overfitting.

These are hypotheses, not established findings. Negative results and boundary conditions are first-class outputs.

## 17. Open questions

1. What is the smallest operational definition of a new structure that remains stable across implementations?
2. How can a system detect residuals without rewarding its own evaluator's blind spots?
3. When should a system create a new UIRTU versus refine an existing one?
4. How should incompatible improvements be combined or kept as alternative perspectives?
5. Can evaluation costs be bounded while still identifying genuine structural gains?
6. Which evidence fields are indispensable for cross-laboratory replication?
7. How should structural provenance and contributor credit propagate through compositional reuse?
8. What governance rules remain necessary when strategy search outpaces human inspection?

## 18. Research guidance

Start with the smallest game and the smallest structural mutation that can be measured. Separate execution, evaluation, and evolution logs. Report the entire experimental budget, not only win rate. Keep rejected proposals and failures accessible. Make every accepted change reversible. Publish portable evidence even when code or trained models cannot be shared.

The purpose of this specification is not to force a single architecture. It is to enable researchers to test different architectures without losing the ability to compare evidence or transfer discoveries.

## 19. Conclusion

Chess-SSIL proposes that competitive play can serve as an experimental substrate for structural strategy evolution. SPEC-003 adds the missing accountability layer: **what changed, why it changed, how it was tested, what failed, who reproduced it, and whether it should be retained**.

A structural growth claim is credible only when the change is identifiable, its benefit survives fair comparison, and its evidence remains portable and falsifiable. This is the bridge from autonomous strategy experimentation to collective structural intelligence research.

---

**Citation:** Sizhe Tan & GPT-Obot. *SPEC-003 — Structural Growth and Evidence Record*. Chess as a Strategic Structural Intelligence Laboratory, v1.0.0 (2026). DOI: pending release.

**License:** Refer to the repository-level license and metadata.
