# SPEC-001 — Game State, Localization, and UIRTU Contract

**Repository:** Chess as a Strategic Structural Intelligence Laboratory (Chess-SSIL)  
**Version:** 1.0.0 (provisional research specification)  
**Authors:** Sizhe Tan & GPT-Obot  
**Status:** Proposed; not an established interoperability standard  
**Companion:** CSSIL-001 through CSSIL-005; SPEC-002 and SPEC-003 (planned)

## Abstract

This specification defines a minimal, implementation-neutral contract linking a rule-governed game state to structural localization, per-node intelligence, and a UIRTU invocation. Its purpose is reproducible experimentation and portable research contributions—not to prescribe the internals of a chess engine. A researcher should be able to replace a localization operator or a decision unit without silently changing the game rules, information available to the agent, or evaluation protocol.

## 1. Scope and Non-goals

The contract covers: (1) immutable game-state snapshots, (2) rules and observation boundaries, (3) localization requests and structured results, (4) UIRTU decision requests and responses, (5) evidence/provenance and reproducibility, and (6) validation and failure semantics.

It does **not** specify a universal representation of strategy, a mandatory differential-tree implementation, a learning algorithm, or a proof of autonomous structural evolution. Search, training, tournaments, and structural mutation are addressed by companion research protocols.

Normative keywords **MUST**, **SHOULD**, and **MAY** apply only within this proposed contract.

## 2. Canonical Processing Boundary

```text
Game Rules + Immutable State + Agent Observation
                       |
                       v
             Localization Operator
                       |
              Localized Perspective(s)
                       |
                       v
                 UIRTU Decision
                       |
            Proposed Action + Evidence
                       |
                       v
        Independent Rules Validator
                       |
                State Transition
```

A proposed action is **not** a state transition until the authoritative game environment validates and applies it. The localization operator is a replaceable interpretation layer, not the game-state authority.

## 3. Common Envelope

Every exchanged record MUST contain:

| Field | Type | Meaning |
|---|---|---|
| `schema_version` | string | Contract revision, initially `1.0.0` |
| `record_id` | string | Unique ID for this record |
| `run_id` | string | Shared ID for an experimental run |
| `created_at` | string | ISO 8601 UTC timestamp |
| `producer` | object | Tool name and version |
| `payload_type` | string | Record kind |

A receiving component MUST reject unknown major schema versions, and SHOULD preserve unrecognized extension fields for forwarding. Timestamps are metadata, not a substitute for deterministic state ordering.

## 4. Game State Snapshot

### 4.1 Required fields

| Field | Type | Requirement |
|---|---|---|
| `game_id` | string | Ruleset identifier, e.g. `chess.standard` |
| `ruleset_version` | string | Exact ruleset version |
| `state_id` | string | Content-addressed or stable state identifier |
| `turn_index` | integer | Number of transitions already applied |
| `side_to_move` | string | Current player ID |
| `position` | object | Ruleset-specific canonical position |
| `history_ref` | string or null | Immutable reference to prior transitions |
| `legal_actions` | array | Authoritatively enumerated action IDs, if provided |
| `terminal` | object | `is_terminal`, `outcome`, `reason` |
| `observation_scope` | string | `full`, `player_view`, or defined custom scope |

For standard chess, `position.fen` MAY be used, but FEN alone is not sufficient for all adjudication or repetition questions. The history or adjudication state MUST retain information needed for the selected rule protocol. A game state MUST distinguish the actual position from what an agent is permitted to observe; chess normally uses full observation, while other games may not.

### 4.2 State invariants

- The rules engine MUST be the sole authority for legal actions, terminal status, and state transitions.
- `state_id` MUST bind the relevant canonical position, player-to-move, rule state, and adjudication context; a hash algorithm and canonicalization procedure MUST be documented.
- A component MUST NOT modify a received snapshot in place.
- Replaying the same initial state and action sequence under the same ruleset MUST produce equivalent states and outcomes.
- Terminal states MUST NOT accept further gameplay actions.

## 5. Localization Contract

### 5.1 Request

A localization request contains `state_ref`, `agent_id`, `observation`, `perspectives`, `budget`, and optional `precedent_refs`. `perspectives` names the analyses requested (e.g. material balance, king safety, mobility, threats, endgame structure). The budget declares computation/time limits and MUST be logged for fair comparisons.

### 5.2 Result

A localization result MUST include:

