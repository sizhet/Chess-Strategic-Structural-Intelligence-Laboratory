# Figure Index

**Chess-SSIL — Chess as a Strategic Structural Intelligence Laboratory**  
*From Competitive UIRTU-Relay to Autonomous Strategy Evolution and Collective Learning*

**Version:** 1.0.0  
**Authors:** Sizhe Tan & GPT-Obot  
**Status:** Research architecture and validation proposals; not a claim of demonstrated general autonomous structural evolution.

## Purpose

This index documents the five architecture figures, their intended meanings, suggested locations in the research papers, and the distinctions each figure must preserve. Figures are conceptual research aids, not empirical results. All image references below assume that the corresponding standalone PNG files are present in [`figures/`](figures/).

## Figure Catalog

| ID | Figure | Primary subject | Suggested primary placement |
| --- | --- | --- | --- |
| Fig-001 | [Chess-SSIL Grand Map](figures/Fig-001-Chess-SSIL-Grand-Map.png) | End-to-end laboratory architecture and evidence flow | [`docs/CSSIL-001-Chess-as-a-Canonical-SSICR-Laboratory.md`](docs/CSSIL-001-Chess-as-a-Canonical-SSICR-Laboratory.md) |
| Fig-002 | [Chess Localization and Per-Node Intelligence](figures/Fig-002-Chess-Localization-and-Per-Node-Intelligence.png) | State representation, localization, per-node decisions and contracts | [`docs/CSSIL-002-Localization-Per-Node-and-Strategy-Generation.md`](docs/CSSIL-002-Localization-Per-Node-and-Strategy-Generation.md) |
| Fig-003 | [Competitive Strategy Evolution Loop](figures/Fig-003-Competitive-Strategy-Evolution-Loop.png) | Candidate strategies, competitive testing, evaluation and revision | [`docs/CSSIL-003-Competitive-Relay-and-Autonomous-Strategy-Evolution.md`](docs/CSSIL-003-Competitive-Relay-and-Autonomous-Strategy-Evolution.md) |
| Fig-004 | [Autonomous Structural Growth Ladder](figures/Fig-004-Autonomous-Structural-Growth-Ladder.png) | Search, learning, structural evolution and evidence gates | [`docs/CSSIL-004-Residual-Intelligence-and-Structural-Growth.md`](docs/CSSIL-004-Residual-Intelligence-and-Structural-Growth.md) |
| Fig-005 | [Collective Learning and Research Relay](figures/Fig-005-Collective-Learning-and-Research-Relay.png) | Portable results, independent replication, relay and compositional growth | [`docs/CSSIL-005-Collective-Learning-and-Research-Relay.md`](docs/CSSIL-005-Collective-Learning-and-Research-Relay.md) |

## Figure Details and Insertion Guidance

### Fig-001 — Chess-SSIL Grand Map

**File:** `figures/Fig-001-Chess-SSIL-Grand-Map.png`

**Caption:** *Chess-SSIL as a bounded laboratory for state localization, per-node intelligence, strategy generation, competitive relay, evidence collection, and candidate structural evolution.*

**Primary insertion:** CSSIL-001, immediately after the introductory description of the laboratory architecture and before detailed component analysis.

**Additional use:** `README.md`, near the first architectural overview.

**Interpretive guardrail:** The diagram describes an experimental architecture; it must not imply that every proposed evolution stage has been implemented or validated.

### Fig-002 — Chess Localization and Per-Node Intelligence

**File:** `figures/Fig-002-Chess-Localization-and-Per-Node-Intelligence.png`

**Caption:** *From game state and contextual localization to specialized per-node intelligence, strategy candidates, and contract-bound decisions.*

**Primary insertion:** CSSIL-002, after the distinction between state encoding, localization, and per-node evaluation.

**Related specification:** [`specs/SPEC-001-Game-State-Localization-and-UIRTU-Contract.md`](specs/SPEC-001-Game-State-Localization-and-UIRTU-Contract.md).

**Interpretive guardrail:** A legal-move generator, a localized evaluator, and a strategy generator are separate functions even when one implementation combines them.

### Fig-003 — Competitive Strategy Evolution Loop

**File:** `figures/Fig-003-Competitive-Strategy-Evolution-Loop.png`

**Caption:** *A competitive strategy improvement loop with candidate generation, self-play or tournaments, independent evaluation, counter-evidence, structural selection, and rollback.*

**Primary insertion:** CSSIL-003, following the proposed Competitive Structural Strategy Evolution (CSSE) loop.

