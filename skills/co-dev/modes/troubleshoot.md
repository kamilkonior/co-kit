# Troubleshoot

## Intent

Turn an observed failure, flake or misbehaviour into an explained, falsifiable cause, together with the user, before anyone guesses at a fix. Observation pins down the exact gap between expected and actual behaviour, confirms what artefact and configuration are actually running, traces past cascades to the earliest break and preserves volatile evidence intact — surfacing active live harm and reversible containment ahead of deep digging. Search spans every layer that can produce the fault, weighing recent changes, mundane causes and local seams first while pivoting to cold-case inference when cheap reproduction is unavailable. Explanation proves the causal mechanism across observed symptoms and unaffected cases — separating trigger from underlying defect, allowing for concurrent independent faults and stopping at the actionable fault boundary or at a targeted diagnostic trap when cold evidence runs out. Troubleshooting leaves product code and live state untouched, reverts its own temporary local probes and ends when the user holds what failed, why, what was ruled out, what remains uncertain, any invalidated upstream premises, corrupted live state or immediate sibling exposure, and concrete next moves in their hands.

It falls short when fixes are guessed before the cause is proved, volatile traces are wiped before capture, downstream cascades or stale builds stand in for the real break, search stays trapped in one layer or blames external flakiness prematurely, nearby bugs pass for proved mechanisms, active live harm burns uncontained, or raw signals stand where a causal picture belongs. It overshoots when it silently patches code or live state, leaves temporary probes behind, runs disruptive live diagnostics, forces evidence onto the current diff, chases exotic theories or heavyweight harnesses past an obvious cheap seam, insists on airtight local reproduction for a cold-case fault, digs past the actionable fault boundary, or drifts into fixing, auditing or redesigning without the user's call.

## Goals

These goals hold here as well. Read each file in full:

- `../shared/diagnosis.md`
- `../shared/synthesis.md`

#### Forensics

The failing system is observed intact before it is disturbed, grounded in the exact broken expectation, the earliest failure and what is actually running — gating live harm ahead of deep digging.

*Falls short:* wiping volatile traces before capture, chasing downstream cascade noise or stale builds, or missing ongoing live harm. *Overshoots:* heavy or mutating live diagnostics that disturb traffic or corrupt evidence, refusing cheap reversible local probes out of over-caution, or collecting exhaustive telemetry while active harm burns.

Why: some failures leave only one trace, and knowing what is burning and what is actually running sets where every next step belongs.

**Desirable**

- **Live-impact gate:** checks early whether active user harm or data corruption is ongoing and growing, surfacing reversible containment ahead of deep root-cause digging.
- **Preserve evidence:** captures ephemeral logs, dumps, stack traces or runtime state before any restart, retry, cache clear or cleanup wipes them.
- **Expectation delta:** pins down the exact gap between expected and actual behaviour, confirming the system is actually broken rather than a stale expectation or intended constraint.
- **First failure:** traces past cascading downstream errors, timeouts and wrapper messages to the earliest failing signal in the timeline.
- **Running reality:** confirms the failing binary, artefact, config, dependency version and environment actually match the source being inspected before debugging logic.
- **Targeted instrumentation:** where the failure is invisible, introduces cheap, read-only or reversible local observation at the suspected seam — reverted on exit unless the user chooses to keep a reproducer.

**Undesirable**

- **Bleeding while digging:** hunting root cause while active user or data harm grows uncontained and a safe mitigation sits ready.
- **Blind restart:** restarting, redeploying, retrying or clearing caches to make the symptom vanish before capturing what failed.
- **Cascade chasing:** debugging secondary downstream exceptions, retries or wrapped messages instead of the earliest break that triggered them.
- **Phantom build:** debugging source files while the failing process runs a stale build, cached layer, wrong branch, shadow config or mismatched dependency.
- **Disruptive probe:** running heavy queries, verbose hot-path logging or live state-mutating diagnostics that degrade production or corrupt evidence.

#### Narrowing

Search spans every layer that can produce the failure, weighted by realistic priors — recent changes, mundane causes before exotic ones, local seams before external blame — and pivots to inferential narrowing when cheap reproduction is unavailable.

*Falls short:* trapping search in one familiar layer, blaming external systems or flakiness without ruling out local causes, or chasing exotic theories past simple misconfiguration. *Overshoots:* forcing unrelated failures onto the current diff, refusing to test an upstream seam after local evidence points across it, building elaborate diagnostic harnesses before checking an obvious cheap boundary, or stalling in reproduction loops on cold-case faults.

Why: realistic priors cut the search space fastest, while rigid habits either chase ghosts or blind you when the real fault sits across a boundary.

**Desirable**

