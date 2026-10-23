# CSSIL-003 — Competitive Relay and Autonomous Strategy Evolution

**Chess as a Strategic Structural Intelligence Laboratory (Chess-SSIL)**  
**Version:** 1.0.0 — Research proposal  
**Authors:** Sizhe Tan & GPT-Obot  
**Status:** Conceptual architecture and testable hypotheses; not an implemented system

## Abstract

Chess and other finite, rule-governed games offer a controlled laboratory for investigating how strategic intelligence emerges from repeated competitive interaction. This paper interprets alternating play as a **competitive UIRTU-Relay**: each participant localizes a shared state, evaluates candidate actions, commits a legal transition, and receives new evidence through the opponent's response. We distinguish **autonomous strategy learning** within a fixed architecture from **autonomous structural strategy evolution**, in which the localization operators, scoring functions, strategy modules, dispatch policies, or strategy generator itself may be proposed, tested, accepted, and rolled back. We outline a three-stream relay model, a versioned evolution loop, reproducible baselines, and a staged experimental program. Successful self-play in board games supports the feasibility of automatic strategy improvement under well-specified rules and feedback; it does not by itself demonstrate open-world autonomy or artificial superintelligence.

**Keywords:** competitive UIRTU-Relay; SSICR; chess; self-play; strategy generation; structural evolution; counter-evidence; residual intelligence; collective learning

## 1. Research Motivation and Scope

The foundational **Strategic Structural Intelligence and Competitive UIRTU-Relay (SSICR)** framework studies how strategic decisions arise from interactions among structural intelligence units and competing agents. **Chess-SSIL** is a separate, lightweight experimental bridge: rather than re-deriving the general theory, it asks which SSICR claims can be operationalized, falsified, and improved in reproducible games.

The key question is not merely whether a machine can win a game. It is:

> Under explicit rules and measurable feedback, can competitive relay support the automatic generation, evaluation, selection, and eventually structural revision of strategy-producing intelligence?

A game is attractive because its legal transitions and terminal outcomes are explicit. However, the environment still has limitations: winning is an unusually well-defined objective; games omit many open-world problems of incomplete rules, ambiguous values, and deployment governance.

## 2. Competitive Relay as an Operational Model

Let a game be defined by \(G=(S,A,T,P,R,\Omega)\), where \(S\) is the state space, \(A(s)\) the legal actions in state \(s\), \(T(s,a)\) the transition function, \(P(s)\) the player to move, \(R\) the outcome or reward definition, and \(\Omega\) the terminal conditions.

At turn \(t\), player \(i=P(s_t)\) computes:

\[
z_t^i=L_i(s_t,h_t;\theta_L), \qquad
c_t^i=\mathcal{G}_i(z_t^i,\mathcal{M}_i,B_t),
\]

\[
a_t=\Pi_i(c_t^i,z_t^i;\theta_\Pi)\in A(s_t),\qquad
s_{t+1}=T(s_t,a_t).
\]

Here \(L_i\) is localization, \(h_t\) the relevant history, \(\mathcal{M}_i\) the available intelligence modules, \(B_t\) the computation budget, \(\mathcal{G}_i\) the strategy generator, and \(\Pi_i\) the final selection policy. The notation specifies an experimental decomposition, **not** the internal architecture of AlphaGo or any other existing engine.

A **UIRTU** in this proposal is a reusable, contract-bound intelligence unit. A move is an *execution instance* of one or more units, not necessarily a distinct UIRTU in its own right. A relay links these instances through state transitions, evidence, and control decisions. The opponent is not a passive data source: its actions actively change the decision landscape.

### 2.1 Three coupled streams

| Stream | What is produced | What must be recorded |
|---|---|---|
| **Execution** | Legal actions and new board states | State, action, rules version, actor, timestamps or turn index |
| **Evidence** | Prediction errors, tactical refutations, outcomes, uncertainty | Predicted scores, candidate set, realized continuation, counter-evidence |
| **Evolution** | Candidate policy or structural revisions | Parent version, proposed delta, evaluation protocol, acceptance decision |

These streams are **not automatically equivalent**. A game transcript creates execution data; turning it into useful evidence requires evaluators and attribution; turning evidence into structural growth requires an explicit proposal-and-validation mechanism.

