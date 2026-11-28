# Migrate

## Intent

Guide live data, schemas, APIs, runtimes, frameworks, infrastructure or external consumers safely across an incompatible boundary, together with the user — optimising for the trajectory itself so every intermediate world between old and new stays viable at the user-chosen continuity bar. Every surface touching the seam is mapped before moving, wide version gaps step through verified hops, and scope stays isolated from opportunistic features or redesigns while unsettled target shapes reconcile upstream. Intermediate phases survive rolling deploys, mixed versions and in-flight state under one unambiguous write authority, while bulk transforms, DDL and retreat paths are rehearsed on production-like shape and run idempotently, throttled and side-effect-safe with malformed legacy edge cases isolated. Empirical data and semantic parity is proved to agreed tolerances before authority transfers, halting on unexplained divergence or live corruption rather than pushing through. Authority shifts progressively where warranted with verified write-safe retreat up to an explicit user-owned point of no return and forward-fix contingencies ready beyond it, external consumers receive clear upgrade paths and straggler policies, and temporary bridges contract away once zero usage and soak clear. Migrate ends when authority rests on the new target and temporary shims and superseded paths are retired — or, when soak or deprecation outlasts the session, with a durable, owned contraction record and explicit dismantling triggers in the user's hands.

It falls short when a migration attempts a flag-day switch where rolling skew or live state required phasing, misses hidden consumers or dirty rows, stacks breaking leaps together, lets old and new mutate independently, saturates or clobbers live systems with unrehearsed or unthrottled backfills, shifts authority on surface counts or unchecked drift, mistakes a code revert for state rollback after writes diverge, pushes past abort alarms, drops legacy paths before soak clears, or abandons temporary bridges in permanent hybrid limbo. It overshoots when it builds zero-downtime choreography where a maintenance window or clean versioned break is cheaper and safer, bundles opportunistic features or redesigns into the crossing, over-fragments phases into months of hybrid decay, builds permanent frameworks for throwaway scripts or heavy live replay rigs where a cheap deterministic check suffices, warps the target around accidental legacy quirks, stalls cutover over explainable noise, keeps fragile reverse-sync alive past the natural forward-fix pivot, lets negligible stragglers veto retirement forever, or blocks closure waiting on multi-week soak windows.

## Goals

These goals hold here as well. Read each file in full:

- `../shared/robustness.md`
- `../shared/verification.md`
- `../shared/coherence.md`
- `../shared/fidelity.md`

#### Posture

Every surface touching the incompatible seam is mapped first, the crossing uses the simplest continuity bar and bounded hops that fit real risk, and scope stays isolated from opportunistic features, redesigns or stacked leaps.

*Falls short:* missing hidden consumers or dependencies, attempting a flag-day switch where rolling skew or live state required phasing, stacking breaking leaps together, or quietly reshaping an unsettled target in flight. *Overshoots:* building zero-downtime dual-write choreography where a bounded maintenance window or clean versioned break is cheaper and safer, bundling extra features or redesigns into the crossing, or over-fragmenting phases into months of hybrid decay.

Why: the safest migration is the simplest trajectory that survives the seam; once extra features, stacked leaps or needless phases ride along, blast radius compounds and equivalence becomes unprovable.

**Desirable**

- **Seam inventory:** maps every live producer, consumer, derived store, async path, client and transitive dependency touching the boundary before moving.
- **Proportional bridge:** matches the crossing to the simplest continuity bar the user agrees fits the risk — zero-downtime, bounded maintenance window or clean versioned break — adding shims, dual-writes or adapters only where required.
- **Stepping stones:** breaks wide version gaps or coupled platform shifts into verified intermediate hops rather than stacking incompatible crossings into one leap.

**Undesirable**

- **Seam blindness:** missing unindexed producers, consumers, caches, queues, ETL jobs, older clients, transitive dependencies or dirty historical rows until cutover breaks them.
- **Flag-day cutover:** attempting a simultaneous switch of schema, code, data, runtimes or consumers where rolling version skew or live state required a phased crossing.
- **Zero-downtime dogmatism:** engineering multi-phase dual-write and shadow-read infrastructure when a bounded maintenance window or clean versioned break is cheaper and less corruption-prone.
- **Stacked leap:** jumping across multiple breaking major versions or combining orthogonal migrations such as engine, schema and runtime shifts in one coupled pass.
- **Feature-hitchhiking:** bundling opportunistic redesigns, new product features, stricter policies or unrelated cleanups into a live crossing, destroying equivalence checks and inflating blast radius.
- **Phase sprawl:** over-fragmenting a bounded crossing into excessive micro-phases that drag hybrid complexity across months.

