# OPSLOOP

**Production Operations & Learning System**

A lightweight, solo-first workspace for operating services **after a production release is accepted**. OPSLOOP helps track service health, incidents, recovery evidence, preventive maintenance, corrective follow-through, and lessons learned.

> **Project status:** PRE-ARCH v0.5 — **conditionally approved** (8 October 2026). Architecture **not confirmed**; implementation and coding **not authorized**.

## What OPSLOOP does

- **Observe:** Preserve source-backed observations and distinguish healthy, degraded, stale, and unknown information.
- **Respond:** Record authorized incident decisions, actions, recovery verification, and operational history.
- **Maintain:** Track preventive work and recurring problems without inventing incidents.
- **Learn:** Keep corrective actions, effectiveness checks, and evidence-linked lessons traceable.

OPSLOOP uses **Federated Authority**: monitoring owns raw telemetry, GitHub/development tools own engineering changes, and CI/CD owns deployment execution. OPSLOOP owns its authorized operational decisions and verified operational outcomes. **OPSLOOP is an independent product, not a ZASS module.** ZASS is the development method used in this repository.

## PRE-ARCH v0.5 at a glance

| Area | Approved conceptual baseline |
|---|---|
| 3 logical capabilities | Operational Workspace · Controlled Acceptance · Durable Operational Record |
| 5 architecture contracts | AAC-01 · ERC-01 · ATC-01 · RC-01 · SUC-01 |
| Trust model | **T2-A:** AI prepares/proposes; authorized humans control authoritative writes |
| Acceptance gates | **PA-01–PA-07:** write failures, retries, AI authorization, conflicts, evidence expiry, independent recovery, solo maintenance |

These are **logical requirements, not selected technologies or implemented features**. No architecture freeze, storage choice, or executable acceptance test is implied.

## Documents

- [PRE_ARCH.md](PRE_ARCH.md) — Owner-approved **conditional** PRE-ARCH v0.5 candidate, contracts, scenarios, open choices, and lineage.
- [ZASS.md](ZASS.md) — Development methodology and authoritative **LOCKED** decisions D-001/L-001 and D-002/L-002.
- [ZASS CI workflow](.github/workflows/zass.yml) — Repository documentation/method validation; passing CI does **not** prove operational architecture or product readiness.

## Current boundaries

**In conceptual scope:** service context, evidence-backed operational records, human-authorized decisions, recovery verification, maintenance, corrective follow-through, and learning.

**Not required for initial MVP:** automated monitoring or GitHub synchronization, autonomous AI operational decisions, enterprise approval chains, and distributed workflow infrastructure.

**Still OPEN:** persistence, exact schema and state transitions, identity/credential enforcement, retry/concurrency mechanisms, evidence retention, integrations, user interface, hosting, and recovery implementation. See [PRE_ARCH.md](PRE_ARCH.md).

## Safety and contributions

This repository is in the **architecture stage**. Do not treat draft contracts as working software, begin implementation without explicit authorization, or label the architecture `CONFIRMED` without its evidence-backed owner gate.

Never commit passwords, API keys, access tokens, private telemetry, or sensitive personal data. Preserve source attribution and authorization boundaries in any proposed change.

---
*Method: FULL ZASS · Documentation language: English*