## 3. Three Levels of Automatic Improvement

### Level A — Autonomous strategy learning

A fixed algorithm or architecture improves its strategy through search, self-play, or parameter updates. Strong precedent exists: AlphaGo Zero and AlphaZero demonstrated that self-play can yield very strong policies without human move-by-move strategic instruction. This does not imply that their full architectures were autonomously invented.

### Level B — Autonomous structural strategy evolution

The system proposes changes to its **structure**, for example:

- Add or remove a localization perspective (king safety, material imbalance, mobility, territory).
- Introduce a specialized per-node evaluator or residual-handling module.
- Modify the strategy generator's module dispatch, composition, or search-budget allocation.
- Fold recurring successful sequences into reusable macro-strategies; unfold a brittle macro when counter-evidence appears.
- Revise evaluator selection or calibration while retaining historical comparison data.

The research claim is **conditional**: structural search *may* outperform a fixed architecture on defined tasks and budgets. Whether it does so is an empirical question.

### Level C — Open-world autonomous intelligence evolution

Rules, objectives, participants, and evidence may change or be only partially known. Success at Levels A or B does **not** establish Level C. Open-world transfer additionally requires goal governance, uncertainty handling, nonstationarity management, safety boundaries, and trustworthy evaluation.

**The “automatic license” is therefore a license to investigate increasingly autonomous strategy improvement in controlled environments, not proof of unrestricted ASI.**

## 4. Competitive Structural Strategy Evolution (CSSE)

We propose **CSSE** as a candidate mechanism within Chess-SSIL, not as an established algorithm:

1. **Observe:** collect board states, candidate evaluations, actions, and game outcomes.
2. **Diagnose:** identify failures, residual states, disagreement among perspectives, or expensive search patterns.
3. **Propose:** generate a typed structural delta \(\Delta_k\) to a localization operator, scoring module, dispatch rule, macro, or generator.
4. **Sandbox:** validate legality, interface conformance, deterministic replay, and resource limits.
5. **Compete:** evaluate the candidate against its parent and independent baselines under matched budgets.
6. **Select:** accept, reject, quarantine, or roll back the delta using prespecified criteria.
7. **Relay:** publish a versioned artifact, provenance, counter-evidence, and reproduction instructions for collective learning.

A simplified update is:

\[
M_{k+1}=\begin{cases}
\operatorname{Apply}(M_k,\Delta_k), & \text{if } V(\Delta_k\mid M_k,D_k,B)\geq \tau \\
M_k, & \text{otherwise,}
\end{cases}
\]

where \(M_k\) is the current structural configuration, \(D_k\) is a held-out evaluation suite, \(B\) is a matched resource budget, and \(V\) is a preregistered validation measure. A single noisy win-rate estimate should not be treated as sufficient evidence of improvement.

### 4.1 Structural versus parametric updates

Every proposed improvement should be classified as one of:

- **Parameter update:** weights change but the executable graph and contracts remain fixed.
- **Search update:** more or better-directed computation is used without a persistent structural change.
- **Structural update:** a persistent, inspectable change modifies modules, interfaces, composition, dispatch, or control logic.

This classification prevents ordinary training gains from being mislabeled as structural evolution.

## 5. Competitive Evaluation and Anti-Goodhart Controls

Self-play is useful but insufficient as the only judge: agents can exploit their own blind spots, co-adapt to a narrow opponent population, or optimize proxy scores that do not generalize.

Recommended safeguards:

- Evaluate against **fixed baselines**, prior versions, and a **diverse opponent pool**.
- Separate training opponents from held-out evaluation opponents and positions.
- Use color-balanced paired matches, multiple seeds, and fixed time/node/energy budgets.
- Report confidence intervals for win rate or Elo differences; track draws and illegal moves.
- Test tactical puzzles, unfamiliar openings, adversarially selected positions, and endgames.
- Audit whether gains survive ablations removing the new module.
- Keep immutable game logs and evaluator versions; reserve a rollback path.

For a two-player zero-sum game, the empirical score of a candidate \(C\) against a baseline \(B\) can be reported as

