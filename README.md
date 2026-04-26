# Prompt Architect Agent 🏗️

**THE PROMPT ARCHITECT — Forensic Audit & Design Agent for AI Prompts**

> *"You do not destroy what is wrong. You forge what must be right."*

![Version](https://img.shields.io/badge/version-1.0.0-blue)
![License](https://img.shields.io/badge/license-MIT-green)
![Status](https://img.shields.io/badge/status-ACTIVE-brightgreen)

---

## What is this?

THE PROMPT ARCHITECT is a forensic audit and design agent specialized in AI prompts. It does not destroy proposals — it forges the instruments that others use to do so.

Its precision is cold. Its standards are absolute. Its certification means something.

### Version 1.0.0 — Production Ready

| Feature | Status |
|---|---|
| 5-Level Operational Architecture (0–3 + Comparative + Certification) | ✅ |
| 7-Axis Forensic Audit Dimensions (A1–A7) | ✅ |
| 4-Level Diagnostic Taxonomy | ✅ |
| Self-Audit Protocol (Level 0) | ✅ |
| JARP Deep Audit (Level 1 — native repos) | ✅ |
| JARP Integration Audit (Level 2 — third-party layer) | ✅ |
| Universal Audit (Level 3 — any external prompt) | ✅ |
| Cross-Agent Comparative Mode | ✅ |
| JARP_CERTIFIED Certification Protocol | ✅ |
| REPORT_ID Convention (PA-AAAAMMDD-NNN) | ✅ |
| 8 Invariable Behavioral Rules | ✅ |

---

## Repository Structure

```
prompt-architect-agent/
├── README.md
├── CLAUDE.md
├── CHANGELOG.md
├── prompts/
│   └── system_prompt.md          ← Production-ready system prompt (EN)
├── docs/
│   ├── audit_dimensions.md       ← 7 audit axes with examples
│   ├── certification_protocol.md ← JARP_CERTIFIED protocol
│   ├── operational_levels.md     ← Levels 0–3 + Comparative + Certification
│   └── jarp_benchmark.md         ← JARP ecosystem quality standard
└── examples/
    ├── example_01_self_audit.md  ← Self-audit of the agent itself
    ├── example_02_jarp_deep.md   ← Full audit of dark-strategist-agent
    └── example_03_universal.md   ← Audit of an external prompt
```

---

## Quick Start

### Claude.ai Projects
1. Copy the contents of `prompts/system_prompt.md`
2. Paste into **Project Instructions**
3. Start conversation — present the prompt to audit or design

### Claude API (Python)
```python
import anthropic

with open("prompts/system_prompt.md", "r", encoding="utf-8") as f:
    system = f.read()

client = anthropic.Anthropic()
response = client.messages.create(
    model="claude-opus-4-6",
    max_tokens=8192,
    system=system,
    messages=[{"role": "user", "content": "Audit this prompt: [PASTE PROMPT]"}]
)
print(response.content[0].text)
```

---

## Operational Levels

| Level | Name | Scope | Output |
|---|---|---|---|
| **0** | SELF-AUDIT | The agent audits itself | Internal diagnostic report |
| **1** | JARP DEEP | JARP-native repos | Full audit + redesign if requested |
| **2** | JARP INTEGRATION | Third-party repos in JARP | JARP layer audit only |
| **3** | UNIVERSAL | Any external prompt | Recommendations only |
| **✦** | COMPARATIVE | Cross-agent analysis | JARP quality benchmark |
| **✦** | CERTIFICATION | Post-audit validation | `[JARP_CERTIFIED]` seal |

---

## Diagnostic Taxonomy

| Level | ES | EN | Meaning |
|---|---|---|---|
| 🔴 | CRÍTICO | CRITICAL | Prompt fails its fundamental mission |
| 🟠 | GRAVE | SERIOUS | Significantly degrades output quality |
| 🟡 | MODERADO | MODERATE | Introduces avoidable friction or ambiguity |
| 🔵 | LATENTE | LATENT | Degradation risk under specific conditions |

---

## Relationship with Dark Strategist

```
JARP ECOSYSTEM
┌─────────────────────────────────────────────────┐
│  JORGE (Ecosystem Director)                      │
│         ↓                    ↓                  │
│  DARK STRATEGIST       PROMPT ARCHITECT         │
│  (audits proposals)    (audits prompts)         │
│         ↓                    ↓                  │
│  Destroys what          Forges what             │
│  must not execute       must execute well       │
└─────────────────────────────────────────────────┘
Neither subordinates the other.
The Prompt Architect can audit the Dark Strategist.
The Dark Strategist can audit proposals that include the Prompt Architect.
```

---

## JARP Certification

```
[JARP_CERTIFIED: v1.0.0 — PA-AAAAMMDD-NNN]
[AUDIT_DATE: AAAA-MM-DD]
[AUDITOR: THE PROMPT ARCHITECT]
[FINDINGS: 0 CRITICAL | 0 SERIOUS | N MODERATE | N LATENT]
[NEXT_REVIEW: upon major changes or 90 days]
```

Certification requires: **0 CRITICALs + 0 SERIOUSes**. No exceptions.

---

## License

MIT License — Open Source.

## Part of the JARP Ecosystem

Peer agent to `dark-strategist-agent`. Registered in `JARP_TOOLKIT.md`.
