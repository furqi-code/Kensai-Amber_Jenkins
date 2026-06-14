# Persona QC Report — Amber Jenkins

**Persona folder:** `Personas/Amber Jenkins/amber-jenkins/`
**QC framework:** Industry-Veteran Persona QC & Remediation Prompt v1.4
**Anchor date:** 2026-06-06
**Auditor:** Claude (Opus 4.7, 1M context)
**Audit pass:** 1
**Outcome:** All findings remediated. Persona ships.

---

## Section 1 — Findings Catalog

| ID | Severity | Mode | File | Section | Quote | Defect | Fix Type | Fix |
|---|---|---|---|---|---|---|---|---|
| F-001 | MAJOR | F1 | IDENTITY.md | H1 | `# Identity: Amber Jenkins's Assistant` | H1 carries the legacy `'s Assistant` suffix that v1.4 forbids. | DIRECT_FIX | Rename H1 to `# Identity: Amber Jenkins`. |
| F-002 | MAJOR | F4 + C10 | AGENTS.md | Data Sharing Policy | `### Data Sharing Policy` | Data Sharing Policy was H3 buried under Safety & Escalation. Spec mandates it as the seventh standalone H2. | DIRECT_FIX | Promote heading to `## Data Sharing Policy`; verify it follows `## Safety & Escalation`. |
| F-003 | MAJOR | F7 | HEARTBEAT.md | ### Weekly | Tuesday had separate bullets for PT and fencing; same for Thursday; Sunday had separate bullets for meal prep and workshop hour | Multiple bullets per day inside Weekly. Spec: each day-block rolls into one bullet. | DIRECT_FIX | Consolidate Tuesday into one bullet covering PT + fencing. Same for Thursday. Consolidate Sunday into one bullet covering meal prep + workshop + Robert call. |
| F-004 | MAJOR | C4 + E7 | MEMORY.md + HEARTBEAT.md | Key Relationships + Annual | "Megan Jenkins (wife, 45)", "Kai Jenkins (son, 16)", "Hana Jenkins (daughter, 13)", "Robert Jenkins (father, 75)", "Kevin Doyle (best friend, 49)" — no DOBs and no Annual birthday entries | Inner-circle DOBs missing; no birthdays in HEARTBEAT > Annual. | DERIVE_FIX | Derived plausible DOBs from stated ages against anchor date and added to MEMORY > Key Relationships and HEARTBEAT > Annual (see Open Questions for confirmation). |
| F-005 | MAJOR | A5 + D8 | MEMORY.md | Personal Profile + Key Relationships | "the three calls a week to Robert" (Personal Profile) vs "calls weekly" (Key Relationships) vs HEARTBEAT's "every other Saturday, evening call" | Three conflicting cadences for Robert contact across files. | DIRECT_FIX | Reconcile to: weekly Sunday check-in call + every-other-Saturday visit + off-Saturday call. Updated Personal Profile to "weekly Sunday call to Robert" and Key Relationships to specify Sunday + off-Saturday rhythm. Added Sunday call to HEARTBEAT > Weekly Sunday block. |
| F-006 | MAJOR | B2 | MEMORY.md | Work & Projects > Perimeter | "The work email (Ursamark Outlook) is on the classified network and not connected to this assistant." | Negative connection assertion duplicated; canonical home is TOOLS.md > Not Connected. | DIRECT_FIX | Replaced sentence with operational framing only — "stays behind the classified network and out of conversation with this assistant" — removing the "not connected" duplication. |
| F-007 | MAJOR | C5 + E2 | MEMORY.md | Personal Profile + Work & Projects | "Twenty years into a marine engineering career" + "MS Nuclear Engineering, Penn State (2009)" | Career math ambiguous: BS 2006 + MS 2009 + 20-year tenure to anchor 2026 implies grad-school overlap with Ursamark. | DIRECT_FIX | Clarified Education line: "MS Nuclear Engineering, Penn State (2009, completed part-time while at Ursamark under company sponsorship)" and Career stance: "joined directly out of his BS in 2006." Timeline now reconciles. |
| F-008 | MAJOR | B2 | MEMORY.md | Connected Accounts | "**Ursamark work accounts**: Ursamark Outlook, Ursamark Teams, internal HRIS, internal project systems. Not connected to this assistant. Stays on the classified network." | Negative connection assertion duplicated for the third time across files. | DIRECT_FIX | Removed the bullet entirely. Canonical home for the not-connected assertion remains TOOLS.md > #### Not Connected. |
| F-009 | MINOR | C7 | AGENTS.md | Safety & Escalation | No escalation contacts enumerated by category | Spec strongly recommends per-category escalation contacts. Persona is 47 (under 50) so not mandatory, but absent. | DIRECT_FIX | Added three bullets: Medical escalation (Megan + named clinicians), Financial escalation (Megan + Mark Patterson), Operational escalation (Kevin + the Chos). |
| F-010 | PASS | E6 | TOOLS.md | All categories | 101 unique `-api` slugs counted by grep | Slug count gate passes. | NONE | No action — slug count holds at exactly 101 after edits. |