**Related specification:** [`specs/SPEC-002-Strategy-Evaluation-and-Competitive-Relay.md`](specs/SPEC-002-Strategy-Evaluation-and-Competitive-Relay.md).

**Interpretive guardrail:** Self-play improvement of policies is established in bounded games; autonomous modification of the strategy-generating architecture remains a separate, testable research hypothesis.

### Fig-004 — Autonomous Structural Growth Ladder

**File:** `figures/Fig-004-Autonomous-Structural-Growth-Ladder.png`

**Caption:** *Evidence-gated progression from searchable strategies to learnable strategies and structurally evolvable systems, with residual handling and rollback.*

**Primary insertion:** CSSIL-004, near the discussion of structural growth and residual intelligence.

**Additional insertion:** [`docs/CSSIL-006-Strategy-Generability Partition and Residual-to-Generable Evolution.md`](docs/CSSIL-006-Strategy-Generability%20Partition%20and%20Residual-to-Generable%20Evolution.md), following the G1/G2/G3 maturity definitions, if that exact filename is used in the repository.

**Related specification:** [`specs/SPEC-003-Structural-Growth-and-Evidence-Record.md`](specs/SPEC-003-Structural-Growth-and-Evidence-Record.md).

**Interpretive guardrail:** G1 (searchable), G2 (learnable), and G3 (structurally evolvable) are capability levels, not automatic guarantees of safety, generality, or ASI.

### Fig-005 — Collective Learning and Research Relay

**File:** `figures/Fig-005-Collective-Learning-and-Research-Relay.png`

**Caption:** *Independent researchers exchange portable intelligence units, evidence, counter-evidence, and validation results to enable discovery, relay, and compositional growth.*

**Primary insertion:** CSSIL-005, after the discussion of discovery growth, relay growth, and compositional growth.

**Additional use:** `START-HERE.md`, near the contribution pathway for independent researchers.

**Interpretive guardrail:** A shared artifact is not automatically transferable; interoperability, provenance, and independent replication remain necessary.

## CSSIL-006: Strategy-Generability Partition and RGC

The sixth core paper extends the five-figure architecture without requiring a sixth figure in the v1.0.0 release. It introduces:

- **Strategy-Generability Partition (SGP):** classify tasks by whether strategy search, learning, or structural evolution can be evaluated reliably.
- **Residual-to-Generable Conversion (RGC):** transform initially non-generable tasks through decomposition, better evidence, localization, simulation, and evaluators.
- **Autonomous Strategy Coverage (ASC):** measure verified autonomy over a declared task distribution, with explicit costs and reliability criteria.

**Recommended reuse:** Cite Fig-004 to connect the G1/G2/G3 ladder to the SGP maturity model, and Fig-005 to show how shared evidence and portable mechanisms may help convert residual tasks into generable ones.

**Future optional figure:** A dedicated `Fig-006-Strategy-Generability-Partition-and-RGC.png` may be added in a subsequent version, but is **not** part of the five-figure v1.0.0 catalog. If added, update this index, `CONTENTS.md`, and the release metadata consistently.

## Markdown Embedding Examples

From a document inside `docs/`:

```markdown
![Fig-001 — Chess-SSIL Grand Map](figures/Fig-001-Chess-SSIL-Grand-Map.png)

*Figure 1. Chess-SSIL as a bounded laboratory for competitive strategy generation and structural learning.*
```

From the repository root:

```markdown
![Fig-001 — Chess-SSIL Grand Map](figures/Fig-001-Chess-SSIL-Grand-Map.png)
```

## Release Checklist

- [ ] Confirm five **separate** PNG files exist under `figures/` with exact case-sensitive filenames.
- [ ] Confirm each image depicts the intended architecture and has legible labels.
- [ ] Verify all relative links and image references render on GitHub.
- [ ] Check that figure numbering, captions, and article references agree.
- [ ] Distinguish proposed mechanisms from experimentally demonstrated results.
- [ ] Check readability and accessibility, including meaningful alternative text.
- [ ] Verify the CSSIL-006 filename used in links matches the actual repository filename (including spaces or hyphens).

## Citation and Reuse

When citing an illustration, reference its figure number and the relevant Chess-SSIL document. For repository-wide attribution, use [`CITATION.cff`](CITATION.cff) once available. No DOI is asserted here until a release has been archived and assigned one.

---

**Chess-SSIL — v1.0.0**  
**Sizhe Tan & GPT-Obot**
