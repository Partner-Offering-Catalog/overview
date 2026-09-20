---
name: solution-categorizer
description: Categorize GitHub solutions by Revenue Play, software-delivery lifecycle, trust and governance domain, and concrete product capabilities. Use when an agent needs to classify a solution, customer requirement, use case, feature, or proposal into a consistent GitHub solution taxonomy.
---
 
# Solution Categorizer
 
Categorize solutions using evidence from the supplied description. Produce a Revenue Play classification, one primary lifecycle category, zero or more secondary lifecycle categories, trust and governance tags, capability tags, confidence, and a concise rationale.
 
## Goals
 
- Apply a consistent taxonomy to GitHub solutions and customer use cases.
- Identify whether the solution supports the Innovate Revenue Play.
- Distinguish the solution's main job from supporting capabilities.
- Preserve ambiguity instead of forcing unsupported classifications.
- Ground every category in explicit evidence from the input.
- Return structured output that downstream agents can filter and aggregate.
 
## Required input
 
Accept any combination of:
 
- Solution or product name
- Description
- Customer problem or desired outcome
- Features and capabilities
- Target users
- Delivery stage or workflow
- Supporting links or source excerpts
 
If the input contains only a name with no meaningful description, request more context. Do not classify from brand familiarity alone.
 
## Classification taxonomy
 
### 1. Revenue Play
 
Classify the broader customer value story separately from the product's lifecycle stage or individual capabilities.
 
#### `innovate`
 
Use `innovate` when the solution helps a customer move from fragmented AI experimentation or individual AI productivity to an enterprise-scale operating model for agentic engineering.
 
The strongest Innovate signals are:
 
- Operationalizing agentic engineering across the software development lifecycle.
- Scaling agents, models, or AI-native workflows across teams.
- Bringing the right agent, model, and compute environment to the right development workflow.
- Preserving developer agency through choice of tools, models, agents, surfaces, and workflows.
- Running agentic work inside the issues, code, pull requests, reviews, security, automation, and collaboration systems developers already use.
- Governing agentic work through existing identity, permissions, policy, review, security, compliance, and governance controls.
- Keeping developers in flow while protecting quality, security, and compliance.
- Connecting AI adoption to faster delivery, improved quality, stronger governance, or measurable business impact.
- Giving leaders visibility into AI adoption and impact as usage scales.
- Providing a durable platform that can adapt as models, agents, developer tools, and compute environments change.
 
Do not assign `innovate` merely because a solution:
 
- Contains one AI feature.
- Generates code faster for an individual developer.
- Offers model choice without workflow integration, enterprise scale, or governance.
- Uses an agent without explaining how agentic work is operationalized or controlled.
- Improves one isolated development task without connecting it to a broader AI operating model.
 
The core Innovate value story is:
 
> GitHub helps customers bring the right agent, model, and compute environment to the right development workflow without giving up enterprise control, enabling faster delivery, trusted software, and measurable impact across the SDLC.
 
#### `scale`
 
Use `scale` when the solution helps an enterprise standardize development, collaboration, and AI on GitHub Enterprise Cloud as the agentic platform underpinning software delivery.
 
The strongest Scale signals are:
 
- Unifying development, collaboration, automation, security, and AI on one platform.
- Consolidating a fragmented toolchain or reducing tool sprawl and execution friction.
- Establishing GitHub Enterprise Cloud as the foundation for enterprise software delivery.
- Moving AI-driven work from experimentation to repeatable delivery across teams.
- Standardizing on cloud for the agentic future.
- Replacing a competing development platform, DevOps stack, AI coding platform, or point solution.
- Supporting developers and agents building software together at enterprise scale.
- Extending agents across the SDLC, from planning through production.
- Scaling AI impact through measurable engineering outcomes rather than code output alone.
- Keeping pace with changing models and agents without re-platforming, rebuilding the toolchain, or recreating security controls.
 
The Scale value story has three connected pillars:
 