\[
\widehat{S}(C,B)=\frac{W+\tfrac12D}{N},
\]

where \(W\) is candidate wins, \(D\) draws, and \(N\) total games. This is a **match score**, not proof of a globally optimal strategy. Statistical uncertainty, opponent selection, and computational cost must accompany it.

## 6. Residual Intelligence and Counter-Evidence

A **residual** is not simply an unfamiliar position. It is a state, discrepancy, or capability gap that the current structural representation or evaluation pipeline does not adequately explain or handle.

Possible triggers include:

- Large disagreement between short-horizon and long-horizon evaluations.
- Persistent prediction-versus-outcome mismatch for a recognizable position class.
- A tactical refutation repeatedly missed by the active scoring forest.
- Low-confidence localization or failure to select an appropriate specialized module.
- Unexpected performance collapse against a new opponent family.

A residual record should contain the state and rules version, triggering observation, relevant predictions, proposed explanation, counter-evidence, and the follow-up experiment. The system may respond by expanding search, requesting another perspective, generating a new module, or declining to update until evidence improves.

Crucially, **not every residual warrants a new module**. Some arise from noise, insufficient search, a bad objective, or an evaluator bug. Diagnosing the source is part of the research problem.

## 7. Strategy-Generator Evolution: The Higher-Order Target

Improving the next move is first-order optimization. Improving a policy over moves is second-order. Improving the **process that assembles policies and allocates intelligence resources** is a higher-order target:

\[
\mathcal{G}_{k+1}=\operatorname{SelectValidated}\bigl(\mathcal{G}_k,\operatorname{ProposeDelta}(E_k)\bigr),
\]

where \(E_k\) contains competitive evidence and structural failure analyses.

Candidate higher-order changes include selecting different perspective sets by phase of play, dynamically choosing between rule-based and search-based units, and learning when a residual merits expensive exploration. A credible demonstration must show that the *generator's persistent decision structure* changed, and that the change transfers beyond the exact positions used to create it.

## 8. Minimal Experimental Program

| Phase | Game / setup | Experimental question | Deliverable |
|---|---|---|---|
| **P0** | Tic-Tac-Toe or Nim | Can state, localization, UIRTU calls, and evidence be logged without ambiguity? | Replayable relay trace and contract tests |
| **P1** | Small solved game | Can strategy learning recover known optimal behavior from rules and feedback? | Baseline comparison against exact solver |
| **P2** | Connect Four or constrained chess | Can a candidate structural delta improve held-out performance at equal cost? | Versioned delta, paired matches, ablation |
| **P3** | Chess | Does multi-perspective dispatch or residual handling generalize across opponent families? | Cross-opponent evaluation and failure atlas |
| **P4** | Independent research teams | Can one team's validated UIRTU or evidence artifact be reused by another? | Reproduction and interoperability report |

A **minimal first experiment** can compare (A) a fixed heuristic/search baseline, (B) the same baseline with ordinary parameter tuning, and (C) a structurally adaptive dispatcher. Equalize training opportunities and inference budgets; report performance and complexity. If C fails to improve, publish the counter-evidence.

## 9. Provisional Research Contracts

This paper relies on three companion specifications:

- **SPEC-001 — Game State, Localization, and UIRTU Contract:** input state, rule set, legal-action mask, perspectives, typed module outputs.
- **SPEC-002 — Strategy Evaluation and Competitive Relay:** candidate actions, search budgets, match protocol, score and uncertainty records.
- **SPEC-003 — Structural Growth and Evidence Record:** delta identifiers, parent versions, provenance, validation, rollback, residual and counter-evidence schema.

The specifications are intended as *research interoperability proposals*, not mature standards. Compatibility and reproducibility are measurable research outcomes.

## 10. Hints for Collective Learning

