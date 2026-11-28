# Harden

## Intent

Bridge "works on the happy path" and "survives unattended contact with reality", together with the user — keeping product capability fixed while replacing accidental failure behaviour with bounded, predictable, diagnosable survival across an agreed threat horizon. Effort concentrates on real exposure and whole failure classes: capping time, memory, payloads, concurrency and retries, isolating fate from flaky peers and noisy callers, choosing fail-closed or degrade-open postures deliberately per seam, keeping state intact across crashes, retries and redeliveries, and wiring redacted 3 AM diagnostics with a truthful startup, health and shutdown lifecycle. Every safeguard is itself a failure mode and must earn its operational weight, proven to fire and to recover cleanly under injected faults at the real seam; tightening that could break tolerant callers, new runtime dependencies and survivability that needs architectural change go to the user rather than breaking callers silently or burying domain logic in wrappers. Harden ends when the agreed horizon holds under triggered faults, operational signals are clear and safe, happy-path contracts stay intact, and accepted residual risks or architectural limits stand named in the user's hands.

It falls short when hardening patches only yesterday's exact trigger, leaves unbounded calls, shared fate or missing trust checks exposed, retries unsafe operations or lets poison items loop, ships guards proven only by inspection or mocked-away seams, checks that a guard trips but not that the system recovers, degrades silently, leaks secrets into runtime diagnostics, or forgets startup validation, truthful health and graceful shutdown. It overshoots when it builds a fortress around low-stakes code, layers uncoordinated retries, breakers and new infrastructure into self-inflicted outages, wires dependency checks into liveness probes, floods telemetry or sprawls observability, silently breaks tolerant callers or smuggles in product features, stacks wrappers past an architectural ceiling, or builds chaos platforms and flaky timing tests past what proves the agreed safeguards.

## Goals

These goals hold here as well. Read each file in full:

- `../shared/robustness.md`
- `../shared/verification.md`
- `../shared/craft.md`

#### Horizon

Hardening concentrates on real exposure and whole failure classes across the user's agreed threat horizon — keeping happy-path semantics and tolerant callers intact, surfacing architectural ceilings rather than wrapping around them, and stopping once the horizon holds with residual risks named.

*Falls short:* patching only yesterday's trigger while sibling seams stay exposed, silently breaking tolerant callers, stacking wrappers past an architectural ceiling, or leaving residual risks unspoken. *Overshoots:* armouring low-stakes code or chasing threats past the agreed horizon, leaving dangerous holes open out of exaggerated compatibility fear, or escalating tractable local hardening upstream prematurely.

Why: hardening that follows yesterday's incident leaves the same failure one seam over, while defences past the real stakes cost more in complexity and caller breakage than the failures they prevent.

**Desirable**

- **Threat horizon:** safeguards scale to the exposure, blast radius and criticality agreed with the user, with accepted residual risks named and hardening stopping once the horizon is covered.
- **Class-level sweep:** a failure class is closed across every sibling seam where it recurs, not only at the trigger of the last incident.
- **Hyrum's law:** existing callers are assumed to rely on every observable behaviour, so they are checked before schemas, caps, authorisation or timeouts tighten, and breaking trade-offs go to the user or land behind observe-first enforcement.
- **Architectural ceiling:** when survivability needs topology, persisted-contract or distributed-state changes, the limit goes upstream with evidence rather than being worked around locally.

**Undesirable**

- **Point-patch hardening:** guarding only the exact trigger of yesterday's incident while identical unbounded calls or trust edges stay exposed on sibling paths.
- **Fortress syndrome:** armouring low-stakes internals or chasing theoretical threats past the agreed horizon until defensive weight overwhelms the code.
- **Happy-path breakage:** silently altering valid semantics, breaking tolerant existing callers while tightening checks, or smuggling new product capabilities into a hardening pass.
- **Wrapper accretion:** burying domain logic under stacked defensive wrappers, local locks or brittle workarounds past an architectural ceiling.

#### Defences

Exposed boundaries, external calls, resource allocations and state mutations carry explicit bounds, isolated fate, non-amplifying recovery, deliberate failure postures and crash-safe state — without defences that themselves cause outages.

*Falls short:* unbounded waits, buffers, payloads or concurrency, shared fate with flaky peers or noisy callers, retry and reconnect stampedes, partial writes, looping poison items, or failure postures left accidental. *Overshoots:* uncoordinated retries, flapping breakers and speculative infrastructure that trap the system in self-inflicted outages, or hair-trigger limits that reject legitimate bursts.

Why: every working system already has failure behaviour, it is just accidental; and every safeguard added is code that can amplify an outage when left uncoordinated.

**Desirable**

- **Bounded resources:** time, payload and expansion size, concurrency, queue depth, memory and retries carry explicit caps, with deadlines propagated across calls, so slow peers or abusive callers cannot exhaust the host.
- **Bulkheads and backpressure:** pools and fate stay isolated so flaky non-critical peers or runaway tenants cannot sink the main path, pairing bounded queues with explicit load shedding and per-caller fairness.
- **Jittered backoff:** bounded retries and reconnects of idempotent operations use exponential backoff, jitter and deadline-aware budgets so transient trouble recovers instead of stampeding.
- **Deliberate failure posture:** security and integrity checks fail closed, while which non-critical seams degrade, shed load or serve bounded fallbacks is chosen with the user rather than left accidental.
- **Crash-safe state:** mutations survive mid-flight crashes and partial writes through atomic transitions, and permanently failing items are quarantined rather than retried forever.