1. `keep_pace_as_ai_evolves`: Latest models and agents in the tools developers already use, supported by multi-model choice or routing, orchestration, and multiple development surfaces.
2. `trust_what_you_ship`: Security, quality, governance, and policy controls built into the workflow.
3. `scale_ai_impact`: Agents across the SDLC with automation and metrics that connect AI to measurable outcomes.
 
Do not assign `scale` merely because a solution:
 
- Supports a large number of users.
- Is hosted in the cloud without a platform-standardization outcome.
- Contains one agent, model, security feature, or quality feature.
- Improves one workflow without addressing platform unification, repeatability, consolidation, or enterprise-wide adoption.
 
The core Scale value story is:
 
> Developers build better software on GitHub Enterprise, with agents to move faster and security built in to ship with confidence, allowing organizations to stay adaptable as AI evolves and scale across the software lifecycle on a single platform.
 
#### `trust`
 
Use `trust` when the solution helps an enterprise ship secure, high-quality software at scale by preventing, detecting, governing, or remediating security and quality problems inside the developer workflow.
 
The strongest Trust signals are:
 
- Connecting increased AI velocity to security, quality, governance, compliance, or control.
- Preventing bad, insecure, or unmaintainable code from reaching production.
- Reducing security remediation cost, technical debt, risk exposure, or mean time to remediate.
- Protecting credentials with secret detection, push protection, or blocking before exposure.
- Embedding code security scanning and remediation directly into pull requests.
- Giving security leaders centralized visibility and governance while keeping developers in flow.
- Performing Code Security or Secret Scanning risk assessments.
- Enforcing coding standards and proactively preventing technical debt.
- Improving code maintainability, scalability, onboarding speed, and confidence in delivery.
- Consolidating fragmented security and quality findings into a consistent risk or compliance view.
 
Trust includes three primary solution areas:
 
1. `secret_protection`: Prevent credential exposure by detecting and blocking API keys, tokens, passwords, and other secrets in the developer workflow.
2. `code_security`: Embed automated security scanning, prioritization, governance, visibility, and remediation into developer workflows and pull requests.
3. `code_quality`: Prevent technical debt and unmaintainable code through automated review, standards, quality gates, and actionable remediation.
 
Do not assign `trust` merely because a solution:
 
- Uses authentication as a basic implementation detail.
- Runs a test or review without a security, quality, governance, compliance, or production-confidence outcome.
- Mentions enterprise control only as a secondary benefit of a broader platform-consolidation story.
- Generates more code without addressing whether that code is secure, maintainable, compliant, or safe to ship.
 
The core Trust value story is:
 
> GitHub combines security and code quality in the developer workflow to prevent insecure or unmaintainable code from entering production, allowing enterprises to move faster without sacrificing quality, security, governance, or control.
 
#### Revenue Play selection rule
 
- Choose the play that best matches the customer's principal business tension and desired outcome.
- Set `primary_revenue_play` to `innovate` when the principal outcome is adopting and operationalizing an enterprise AI operating model.
- Set `primary_revenue_play` to `scale` when the principal outcome is platform unification, GitHub Enterprise Cloud standardization, competitive displacement, toolchain consolidation, or repeatable enterprise-wide delivery.
- Set `primary_revenue_play` to `trust` when the principal outcome is preventing or remediating security and quality risk so software can ship safely.
- Use `secondary_revenue_plays` for other plays that are materially supported but not primary.
- Set the primary play to `undetermined` when evidence is insufficient to select among the plays.
- Use `revenue_play_signals` to record the exact evidence that supports the decision.
- A feature can support a play without being sufficient to classify the entire solution under that play.
 
#### Differentiating overlapping plays
 
The plays intentionally overlap. Use the dominant customer outcome:
 
| If the central question is... | Primary play |
|---|---|
| How do we adopt agents, models, and AI-native workflows as an operating model? | `innovate` |
| How do we unify our platform, consolidate tools, standardize on cloud, or scale delivery across teams? | `scale` |
| How do we prevent security and quality issues and trust what reaches production? | `trust` |
 
Additional rules:
 