1. **Begin with a solved small game.** Ground-truth optimal play helps detect conceptual and implementation errors.
2. **Separate the three streams.** A successful move, a useful counterexample, and a validated structural revision are different artifacts.
3. **Do not equate self-play with structural self-improvement.** Show the persistent architectural delta.
4. **Preserve negative results.** Failed strategies and unsuccessful deltas prevent other researchers from repeating avoidable mistakes.
5. **Compare under matched budgets.** Improvements attributable only to extra compute are not evidence for structural advantage.
6. **Publish portable pieces.** A small reusable evaluator, trigger, dataset, or relay trace can be more valuable than an opaque monolithic engine.
7. **Treat opponent diversity as part of the evaluator.** Competitive co-adaptation can hide fragility.
8. **Keep the claim boundary visible.** Finite-game automatic learning is evidence for bounded autonomy, not proof of general autonomous evolution.

## 11. Testable Hypotheses

- **H1 — Competitive Learning:** under fixed rules, an agent with valid feedback and exploration can improve against its initial policy without human-authored move prescriptions.
- **H2 — Structural Benefit:** for at least one preregistered task distribution and matched compute budget, a validated structural change outperforms both its parent and a parameter-only control.
- **H3 — Residual Utility:** targeted residual triggers improve sample efficiency or held-out robustness relative to indiscriminate retraining or fixed search expansion.
- **H4 — Generator Transfer:** an evolved strategy generator improves performance on positions and opponent families not used to propose its structural delta.
- **H5 — Relay Reuse:** a documented, contract-compliant module can be independently integrated and reproduced with lower effort than an equivalent undocumented module.

Each hypothesis is falsifiable. Null and adverse outcomes should remain first-class research results.

## 12. Open Questions and Boundaries

- Which aspects of a strategy generator can be modified without destabilizing the evaluator?
- What constitutes a meaningful *structural* improvement rather than a renamed heuristic?
- How can residual triggers avoid overfitting to rare but irrelevant positions?
- What is the right unit of reusable strategy intelligence: rule, module, macro, evaluator, or generator?
- How should conflicting perspectives be folded without suppressing uncertainty?
- How do we prevent self-play from producing narrow co-adaptation and Goodhart effects?
- Which lessons transfer from perfect-information games to partial-information or changing-rule environments?
- What governance is required when autonomous structural changes affect external actions rather than sandbox games?

This work does **not** claim a chess-solving breakthrough, a novel AlphaGo implementation, guaranteed monotonic improvement, or demonstrated ASI. It offers a research architecture and validation path.

## 13. Relationship to the Chess-SSIL Series

- **CSSIL-001:** Chess as a Canonical SSICR Laboratory — conceptual mapping and research motivation.
- **CSSIL-002:** Localization, Per-Node Intelligence, and Strategy Generation — decision architecture.
- **CSSIL-003 (this paper):** Competitive Relay and Autonomous Strategy Evolution — evidence-driven improvement loop.
- **CSSIL-004:** Residual Intelligence and Structural Growth — detecting and addressing capability gaps.
- **CSSIL-005:** Collective Learning and Research Relay — portability, contribution, and interoperability.

**Suggested figures:** `Fig-003-Competitive-Strategy-Evolution-Loop.png` after Section 4 and `Fig-004-Autonomous-Structural-Growth-Ladder.png` after Section 3.

## 14. Selected Background References

1. Silver, D., et al. (2016). *Mastering the game of Go with deep neural networks and tree search.* Nature 529, 484–489. https://doi.org/10.1038/nature16961
2. Silver, D., et al. (2017). *Mastering the game of Go without human knowledge.* Nature 550, 354–359. https://doi.org/10.1038/nature24270
3. Silver, D., et al. (2018). *A general reinforcement learning algorithm that masters chess, shogi, and Go through self-play.* Science 362, 1140–1144. https://doi.org/10.1126/science.aar6404
4. Campbell, M., Hoane, A. J., and Hsu, F.-h. (2002). *Deep Blue.* Artificial Intelligence 134, 57–83. https://doi.org/10.1016/S0004-3702(01)00129-1

These references establish relevant historical precedents for game search and self-play; they do not validate the proposed SSICR structural contracts or CSSE mechanism.

---

**Citation note:** Cite the released Chess-SSIL DOI when available; do not insert a placeholder DOI as though it were assigned. The foundational SSICR repository should be linked from the project README after its verified canonical URL and DOI are recorded.

**License and reuse:** Follow the repository's published license and citation metadata. Independent experiments, corrections, counterexamples, and portable modules are encouraged.
