# Changelog

All notable changes to **Chess as a Strategic Structural Intelligence Laboratory (Chess-SSIL)** are documented here.

This repository is a research framework and experimental agenda. A listed research mechanism, specification, or hypothesis does **not** imply that an executable implementation or empirical validation has been completed.

The format follows the principles of [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and releases use semantic-style version labels for repository publication.

## [Unreleased]

### Planned

- Implement minimal reproducible game laboratories, beginning with Tic-Tac-Toe or Nim.
- Publish baseline agents, evaluation protocols, experiment seeds, and evidence records.
- Test Strategy-Generability Partition (SGP) and Residual-to-Generable Conversion (RGC) on controlled task families.
- Evaluate Autonomous Strategy Coverage (ASC) under explicitly defined task distributions and resource budgets.
- Develop portable Research Relay Units for independent replication and collective learning.
- Extend the figure set if a dedicated SGP/RGC architecture illustration is needed.

## [1.0.0] — 2026-10-23

### Added — Core research papers

- `docs/CSSIL-001-Chess-as-a-Canonical-SSICR-Laboratory.md` — Chess and other bounded games as falsifiable laboratories for strategic structural intelligence.
- `docs/CSSIL-002-Localization-Per-Node-and-Strategy-Generation.md` — Game-state localization, per-node intelligence, and strategy generation.
- `docs/CSSIL-003-Competitive-Relay-and-Autonomous-Strategy-Evolution.md` — Competitive UIRTU-Relay, self-play, evaluation, and candidate structural evolution.
- `docs/CSSIL-004-Residual-Intelligence-and-Structural-Growth.md` — Counter-evidence, residual discovery, and evidence-governed structural growth.
- `docs/CSSIL-005-Collective-Learning-and-Research-Relay.md` — Portable research contributions, relay interoperability, and collective learning.
- `docs/CSSIL-006-Strategy-Generability Partition and Residual-to-Generable Evolution.md` — Strategy-Generability Partition (SGP), Generability maturity levels, Residual-to-Generable Conversion (RGC), and Autonomous Strategy Coverage (ASC).

### Added — Specifications

- `specs/SPEC-001-Game-State-Localization-and-UIRTU-Contract.md` — Proposed state, localization, and intelligence-unit interfaces.
- `specs/SPEC-002-Strategy-Evaluation-and-Competitive-Relay.md` — Proposed strategy evaluation and competitive relay contracts.
- `specs/SPEC-003-Structural-Growth-and-Evidence-Record.md` — Proposed structural change, provenance, evidence, and rollback records.

### Added — Research and validation

- `research/OPEN-QUESTIONS.md` — Unresolved conceptual and engineering questions.
- `research/TESTABLE-HYPOTHESES.md` — Falsifiable hypotheses and candidate measurements.
- `research/VALIDATION-ROADMAP.md` — Staged experimental program with evidence and validation gates.

### Added — Navigation and publication support

- `README.md` — Project scope, architecture, contribution principles, and repository navigation.
- `START-HERE.md` — Entry paths for readers, implementers, and independent evaluators.
- `CONTENTS.md` — Repository content map.
- `GLOSSARY.md` — Terminology and operational distinctions.
- `FIGURE-INDEX.md` — Planned figure catalog and placement guidance.
- `FUTURE-DIRECTIONS.md` — Research extensions and experimental priorities.
- `CHANGELOG.md` — Release history.

### Added — Figure plan

- `figures/Fig-001-Chess-SSIL-Grand-Map.png`
- `figures/Fig-002-Chess-Localization-and-Per-Node-Intelligence.png`
- `figures/Fig-003-Competitive-Strategy-Evolution-Loop.png`
- `figures/Fig-004-Autonomous-Structural-Growth-Ladder.png`
- `figures/Fig-005-Collective-Learning-and-Research-Relay.png`

*Figure entries identify the intended v1.0.0 assets; confirm that all five separate PNG files exist and render correctly before publication.*

### Research distinctions established

- Distinguished **strategy search**, **strategy learning**, **structural strategy evolution**, and **open-world autonomous evolution**; these are not interchangeable achievements.
- Distinguished a **Generable Domain** from a **Residual Domain**, with reassessment as evidence and capabilities change.
- Proposed **G1 / G2 / G3** strategy-generability maturity levels and an explicit non-generable or not-yet-assessed category.
- Proposed **RGC** as a validation-gated conversion process rather than an assumption that all residual problems can be automated.
- Proposed **ASC** as a task-distribution-dependent metric, not a universal intelligence score.
- Preserved the separation between **strategy-generation capability** and **authority to act**, including human and multi-subject governance requirements.

### Publication notes

- **Authors:** Sizhe Tan & GPT-Obot.
- **Status:** Initial research-framework release; empirical results must be separately identified and independently verified.
- **DOI:** To be assigned upon archival publication. Do not substitute a placeholder DOI in citation metadata.
- Verify repository links, figure files, citation metadata, license declarations, and GitHub rendering before tagging `v1.0.0`.

---

## Release policy

Future entries should distinguish **Added**, **Changed**, **Fixed**, **Deprecated**, and **Removed** items as appropriate. Experimental claims must state their evidence level and point to reproducible artifacts. Changes to interface contracts or evaluation criteria should document compatibility implications and migration guidance.