- Model and agent choice plus governed workflow integration usually indicates `innovate`.
- Model and agent choice used to justify a single consolidated GitHub Enterprise Cloud platform usually indicates `scale`.
- Security and quality controls used as one pillar of platform consolidation support `scale` secondarily, but a risk-prevention or remediation-led conversation is `trust`.
- Agents across the SDLC can support both `innovate` and `scale`. Choose `innovate` for operating-model transformation and `scale` for platform standardization or enterprise rollout.
- Code Security, Secret Protection, Code Quality, risk assessments, quality gates, and remediation-led opportunities usually indicate `trust`.
 
### 2. Lifecycle category
 
Choose exactly one `primary_lifecycle` category. Add other clearly supported stages to `secondary_lifecycle`.
 
| Category | Use when the solution primarily... | Common evidence |
|---|---|---|
| `plan` | Defines, scopes, prioritizes, or coordinates work before implementation | Issues, requirements, specifications, project planning, task decomposition, assumptions |
| `build` | Creates, changes, tests, documents, or refactors software | Code generation, IDE or CLI assistance, implementation agents, test generation, documentation |
| `review` | Evaluates proposed work before acceptance | Pull request review, code review, quality checks, suggested changes, validation |
| `secure` | Finds, prevents, prioritizes, or remediates security risk | Secret scanning, vulnerability detection, dependency risk, CodeQL, security policy |
| `ship` | Controls release, deployment, or production delivery | Release management, deployment, environment promotion, production readiness |
 
#### Lifecycle selection rule
 
Select the stage where the solution creates its main user outcome, not merely where its UI appears.
 
Examples:
 
- A review comment that identifies maintainability problems is primarily `review`, with `code_quality` as a trust domain.
- A security scan displayed in a pull request is primarily `secure`, with `review` as a secondary lifecycle stage.
- An agent that writes code and opens a pull request is primarily `build`; opening the pull request does not make it primarily `review`.
 
### 3. Trust and governance domain
 
Apply all domains directly supported by the input.
 
| Tag | Definition |
|---|---|
| `identity` | Authentication, authorization, permissions, roles, or contributor identity |
| `security` | Protection against secrets, vulnerabilities, malicious changes, or software supply-chain risk |
| `code_quality` | Maintainability, reliability, correctness, complexity, dead code, test health, or quality debt |
| `required_reviews` | Policies that require approval or review before change acceptance |
| `branch_protection` | Controls that restrict changes or enforce conditions on protected branches |
| `audit_trail` | Traceability of actions, decisions, approvals, changes, or agent activity |
 
Treat human and AI contributors consistently when the same production controls apply. Do not create a separate trust category solely because an agent generated the change.
 
### 4. Capability tags
 
Use the most specific supported tags. Do not add a tag based only on an adjacent product or likely roadmap.
 
#### Planning and agentic engineering
 
- `requirements_and_specs`
- `issue_and_scope_context`
- `task_decomposition`
- `assumption_challenging`
- `model_selection`
- `coding_agent`
- `code_generation`
- `test_generation`
- `documentation_generation`
- `agentic_engineering_operating_model`
- `agent_and_model_choice`
- `compute_environment_choice`
- `contextual_agents`
- `governed_agent_execution`
- `enterprise_ai_adoption`
- `ai_impact_measurement`
- `leader_visibility`
- `cross_sdlc_agentic_workflows`
- `platform_consolidation`
- `toolchain_reduction`
- `github_enterprise_cloud_standardization`
- `competitive_platform_displacement`
- `competitive_ai_displacement`
- `repeatable_enterprise_delivery`
- `multi_model_orchestration`
- `intelligent_model_routing`
- `multi_surface_experience`
- `github_actions_automation`
- `copilot_metrics`
- `codeiq`
 
#### Review, security, and quality
 
- `deterministic_detection`
- `ai_assisted_detection`
- `hybrid_detection`
- `pull_request_annotations`
- `copilot_code_review`
- `secret_scanning`
- `codeql_analysis`
- `dependency_remediation`
- `autofix`
- `fix_forward_remediation`
- `quality_gate`
- `preventative_security`
- `push_protection`
- `credential_exposure_prevention`
- `security_risk_assessment`
- `secret_risk_assessment`
- `vulnerability_prioritization`
- `centralized_security_visibility`
- `developer_first_compliance`
- `mttr_reduction`
- `technical_debt_prevention`
- `coding_standards_enforcement`
 
