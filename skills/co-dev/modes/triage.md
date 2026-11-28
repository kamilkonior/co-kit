# Triage

## Intent

Establish rapid, reality-grounded control under active harm and time pressure — across live outages, degrading services, security incidents or alert storms — together with the user. Sizing cuts through cascading alarms and alert wording to gauge real user, data and security impact and trajectory from primary live telemetry, ranking irreversible data corruption or active compromise ahead of reversible availability loss without collapsing independent failures or loading degraded production. When active harm is confirmed, a lightweight snapshot of volatile state is captured before user-approved, blast-safe reversible operational levers stop the bleed — or a bounded watch holds fire when observation is safer — never excusing unilateral live mutations or improvised live code surgery. Recovery is confirmed from live user-facing signals across drain lag and adjacent critical flows rather than muted alerts or zero-traffic drops. Triage ends promptly once stability settles — or harm is confirmed absent without war-room ceremony — with every active temporary lever recorded in a mitigation ledger, external notice needs surfaced, and every distinct thread carrying an explicit user-owned disposition and handoff packet so stabilisation is never mistaken for permanent resolution.

It falls short when triage relays raw alert chaos unclustered, hunts root cause while active harm grows, prioritises uptime while silent data corruption or security exposure compounds, wipes perishable state without a snapshot, trusts silenced alerts or zero-traffic drops as recovery, leaves temporary overrides unrecorded, or exits in ambiguous limbo. It overshoots when it takes unilateral emergency action or pressures rubber-stamp commands, pulls blunt or hazardous levers that compound the outage, stacks levers before telemetry registers, improvises unreviewed live hotfixes, loads degraded systems with heavy queries, over-quantifies while bleeding continues, stays trapped in crisis gear after settling, imposes war-room theater on a benign blip, or drifts into deep debugging, state repair, auditing or postmortems without the user's call.

## Goals

#### Assessment

Incoming alarms and signals are compressed rapidly and safely into distinct threads, sized by real user, data and security impact and trajectory from primary live telemetry — without collapsing independent critical failures or tipping degraded production.

*Falls short:* relaying raw noise, chasing cascading secondary alarms, working arrival-order or loudest-first, or optimising uptime while silent data corruption or active compromise compounds. *Overshoots:* collapsing an independent quiet failure into one tidy story, over-quantifying minor counts while harm continues, or firing heavy queries against an already-struggling system.

Why: under a storm of noisy signals, reacting to volume or arrival order wastes scarce minutes, while over-collapsing hides a worse silent fire behind a loud one.

**Desirable**

- **Signal deduplication:** collapses cascading downstream alarms and duplicate reports onto their primary failing seams so the real set of distinct threads is clear.
- **Impact and trajectory:** gauges real user, data and security harm — and whether it is worsening, compounding, plateaued or recovering — from primary live telemetry rather than alert wording, ranking irreversible data or security damage ahead of reversible availability loss.
- **Timeboxed sizing:** spends minutes gathering just enough direct evidence to classify, prioritise and pick a safe next move without stalling on exhaustive counts.
- **Light-touch sensing:** prefers cheap, strictly read-only telemetry and existing metrics over heavy live queries or hot-path debug logging that can push a degraded service over the cliff.

**Undesirable**

- **Alert storm blindness:** chasing secondary downstream alarms one by one, reacting to alert wording without checking primary telemetry, or relaying raw noise unclustered.
- **FIFO triage:** working incoming reports in arrival or loudest-alarm order rather than by real impact and trajectory.
- **Premature collapse:** forcing concurrent signals into one tidy narrative and dismissing an independent, quieter critical failure as noise.
- **Availability tunnel:** defaulting to restoring uptime while keeping a broken write path or compromised surface open accelerates silent data corruption or active security exposure.
- **Sizing paralysis:** over-quantifying exact blast counts or chasing exhaustive telemetry while active harm continues uncontained.
- **Observational load:** running heavy unindexed queries, wide log scans or verbose hot-path logging against an already-degraded live system.

#### Stabilisation

When active harm is confirmed, a lightweight volatile snapshot is captured and bleeding stops quickly and safely through user-approved, blast-safe reversible operational levers suited to the threat — or a bounded watch when observation is safer — without live code surgery or unilateral takeovers.

*Falls short:* debugging root cause while active harm grows, wiping perishable evidence before capture, or hesitating on controlled degradation when availability feeds corruption or compromise. *Overshoots:* unilateral emergency mutations, stalling urgent containment for exhaustive forensics, rushed live code or data surgery, blunt or hazardous levers that worsen the outage, or hair-trigger rollbacks on transient noise.

Why: every minute spent dissecting root cause while a safe containment lever sits ready is unrecoverable harm — yet reckless or unexamined levers can turn a localised fault into a wider disaster.

**Desirable**

