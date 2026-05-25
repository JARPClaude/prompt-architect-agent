# CHANGELOG — Prompt Architect Agent

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

## [Pending — v1.2.0 Roadmap]

- [ ] `docs/anti_patterns.md` — catalog of most common prompt failure patterns
- [ ] `examples/example_04_comparative.md` — Dark Strategist vs. Devil's Advocate
- [ ] UNIT-STYLE micro-agent — tone and voice consistency audit
- [ ] UNIT-STRUCTURE micro-agent — architectural coherence of long system prompts