- **Full-stack scope:** treats code, build, config, dependencies, data, environment, runtime and infrastructure as equal candidate layers.
- **Recent changes:** inspects what shifted right before the failure started — deploys, config, dependencies, schemas, data or environment — early as a high-prior lead.
- **Horses, not zebras:** rules out mundane, high-probability faults such as typos, wrong environment, bad data, version drift or exhausted limits before chasing exotic compiler, kernel or race theories.
- **"select() isn't broken":** rules out local code, config, usage and state before blaming flaky CI, the runtime, the OS or an external service — while following evidence across that boundary once local causes are falsified.
- **Cold-case inference:** when a fault is transient, production-only or cannot be reproduced cheaply, narrows systematically from timelines, invariants, logs and differential traces rather than stalling on local reproduction.

**Undesirable**

- **Tunnel diagnosis:** staying trapped in one familiar layer such as application code while ignoring build, config, dependencies, data or infrastructure.
- **Diff bias:** forcing evidence to fit the current branch or recent edit when the real cause lies elsewhere.
- **Zebra hunting:** leaping to elaborate concurrency, compiler or infrastructure theories before ruling out mundane configuration, data or wiring mistakes.
- **Premature externalisation:** blaming flaky CI, the environment, a library or an external service without ruling out local code, config or state.
- **Upstream blindness:** refusing to test a library, runtime, compiler or external-service seam after local evidence genuinely points across it.
- **Repro fixation:** insisting on an airtight local reproducer for a transient or production-only failure when existing traces already narrow the cause or point to a targeted trap.

#### Causation

The explanation proves how the defect mechanistically produces every observed symptom — separating trigger from underlying fault, handling concurrent independent faults and stopping at the actionable fault boundary or at an honest diagnostic trap when cold evidence runs out.

*Falls short:* stopping at a nearby oddity without proving reachability and mechanism, halting at the immediate trigger, ignoring contradicting anomalies, or claiming certainty past what evidence supports. *Overshoots:* forcing independent concurrent failures into one tidy root cause, digging layers past the actionable fault boundary, or refusing to conclude until airtight proof exists when a diagnostic trap is the right next step.

Why: a plausible guess or trigger-level stop invites band-aid fixes that leave the broken invariant alive, while unproved certainty misleads everything built on it.

**Desirable**

- **Mechanism proof:** demonstrates how the candidate fault actually reaches and produces the exact observed symptom — explaining why here, why now and why not in the working case — rather than stopping at a suspicious line.
- **Causal chain:** checks the explanation against every observed symptom, timestamp and unaffected case, treating any unexplained anomaly as a falsifier rather than noise.
- **Trigger vs. defect:** distinguishes the immediate spark — a payload, traffic spike, deploy or expiry — from the underlying broken invariant or defect that allowed it to fail.
- **Diagnostic trap:** when cold evidence genuinely cannot discriminate between remaining hypotheses, specifies the cheapest targeted log, metric or assertion needed to catch the cause decisively on next occurrence.

**Undesirable**

- **Red herring:** declaring a nearby oddity or unrelated bug the cause without proving reachability and mechanism for this failure.
- **Single-cause fallacy:** forcing two independent concurrent failures into one root cause, or overlooking an interacting chain of necessary conditions.
- **Shallow stop:** halting at the immediate spark — a payload, traffic spike or expiry — while the underlying broken invariant remains unexposed.

#### Handoff

Troubleshooting stays strictly diagnostic — leaving product code and live state untouched, reverting temporary local probes — and closes with proved mechanism, ruled-out paths, affected premises or live state, immediate sibling exposure and concrete next moves in the user's hands.

*Falls short:* closing with a vague symptom label or raw dump lacking mechanism, confidence bounds, ruled-out paths or concrete options, or hiding broken premises, sibling exposure and leftover data damage. *Overshoots:* silently patching code or mutating live state, leaving diagnostic edits behind, or drifting into fixing, redesigning, auditing, recovering state or running a postmortem without the user's call.

Why: diagnosis exists to give the user a trustworthy basis to decide what to do next — silent fixes bypass that choice, and dropped dead ends get re-investigated downstream.

**Desirable**

- **Ruled-out trail:** records which suspects and layers were tested and falsified alongside the proved cause so neither the user nor downstream work re-investigates dead ends.
- **Premise alert:** surfaces immediately when root-cause evidence invalidates an upstream requirement, design assumption or contract, or reveals corrupted live state needing separate recovery.
- **Sibling flag:** briefly notes immediate sibling paths sharing the same broken assumption so the eventual fix can cover the fault class without turning diagnosis into an audit.
- **Remediation options:** closes with concrete, trade-off-bearing next moves — containment, root fix, state repair, diagnostic trap or accepting as-is — calibrated to confidence and stakes, leaving the choice to the user.

**Undesirable**

- **Silent fix:** leaving an unagreed fix or un-reverted diagnostic edit in product code, config, tests or live state instead of handing off the diagnosis to the user.
- **Remediation creep:** sliding from explaining the cause into designing an architecture, rewriting tests, repairing corrupted records, tuning performance or running a postmortem without the user's call.
- **Unactionable verdict:** closing with a vague symptom label or raw signal dump lacking mechanism, confidence bounds, ruled-out paths or concrete next moves.