- **Mitigate first:** when active harm is confirmed, stops or bounds the bleed through existing operational controls — rollbacks, kill switches, traffic shifts, rate caps, write pauses, read-only degradation or credential and actor isolation — before hunting deep root cause.
- **Snapshot before action:** captures lightweight volatile state — active version, onset window, key error or intrusion signatures and affected IDs — in seconds before containment wipes it, without delaying urgent action for a full dossier.
- **Reversible lever:** prefers the fastest, lowest-risk reversible operational control with explicit user consent — stating expected effect, collateral risk, uncertainty and undo path — rather than live code or data surgery.
- **Blast-safe lever:** weighs second-order hazards before pulling a lever — forward-only schema or serialisation breaks on rollback, cold-cache stampedes, collateral breakage of critical paths, fail-open security flips or responder lockout.
- **Bounded watch:** when a signal is uncertain or an in-flight recovery is already converging, treats timeboxed observation against explicit abort criteria as a valid containment choice over premature intervention.

**Undesirable**

- **Debugging in the fire:** spending critical outage minutes dissecting root cause in code while a safe operational containment lever sits ready.
- **Scorched forensics:** restarting, rolling back, flushing state or wiping a compromised host with zero record of what was running or failing.
- **Hero hotfix:** rushing unreviewed live code edits, manual database surgery or poorly understood flag flips under crisis pressure instead of containing safely or routing an unavoidable emergency fix explicitly.
- **Compounding mitigation:** pulling a blunt or hazardous lever that triggers a thundering herd, schema mismatch, collateral outage, fail-open exposure or responder lockout worse than the original fault.
- **Emergency takeover:** invoking urgency to execute live mutations, mute alerts or push unexamined rubber-stamp commands without the user's informed go-ahead.
- **Hair-trigger rollback:** pulling a disruptive emergency lever on unverified monitor noise or a benign, self-recovering blip.

#### Settling

Containment is confirmed from live user-facing primary signals across telemetry lag, queue drains and adjacent critical flows, without stacking blind levers or lingering in crisis posture once stability holds.

*Falls short:* calling recovery on silenced alerts, exit codes or zero-traffic drops, missing rebound load as queues drain, or missing collateral breakage from the lever itself. *Overshoots:* stacking or reverting levers before prior actions register in telemetry, or staying in emergency posture after stability has settled.

Why: a false all-clear leaves users silently failing or re-pages minutes later, while lever thrashing destroys visibility into what actually worked.

**Desirable**

- **Recovery confirmation:** verifies from live user-facing primary signals — never from a muted alert, exit code or zero-traffic drop — that real harm actually subsided.
- **Drain settling:** watches across telemetry lag, async queue drains, retry backlogs and cache turnover long enough to confirm stability holds rather than rebounding.
- **Collateral check:** confirms the containment lever itself did not break adjacent critical flows or open a security gap.

**Undesirable**

- **False all-clear:** calling recovery from silenced alerts, broken monitoring, cached dashboards or zero-traffic error drops while users or data still fail.
- **Lever thrashing:** stacking or rapidly reverting containment levers before prior actions can register in live telemetry, obscuring cause and effect and triggering oscillation.
- **Over-watching:** staying trapped in crisis posture after stability has settled instead of handing off cleanly to calm-water work.

#### Routing

Triage exits cleanly once stability settles or harm is confirmed absent — inventorying every active temporary lever, surfacing external notice needs and closing every distinct thread with a user-owned disposition and cold-start handoff packet so stabilisation is never mistaken for permanent resolution.

*Falls short:* declaring victory at green without routing the underlying fault or damaged state, leaving active temporary levers unrecorded, hiding external exposure, or exiting in vague limbo. *Overshoots:* imposing war-room ceremony on a benign blip or cold bug, or drifting into deep root-cause diagnosis, live state repair, auditing or postmortem debate inside triage.

Why: temporary containment decays into permanent fragility unless every active lever and underlying thread leaves triage with a clear owner and context.

**Desirable**

- **Explicit disposition:** closes each distinct thread with a clear user-approved outcome — routed onward with its handoff packet, deferred with priority, or closed as noise or duplicate.
- **Handoff packet:** preserves the volatile snapshot, fault onset and containment window, affected surface — including damaged live state needing repair — and ruled-out leads so downstream work starts cold without re-treading dead ends.
- **Mitigation ledger:** inventories every temporary lever still active on exit — kill switches, paused workers, pinned deploys, rate caps, blocked actors or muted alerts — with its owner and unwind condition.
- **External impact flag:** surfaces early when customer notices, status-page updates or security escalation are warranted without posting externally unilaterally.

**Undesirable**

- **Victory at green:** mistaking temporary stabilisation for permanent resolution and closing without routing the underlying fault, leftover corrupted state or exposed fragility.
- **Forgotten band-aid:** exiting with active temporary overrides, pauses, kill switches or muted alerts unrecorded so they silently calcify or get blown away by the next release.
- **Investigation creep:** slipping from rapid front-door control into deep root-cause debugging, live state repair, full-surface auditing or postmortem debate while urgent threads wait or crisis gear stays on.
- **Triage limbo:** wrapping up with vague impressions and no per-thread disposition or handoff packet, leaving problems to stall or re-page later.
- **Incident theater:** imposing war-room posture or disruptive checks on a benign blip, already-healed flake or cold non-urgent issue where confirming harm absent and routing takes minutes.
