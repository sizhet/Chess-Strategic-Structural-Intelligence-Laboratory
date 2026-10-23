# Glossary

**Project:** Chess as a Strategic Structural Intelligence Laboratory (Chess-SSIL / CSSIL)  
**Version:** v1.0.0  
**Authors:** Sizhe Tan & GPT-Obot  
**Status:** Research terminology and proposed operational definitions

## Purpose and interpretation

This glossary establishes a consistent vocabulary for the Chess-SSIL research repository. Terms marked **proposed** describe research constructs or architectural hypotheses, not established scientific results. A successful demonstration in a bounded game does not, by itself, establish general intelligence, autonomous structural evolution, or artificial superintelligence (ASI).

## A. Foundations and architecture

### Structural Intelligence (SI)
An approach to intelligence that represents and improves explicit structures for perception, localization, decision-making, control, execution, and learning, rather than treating intelligence solely as the output of a monolithic model.

### Structural Intelligence Framework (SIF)
The broader framework organizing SI around functional domains, contracts, portable components, evidence, and open-ended structural growth. Chess-SSIL applies selected SIF concepts to reproducible strategy experiments.

### Subjective Structural Intelligence (SSI)
A research perspective emphasizing subject boundaries, perspectives, valuation, agency, and decision sovereignty. It is relevant when strategy optimization affects humans or other decision-making subjects.

### Strategic Structural Intelligence (SSI, contextual abbreviation)
The use of structured representations and control mechanisms to formulate, evaluate, select, execute, and revise strategies. To avoid ambiguity with *Subjective Structural Intelligence*, this repository generally spells out “strategic structural intelligence” or uses **SSICR** for the related research program.

### SSICR
**Strategic Structural Intelligence and Competitive UIRTU-Relay**: the related theoretical program connecting strategy generation, competition, relay, evaluation, and structural evolution. Chess-SSIL is an experimental research companion, not a replacement for SSICR.

### Chess-SSIL / CSSIL
**Chess as a Strategic Structural Intelligence Laboratory**: a bounded, reproducible research environment for investigating strategy generation, competitive relay, residual handling, structural growth, and collective learning. The CSSIL prefix identifies this repository’s numbered research papers.

### UIERU
**Universal Intelligence Evolution and Relay Unit**: a composable unit concept for carrying intelligence structures, interfaces, evidence, and evolution-related information across contexts.

### UIRTU / UIRTU-Relay
A structured intelligence unit and its relay mechanism, as used in the associated research lineage. In Chess-SSIL, the term denotes an explicitly contracted transfer of state, strategy, evaluation, evidence, or learned structure between components or agents. Precise fields and semantics should be defined in the repository's SPEC documents rather than inferred from the acronym alone.

### Intelligence Relay
The transfer of usable intelligence between components, tasks, agents, or research groups, including the contextual information necessary to interpret and validate it.

### Portable Intelligence Unit
A self-describing, reusable intelligence component with a stated interface, scope, assumptions, provenance, and validation evidence. Portability does not imply universal applicability.

### Universal Contract
A machine-readable or documented agreement specifying the inputs, outputs, semantics, constraints, and evidence requirements for interoperating SI components.

### Control Plane
The mechanisms that govern selection, authorization, execution boundaries, evaluation, escalation, and rollback across intelligence components.

### Subject Boundary
The boundary defining whose objectives, preferences, rights, and authority a strategy serves. It must not be conflated with a strategy optimizer's technical ability.

### Scoring Sovereignty
The authority to define, approve, or contest the objectives and scoring criteria used in decisions. Particularly important in social and human-impacting applications.

## B. Games, strategy, and evaluation

### Game State
A representation of the relevant configuration of a game at a given time, including turn, legal actions, and any additional state required by the rules.

### Game-State Localization
Mapping a raw game position or observation into a task-relevant structural representation used for decision-making. Localization may produce several perspectives, features, subproblems, or candidate precedents.

### Localization
Selecting, identifying, and relating relevant structural context for a problem or component. Localization is not synonymous with geographic location or simply retrieving text.

### Per-Node Intelligence
Decision or reasoning capabilities associated with a particular node or localized context, potentially using specialized algorithms, models, evaluators, or rules.

### Strategy
A policy, plan, or conditional decision structure that selects actions in relation to objectives, constraints, and possible future states. A strategy may be partial or contingent rather than a fixed action sequence.

### Strategy Generator
A component or system that produces candidate strategies from problem representations and constraints. Its output requires independent evaluation before a reliability claim.

### Autonomous Strategy Generation (ASG)
Producing strategies with limited or no case-by-case human direction within explicitly stated task, resource, evaluation, and authorization boundaries. Autonomy is a matter of degree, not an unrestricted property.

### Strategy Search
Exploration of candidate actions, plans, or policies using search, optimization, simulation, or related methods.

