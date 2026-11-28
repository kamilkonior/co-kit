# Test

## Intent

Raise durable, high-signal verification confidence in existing behaviour, together with the user, by engineering the verification suite and harness itself — adding risk-weighted coverage, pinning undocumented legacy behaviour ahead of change, strengthening weak assertions, deflaking unreliable checks and pruning obsolete weight so meaningful regressions fail loudly while harmless internal refactors stay green. Each risk sits at the cheapest layer that still exercises the real failure seam, backed by real collaborators or verified fakes and proven to fail when target behaviour breaks rather than trusting an immediate green run against existing code. Production behaviour stays invariant: suspected defects, ambiguous legacy quirks, production races hiding behind flakes and hard structural testability walls go to the user rather than being silently patched in production code, canonised as requirements or twisted into brittle hacks. Tests stay hermetic, deterministic, readable in place and fast enough to run continuously, with meaningful deletions and flake quarantines agreed explicitly. Test ends when the agreed risk surface holds proven, maintainable coverage, every surfaced anomaly or seam trade-off has a clear disposition, and the codebase is safer to change tomorrow.

It falls short when tests check only happy paths, verify mocks or mirrored production formulas instead of real contracts, trust unverified first-run greens or shallow smoke assertions, canonise suspected legacy bugs as permanent requirements, mask flakes or production races behind sleeps, retries or timing patches, or leave cryptic, order-dependent failures that train people to hit rerun. It overshoots when it chases arbitrary coverage percentages on trivial code, duplicates the same rule across every layer, locks in private wiring or sprawling snapshots, strips concurrency out of concurrency tests in the name of determinism, over-abstracts setup into opaque fixtures or helper hierarchies, trades realism for vanity speed, silently edits or distorts production code, or drifts into report-only critique, production hardening, runtime benchmarking or throwaway adversarial fuzzing.

## Goals

These goals hold here as well. Read each file in full:

- `../shared/verification.md`
- `../shared/craft.md`
- `../shared/coherence.md`
- `../shared/diagnosis.md`

#### Portfolio

Effort targets high-consequence contracts, boundaries and failure modes at the cheapest layer that exercises the real failure seam, pruning dead or redundant tests as readily as adding new ones.

*Falls short:* testing only happy paths, leaving integration seams or failure modes unguarded, or letting obsolete and duplicate tests accumulate. *Overshoots:* chasing coverage percentages on trivial boilerplate or framework internals, duplicating the same rule across every layer, or dropping load-bearing safety nets without consent.

Why: every test carries ongoing runtime and maintenance cost; coverage aimed at real regression risk compounds safety, while vanity and redundant tests turn the suite into drag.

**Desirable**

- **Risk-weighted coverage:** concentrates depth on load-bearing contracts, state transitions, edge values, error paths and rich-space invariants, using parameterised or property-based checks where helpful, rather than uniform line counts or trivial plumbing.
- **Right test level:** matches each risk to the cheapest layer that still exercises the real failure seam without repeating the same rule across layers.
- **Suite pruning:** deletes or consolidates obsolete, duplicate or permanently low-signal tests, with user consent before dropping meaningful coverage, so carrying cost stays low.

**Undesirable**

- **Ice-cream cone:** piling slow, brittle end-to-end tests onto pure logic, or testing only isolated helpers while real integration seams go unchecked.
- **Layer duplication:** re-testing the exact same fine-grained rule across unit, integration and end-to-end layers so one rule change breaks checks in every tier.
- **Happy-path myopia:** testing only nominal, well-formed inputs while leaving error contracts, boundary values and degenerate states unguarded.

#### Oracle

Tests assert observable contracts and state transitions against real collaborators or verified fakes, using independent expectations proven to fail when existing behaviour breaks.

*Falls short:* mocking away the risk, relying on drifting fakes, duplicating production formulas in assertions, writing shallow smoke assertions, or trusting first-run greens on existing code. *Overshoots:* asserting private wiring or sprawling snapshots, insisting on heavy live dependencies where a verified fake suffices, or running exhaustive mutation sweeps on trivial logic.

Why: an oracle written against already-working code passes on its first run by default; without independent expectations, real seams and fault proof, green runs give false confidence.

**Desirable**

- **Observable contract:** asserts on public outputs, persisted state transitions or boundary effects rather than private methods, call counts or internal wiring.
- **Real collaborators:** uses real databases, parsers, filesystems or serialisers where integration risk lives in queries, schemas, concurrency or protocol semantics.
- **Verified fake:** where a real collaborator is too costly or nondeterministic, uses an in-memory fake backed by shared contract checks rather than an ad-hoc stub.
- **Mutation proof:** when adding or strengthening tests around existing code, temporarily injects and reverts a local fault to prove the oracle fails when target behaviour breaks rather than trusting an immediate green pass, without exhaustive campaigns on trivial logic.

**Undesirable**

- **Mock mirror:** mocking so many collaborators that the test merely echoes its own mock setup and stays green when real integration breaks.
- **Fake drift:** relying on hand-rolled stubs or fakes whose error codes, constraints or edge semantics silently diverge from the real collaborator.
- **Mirrored logic:** computing expected outputs by duplicating production formulas or algorithms inside the test so shared defects pass cleanly.
- **Shallow assertion:** checking only no-throw, non-nullness or a generic success status while ignoring postconditions, persisted state or invariants.
- **Snapshot sprawl:** capturing large opaque snapshots or incidental formatting that breaks on harmless edits and gets blindly updated instead of reviewed.

#### Invariance