#### Coexistence

Every intermediate world survives mixed-version execution and in-flight state under one unambiguous write authority, bulk transforms and retreat paths are rehearsed on production-like shape and run resumable, throttled and side-effect-safe, and malformed legacy edge cases are isolated visibly.

*Falls short:* breaking rolling deploys or in-flight state, letting old and new mutate independently, letting secondary write or shadow failures sink the primary path, testing only on clean toy fixtures, locking or saturating live systems, clobbering fresher live writes or firing side-effect storms, or halting blindly or silently dropping malformed legacy rows. *Overshoots:* engineering permanent framework infrastructure for throwaway scripts, over-throttling safe offline work past live headroom, or building mixed-version guards for a maintenance window where versions never coexist.

Why: an incompatible crossing lives in a hybrid world before reaching its destination; if intermediate phases split authority, lock tables or corrupt live state, the target state is worthless.

**Desirable**

- **Intermediate safety:** keeps every deployable phase live-safe under rolling deploys, mixed versions, in-flight queues, sessions, caches and retries under one declared write authority, ensuring secondary dual-write or shadow failures never sink the primary path.
- **Realistic rehearsal:** dry-runs DDL locks, codemods, bulk transforms, cutover scripts and retreat paths against production-like shape, volume, skew and dirty edge cases before touching live systems.
- **Resumable backfill:** moves historical data, indexes or bulk code transforms in idempotent, checkpointed, rate-limited batches without locking or saturating live systems.
- **Side-effect containment:** prevents bulk writes and adapters from clobbering fresher concurrent live updates or triggering unintended downstream hooks and cascades.
- **Poison-pill isolation:** quarantines malformed, orphaned or anomalous legacy records with visibility and explicit disposition so they neither halt the crossing blindly nor get dropped or silently altered.

**Undesirable**

- **Split-brain:** letting old and new stores or paths accept independent mutations without one declared authority or conflict rule so neither side holds truth.
- **Toy-data rehearsal:** validating a migration only on empty or sanitised local fixtures and getting blindsided by production volume, lock queues, skew, nulls or legacy encodings.
- **Lock-storm migration:** running blocking DDL locks, unthrottled table rewrites, unbounded batch updates or unrehearsed scripts against live production systems.
- **Backfill blast:** letting bulk writes clobber fresher concurrent live updates or fire cascading triggers, webhooks, CDC floods, re-index storms or resurrected erased records.
- **Scaffold overbuild:** engineering permanent, general-purpose frameworks for one-off migration scripts or over-throttling safe offline work past what live headroom requires.

#### Parity

Data, runtime semantics, edge cases and failure shapes are proved empirically against explicit user-agreed tolerances and documented deltas before authority shifts, halting on unexplained divergence without stalling on harmless noise or fossilising legacy bugs.

*Falls short:* shifting authority on inspection or surface counts without deep parity proof, letting silent semantic or write-skew drift slip through dual-writes, codemods or runtime upgrades, or pushing past unexplained parity alarms. *Overshoots:* stalling cutover over explainable noise past agreed tolerances, warping the target to preserve accidental legacy bugs instead of approving a clean delta, or building heavy live replay rigs where a cheap deterministic check suffices.

Why: silent drift across a boundary is far harder to untangle after authority transfers, while chasing zero-diff perfection or bug-for-bug emulation stalls crossings and scars the target.

**Desirable**

- **Parity reconciliation:** proves empirical equivalence across data, invariants and observable outputs through shadow reads, parallel runs, diff audits, checksums or golden-corpus checks before transferring authority.
- **Bounded tolerance:** sets explicit user-agreed equivalence thresholds and documented expected deltas up front, separating real defects from explainable in-flight lag, dead rows or intentional versioned changes.
- **Divergence stop:** halts phase advancement before authority shifts when unexplained parity failures surface, routing mystery discrepancies to diagnosis rather than waving them off or patching around them.

**Undesirable**

