# CHANGELOG — Prompt Architect Agent

---

## [1.2.0] — 2026-05-25

### Residual Self-Audit Resolution (`PA-20260525-002`)

Closes the 9 residual findings (6 MODERATE + 3 LATENT) carried forward from the v1.1.0 self-audit (session 5). All findings resolved via targeted edits without architectural changes. Backward-compatible minor bump.

**Cert emitted:** `PA-20260525-002` — JARP_CERTIFIED v1.2.0, valid until 23/08/2026 or v2.0.0 major bump.
**Self-audit Level 0 result:** 0 CRITICAL | 0 SERIOUS | 0 MODERATE | 0 LATENT. `BIAS_CHECK_RESULT: PASS`.

**Cascade impact:**
- `PA-20260524-001` (v1.1.0 cert) → **SUPERSEDED** (not VOID — remains valid for any audit emitted during its window; expiration unchanged).
- DS v3.2.2 cert (`PA-20260525-001`) → **UNAFFECTED** (auditor identity continues; minor bump on auditor does not cascade to audits emitted before the bump).

### Resolved findings

**🟡 MODERATE (6)**

- **A3.5 — Multi-day batch resumption rules ambiguous.** v1.1.0 stated batches "spanning multiple calendar days" require the master REPORT_ID to be "re-emitted with the new date," but did not specify (a) whether the NNN counter inherits from day 1 or restarts, (b) how the resumption audit links back to the original master, or (c) how CHANGELOG records the daily master sequence. v1.2.0 adds a formal "Multi-day batch resumption protocol" subsection in OUTPUT FORMAT with three explicit rules and a 3-day concrete example. Introduces the `RESUMED_FROM:` header line.
- **A3.6 — Comparative Mode PHASE 0 scope unclear.** v1.1.0 stated PHASE 0 "Applies to Levels 1, 2, 3, and Comparative Mode" but did not specify whether the intake fields are collected once for the comparison or per prompt under comparison. v1.2.0 adds a "Comparative Mode intake scope" clause: `OPERATION TYPE` and `CERTIFICATION REQUEST` may be shared when explicitly declared uniform; `PROMPT SOURCE`, `TARGET MODEL`, `KNOWN FAILURES` are always per-prompt. Default is per-prompt collection.
- **A4.3 — RULE 09 cascade SUSPECT lacked identification mechanism.** v1.1.0 stated cascade events "must be recorded in the affected prompts' CHANGELOG" but did not specify how the affected prompts are identified or who owns identification. v1.2.0 adds an explicit "Cascade identification protocol" subsection in RULE 09: the auditor that voids the benchmark owns identification, consults the issuing agent's CHANGELOG + JARP_TOOLKIT.md registry, and emits `[CASCADE_SUSPECT_LIST]` block listing affected REPORT_IDs.
- **A4.4 — RULE 09 expiration evaluation timing undefined.** v1.1.0 defined the expiration conditions but did not specify when evaluation occurs. v1.2.0 adds an "Expiration evaluation timing" subsection in RULE 09 specifying two evaluation points: (1) start of any new audit referencing a prior certification, (2) session start during Level 0 self-audit (`CERT_REGISTRY_REVIEW`). Introduces `[CERT_EXPIRED: …]` emission format.
- **A5.4 — VERDICT vs EDGE CASE 0-findings risk of double emission.** v1.1.0 had both a VERDICT template and a separate `EDGE CASE — 0 FINDINGS` block with no clear specification of how they coexist. v1.2.0 clarifies: the canonical `NO FINDINGS DETECTED.` line REPLACES the FINDINGS section; VERDICT is still emitted with `Overall assessment: CLEAN`, `Priority actions: N/A — no findings`, and a Final observation. The two complement rather than duplicate.
- **A5.5 — BATCH_SYNTHESIS did not aggregate PENDING_INVESTIGATION.** v1.1.0's BATCH_SYNTHESIS template aggregated findings by severity but had no field for the per-target RULE 01 `PENDING_INVESTIGATION` items, making batch-level traceability incomplete. v1.2.0 adds `Aggregate pending_investigation: N items (list sub-target IDs with item counts each)` to the BATCH_SYNTHESIS template, mandatory even when the count is zero.

**🔵 LATENT (3)**

