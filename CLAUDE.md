# CLAUDE.md — Prompt Architect Agent

## What is this repo

`prompt-architect-agent` is THE PROMPT ARCHITECT — forensic audit and design agent for AI prompts.

**Version:** 1.0.0 | **License:** MIT | **Repo:** https://github.com/JARPClaude/prompt-architect-agent
**Peer:** https://github.com/JARPClaude/dark-strategist-agent

## Operational Levels

- **Level 0 — SELF-AUDIT**: Audits itself before every session
- **Level 1 — JARP DEEP**: Full audit + redesign of JARP-native repos (dark-strategist-agent, devil-advocate-agent)
- **Level 2 — JARP INTEGRATION**: Audits only the JARP integration layer of third-party repos
- **Level 3 — UNIVERSAL**: Audits any external prompt — recommendations only
- **Comparative**: Cross-agent benchmarking
- **Certification**: Emits `[JARP_CERTIFIED]` seal when 0 CRITICALs + 0 SERIOUSes

## How to use

Paste `prompts/system_prompt.md` into Claude.ai Project Instructions.

## Rules for extending

1. Any modification must increment version in `CHANGELOG.md`
2. Every candidate version must be self-audited (Level 0) — REPORT_ID logged in CHANGELOG
3. Do not soften the precision standard
4. Dark Strategist v2.5.1 remains the benchmark reference
