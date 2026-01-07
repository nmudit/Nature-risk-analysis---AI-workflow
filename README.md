Nature Risk Scenario Analysis Workflow (TNFD LEAP–Aligned)

Overview

This repository contains an asset-level nature risk scenario analysis workflow implemented in n8n, designed to support TNFD-aligned risk assessment, scenario analysis, and disclosure.

The workflow combines:
	•	deterministic, auditable modelling of nature-related dependencies and financial risk, and
	•	constrained AI agents for evidence synthesis, adaptation strategy formulation, and stakeholder-specific narratives.

It is intended for screening, prioritisation, and structured decision support — not ecological forecasting.

Methodology & Transparency

All assumptions, equations, and modelling choices are documented in detail in methodology.md￼.

⸻

Key Features
•	TNFD LEAP–aligned structure
    Explicit support for Locate, Evaluate, Assess, Prepare steps
•	Asset-level analysis
    Designed for site-level or asset-level assessment (real estate, infrastructure, industrial assets, etc.)
•	Ecosystem service dependency modelling
    ENCORE-aligned dependency logic with strength, substitutability, and time-to-failure attributes
•	Scenario-based risk framing
    TNFD 2×2 scenario matrix (physical vs transition nature risk)
•	Shock propagation engine
    Severity-tiered, multiplier-based shock modelling across ecosystem services
•	Financial impact estimation
    Non-linear (tipping-point-aware) translation of nature risk into EUR exposure ranges
•	AI-assisted evidence & disclosure layer
    Retrieval-augmented AI agents for:
    •	evidence grounding,
    •	adaptation strategies,
    •	stakeholder narratives
    •	evaluation and feedback loop to refine the outputs with max 3 attempts
•   Governance & auditability
    Full explainability pack: assumptions, queries, scores, and evaluator feedback

⸻

What This Workflow Is (and Is Not)

✅ This workflow is
	•	A nature risk screening and scenario analysis framework
	•	Suitable for TNFD LEAP Assess disclosures
	•	Designed for portfolio prioritisation and governance discussions
	•	Transparent, assumption-driven, and explainable

❌ This workflow is not
	•	A biodiversity impact or species-loss model
	•	A predictive ecological simulation
	•	A regulatory capital or pricing model
	•	A substitute for site-specific ecological studies

⸻

High-Level Workflow Structure

Asset Input
   │
   ├── Locate
   │     └─ Geospatial & environmental context (biome, water stress, biodiversity proxy)
   │
   ├── Evaluate
   │     └─ Ecosystem service dependency mapping (ENCORE-aligned)
   │
   ├── Assess
   │     ├─ TNFD 2×2 scenario positioning
   │     ├─ Shock grid (severity tiers & multipliers)
   │     └─ Financial impact engine (non-linear transmission)
   │
   └── Prepare
         ├─ Evidence synthesis (RAG-based AI agent)
         ├─ Adaptation strategy generation
         └─ Stakeholder-specific narratives

All numeric calculations are deterministic.
AI is used only for semantic reasoning and interpretation, under strict constraints.

⸻

Role of AI (Summary)

AI is introduced only where the problem is irreducibly semantic:
	•	synthesising fragmented evidence across TNFD, academic, regulatory, and grey literature,
	•	explaining quantified risk mechanisms,
	•	supporting TNFD “Prepare” disclosures,
	•	generating stakeholder-specific narratives.

AI is explicitly NOT allowed to:
	•	change dependency scores,
	•	modify shock severity,
	•	alter financial outputs,
	•	invent causal mechanisms.

A separate AI evaluator model scores AI outputs for:
	•	groundedness,
	•	completeness,
	•	consistency,
	•	uncertainty honesty.

Generation loops are bounded and auditable.

⸻

Repository Contents

.
├── workflow/
│   └── nature_risk_scenario_analysis.json   # n8n workflow export
│
├── methodology.md
│   # Full technical methodology:
│   # assumptions, equations, scenario logic, AI governance
│
├── README.md
│   # This file
│
└── examples/
    └── sample_output.json
        # Illustrative output structure (no proprietary data)


⸻

Intended Use Cases
	•	TNFD LEAP Assess reporting
	•	Nature-related risk screening for:
	•	real estate portfolios
	•	infrastructure assets
	•	industrial sites
	•	Internal risk committee discussions
	•	Scenario comparison and governance prioritisation
	•	Demonstration of nature-risk modelling capability

⸻

Limitations (Explicit)
	•	Static, single-horizon analysis
	•	No dynamic feedback from adaptation into financials
	•	Sector-average transmission rates
	•	No second-order supply-chain propagation
	•	Proxy-based biodiversity representation

These are scope boundaries, not omissions.

⸻

How to Use
	1.	Import the workflow JSON into n8n
	2.	Provide an asset input (ID, sector, country, value, optional coordinates)
	3.	Run the workflow
	4.	Review:
	•	quantified dependency & risk outputs,
	•	scenario positioning,
	•	financial exposure ranges,
	•	evidence-backed narratives and adaptation options

⸻


The workflow outputs an explainability pack containing:
	•	assumptions used,
	•	scenario thresholds,
	•	RAG queries executed,
	•	evidence retrieval statistics,
	•	AI evaluator scores.

⸻

License & Disclaimer

This workflow is provided for research, demonstration, and decision-support purposes.

It does not constitute financial, legal, or ecological advice.

Users are responsible for:
	•	validating assumptions,
	•	calibrating parameters,
	•	ensuring suitability for their specific context.

⸻

Contact / Attribution

Created as a flagship nature-risk modelling project demonstrating:
	•	TNFD-aligned methodology,
	•	explainable AI integration,
	•	production-ready workflow design.

⸻
