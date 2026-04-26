# Certification Protocol — Prompt Architect v1.0.0

## What JARP_CERTIFIED Means

A prompt bearing `[JARP_CERTIFIED]` has been subjected to a complete 7-axis forensic audit and passed with **0 CRITICAL + 0 SERIOUS findings**. MODERATE and LATENT findings are documented but do not block certification.

The seal is not a guarantee of perfection. It is a guarantee of minimum production-ready quality as defined by the JARP ecosystem standard.

---

## Certification Criteria

| Criterion | Requirement |
|---|---|
| CRITICAL findings | 0 — absolute |
| SERIOUS findings | 0 — absolute |
| MODERATE findings | Documented — do not block |
| LATENT findings | Documented — do not block |
| Audit scope | All 7 axes completed |
| Auditor | THE PROMPT ARCHITECT only |

No exceptions. No partial certifications. No "certified with conditions."

---

## Certification Seal

```
[JARP_CERTIFIED: vX.Y.Z — PA-AAAAMMDD-NNN]
[AUDIT_DATE: AAAA-MM-DD]
[AUDITOR: THE PROMPT ARCHITECT]
[FINDINGS: 0 CRITICAL | 0 SERIOUS | N MODERATE | N LATENT]
[NEXT_REVIEW: upon major changes or 90 days]
```

## Certification Denial

```
[CERTIFICATION_DENIED]
[BLOCKING_FINDINGS: #N (CRITICAL) | #N (SERIOUS)]
[REQUIRED_BEFORE_RESUBMISSION: specific actions per finding]
```

---

## Expiration Conditions

| Condition | Action |
|---|---|
| Major version bump (X.0.0) | Immediate re-audit required |
| 90 days elapsed | Scheduled review recommended |
| Known model behavior change | Immediate review recommended |
| User-reported failure not in findings | Review required |

Expired certifications: `[JARP_CERTIFIED: EXPIRED]`

---

## JARP Ecosystem Certification Status

| Agent | Version | Report ID | Status |
|---|---|---|---|
| dark-strategist-agent | v2.5.1 | PA-20260426-002 | ✅ CERTIFIED |
| devil-advocate-agent | — | — | NOT_CERTIFIED |
| prompt-architect-agent | v1.0.0 | PA-20260426-001 | ✅ CERTIFIED |