### Strategy Learning
Improvement in strategy selection or generation based on experience, data, feedback, competition, or optimization. This does not necessarily alter the structure of the strategy generator itself.

### Strategy Evaluation
Assessing candidate strategies against explicit criteria such as legality, reward, robustness, resource cost, and generalization to held-out settings.

### Independent Evaluation
Testing conducted using evidence, environments, opponents, or evaluators sufficiently separated from those used to construct or tune a candidate. Separation should be documented, not assumed.

### Baseline
A specified reference method used for comparison, such as a random policy, classical search algorithm, established game engine, or fixed strategy generator. Fair comparisons control for computational budget and access to information.

### Self-Play
Training or evaluating agents by playing against copies, variants, or previous versions of themselves. Self-play can support strong strategy learning in bounded games but does not alone demonstrate open-ended structural evolution.

### Competitive Relay
An interaction cycle in which competing agents or strategies generate actions, receive outcomes and counter-evidence, and transfer validated information into subsequent decision or learning stages.

### Tournament Evaluation
Comparison across multiple opponents, starting positions, seeds, or conditions to estimate strategy performance and robustness rather than relying on a single match.

### Distribution Shift
A change between training or development conditions and evaluation or deployment conditions that may undermine previously measured performance.

### Reward Hacking / Goodhart Failure
Exploiting a metric or proxy in ways that improve the reported score without achieving the intended objective. Independent tests and counter-evidence are needed to detect these failures.

## C. Strategy-generability partition and residual evolution

### Strategy-Generability Partition (SGP) — proposed
A classification of tasks or task components according to whether strategies can be generated and validated with sufficient reliability under explicit assumptions, resource budgets, and authorization constraints. Membership is conditional and can change over time.

### Generable Domain — proposed
The subset of tasks for which the system can produce strategies and satisfy a declared evaluation standard. “Generable” never means guaranteed correct or universally safe.

### Residual Domain — proposed
Tasks, subproblems, uncertainties, or constraints that do not currently meet the generability criteria. Residual status is a research and engineering classification, not proof of permanent impossibility.

### Generability Assessment — proposed
A documented check of whether a task has adequate state representation, available actions, objectives, evaluators, feedback, safety constraints, and validation methods for a proposed level of automation.

### G1: Strategy Searchable — proposed
A task supports a defined search space and evaluation procedure for candidate strategies. This does not establish that learning or structural adaptation occurs.

### G2: Strategy Learnable — proposed
A task supports repeatable improvement of strategies using experience or feedback, demonstrated against suitable baselines and held-out tests.

### G3: Structurally Evolvable — proposed
A task supports validated changes to the strategy-generation machinery itself—for example, to localization, scoring, decomposition, relay, or generator composition—rather than merely adjusting a policy's parameters. Claims require controlled ablations and rollback-capable evidence.

### Residual-to-Generable Conversion (RGC) — proposed
A process that attempts to transform residual tasks or subproblems into validated generable tasks by acquiring evidence, refining representations, decomposing objectives, constructing evaluators, and testing transfer under independent conditions.

### Residual Diagnosis
Identifying why a task fails generability criteria, such as missing observations, ambiguous objectives, insufficient feedback, unverifiable outcomes, unsafe actions, or inadequate compute.

### Generability Frontier — proposed
The changing boundary between tasks that meet a declared autonomous-strategy standard and those that remain residual under the same standard.

### Autonomous Strategy Coverage (ASC) — proposed
A distribution- and threshold-dependent measure of the weighted fraction of tasks meeting specified autonomous strategy generation and validation criteria:

\[
\mathrm{ASC}(t;D,\tau)=
\frac{\sum_{i=1}^{n}w_i\,\mathbf{1}[\mathrm{Pass}(T_i,t,\tau)]}
{\sum_{i=1}^{n}w_i},
\]

where \(D\) is the evaluated task set or distribution, \(w_i\) are nonnegative task weights, and \(\tau\) contains the declared reliability, cost, autonomy, and safety thresholds. ASC values from different distributions or thresholds are not directly comparable.

### Conversion Yield — proposed
The proportion of attempted RGC cases that satisfy predefined independent validation criteria. Reports should also state attempts, failures, exclusions, and cost.

### Coverage Expansion
An increase in validated ASC or in the diversity of tasks meeting the generability standard, measured on a fixed or carefully calibrated benchmark to avoid apparent gains caused by easier task selection.

## D. Structural growth and evidence

### Competitive Structural Strategy Evolution (CSSE) — proposed
A candidate structural-growth cycle involving generation, competition, evaluation, counter-evidence, selection, integration, and rollback. It is a research architecture whose effectiveness must be tested.

### Structural Strategy Evolution
Validated improvement in the organization or composition of strategy-generating components, distinct from ordinary policy tuning or search-depth increases.

