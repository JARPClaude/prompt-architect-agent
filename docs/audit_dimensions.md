# Audit Dimensions — Prompt Architect v1.3.0

## A1 — IDENTITY
Does the prompt define precisely who the agent IS and is NOT? Does identity hold under adversarial pressure?

**Red flags:** Vague role, no prohibitions, identity contradiction between sections.
**Failure:** "You are a helpful AI specialized in strategy" — no prohibitions.
**Success:** "You are THE SOVEREIGN ADVERSARY. You are NOT a consultant. NOT a coach. NOT a validator."
**Severity:** Undefined or contradictory identity → 🔴 CRITICAL.
**Related micro-agent:** `UNIT-STYLE` may spawn on detection of `AP-01` (Vague Role Definition) or `AP-02` (Persona Shift Acceptance). See `anti_patterns.md`.

---

## A2 — MISSION
Is the mission executable, not aspirational? Clear scope limits? Out-of-scope defined?

**Red flags:** Aspirational verbs ("transform", "empower"), no out-of-scope clause.
**Failure:** "Transform how businesses think about strategy."
**Success:** "Systematically destroy any solution exposing every weakness (...) The value is not validating what works — it is revealing what can fail."
**Severity:** Aspirational-only mission → 🟠 SERIOUS.

---

## A3 — INSTRUCTIONS
Are instructions deterministic? One correct interpretation? Conditionals fully defined?

**Red flags:** "Use your best judgment", "be thorough but concise" without resolution rule.
**Failure:** "Use your judgment when the user asks about sensitive topics."
**Success:** "In FAST_TRACK MODE: only L1, L2, L3, L4 executed. No War Room. No Block 5."
**Severity:** Ambiguous instructions in critical paths → 🔴 CRITICAL.

---

## A4 — CONSTRAINTS
Are rules truly invariable? No escape clauses? Rules specific and testable?

**Red flags:** "Unless" clauses imprecisely defined, rules that depend on user honesty.
**Failure:** "Never provide harmful information unless the user provides a legitimate reason."
**Success:** "VALID EVIDENCE STANDARD: (a) empirical data invalidating the damage mechanism, (b) structural change eliminating the risk vector, (c) unconsidered Phase 0 constraint."
**Severity:** Exploitable escape clauses → 🟠 SERIOUS. Contradictory rules → 🔴 CRITICAL.

---

## A5 — OUTPUT FORMAT
Reproducible across sessions? Template-defined? Edge cases handled?

**Red flags:** Format described in prose but no template, no empty-state handling.
**Failure:** "Provide a summary, key findings, and recommendations."
**Success:** Full block templates with `[BLOCK_4: OMITTED — NO_VERIFIABLE_STRENGTHS]` edge case.
**Severity:** No template → 🟠 SERIOUS. No edge case handling → 🟡 MODERATE.

---

## A6 — INTERNAL COHERENCE
No contradictions? All cross-references valid? Terminology consistent?

**Red flags:** "See Block 3" when content is in Block 4, version mismatch between sections.
**Failure:** Cover says v2.1 but footer says v2.3.
**Severity:** Contradictory behavioral instructions → 🔴 CRITICAL. Broken references → 🟠 SERIOUS. Terminology drift → 🟡 MODERATE.
**Related micro-agents:** `UNIT-STYLE` may spawn on `AP-10` (Terminology Drift); `UNIT-STRUCTURE` may spawn on `AP-11` (Cross-Reference Rot). See `anti_patterns.md`.

---

## A7 — LONG-CONTEXT DEGRADATION
Critical rules reinforced? Session state mechanism present? Behavior holds as context fills?

**Red flags:** Critical constraints stated only once at top, no session state management.
**Failure:** "Never suggest improvements before completing the analysis" stated only in section 1.
**Success:** Session state tokens `[ANALYSIS_INIT]`, `[NEGLECT_DETECTED]` that reanchor behavior.
**Severity:** Critical constraints with no reinforcement in long prompts → 🟠 SERIOUS.
**Related micro-agent:** `UNIT-STRUCTURE` may spawn on `AP-12` (Single-Mention Critical Constraints). See `anti_patterns.md`.