Production behaviour stays strictly invariant: undocumented legacy behaviour is pinned explicitly as observed reality rather than endorsed spec, discovered defects and production races go to the user, and testability walls are negotiated cleanly without hacks or production distortion.

*Falls short:* silently editing production code, canonising broken legacy behaviour as a permanent requirement, or distorting production design with test-only hooks. *Overshoots:* twisting tests into fragile reflection or monkey-patch hacks to avoid surfacing a seam trade-off, or refusing a cheap coarse safety net until legacy code is redesigned.

Why: silently changing production under cover of testing bypasses the user's call, while locking bugs in or contorting either side around untestable seams trades safety for brittle debt.

**Desirable**

- **Characterisation pin:** pins undocumented or legacy behaviour explicitly as currently observed reality, labelled clearly as a temporary safety net ahead of change rather than an endorsed specification.
- **Bug-vs-spec flag:** separates intended contracts from suspected defects, ambiguous legacy quirks or production races, surfacing them with concrete evidence so the user decides whether to fix, pin or leave them.
- **Seam negotiation:** lays down a cheap coarse black-box safety net where viable, and surfaces hard structural testability walls as an explicit trade-off rather than hacking around them or silently refactoring production code.

**Undesirable**

- **Stealth prod edit:** leaving unagreed changes to production logic, error semantics, public contracts or architecture under a test task without the user's call.
- **Bug ossification:** asserting broken or accidental legacy behaviour as a permanent normative requirement instead of flagging the defect or labelling a temporary characterisation pin.
- **Test-induced design damage:** proposing or introducing test-only branches, widened visibility purely for white-box tests, or mock-only constructor sprawl in production code just to satisfy unit tests.
- **Seam contortion:** twisting tests into fragile reflection, private-field inspection or global monkey-patch hacks to avoid surfacing a seam trade-off, or refusing a coarse safety net until legacy code is redesigned.

#### Determinism

Every test is isolated, order-independent and repeatable across environments and calendar boundaries, and flaky failures are attributed to their real root cause and proven stable under stress rather than masked.

*Falls short:* shared mutable state, wall-clock sleeps, ambient clock or network coupling, masking flakes or production races behind retries and timing patches, or trusting a single lucky rerun. *Overshoots:* spinning up heavy per-test environments where cheap isolation works, or serialising away real concurrency and timing execution in tests meant to guard concurrent behaviour.

Why: a flaky suite trains engineers to ignore red builds and hit rerun, while papering over flakes hides real concurrency defects until production.

**Desirable**

- **Hermetic isolation:** each test owns its state, temp files, ports, transactions, locale and network boundary so tests pass identically in any order, in parallel and offline.
- **Controlled nondeterminism:** once a production race is ruled out, replaces wall-clock sleeps, ambient clocks, timezones, unsorted maps and unseeded randomness with injected clocks, condition waits, seeded generators or deterministic fakes without stripping concurrency from tests meant to verify it.
- **Flake attribution:** isolates whether an intermittent failure stems from test setup, timing or state leakage versus a real production concurrency or state defect before altering either side, quarantining genuinely external flakes explicitly with the user rather than muting them silently.
- **Stress-proven deflake:** validates a deflaked test under repeated runs, shuffled order and parallel load rather than trusting a single lucky green pass.

**Undesirable**

- **Sleep-and-pray:** using arbitrary wall-clock delays or padded timeouts to paper over async coordination instead of waiting on an explicit condition or controlling the clock.
- **Retry papering:** masking flakiness with test retries or widened timing tolerances, or hiding a real production concurrency defect behind test-side timing workarounds.
- **Order-dependent suite:** sharing mutable globals, singletons, databases, environment variables or static ports across tests so failures appear or vanish with execution order or parallelism.
- **Ambient coupling:** letting tests silently bind to live external networks, wall-clock dates, daylight-saving shifts or host timezones so runs fail across environments or calendar boundaries.

#### Harness

Tests, fixtures and helpers explain themselves in place, diagnose failures immediately and stay fast enough to run continuously without burying setup behind hidden fixtures or sacrificing realism for vanity speed.

*Falls short:* hidden fixtures or implicit setup, opaque helper hierarchies, cryptic failure diffs, or slow suites developers skip locally. *Overshoots:* stripping real seams or isolation in pursuit of microsecond speed, adding heavy new test infrastructure past the risk, or copy-pasting noisy setup where a lean builder would clarify causal inputs.

Why: a suite nobody can read on failure or afford to run locally stops guiding everyday changes and decays into CI-only bureaucracy.

**Desirable**

- **DAMP clarity:** favours self-contained, readable test cases so a failing test explains its scenario in place, complementing single-source truth for shared schemas and builders.
- **Test data builder:** uses lean builders or factories with sensible defaults so each test overrides only the inputs causally relevant to its assertion, keeping boilerplate out of sight.
- **Actionable failure:** structures assertions, diffs and failure context so a red run pinpoints which invariant broke, expected versus actual and under what inputs without stepping through a debugger.
- **Fast feedback loop:** keeps inner-loop verification fast enough to run continuously through cheap isolation such as transaction rollbacks, immutable templates or in-process seams, separating slow integration tiers explicitly without dropping needed realism.

**Undesirable**

- **Mystery guest:** hiding causally relevant data inside external fixture files, giant seed dumps or implicit pre-populated state so a reader cannot tell from the test body why the assertion holds.
- **Test-helper labyrinth:** over-abstracting setup and assertions into nested base classes, hidden setup chains or bespoke test DSLs so nobody can tell what a test actually sets up or checks.
- **Slow-suite creep:** adding redundant full-stack boots, expensive per-test resets or untiered heavy scenarios until developers stop running the suite locally.
