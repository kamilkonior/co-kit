# Recover

## Intent

Make wrong live state right again, together with the user — acting on the damage a fault already left behind, not on the fault: changing what the system holds, never what it does. The damaged set is defined by evidence rather than complaints, bounded in time, followed through every copy and escaped effect, and protected against expiring backups, logs or downstream jobs that would amplify bad state. What "right" means for each damage class rests on the authoritative record and a user-owned policy — preserving legitimate post-incident writes, honouring lawful erasures, using adjusting entries on immutable ledgers rather than rewriting history, checking whether stale dropped work should still replay, and quarantining what cannot be reconstructed. Read-only scoping and drafting proceed while a fault is live, yet no live repair applies until new damage stops or a verified cutoff bounds it; internal mutations land via the lightest, cheapest-to-undo rehearsed intervention — previewed, concurrency-guarded, backed by before-images, rate-capped and trigger-controlled — calibrated to irreversibility and blast radius. Escaped external effects are answered only after internal state reconciles, with cross-channel exactly-once accounting and user consent given knowing they cannot be undone. Recover ends when an independent tie-out shows every copy, external record-holder and untouched neighbour at its target, each affected party has been made whole and told as decided, temporary pauses are unwound, before-images carry an expiry, residual rulings are on record, and stopping the fault, explaining its cause and preventing a repeat sit cleanly in the user's hands.

It falls short when recovery fixes only reported cases, guesses the window, lets perishable logs expire or downstream jobs amplify bad rows, leaves caches, indexes, warehouses or partner records disagreeing with the primary store, trusts a corrupted or intent-only record, settles remedy policy silently, repairs while the fault still leaks, runs unpreviewed live writes, overwrites legitimate edits or resurrects erased data, triggers cascades or refunds twice, or closes on "the script exited 0". It overshoots when it keeps digging while harm compounds and dispute windows close, mutates healthy records or closed ledgers in place, rolls back a whole database or freezes writes to fix one table, puts ledger-grade ceremony on a cache rebuild, sweeps in older unrelated data problems, holds personal data past retention, grows a one-off script into a standing framework or app-code patch, or drifts into root cause, permanent code fixes or prevention.

## Goals

These goals hold here as well. Read each file in full:

- `../shared/fidelity.md`
- `../shared/verification.md`

#### Scoping

The damaged set is defined by evidence over authoritative data, bounded in time, traced through every copy and escaped effect, and guarded against expiring recovery sources or downstream amplification — without sweeping in unrelated older debt or stalling while windows close.

*Falls short:* fixing only reported tickets, guessing the window, missing derived copies or escaped effects, catching healthy records, or letting backups, logs or downstream jobs worsen the damage while scoping. *Overshoots:* chasing certainty on the last sliver while harm compounds and retention or dispute windows close, or pulling older unrelated data problems into this repair.

Why: a repair is only as right as its boundary — missed records surface later in support or audits, while an over-wide rule turns the repair itself into damage.

**Desirable**

- **Blast radius:** defines the damaged set by a rule over authoritative data rather than collected complaints, with a window starting and ending on evidence of when the fault began and when new damage stopped.
- **Precision and recall:** checks the selection both ways against an independent signal — event log, processor records or an invariant check — showing which damaged records it misses and which healthy ones it catches.
- **Data lineage:** follows the damage into every copy and consequence — replicas, caches, search indexes, warehouses, downstream consumers and escaped effects such as charges, emails, webhooks and partner state.
- **Perishable sources:** checks early whether backups, logs, dead-letter queues, processor records or dispute windows are expiring — or scheduled downstream jobs are about to consume bad local state — preserving forensic inputs and gating consumers before slow digging loses them.

**Undesirable**

- **Streetlight effect:** scoping the damage where it is easiest to see — incoming tickets, the primary table or the obvious window — while derived copies, escaped effects and slow-built damage stay dark.
- **Friendly fire:** widening the selection until it catches healthy records, legitimate concurrent writes or records already repaired by hand, so the correction itself causes damage.
- **Decay paralysis:** chasing certainty on the last sliver of the set while customers stay wronged, legitimate writes pile onto damaged rows, and backup-retention or chargeback windows close.
- **Historical sweep:** holding the data to a standard it never met before the incident and pulling unrelated older data problems into this repair.