- `state_ref` and `localizer_id` with version;
- `perspectives`: a list of perspective-specific features or structural interpretations;
- `coverage`: declared supported/unsupported feature families;
- `uncertainty`: a typed description of unknowns or estimation limits;
- `evidence_refs`: pointers to observations, calculations, or precedent records;
- `residuals`: zero or more unresolved or contradictory observations;
- `status`: `ok`, `partial`, or `failed`.

A perspective result SHOULD declare `perspective_id`, `representation_type`, `features`, `confidence_semantics`, and `provenance`. A confidence number MUST NOT be presented as a calibrated probability unless calibration has been established. Differential trees, graph patterns, learned embeddings, and symbolic features are all allowed as typed representations.

### 5.3 Residual record

Each residual SHOULD include `residual_id`, `category`, `trigger`, `affected_perspectives`, `evidence_refs`, `severity`, and `handling_recommendation`. Suggested categories include `coverage`, `prediction`, `decision`, `search`, `relay_integration`, and `transfer`. Residual detection is not proof that a new structure is required.

## 6. UIRTU Decision Contract

A UIRTU invocation MUST specify `unit_id`, `unit_version`, `state_ref`, `localization_refs`, `objective_id`, `legal_action_scope`, `resource_budget`, and `invocation_id`. The unit MAY call a rules engine, search module, scoring operator, or other UIRTU through a documented relay interface.

The decision response MUST contain:

| Field | Type | Meaning |
|---|---|---|
| `invocation_id` | string | Correlates with request |
| `state_ref` | string | State evaluated |
| `proposed_action` | string or null | Canonical ruleset action ID |
| `status` | string | `proposed`, `abstain`, `failed`, or `timeout` |
| `candidate_actions` | array | Optional scored alternatives |
| `strategy_ref` | string or null | Strategy or generator version |
| `localization_refs` | array | Inputs actually used |
| `evidence_refs` | array | Supporting or opposing evidence |
| `budget_used` | object | Measured computational consumption |
| `limitations` | array | Uncertainty, coverage, or other caveats |

A UIRTU MUST NOT declare its own action legal merely because it has selected it. A stale `state_ref` MUST trigger rejection or explicit reevaluation. Abstention MUST be representable without inventing a move. Scores from different evaluators MUST NOT be compared without documented scale and direction conventions.

## 7. Illustrative JSON Records

The following example is schematic; IDs and timestamps are illustrative. The localizer output demonstrates interface shape, not an asserted chess evaluation.

```json
{
  "schema_version": "1.0.0",
  "record_id": "state-0001",
  "run_id": "demo-001",
  "created_at": "2026-10-23T18:00:00Z",
  "producer": {"name": "reference-game-adapter", "version": "0.1.0"},
  "payload_type": "game_state",
  "game_id": "chess.standard",
  "ruleset_version": "declared-rules-v1",
  "state_id": "demo-initial-state",
  "turn_index": 0,
  "side_to_move": "white",
  "position": {"fen": "rnbqkbnr/pppppppp/8/8/8/8/PPPPPPPP/RNBQKBNR w KQkq - 0 1"},
  "history_ref": "demo-history-0000",
  "legal_actions": ["e2e4", "d2d4"],
  "legal_actions_complete": false,
  "terminal": {"is_terminal": false, "outcome": null, "reason": null},
  "observation_scope": "full"
}
```

`legal_actions` above is an explicitly **incomplete illustration** (`legal_actions_complete: false`); a conforming authoritative adapter MUST either provide the full legal-action set or omit it and supply an authoritative validation endpoint. For actual initial-position chess there are 20 legal moves, not two.

```json
{
  "schema_version": "1.0.0",
  "record_id": "loc-0001",
  "run_id": "demo-001",
  "created_at": "2026-10-23T18:00:01Z",
  "producer": {"name": "sample-localizer", "version": "0.1.0"},
  "payload_type": "localization_result",
  "state_ref": "demo-initial-state",
  "localizer_id": "sample-localizer@0.1.0",
  "perspectives": [{
    "perspective_id": "development",
    "representation_type": "symbolic_features",
    "features": {"opening_phase": true},
    "confidence_semantics": "not_calibrated",
    "provenance": ["state-0001"]
  }],
  "coverage": {"supported": ["development"], "unsupported": ["endgame"]},
  "uncertainty": {"type": "unquantified"},
  "evidence_refs": ["state-0001"],
  "residuals": [],
  "status": "ok"
}
```

