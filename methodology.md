
Methodology

Nature Risk Scenario Analysis Workflow

TNFD LEAP–Aligned, Asset-Level, Scenario-Based Framework

⸻

1. Purpose and modelling philosophy

1.1 Objective

This workflow implements a nature-related risk scenario analysis at asset level, aligned with the expectations of the Taskforce on Nature-related Financial Disclosures (TNFD).

The objective is to:
	•	identify material dependencies on ecosystem services,
	•	assess nature-related physical and transition risks under plausible scenarios,
	•	translate these risks into financial exposure ranges,
	•	support TNFD-compliant disclosure, strategy, and governance discussions.

The model is designed for screening, prioritisation, and structured decision support — not ecological forecasting.

⸻

1.2 What this model is

This workflow is a hybrid deterministic + AI-assisted methodology combining:
	1.	Deterministic, auditable modelling:
	•	dependency mapping,
	•	scenario framing,
	•	shock propagation,
	•	financial impact estimation.
	2.	Constrained AI reasoning:
	•	evidence synthesis from fragmented literature,
	•	interpretation of quantified outputs,
	•	formulation of adaptation strategies,
	•	stakeholder-specific narrative generation.

⸻

1.3 What this model is not

Explicit exclusions:
	•	not a biodiversity impact or species-loss model,
	•	not a probabilistic climate–nature simulation,
	•	not a regulatory capital or pricing model,
	•	not a site-specific ecological assessment.

These boundaries are intentional and consistent with TNFD’s proportionality principle.

⸻

2. TNFD LEAP alignment (structural mapping)

LEAP step	Objective	Workflow implementation
Locate	Identify asset–nature interface	Asset definition, geospatial & biome context
Evaluate	Identify dependencies	ENCORE-aligned dependency mapping
Assess	Quantify risk under scenarios	Scenario axes → shock grid → financial engine
Prepare	Response & disclosure	Evidence synthesis, adaptation, narratives

Each step produces machine-readable outputs consumed by subsequent steps.
No narrative or AI output feeds back into numeric calculations.

⸻

3. Locate — asset and environmental context

3.1 Asset representation

Each asset is represented as:

A = \{ id,\; sector,\; country,\; value_{EUR},\; lat,\; lon \}

Where:
	•	value_EUR defines the financial exposure base,
	•	lat, lon enable spatial enrichment (optional).

⸻

3.2 Environmental context variables

Contextual variables include:
	•	biome classification,
	•	biodiversity proxy (e.g. GBIF species richness),
	•	water stress category,
	•	flood or hydrological proxies.

Key assumption:
These variables do not define risk directly.
They act only as modifiers in later dependency and shock calculations to avoid double-counting.

⸻

4. Evaluate — ecosystem service dependency modelling

4.1 Conceptual foundation

Dependencies are defined as:

The degree to which continued asset operation requires sustained provision of a given ecosystem service.

This is dependency, not impact.

Each dependency d_i is defined as:

d_i = \{ s_i,\; \text{strength}_i,\; \text{substitutability}_i,\; \text{time\_to\_failure}_i \}

Where:
	•	s_i = ecosystem service (e.g. surface water),
	•	strength ∈ {Low, Medium, High, Very High},
	•	substitutability ∈ {High, Medium, Low},
	•	time_to_failure ∈ {Long, Medium, Short}.

⸻

4.2 Interpretation of dependency attributes

Dependency strength
	•	Very High: asset cannot operate without the service.
	•	High: severe degradation materially disrupts operations.
	•	Medium: degradation increases costs or reduces efficiency.
	•	Low: marginal or indirect reliance.

Substitutability
	•	High: alternatives exist at reasonable cost.
	•	Medium: partial substitution possible.
	•	Low: few or no viable substitutes.

Time-to-failure
	•	Short: operational failure occurs rapidly after degradation.
	•	Medium: buffers exist but erode.
	•	Long: degradation impacts are delayed.

⸻

4.3 Sensitivity flag (screening indicator)

A sensitivity flag is computed only for prioritisation, not financial modelling.

Let:
	•	D_{VH} = 1 if any dependency has Very High strength,
	•	D_H = 1 if any dependency has High strength,
	•	B = 1 if biome sensitivity is high,
	•	W = 1 if water stress is high,
	•	Bio = 1 if biodiversity sensitivity is high.

Then:
	•	Very High sensitivity if
(D_{VH} \land B) \lor (D_{VH} \land W)
	•	High sensitivity if
D_{VH} \lor (D_H \land B)
	•	Medium sensitivity if
D_H \lor Bio

This flag supports governance focus, not quantification.

⸻

5. Assess — TNFD scenario framing (2×2 matrix)

5.1 Scenario axes

Assets are positioned on two orthogonal axes:

Axis X — Ecosystem Service Degradation (Physical Nature Risk)
X \in [0,1]

Higher values represent increasing degradation, scarcity, or disruption of ecosystem services critical to the asset.

Derived from:
	•	dependency aggregation,
	•	environmental context modifiers,
	•	service criticality.

⸻

Axis Y — Market & Non-Market Alignment (Transition Nature Risk)
Y \in [0,1]

Higher values represent stronger alignment with:
	•	regulation,
	•	market expectations,
	•	societal norms related to nature.

⸻

5.2 Quadrant assignment

Let:
	•	X \ge \theta_X ⇒ Severe degradation,
	•	Y \ge \theta_Y ⇒ High alignment.