### Strategy-Generator Evolution
Modification of the generator itself, such as its decomposition rules, localization operators, scoring structures, or orchestration policy. A claimed improvement must be evaluated independently.

### Structural Growth
The addition, revision, recombination, or removal of reusable intelligence structures that improves capability under stated criteria.

### Folding / Unfolding
Structural operations that compress or combine representations (**folding**) or expand, specialize, or recover useful distinctions (**unfolding**). Their effects on uncertainty and correctness require explicit evaluation.

### Residual Intelligence
Mechanisms for detecting, representing, investigating, and learning from unexplained errors, unmet objectives, unknown factors, and cases outside current capabilities.

### Counter-Evidence
Observations or experiments that challenge a candidate strategy, structural hypothesis, claimed improvement, or evaluator. Counter-evidence should remain traceable even when a candidate is accepted.

### Evidence Record
A structured artifact capturing a hypothesis or candidate, provenance, configuration, baselines, evaluation protocol, outcomes, uncertainty, failures, and replication details.

### Provenance
The traceable origin and transformation history of a model, dataset, strategy, component, or evidence item.

### Ablation Study
A controlled comparison that removes or alters a component to estimate its contribution to an observed result.

### Rollback
Restoring a previously validated configuration when a proposed change fails safety, correctness, or performance criteria.

### Validation Gate
A predefined pass/fail decision point requiring evidence before a candidate progresses to broader use or more autonomous operation.

### Reproducibility
The ability to repeat an experiment from a sufficiently complete specification of rules, versions, seeds, compute, data, and evaluation methods.

## E. Collective learning and research transfer

### Collective Learning
Improvement of a broader research ecosystem through sharing reproducible evidence, reusable components, failures, interfaces, and validated methods across independent contributors.

### Research Relay
The structured transfer of research results, hypotheses, experiments, counter-evidence, and reusable components so that other investigators can interpret and test them.

### Discovery Growth — proposed
Growth arising from genuinely new findings, mechanisms, or capabilities.

### Relay Growth — proposed
Growth arising when previously known intelligence becomes discoverable, accessible, interpretable, or usable in a new context.

### Compositional Growth — proposed
Growth arising from combining existing components into a capability that the components could not deliver independently.

### Research Relay Unit — proposed
A portable contribution package containing a problem statement, assumptions, interface, method, evidence, limitations, and instructions for replication or integration.

### Interoperability
The ability of components or research artifacts to exchange information with compatible semantics and verifiable behavior, not merely compatible file formats.

### Structural Precedent
A previously documented problem structure, solution, or experimental result that can inform localization or strategy generation in a new case, subject to applicability checks.

### Open-Ended Growth
The potential for continued discovery, integration, and refinement of new structural capabilities without a predefined finite catalog. This is a research objective, not a demonstrated guarantee of limitless improvement.

## F. Scope and interpretation boundaries

### Bounded Game
An environment with sufficiently specified rules, legal actions, and outcome or reward signals to support controlled experimentation. Chess is a rich bounded game, not a complete model of the open world.

### Open-World Problem
A problem involving incomplete or changing rules, observations, objectives, stakeholders, or consequences that cannot be fully captured by a fixed game specification.

### Artificial Superintelligence (ASI)
A proposed level of AI capability substantially exceeding human capabilities across a broad range of consequential domains. Chess-SSIL does not claim to demonstrate ASI or that ASC alone measures it.

### Action Authority
Permission to execute actions affecting an environment or stakeholders. Technical ability to generate a strategy does not confer authorization to carry it out.

### Human Oversight
Human review, approval, intervention, or appeal mechanisms appropriate to the risk, reversibility, and stakes of an automated decision.

### Research Hypothesis
A proposition with explicit assumptions and observable criteria that could support or falsify it. Architectural plausibility is not empirical validation.

## Related repository documents

- [README.md](README.md) — project overview and scope.
- [START-HERE.md](START-HERE.md) — reading and experiment entry points.
- [CONTENTS.md](CONTENTS.md) — repository navigation.
- [CSSIL-006: Strategy-Generability Partition and Residual-to-Generable Evolution](docs/CSSIL-006-Strategy-Generability%20Partition%20and%20Residual-to-Generable%20Evolution.md) — proposed SGP/RGC framework.
- [Open Questions](research/OPEN-QUESTIONS.md), [Testable Hypotheses](research/TESTABLE-HYPOTHESES.md), and [Validation Roadmap](research/VALIDATION-ROADMAP.md) — research status and empirical requirements.

---

**Terminology policy:** Use the full term at first occurrence; retain the distinction between established techniques, proposed architecture, and experimentally verified claims. New terminology should be accompanied by an operational definition and, where applicable, a falsifiable test.