```json
{
  "schema_version": "1.0.0",
  "record_id": "decision-0001",
  "run_id": "demo-001",
  "created_at": "2026-10-23T18:00:02Z",
  "producer": {"name": "sample-uirtu", "version": "0.1.0"},
  "payload_type": "decision_response",
  "invocation_id": "invoke-0001",
  "state_ref": "demo-initial-state",
  "proposed_action": "e2e4",
  "status": "proposed",
  "candidate_actions": [],
  "strategy_ref": "sample-strategy@0.1.0",
  "localization_refs": ["loc-0001"],
  "evidence_refs": ["state-0001"],
  "budget_used": {"nodes_evaluated": 1},
  "limitations": ["illustrative choice; no claim of optimality"]
}
```

## 8. Validation and Conformance

A minimal adapter SHOULD pass the following checks:

1. **Replay:** identical initial state and action log yield identical canonical state IDs.
2. **Legality:** invalid actions are rejected by the independent rules authority.
3. **State freshness:** a decision referencing an outdated state cannot be applied silently.
4. **Perspective substitution:** replacing a localizer does not alter the game rules or action encoding.
5. **Observation discipline:** no hidden state leaks into localization or UIRTU inputs.
6. **Evidence trace:** every decision identifies the localization and strategy versions it used.
7. **Residual propagation:** a partial or failed localization can be reported without fabricating certainty.
8. **Determinism audit:** seeds, budgets, versions, and environment settings are recorded when reproducibility is claimed.
9. **Terminal behavior:** terminal positions do not generate executable game actions.
10. **Interoperability:** independently implemented producer and consumer can exchange a conforming sample record.

A passing conformance test establishes **interface compatibility only**, not playing strength, strategy novelty, structural growth, or general intelligence.

## 9. Research Comparison Protocol

At minimum, compare (A) a raw-state baseline, (B) a fixed localization + fixed decision unit, and (C) a replaceable multi-perspective localization + decision unit. Hold game rules, opponent pool, compute budgets, seeds where applicable, and evaluation schedule constant. Report win/draw/loss rates, confidence intervals, wall-clock cost, node evaluations, illegal-action rate, and residual handling frequency. Use ablations to attribute gains to localization rather than increased search or compute.

Claims about autonomous **structural** evolution require separate versioned evidence of a structural change, independent validation, and comparison with parameter-only and compute-only baselines (see planned SPEC-003).

## 10. Collective Learning Contribution Package

A portable contribution SHOULD ship:

- the exact contract version and compatible game/ruleset identifiers;
- a concise description of the localization operator or UIRTU;
- machine-readable input/output examples and conformance results;
- executable or sufficiently detailed reproduction instructions;
- baselines, budgets, random seeds, and measured outcomes;
- failure cases, counter-evidence, and scope limitations;
- license, authorship, provenance, and version references.

A negative result with reproducible evidence is a valid research contribution. Contributors are not required to implement a full SSICR system to test one module.

## 11. Open Issues

- How should state equivalence and hashing treat repetition and adjudication history across games?
- What typed representation can exchange structural localization without forcing all systems into one ontology?
- Which uncertainty metrics can be calibrated across heterogeneous scorers?
- When should a residual trigger deeper search versus creation of a new structural module?
- How can privacy, ownership, and agent-specific observation policies survive relay across implementations?
- What constitutes a portable Strategy Generator artifact rather than a parameter snapshot?

## 12. Relationship to the Chess-SSIL Program

- **CSSIL-001:** conceptual mapping of chess to SSICR.
- **CSSIL-002:** localization, per-node intelligence, and strategy generation.
- **CSSIL-003:** competitive relay and autonomous strategy evolution.
- **CSSIL-004:** residual intelligence and structural growth.
- **CSSIL-005:** collective learning and research relay.
- **SPEC-002 (planned):** competitive evaluation, opponent protocols, and relay events.
- **SPEC-003 (planned):** structural growth records, counter-evidence, and validation.

## 13. Closing Principle

> Separate the authoritative game state from its strategic interpretation, and separate a proposed UIRTU action from the validated game transition. These boundaries make structural intelligence experiments reproducible, replaceable, and collectively extensible.

---

**Citation:** Sizhe Tan & GPT-Obot. *SPEC-001 — Game State, Localization, and UIRTU Contract*. Chess-SSIL, v1.0.0, provisional research specification (2026). Repository DOI to be added after release.