#### Remedy

What "right" means for each damage class rests on an authoritative source and explicit user policy — preserving legitimate post-incident writes, lawful erasures and immutable history, checking replay fitness and quarantining what cannot be reconstructed.

*Falls short:* deriving targets from corrupted or intent-only records, settling clawbacks or write-offs silently, replaying stale work blindly, resurrecting lawfully erased data or overwriting immutable ledgers. *Overshoots:* demanding record-by-record forensic reconstruction where a clean policy remedy or quarantined exception queue would serve better and faster.

Why: code and logs show what happened, never what business remedy is fair — a wrong target overwrites good state on purpose, and an unowned policy call breaks customer and legal trust.

**Desirable**

- **System of record:** names the authoritative record deciding the target for each damage class — letting an outside party's record of what happened outrank local intent, keeping legitimate post-incident writes, honouring lawful erasures and using adjusting entries on append-only ledgers or closed periods.
- **Make-whole policy:** puts what "right" means for each damage class to the user as a decision — exact restitution, blanket credit, materiality write-off or clawback, and who is told — with counts, value at stake and samples rather than raw rows.
- **Replay fitness:** decides with the user whether dropped or missing work still means what it meant — whether to replay as-is, adapt to current prices, flags and account status, or drop with notice.
- **Quarantine:** separates what is reconstructible from what is genuinely unknowable or ambiguous into an explicit holding set, so the high-confidence core repairs now and each ambiguous class gets the user's ruling or an owned exception queue.

**Undesirable**

- **Garbage in, garbage out:** deriving the target from a corrupted, derived or intent-only record — or from pre-incident values regardless of intervening writes — so the repair faithfully reproduces an error.
- **Silent clawback:** settling an ambiguous or customer-impacting remedy inside a script — such as taking back credits already spent or guessing genuinely lost values — without the user's ruling.
- **Stale replay:** replaying dropped work that no longer means what it meant — a "ships today" email three days late — or running it out of order under today's prices, flags and account status without anyone deciding that was right.
- **Data resurrection:** bringing back personal data that was lawfully erased or expired through a backup restore, a replay or re-inserting deleted records.
- **History rewrite:** mutating append-only ledgers, closed accounting periods or external history in place to look as if the incident never happened instead of recording a clean adjusting or compensating entry.
- **Over-reconstruction:** demanding record-by-record forensic reconstruction where a clean policy remedy such as a blanket credit, write-off or quarantine would serve better and faster.

#### Intervention

Internal live repairs wait until new damage stops or a verified cutoff bounds it, landing as the lightest, cheapest-to-undo rehearsed intervention — previewed, concurrency-guarded, backed by before-images, rate-capped and trigger-controlled — calibrated to blast radius and irreversibility.

*Falls short:* repairing while the fault still leaks, running unreviewed live SQL without a previewed diff, overwriting concurrent writes, locking live tables with unthrottled replays or letting repair writes fire unintended triggers and webhooks. *Overshoots:* blocking read-only scoping while containment runs, rolling back a whole database or freezing writes for one table, or putting ledger-grade ceremony on a cheap rebuildable cache.

Why: a repair is a live production mutation made under pressure — careless execution creates second-order corruption that fuses the original bug with the repair bug.

**Desirable**

- **Cutoff gate:** keeps read-only scoping and drafting moving while a fault is live, yet applies no live repair until new damage has stopped or a verified cutoff watermark bounds it.
- **Compare-and-swap:** applies each write only if the record still holds the bad value observed, so legitimate writes made since or during the repair survive without freezing the system.
- **Before-image:** captures the prior value of every changed record with what decided its target, the action and the outcome so a bad batch can be undone cleanly, held no longer than undo or retention obligations allow.
- **Canary batch:** runs a rehearsed, previewed diff on a cheap pilot slice first, then in rate-capped, resumable batches with a stop switch, watching live load and controlling triggers, hooks and outbound events deliberately.

**Undesirable**