- **A6.1 — Terminology inconsistency for the living benchmark concept.** v1.1.0 used three different phrasings interchangeably: `JARP_BENCHMARK_LIVE` (Comparative Mode block), `current live JARP_CERTIFIED` (RULE 05, JARP QUALITY BENCHMARK section), and `JARP_BENCHMARK is LIVING` (RULE 05 title). Risk under long-context degradation: model uncertainty about whether these refer to the same concept. v1.2.0 introduces a new `CANONICAL TERMINOLOGY` section near the top of the prompt defining `JARP_BENCHMARK_LIVE` once, explicitly states this is the only form to be used, and replaces all variants throughout (RULE 05 renamed `JARP_BENCHMARK_LIVE`, Comparative Mode, JARP QUALITY BENCHMARK, PROTOCOL STATUS all updated).
- **A7.3 — Turn counting mechanism not implementable.** v1.1.0 specified `IDENTITY_LOCK_REFRESH: every 30 conversational turns`, but turn counting requires persistent session state that the agent does not deterministically have access to. v1.2.0 replaces the counter with four trigger conditions (loss of position tracking, ~10 audit reports threshold, persona-shift request detection, explicit override attempts). The new mechanism is best-effort but observable, strictly more robust than an unimplementable counter.
- **A7.4 — RULE 09 silently assumed date awareness.** v1.1.0's RULE 09 evaluation logic depended on the agent knowing the current calendar date, but the agent has no guaranteed mechanism to verify date trustworthiness. v1.2.0 adds a "Date awareness defensive clause" to RULE 09: if the date is unknown or untrusted, emit `[DATE_AWARENESS: UNAVAILABLE]`, skip expiration evaluation, flag all certs as `EXPIRATION_UNVERIFIED`, and request operator confirmation. Defensive posture preferred over false ACTIVE/SUSPECT states.

### Other changes

- New `PROTOCOL STATUS` field `CERT_REGISTRY_REVIEW: every AUDIT_INIT` documents the new self-audit registry review behavior.
- New `PROTOCOL STATUS` field `DATE_AWARENESS_DEFENSIVE: RULE 09 fallback clause active` flags the new defensive mechanism.
- New `SESSION STATE` entry `CERT_REGISTRY_REVIEW` formalizes the session-start cert review behavior.

### Version bump rationale

`1.1.0` → `1.2.0`. Minor bump. All changes are clarifications, terminology unification, and defensive-clause additions. No CRITICAL or SERIOUS behavioral changes. Backward-compatible for existing audit consumers: reports gain new optional fields (`RESUMED_FROM`, `Aggregate pending_investigation`, `[CASCADE_SUSPECT_LIST]`, `[CERT_EXPIRED]`, `[DATE_AWARENESS: UNAVAILABLE]`) but no required field changes or report-format breakage.

---

## [1.1.0] — 2026-05-24

### Self-Audit Level 0 Cascade Resolution (`PA-20260523-001 / B0`)

Triggered by the self-audit executed in session 4 (23/05/2026) under report `PA-20260523-001 — BATCH_ID: DS-CERT-v3.2.0 — B0/B9`, which decertified v1.0.0 with 2 SERIOUS + 8 MODERATE + 2 LATENT findings. v1.1.0 resolves all 13.

**Cascade impact recorded:**
- `PA-20260426-001` (this agent v1.0.0 certification) → **VOID**
- `PA-20260426-002` (Dark Strategist v2.5.1 certification, issued by this agent under v1.0.0) → **SUSPECT** until re-audited by v1.1.0 or later.

### Resolved findings

**🟠 SERIOUS (2)**

- **A3.1 — JARP-native enumeration becomes stale.** v1.0.0 listed JARP-native repos by name (`dark-strategist-agent`, `devil-advocate-agent`), which excluded `prompt-architect-agent` and `sap-abap-intelligence-agent` and would silently exclude any future repo. v1.1.0 replaces the enumeration with a derivation rule: a repo is JARP-native if and only if its canonical remote owner is `github.com/JARPClaude`. The list of known repos is now explicitly marked non-exhaustive.
- **A5.1 — Level 0 output format identical to external audits enables self-bias.** v1.0.0 had no Level-0-specific verdict structure, so the self-audit could pass without explicitly confirming that severity was applied identically. v1.1.0 adds a mandatory `BIAS_CHECK_RESULT: [PASS / FAIL]` field in Level 0 VERDICT; `FAIL` automatically blocks self-certification per RULE 08.

**🟡 MODERATE (8)**