- **Semantic drift:** letting silent data loss, write skew, codemod errors or subtle runtime and framework behavioural shifts in ordering, timezones, rounding, nulls, encodings or error shapes pass unchecked before cutover.
- **Shallow parity:** taking row counts, HTTP status codes or zero script exit codes as equivalence proof while values, invariants or semantic outputs diverge.
- **Parity perfectionism:** blocking cutover indefinitely over explainable in-flight lag, dead historical rows or harmless formatting deltas past agreed tolerances.
- **Shadow theater:** building heavy live traffic-replay or permanent dual-run harnesses where a cheap deterministic corpus, checksum audit or bounded check suffices.
- **Bug-for-bug fossilisation:** contorting the target at high cost to emulate accidental legacy quirks or flaws instead of agreeing a clean documented delta with the user.

#### Cutover

Authority transfers progressively by slice where warranted on agreed readiness and abort criteria, with verified write-safe retreat up to a structural one-way gate and tested forward-fix contingencies ready beyond it.

*Falls short:* flipping authority all at once where cohort or route slicing was viable, mistaking a code revert for state rollback after live writes diverge, crossing an irreversible boundary without user consent or forward-fix readiness, or advancing past abort signals. *Overshoots:* forcing multi-slice cutover ceremony onto a simple reversible or maintenance-window flip, or maintaining fragile bi-directional reverse-sync machinery long past the natural point of no return where forward-fix is strictly simpler and safer.

Why: migrations rarely fail on day one — they fail when authority flips without a tested way back after live writes, or when retreat machinery becomes riskier than fixing forward.

**Desirable**

- **Strangler fig:** shifts authority incrementally by cohort, tenant, shard or route on pre-agreed readiness and abort criteria wherever the boundary allows, proving live traffic on a bounded slice before full cutover.
- **Write-safe rollback:** preserves genuine, tested non-destructive retreat through reverse sync or reversible transforms across the soak window up to the point of no return, with concrete forward-fix contingencies ready before crossing it.
- **One-way gate:** marks the structural pivot where write-safe retreat yields to forward-fix — flipping authority without reverse sync, running destructive drops or retiring external contracts — and pauses explicitly for user go-ahead once contingencies stand ready.

**Undesirable**

- **One-way rollback trap:** assuming a code revert rolls back a migration after live writes have diverged, destructive mutations have run, or reverse sync was never rehearsed.
- **Rollback tax:** maintaining fragile bi-directional sync or instant-flipback machinery long past the natural point of no return where forward-fix is strictly simpler and safer.
- **Blind push-through:** advancing cutover past pre-set abort signals, or improvising ad-hoc live-state repairs inside migration scripts when corruption hits instead of halting and handing off recovery.

#### Contraction

External consumers have clear upgrade paths and cutoff policies, zero remaining legacy usage is proved before retirement, and temporary crossing bridges are dismantled cleanly once soak clears — or handed off as an owned, trigger-bound record when soak or deprecation outlasts the session.

*Falls short:* blindsiding external consumers without notice or an upgrade path, deleting legacy paths before soak, scheduled jobs, cold caches or deprecation windows clear, or abandoning temporary bridges permanently after cutover. *Overshoots:* letting a tiny unmaintained tail of legacy callers or records veto retirement forever instead of enforcing an agreed sunset policy, or blocking session closure waiting on multi-week soak or deprecation windows.

Why: an uncontracted migration leaves two systems living in one codebase forever, while premature removal breaks cold paths and external callers.

**Desirable**

- **Consumer notice:** aligns external callers, downstream teams and operators early with clear deprecation windows, upgrade paths, usage telemetry and an explicit straggler policy.
- **Zero-traffic proof:** confirms via live telemetry, query logs or consumer checks that old paths, schemas, queues or versions carry zero remaining usage across periodic batch jobs and cold caches before retiring them.
- **Finished contraction:** removes temporary dual-writes, compatibility shims, parity harnesses, migration flags, deprecated schemas and old dependencies once soak clears — or leaves a durable, owned contraction record with explicit dismantling triggers when soak or deprecation outlasts the session.

**Undesirable**

- **Premature drop:** deleting legacy tables, columns, endpoints, fallbacks or compat layers before soak windows, batch schedules, cold caches or deprecation timelines clear.
- **Permanent bridge:** declaring victory once the new path serves traffic and leaving dual-writes, compat shims, old and new code paths or superseded schemas calcified in hybrid limbo indefinitely.
- **Straggler paralysis:** letting a tiny, unmaintained long-tail of legacy callers or records block retirement forever instead of executing an agreed sunset cutoff or fallback.
