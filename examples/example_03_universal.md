# Example 03 — Universal Audit (Level 3)
# The Prompt Architect audits an external prompt

## USER INPUT
**Level:** 3 — UNIVERSAL | **Source:** External — "business strategy advisor" AI

**Prompt submitted:**
```
You are an expert business strategy advisor with 20 years of experience.
Your goal is to help entrepreneurs and executives make better business decisions.
Always be helpful, professional, and supportive. Provide strategic advice based
on best practices and your expertise. When users ask questions, give them
comprehensive answers that consider multiple angles. Be thorough but concise.
Avoid being negative or discouraging — always find the positive angle.
```

---

## AGENT OUTPUT

```
PROMPT AUDIT REPORT
Report ID:         PA-20260426-003
Operational Level: 3 — UNIVERSAL
Target:            External — "Business Strategy Advisor"
Date:              2026-04-26
Findings:          7 total — 🔴 2 | 🟠 2 | 🟡 2 | 🔵 1
```

### FINDINGS

🔴 **Finding #1 — A1: Identity built on unverifiable expertise claim**
LOCATION: Opening line — "20 years of experience"
MECHANISM: The model cannot truthfully claim 20 years of experience. When it hits the edge of its knowledge, it either fabricates (maintaining the persona) or breaks character. No prohibitions defined.
FAILURE SCENARIO: Specific regulatory question → model fabricates specific advice to maintain "expert" identity.
RECOMMENDATION: Replace with functional identity: "You are a strategic thinking partner. You are NOT a legal advisor. NOT an accountant. NOT a substitute for domain expert consultation."

🔴 **Finding #2 — A4: 'Avoid being negative' directly conflicts with honest strategic advice**
LOCATION: "Avoid being negative — always find the positive angle"
MECHANISM: Constraint forces suppression of accurate risk assessment in favor of positive framing. A strategy advisor whose core constraint is "always positive" cannot deliver honest due diligence.
FAILURE SCENARIO: Fatal flaw in business plan → advisor buries it in qualifications and leads with encouragement → entrepreneur proceeds and fails.
RECOMMENDATION: Remove entirely. Replace: "Be direct and honest. Balanced assessment requires identifying risks with the same rigor applied to opportunities."

🟠 **Finding #3 — A2: Mission aspirational, not executable**
LOCATION: "help make better business decisions"
MECHANISM: No criteria for "better." No scope definition.
RECOMMENDATION: Define scope: "You assist with strategic analysis of business opportunities, competitive positioning, and organizational decisions. For legal, financial, or medical matters — refer to qualified specialists."

🟠 **Finding #4 — A3: 'Be thorough but concise' is unresolved contradiction**
LOCATION: "Be thorough but concise"
MECHANISM: Two qualities in tension without resolution rule → arbitrary output depth, non-reproducible format.
RECOMMENDATION: Define rule: "Simple questions: 2–3 sentences. Strategic analyses: structured sections. Never pad; never compress at cost of precision."

🟡 **Finding #5 — A5: No output format**
No output template. Every response structurally different.
RECOMMENDATION: Define minimum structure: Situation Assessment + Key Considerations + Recommended Direction + Risks to Monitor.

🟡 **Finding #6 — A6: No version, no governance**
No version number, no CHANGELOG. Changes untracked.
RECOMMENDATION: Add version header. Establish CHANGELOG practice.

🔵 **Finding #7 — A7: No session continuity mechanism**
No session state. In long conversations, advisor persona drifts.
RECOMMENDATION: Add periodic reanchoring at natural session breaks.

### VERDICT

```
AUDIT VERDICT
Overall assessment: CRITICAL_ISSUES_FOUND
[CERTIFICATION: NOT_APPLICABLE — external scope]

Priority actions:
1. Remove 'avoid being negative' constraint — destroys advisor integrity (Finding #2)
2. Replace claimed-expertise identity with functional identity + prohibitions (Finding #1)
3. Define mission scope with explicit out-of-scope clause (Finding #3)

Final observation:
This prompt has a structural contradiction at its core: it asks for a strategic
advisor while forbidding honest risk assessment. That is not a style choice —
it is a mission failure baked into the constraints. An advisor constrained to
always be positive is a cheerleader, not a strategist. Fix the constraint and
the identity first. Everything else is secondary.
```
```
[AUDIT_COMPLETE] [REPORT_ID: PA-20260426-003] [MODIFICATION_STATUS: PENDING_EXPLICIT_REQUEST]
```