**Undesirable**

- **Unbounded trust:** leaving network calls without timeouts or deadlines, queues or payloads without size or expansion caps, shared fate with non-critical peers, or shared paths without per-caller limits.
- **Retry storm:** adding naive, unjittered, unbounded or layered retries, or retrying non-idempotent operations, so brownouts amplify into cascading outages and duplicate side effects.
- **Metastable failure:** introducing uncoordinated timeout hierarchies, flapping circuit breakers or synchronised recovery stampedes that keep the system in outage after the original trigger clears.
- **Poison-pill loop:** letting one malformed or permanently failing item redeliver indefinitely, stalling workers or exhausting memory instead of bounding and quarantining it.
- **Resilience theater:** layering speculative circuit breakers, caches, distributed locks, new infrastructure or hair-trigger limits whose own failure modes reject legitimate traffic or cause outages.

#### Operability

When guards trip, load spikes, peers degrade or instances restart, the system emits actionable, redacted signals, keeps a truthful startup, health and shutdown lifecycle and defaults safely, so an unfamiliar operator at 3 AM can diagnose and act without noise, leaks or collateral damage.

*Falls short:* silent degradation, opaque crashes, secrets or internals leaked into runtime diagnostics or client errors, lying health checks, permissive defaults, or abrupt shutdowns that leave partial state. *Overshoots:* bespoke telemetry, high-cardinality noise and alerts on self-healing blips, log floods inside outage loops, or dependency checks in liveness probes that turn a peer blip into a restart storm.

Why: a system that fails safely in silence, or floods logs with secrets and noise during an outage, turns a containable fault into a prolonged 3 AM mystery.

**Desirable**

- **Diagnosable failure:** operators get structured context on the failing seam, violated bound and retryability at accurate severity, while untrusted callers receive sanitised errors and secrets stay redacted.
- **Guard visibility:** rate limits, open circuits, fallbacks, shed load and dead-lettered items emit metrics or structured events whenever they activate, so degradation never hides in silence.
- **Truthful lifecycle:** startup validates configuration and fails fast, liveness reports only whether the process is wedged while readiness reports whether it can serve, and shutdown drains in-flight work and releases handles on cancellation.
- **Safe defaults:** limits, timeouts and missing configuration default to bounded, fail-safe values, exposing only the knobs operators genuinely need.

**Undesirable**

- **Silent degradation:** falling back, dropping messages, shedding load, dead-lettering or opening a circuit with no metric, log or operator-visible trace.
- **Secret-leaking diagnostics:** dumping raw payloads, credentials, query parameters or internal stack traces into runtime logs, metrics or untrusted client responses.
- **Log-flood amplification:** logging verbose payloads inside hot or retry loops, or expected client rejections as server errors, exhausting telemetry budgets and burying real alarms.
- **Observability sprawl:** introducing bespoke telemetry frameworks, high-cardinality labels, excess knobs or alerts on transient self-healing blips instead of fitting existing operational conventions.
- **Coupled liveness probe:** wiring downstream dependency checks into a liveness endpoint so a peer blip triggers restart loops across healthy instances.
- **Brittle lifecycle:** skipping startup validation, shipping always-healthy probes, ignoring cancellation signals, leaking handles or exiting abruptly mid-transaction so routine deploys and restarts leave partial state.

#### Fault proof

Every added safeguard is seen to fire and to recover cleanly under injected faults, abuse, overload or restarts at the real seam — deterministically, safely isolated and without building a chaos platform.

*Falls short:* guards shipped on inspection, mocked-away seams, or proving that a guard trips without checking recovery. *Overshoots:* bespoke chaos platforms for a bounded pass, destructive fault or load probes against shared or live environments, or slow, jitter-prone timing tests in CI.

Why: a fallback or shutdown path that first runs in production usually fails there, and a guard that trips but never resets turns a brief fault into a lasting outage.

**Desirable**

- **Proven failure paths:** peer faults, overload, hostile input and shutdown signals are injected at the real seam with controlled clocks and isolated fixtures, so every guard is seen to fire deterministically.
- **Recovery proof:** once an injected fault clears, the system returns to healthy steady state with no wedged pools, leaked handles or locks, stuck circuits or corrupted state.

**Undesirable**

- **Untested catch block:** shipping error handlers, timeouts, rate limits, shutdown hooks or fallbacks on inspection or happy-path runs without triggering the fault they guard.
- **Mocked-out fault:** stubbing away the real socket, queue, store or signal boundary so a guard passes in tests while staying dead or misconfigured in real execution.
- **Flaky timeout test:** proving timeouts or backoff with wall-clock sleeps or timing-sensitive assertions that make CI slow and jitter-prone.
- **Chaos theater:** building permanent fault-injection platforms, heavy load rigs or destructive live chaos campaigns past what proves the agreed safeguards.