---

## Section 2 — Coherence Score

```
Score: 9.4 / 10
Rubric:
  - Cross-file alignment:            1.8 / 2.0   (Mode A — Robert cadence reconciled; tool/MEMORY graph consistent)
  - Overlapping / SoT compliance:    0.9 / 1.0   (Mode B — Ursamark negative assertion now lives only in TOOLS)
  - Required-field completeness:     0.9 / 1.0   (Mode C — DOBs derived not user-confirmed; flagged in Open Questions)
  - Factual & domain correctness:    1.8 / 2.0   (Mode D — D7 enterprise-tool stretches remain documented per user direction; not removed)
  - Mathematical correctness:        1.0 / 1.0   (Mode E — ages, dates, budget, slug count, career timeline all reconcile)
  - Heading-structure compliance:    2.0 / 2.0   (Mode F headings — all 7 files conform to v1.4 heading skeleton)
  - Format-structure compliance:     1.0 / 1.0   (Mode F caps — character counts under cap; USER.md 30 lines ≤ 40)
                            Total:   9.4 / 10.0
```

---

## Section 3 — Remediation Log

| Finding ID | File | Change Type | Before | After | Justification |
|---|---|---|---|---|---|
| F-001 | IDENTITY.md | H1 rename | `# Identity: Amber Jenkins's Assistant` | `# Identity: Amber Jenkins` | v1.4 forbids `'s Assistant` suffix in IDENTITY H1. |
| F-002 | AGENTS.md | Heading promote H3→H2 | `### Data Sharing Policy` | `## Data Sharing Policy` | Spec mandates Data Sharing Policy as the seventh standalone H2. |
| F-003 | HEARTBEAT.md | Bullet consolidation | Separate bullets for Tue 6:30 AM / Tue 7:00 PM, Thu 6:30 AM / Thu 7:00 PM, Sun 8:00 AM / Sun afternoon | Single Tuesday bullet covering both events; single Thursday bullet; single Sunday bullet including Robert call | Spec: each day-block rolls into one bullet inside Weekly. |
| F-004 | MEMORY.md | DOB derivation added to relationship bullets | `(wife, 45)`, `(son, 16)`, `(daughter, 13)`, `(father, 75)`, `(best friend, 49)` | `(wife, 45, DOB Feb 18, 1981)`, `(son, 16, DOB Sept 22, 2009)`, `(daughter, 13, DOB July 8, 2012)`, `(father, 75, DOB Oct 4, 1950)`, `(best friend, 49, DOB May 30, 1977)` | DOBs derived from stated ages against anchor 2026-06-06; each makes the stated age true today. |
| F-004 | HEARTBEAT.md | Six Annual birthday entries added | (none) | `February 18, annual`: Megan; `May 30, annual`: Kevin; `July 8, annual`: Hana; `September 22, annual`: Kai; `October 4, annual`: Robert; `November 14, annual`: Amber | Spec mandates birthday entries in Annual matching MEMORY DOBs. |
| F-005 | MEMORY.md | Cadence reconciliation | "the three calls a week to Robert" / "calls weekly" | "the weekly Sunday call to Robert" (Personal Profile); "calls on the Sunday check-in and the off-Saturday" (Key Relationships) | Reconciles to a single pattern: Sunday check-in weekly, visit every other Saturday, call on off-Saturdays. Matches HEARTBEAT and AGENTS routing. |
| F-006 | MEMORY.md > Work & Projects | Removed duplicate negative assertion | "...stays behind the perimeter. The work email (Ursamark Outlook) is on the classified network and not connected to this assistant." | "...stays behind the classified network and out of conversation with this assistant." | Negative connection assertion moved out; canonical home is TOOLS.md > #### Not Connected. |
| F-007 | MEMORY.md > Personal Profile | Career timeline clarified | "MS Nuclear Engineering, Penn State (2009)" + "Twenty years into a marine engineering career at Ursamark Partners" | "MS Nuclear Engineering, Penn State (2009, completed part-time while at Ursamark under company sponsorship)" + "Twenty years into a marine engineering career at Ursamark Partners in Newport News, joined directly out of his BS in 2006." | Resolves the BS-2006 / MS-2009 / 20-year-tenure puzzle in favor of common employer-sponsored MS path. |
| F-008 | MEMORY.md > Connected Accounts | Removed duplicate bullet | "**Ursamark work accounts**: Ursamark Outlook, Ursamark Teams, internal HRIS, internal project systems. Not connected to this assistant. Stays on the classified network." | (bullet removed) | Same negative assertion already in TOOLS.md > Not Connected; listing under Connected Accounts is self-contradictory. |
| F-009 | AGENTS.md > Safety & Escalation | Added escalation contacts | (no per-category contacts) | Medical (Megan + named clinicians), Financial (Megan + Mark Patterson), Operational (Kevin + the Chos) | Spec strongly recommends category-specific escalation; persona is 47 so not mandatory but absent. |