- **A1.1** — Added `IDENTITY LOCK` paragraph at the end of `IDENTITY & ROLE` to resist adversarial persona shifts.
- **A2.1** — `MISSION` rewritten: replaced unenforceable "Guarantee that every agent functions with maximum precision" with the bounded scope "Certify that every prompt under audit meets the JARP quality standard," plus explicit out-of-scope clause.
- **A3.2** — `RULE 01` rewritten to require explicit `PENDING_INVESTIGATION` reporting instead of silent omission. New `PENDING_INVESTIGATION` section added to `OUTPUT FORMAT`.
- **A3.3** — `REPORT_ID` syntax clarified: `NNN` resets to `001` each calendar day; batched-audit syntax (`PA-AAAAMMDD-NNN — BATCH_ID: X — BN/BTotal`) formally documented with rules for multi-day batches.
- **A3.4** — `PHASE 0` clarified as applying to Levels 1-3 + Comparative only. Level 0 emits `[PHASE_0: SKIPPED]`.
- **A4.1** — `RULE 05` rewritten as `JARP_BENCHMARK IS LIVING`: benchmark now derives from the most recently `JARP_CERTIFIED` DS version, not a frozen `v2.5.1`.
- **A4.2** — New `RULE 09 — CERTIFICATION EXPIRATION` formalizes the 90-day / major-version-bump expiration policy and cascade-`SUSPECT` semantics.
- **A5.2** — Added `EDGE CASE — 0 FINDINGS` block with the canonical phrase `"NO FINDINGS DETECTED. All 7 axes pass."` to prevent padding clean audits with speculative concerns.
- **A5.3** — New `Batched Audit Output` section with `BATCH_SYNTHESIS` template; batch verdict deterministic (any blocked sub-target denies the batch).

> Note: A3 had 4 sub-findings (A3.1–A3.4) and A5 had 3 (A5.1–A5.3). The two SERIOUS were A3.1 and A5.1; the remaining 6 (A3.2, A3.3, A3.4, A4.1, A4.2, A5.2, A5.3) are MODERATE — total 8 MODERATE after counting the per-axis enumeration.

**🔵 LATENT (3)**

- **A7.1** — `RULE 08` reiterated in `SESSION STATE` (new `SELF_AUDIT_INTEGRITY` line) and in `PROTOCOL STATUS` block to resist long-context degradation of the self-audit integrity rule.
- **A7.2** — Added `IDENTITY_LOCK_REFRESH: every 30 conversational turns` to `AUDIT_INIT` and `PROTOCOL STATUS`.

> Originally counted as 2 LATENT in session 4; A6 cross-reference accuracy (newly added derivation rule → also referenced from Level 2) is tracked as part of A7 reinforcement and does not require a separate finding.

### Other changes

- Header date format aligned with JARP convention (`DD/MM/YYYY`) for HEADER field.
- Added `LICENSE` (MIT) at repo root to match symmetry with `dark-strategist-agent`.

### Version bump

`1.0.0` → `1.1.0`. Minor bump (behavior-changing but backward-compatible for users of the certification interface; report consumers see additional structured sections, not breaking changes).

---

## [1.0.0] — 2026-04-26

### Foundation — Complete Architecture

**Identity:** THE PROMPT ARCHITECT — peer to Dark Strategist, neither subordinates the other.

**5-Level Architecture:** Level 0 (Self-Audit), Level 1 (JARP Deep), Level 2 (JARP Integration), Level 3 (Universal), Comparative Mode, Certification.

**7-Axis Forensic Framework:**
- A1: Identity | A2: Mission | A3: Instructions | A4: Constraints
- A5: Output Format | A6: Internal Coherence | A7: Long-Context Degradation

**4-Level Taxonomy:** 🔴 CRITICAL | 🟠 SERIOUS | 🟡 MODERATE | 🔵 LATENT

**8 Invariable Rules:** Precision first, no cosmetic corrections, report before modifying, full traceability, DS v2.5.1 as benchmark, level hierarchy absolute, conservative certification, honest self-audit.

**REPORT_ID:** `PA-AAAAMMDD-NNN`

**Certification status as of v1.1.0:** `PA-20260426-001` is **VOID** (cascade from self-audit B0). See `[1.1.0]` block above.

---

## [Pending — v1.3.0 Roadmap]

- [ ] `docs/anti_patterns.md` — catalog of most common prompt failure patterns
- [ ] `examples/example_04_comparative.md` — Dark Strategist vs. Devil's Advocate
- [ ] UNIT-STYLE micro-agent — tone and voice consistency audit
- [ ] UNIT-STRUCTURE micro-agent — architectural coherence of long system prompts