- **Mopping in a flood:** applying live repairs while the underlying fault still leaks new bad writes into the same set.
- **Blind surgery:** running unreviewed hand-written console writes or unpreviewed live SQL without a dry-run diff showing exact counts, value deltas and samples.
- **Lost update:** restoring old values over legitimate later writes, or overwriting what users changed while the repair ran.
- **Repair stampede:** running unthrottled backfills or replays that lock hot tables, spike replication lag, exhaust connection pools or trip partner rate limits.
- **Trigger cascade:** letting internal repair writes fire database triggers, change-data-capture pipelines, webhooks or automated emails unexpectedly at users or downstream systems.
- **Sledgehammer:** rolling back a whole database, failing over or freezing all writes to fix one table, turning a bounded data problem into an outage.
- **Ledger theater:** imposing full ledger-grade ceremony on a cheap, reversible cache rebuild or derived-index refresh.

#### Make-whole

Irreversible external compensations, replays and notices run only after internal authoritative state reconciles — idempotent, cross-channel deduplicated, accurately targeted and explicitly approved by the user knowing they cannot be undone.

*Falls short:* firing refunds or notices before internal state reconciles, compensating twice across scripts, support or chargebacks, silently reversing customer state without agreed notice, or sending notices that contradict what actually settled. *Overshoots:* compensating or emailing beyond the confirmed affected set without user agreement.

Why: money, messages and partner mutations that leave the system cannot be rolled back — mistakes land directly on people the fault already wronged.

**Desirable**

- **Internal-first order:** reconciles internal authoritative state and upstream stores before firing irreversible external compensations or customer notices, and rebuilds derived copies in causal order so stale stores cannot re-corrupt truth.
- **Compensating transaction:** answers an escaped effect that cannot be undone with a new opposite effect — refund, credit, void or reversal — with explicit user consent given knowing it is irreversible.
- **Exactly-once:** gives every replay and compensation an idempotency key, and counts every channel that may already have made a party whole — the repair itself, support refunds, chargebacks and partner fixes — in one remediation ledger.
- **Targeted notice:** sends customer or partner corrections only to confirmed affected parties, matching what actually settled rather than what is still pending.

**Undesirable**

- **Double compensation:** rerunning a non-idempotent script after a timeout, replaying webhooks a partner already processed, or refunding a party who already won a chargeback or support credit.
- **Premature compensation:** firing refunds, reversals or "you've been credited" notices before internal state is reconciled and the compensating action has actually settled.
- **Misdirected notice:** emailing unaffected users, sending notices that contradict what actually happened, or silently reversing charges and orders without telling affected parties as agreed.

#### Tie-out

Convergence is proved independently across primary stores, derived copies, external record-holders and untouched neighbours; every temporary pause is unwound, kept before-images carry an expiry, and stopping the fault, explaining its cause and preventing a repeat are handed off cleanly.

*Falls short:* trusting a clean script exit code, count-only check or primary-only query, forgetting to re-enable paused triggers or jobs, or leaving before-images holding personal data past retention. *Overshoots:* growing a one-off repair script into a standing reconciliation framework, hiding data patches inside application code, or drifting into root-cause debugging, permanent code fixes or resilience engineering without the user's call.

Why: unverified repairs hide lingering drift across copies and partners, while uncleaned custody artefacts and mode drift leave lasting operational hazards behind.

**Desirable**

- **Independent tie-out:** proves convergence through a check independent of the repair script's own log — comparing values against the system of record and outside record-holders, confirming invariants hold, derived copies agree, untouched neighbouring records had zero collateral mutations, and every remaining delta is explained and owned.
- **Bounded custody:** records what changed, why and what residuals were ruled on while unwinding every temporarily paused trigger, hook or scheduled job on exit and binding kept before-images and staging tables to an explicit owner and retention expiry.

**Undesirable**

- **Self-confirming tie-out:** taking "the script exited 0" as proof, comparing counts instead of values, confirming with the same query that selected the rows, or checking only the primary store while caches, indexes, warehouses, neighbours or outside record-holders still disagree.
- **Toxic custody:** leaving temporary before-images or staging tables containing personal data alive past undo need or retention limits, or forgetting to re-enable paused triggers, hooks or scheduled jobs on exit.
- **Framework creep:** growing a one-off operational repair script into a standing reconciliation framework or burying one-off data patches inside production application code instead of routing durable tooling through the pipeline.
- **Mode drift:** sliding from repairing already-wrong live state into root-cause debugging, permanent code fixes, schema redesign or resilience engineering without the user's call.