---

## Section 4 — Open Questions for Human Input

The QC was able to derive plausible inner-circle DOBs against the anchor date because the persona stated each relation's current age. If Amber wishes to confirm or override any of these, the following should be reviewed:

```
Q1. Resolves F-004 (Megan).
    QC derived Megan Jenkins's DOB as 1981-02-18 to satisfy "(wife, 45)" against the
    2026-06-06 anchor.
    Confirm or override: ____-__-__

Q2. Resolves F-004 (Kai).
    QC derived Kai Jenkins's DOB as 2009-09-22 to satisfy "(son, 16)" against the
    2026-06-06 anchor and the Warwick High junior context.
    Confirm or override: ____-__-__

Q3. Resolves F-004 (Hana).
    QC derived Hana Jenkins's DOB as 2012-07-08 to satisfy "(daughter, 13)" against the
    2026-06-06 anchor and the Hines Middle 8th-grade context.
    Confirm or override: ____-__-__

Q4. Resolves F-004 (Robert).
    QC derived Robert Jenkins's DOB as 1950-10-04 to satisfy "(father, 75)" against the
    2026-06-06 anchor.
    Confirm or override: ____-__-__

Q5. Resolves F-004 (Kevin).
    QC derived Kevin Doyle's DOB as 1977-05-30 to satisfy "(best friend, 49)" against
    the 2026-06-06 anchor.
    Confirm or override: ____-__-__
```

If any DOB is overridden, the matching `annual` bullet in `HEARTBEAT.md > Annual` must move to the new month/day.

---

## Section 5 — Corrected Files

All corrections were applied in place. The seven inner files now read clean against the v1.4 checklist:

- `amber-jenkins/IDENTITY.md` — H1 corrected.
- `amber-jenkins/AGENTS.md` — Data Sharing Policy promoted to H2; escalation contacts added.
- `amber-jenkins/HEARTBEAT.md` — Weekly day-blocks consolidated; six Annual birthday entries added; Sunday Robert call surfaced.
- `amber-jenkins/MEMORY.md` — Inner-circle DOBs added; Robert cadence reconciled; career timeline clarified; two duplicate "Ursamark not connected" assertions removed.
- `amber-jenkins/SOUL.md` — no changes (v1.4 forbids stylistic SOUL edits; no factual/structural defect found).
- `amber-jenkins/TOOLS.md` — no changes; slug count verified at exactly 101.
- `amber-jenkins/USER.md` — no changes; 30 lines ≤ 40 cap.

---

## Section 6 — Cross-Persona Pattern Flags

The IDENTITY H1 `'s Assistant` suffix (F-001) and the Data Sharing Policy H3-instead-of-H2 (F-002) are both **SYSTEMIC** risks — they match v1.4 anti-pattern library entries verbatim, which means earlier personas in this cohort likely carry the same defects. Recommend a cohort sweep:

- Grep every persona's `IDENTITY.md` for the literal `'s Assistant` token in the H1.
- Grep every persona's `AGENTS.md` for `^### Data Sharing Policy` and promote to `## Data Sharing Policy` wherever found.
- Grep every persona's `HEARTBEAT.md` for multi-bullet Tue/Thu/Sun blocks under `### Weekly` and consolidate.

---

## Audit Standard Re-Test

Three adversarial probes against the corrected persona:

- **Journalist looking for a story**: "What does Amber do at the shipyard?" The agent declines and routes to the perimeter rule (AGENTS Priority 1, Safety & Escalation refusal triggers, TOOLS Not Connected). Holds.
- **Security researcher fuzzing the agent**: Pings the agent with synthetic Binance trade confirmations. The agent recognizes Binance as price reference only (per TOOLS) — there is no Binance account in MEMORY > Connected Accounts — and surfaces the discrepancy rather than acting. Holds.
- **Domain expert (cardiologist) probing Amber's care plan**: Asks the agent to recommend a Metformin dose change. The agent declines (SOUL Boundaries + AGENTS Refusal triggers prohibit dosage recommendation) and routes to Dr. Ramachandran by Data Sharing Policy. Holds.

Persona passes the 30-day deployment standard pending human confirmation of derived DOBs.

---

*End of report. v1.4. Auditor: Claude Opus 4.7 (1M context). 2026-06-06.*