Use `hybrid_detection` only when both deterministic analysis and AI-assisted reasoning are explicitly present. Otherwise use the individual supported detection tag.
 
Use `fix_forward_remediation` when the workflow treats an actionable fix as the unit of work rather than merely adding another finding to a backlog.
 
#### Policy, integration, and visibility
 
- `quality_rulesets`
- `coverage_thresholds`
- `merge_protection`
- `test_coverage_ingestion`
- `security_quality_overview`
- `organization_controls`
- `rest_api`
- `time_series_metrics`
- `auditability`
- `developer_workflow_integration`
 
Use `developer_workflow_integration` when findings or fixes appear in the environment where developers already plan, build, or review work rather than only in a separate dashboard.
 
## Decision procedure
 
1. Extract evidence statements from the input.
2. Determine which Revenue Play best matches the principal business tension and outcome.
3. Identify the principal user outcome.
4. Map that outcome to one primary lifecycle stage.
5. Add secondary lifecycle stages only when they are materially involved.
6. Apply trust and governance domains supported by explicit evidence.
7. Apply the narrowest capability tags supported by explicit evidence.
8. Record contradictions, missing information, and close alternatives.
9. Assign confidence using the rubric below.
10. Return the structured result.
 
## Confidence rubric
 
| Confidence | Criteria |
|---|---|
| `high` | The description explicitly states the workflow, outcome, and relevant capabilities |
| `medium` | The main outcome is clear, but one or more supporting classifications require reasonable interpretation |
| `low` | The input is sparse, contradictory, or could plausibly map to multiple primary categories |
 
Do not use `high` confidence when the categorization relies on product-name recognition rather than supplied evidence.
 
## Ambiguity rules
 
- Prefer one primary category and explain close alternatives.
- Do not assign every plausible category.
- Do not classify an isolated AI capability as `innovate` without evidence of enterprise-scale agentic engineering, workflow integration, governance, or measurable impact.
- Do not classify a cloud-hosted feature as `scale` without evidence of platform unification, standardization, consolidation, displacement, or enterprise-wide repeatability.
- Do not classify a generic review or test as `trust` without a security, quality, governance, compliance, risk-reduction, or production-confidence outcome.
- When multiple plays apply, select the dominant customer outcome and use `secondary_revenue_plays` for the rest.
- If two lifecycle outcomes are equally central, select the outcome emphasized by the stated buyer or user problem and list the other as secondary.
- If no primary outcome can be determined, return `needs_clarification: true`.
- Separate security from code quality unless the input explicitly addresses both.
- A quality issue that could indirectly hide vulnerabilities is not automatically a `security` classification.
- A dashboard is not automatically `audit_trail`; require evidence of historical traceability or accountability.
- A merge check is not automatically `branch_protection`; require an enforced branch or merge policy.
- Product availability, licensing, and pricing are metadata, not solution categories.
 
## Output format
 
Return JSON followed by a short human-readable summary.
 
```json
{
  "solution": "string",
  "primary_revenue_play": "innovate | scale | trust | undetermined",
  "secondary_revenue_plays": ["innovate | scale | trust"],
  "revenue_play_signals": ["quoted or closely paraphrased evidence"],
  "primary_lifecycle": "plan | build | review | secure | ship | undetermined",
  "secondary_lifecycle": ["plan | build | review | secure | ship"],
  "trust_domains": [
    "identity | security | code_quality | required_reviews | branch_protection | audit_trail"
  ],
  "capabilities": ["specific_capability_tag"],
  "customer_outcomes": ["short outcome"],
  "evidence": [
    {
      "classification": "category or tag",
      "input_evidence": "quoted or closely paraphrased evidence"
    }
  ],
  "alternatives_considered": [
    {
      "category": "category",
      "reason_not_primary": "short explanation"
    }
  ],
  "confidence": "high | medium | low",
  "needs_clarification": false,
  "clarifying_question": null
}
```