Quadrant	Condition
Ahead of the game	X < \theta_X \land Y \ge \theta_Y
Go fast or go home	X \ge \theta_X \land Y \ge \theta_Y
Sand in the gears	X \ge \theta_X \land Y < \theta_Y
Back of the list	X < \theta_X \land Y < \theta_Y

Assumption:
Scenarios are classification frames, not probabilistic forecasts.

⸻

6. Shock grid — translating dependency into stress

6.1 Severity tiers

Each dependency is evaluated under three exogenous stress tiers:

Tier	Base severity
Expected	0.30
Adverse	0.55
Severe	0.80


⸻

6.2 Shock formulation

For each ecosystem service s, pathway p, and tier t:

\text{Shock}_{s,p,t}
=
\text{BaseSeverity}_t
\times M_{dep}
\times M_{sub}
\times M_{time}
\times M_{scenario}
\times M_{env}

Multipliers
Dependency strength M_{dep}
Very High = 1.15, High = 1.00, Medium = 0.80, Low = 0.60

Substitutability M_{sub}
Low = 1.15, Medium = 0.95, High = 0.70

Time-to-failure M_{time}
Short = 1.10, Medium = 0.95, Long = 0.80

Scenario M_{scenario}
Depends on TNFD quadrant and whether the pathway is physical or transition-driven.

Environmental M_{env}
Primarily driven by water stress and biome sensitivity.

Assumption:
A multiplicative structure approximates compounding stress without double-counting.

⸻

7. Financial impact engine

7.1 Core formulation

Financial impact is calculated as:

\text{Impact}_{EUR}
=
V \times \tau \times f(\text{Shock}) \times M_{sector} \times M_{scenario}

Where:
	•	V = asset value,
	•	\tau = transmission rate,
	•	f(\cdot) = non-linear amplification,
	•	M_{sector} = sector sensitivity,
	•	M_{scenario} = scenario modifier.

⸻

7.2 Non-linear amplification (tipping points)

To reflect ecological and operational thresholds:

f(x) = \frac{1}{1 + e^{-k(x - x_0)}}

With:
	•	k = 10,
	•	x_0 = 0.60.

Interpretation:
	•	below 0.6 → gradual cost increase,
	•	above 0.6 → rapid escalation due to loss of buffers and cascading effects.

⸻

7.3 Output structure

The engine produces:
	•	pathway-level impacts,
	•	totals by severity tier,
	•	dominant drivers,
	•	confidence ranges,
	•	explicit methodological metadata.

⸻

8. Role of AI — detailed methodological integration

8.1 Why AI is required

AI is used only where the problem is irreducibly semantic:
	1.	Evidence is fragmented across heterogeneous sources.
	2.	TNFD requires narrative explanation, not just numbers.
	3.	Adaptation and disclosure require contextual reasoning.

AI is not used for numeric risk estimation.

⸻

8.2 Separation of concerns (hard boundary)

Component	AI allowed?
Dependency mapping	❌
Scenario scoring	❌
Shock calculation	❌
Financial modelling	❌
Evidence synthesis	✅
Adaptation strategy	✅
Stakeholder narratives	✅
Quality evaluation	✅ (separate model)

This boundary is enforced at workflow level.

⸻

8.3 AI Agent 1 — Evidence Synthesizer (RAG)

Purpose:
Ground quantified risk pathways in documented real-world evidence.

Method:
	•	Retrieval-Augmented Generation (RAG),
	•	multi-query strategy aligned to LEAP steps,
	•	ecosystem-service-specific queries,
	•	scenario-specific queries.

Key rule:
The agent may explicitly state “evidence insufficient”.

The agent cannot:
	•	modify shocks,
	•	adjust financial outputs,
	•	invent causal mechanisms.

⸻

8.4 AI Agent 2 — Adaptation Strategy Generator (RAG)

Purpose:
Support TNFD “Prepare” by proposing plausible, sequenced management responses that are grounded in science based strategy frameworks, WWF guides and cost benchmarks

Constraints:
	•	uses locked quantitative outputs,
	•	actions must map to specific dependencies,
	•	strategies are illustrative, not prescriptive.

⸻

8.5 AI Agent 3 — Stakeholder Narrative Generator

Purpose:
Translate identical analysis into narratives for:
	•	CFO,
	•	risk committee,
	•	sustainability disclosures,
	•	operations.

Constraint:
No reinterpretation or recalculation allowed.

⸻

8.6 AI Evaluator — quality control

A separate evaluator model scores AI outputs on:
	•	groundedness,
	•	completeness,
	•	consistency with numeric results,
	•	honesty about uncertainty.

Failed outputs are regenerated with feedback, capped at a fixed number of attempts.

⸻

9. Explainability, auditability, and governance

The final output includes:
	•	all RAG queries used,
	•	number of retrieved evidence chunks,
	•	dependency derivation metadata,
	•	scenario methodology,
	•	evaluator scores.

This enables:
	•	internal review,
	•	third-party assurance,
	•	regulator dialogue.

⸻

10. Limitations (explicit)
	1.	Static, single-horizon analysis
	2.	No feedback from adaptation into financials
	3.	Sector-average transmission rates
	4.	No second-order supply-chain propagation
	5.	Proxy-based biodiversity representation

These limitations are scope boundaries, not omissions.

⸻

11. Intended use under TNFD

Suitable for:
	•	LEAP Assess disclosures,
	•	portfolio screening,
	•	scenario comparison,
	•	governance prioritisation.

Not suitable for:
	•	capital requirement setting,
	•	site permitting,
	•	ecological impact studies.

⸻

End of methodology

⸻

