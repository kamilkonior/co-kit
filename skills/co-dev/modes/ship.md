# Ship

## Intent

Carry an accepted change across external or irreversible boundaries into its real destination, together with the user — whether landing a commit, pull request, package, release or production deployment. Release controls scale to blast radius and irreversibility: target state, upstream drift and release timing are checked upfront, routine release plumbing stays inside ship while accepted behaviour stays untouched, and read-only checks and local reversible release prep run freely so user consent concentrates at genuinely external or irreversible gates. Risky changes expose progressively with pre-set abort criteria and a real way back, or explicit roll-forward contingencies past one-way boundaries. If reality exposes a defect, missing migration seam or corrupted live state, exposure halts first and diagnosis, fixing or state repair hands off cleanly rather than panic-patching or engineering platform upgrades mid-flight. Direct, non-invasive destination signals prove the exact new artefact landed, is active and holds up against baseline rather than stopping at a push, merge or green exit status. Ship closes cleanly at full exposure with consumers and operators honestly informed and long-horizon follow-ups tracked, at an honest intermediate state for asynchronous boundaries, or cleanly aborted back to baseline with failure signals preserved and the next move in the user's hands.

It falls short when shipping stops at a push or green deploy without live proof, mistakes a stale or inactive version for live success, crosses external or irreversible gates without explicit consent, verified target state or a real retreat path, silently alters accepted behaviour during conflict resolution or panic-patching, sneaks in last-minute polish, runs destructive changes before stability holds, hides breaking changes from consumers, or leaves a rollout half-shipped. It overshoots when it imposes pre-flight, rollout or announcement theater on low-risk reversible changes, prompts on read-only checks or local reversible plumbing, bounces mechanical release edits back to building, derails into mid-flight platform engineering, runs invasive live checks, aborts on uncorroborated monitor noise, camps on dashboards indefinitely, or blocks closure on long-horizon follow-ups.

## Goals

These goals hold here as well. Read each file in full:

- `../shared/fidelity.md`
- `../shared/verification.md`

#### Release integrity

What crosses the boundary is the exact accepted change — built clean, aimed at the verified target and reconciled with upstream reality — keeping mechanical release plumbing inside ship without silent behavioural edits or platform detours.

*Falls short:* crossing on drifted or unchecked target ground, shipping a dirty, wrong-target or rebuilt-differently artefact, silently editing accepted behaviour during conflict resolution, sneaking in last-minute polish, or shipping into a freeze or active incident. *Overshoots:* prompting on read-only checks or local reversible plumbing, bouncing mechanical release edits back to building, imposing heavy pre-flight ceremony on low-risk reversible changes, or derailing into platform engineering.

Why: silent mutations between acceptance and release bypass review, while platform detours and pre-flight bureaucracy turn safe shipping into gridlock.

**Desirable**

- **Release readiness:** target preconditions — destination ref or environment, upstream drift, configuration, secrets, dependencies, packaging and target checks — are verified before crossing, confirming exact diff and target on direct entry without forcing full review ceremony.
- **Build once:** the exact artefact verified in dry run or staging is what gets promoted or published, from a clean tree free of untracked litter or leaked secrets.
- **Mechanical-only edits:** routine release plumbing — version bumps, tags, lockfiles, release manifests and strictly mechanical conflict resolution — stays inside ship while accepted behaviour stays untouched; any semantic conflict pauses to reconcile upstream.
- **Release window:** timing accounts for change freezes, active incidents, concurrent releases and operator availability proportional to blast radius.

**Undesirable**

- **Silent merge edit:** quietly altering accepted behaviour while resolving upstream rebase or merge conflicts instead of reconciling upstream.
- **Last-minute polish:** sneaking unreviewed tweaks, extra cleanups or incidental commits onto the release after acceptance.
- **Dirty artefact:** shipping from an unclean tree, a rebuilt-differently binary, the wrong ref or target account, or a package contaminated with dev files or secrets.
- **Mid-release platform engineering:** derailing a release to fix flaky CI, rewrite deploy scripts or build new dashboards instead of shipping safely and deferring tooling upgrades for later.
- **Prep theater:** prompting for approval on read-only checks, dry runs or local reversible release plumbing, bouncing mechanical release edits back to building, or imposing heavy pre-flight ceremony on low-risk reversible changes.

#### Rollout

The change crosses into live exposure in controlled steps proportional to blast radius and irreversibility, with pre-set abort criteria and a real way back — or an evidence-preserving abort and routed handoff if reality rejects it.

*Falls short:* exposing risky changes all at once, applying destructive changes before stability holds, mistaking a code revert for a real rollback, pressing on past warning signals, or panic-patching live code. *Overshoots:* imposing multi-stage ceremony on small reversible changes, or aborting on uncorroborated monitor noise.

Why: real destinations hold live state, concurrent traffic and real consumers that local checks never fully reproduce, and mid-flight panic turns containable faults into outages.

**Desirable**

- **Progressive rollout:** exposure expands in stages proportional to risk — from direct release for low-risk reversible changes to staging, canary, ring or pre-release channels for higher stakes.
- **Decouple deploy from release:** where warranted, code lands inactive behind a flag or dark launch so exposure switches independently of redeploying.
- **Backward compatibility:** old and new versions coexist cleanly across rolling deploys, schemas, APIs, running clients and rollbacks, escalating multi-phase live transitions when compatibility seams are missing.
- **Abort threshold:** concrete live failure signals that halt or revert the rollout are settled before crossing, not rationalised mid-flight.
- **Kill switch:** a concrete, verified way to halt exposure or revert exists before crossing — and past genuine one-way boundaries such as immutable registries, public tags or external effects, explicit roll-forward or deprecation contingencies stand ready.
- **Clean abort:** when live reality exposes a defect, volatile failure signals are preserved, exposure halts or reverts to the known-good baseline, and diagnosis, fixing or live-state repair hands off cleanly.

**Undesirable**

- **Big-bang cutover:** exposing a risky change to all users, regions or consumers at once where staged rollout or pre-release validation was possible.
- **Irreversible migration:** applying a destructive schema, data or contract change before the new version is proven stable and retreat is no longer needed.
- **Illusory rollback:** assuming a code revert or re-tag undoes a release after live state diverged, caches or clients pinned the change, or an immutable registry locked it in.
- **Go fever:** continuing to ramp or leaving a degraded release live past abort signals out of momentum or schedule pressure.
- **Panic patching:** editing product code in place inside ship when a live failure hits instead of containing exposure and handing off diagnosis or a proper fix.
- **Release theater:** imposing multi-stage rollouts, flags or formal ceremony onto a small, low-risk, easily reverted change.
- **Hair-trigger abort:** halting or rolling back on uncorroborated monitor jitter or pre-existing baseline noise without comparing against the pre-ship baseline.

#### Live proof

Direct, non-invasive signals from the real destination confirm the exact new artefact landed, is active and holds up against baseline without degrading its surroundings.

*Falls short:* treating a push, merge or green exit status as shipped, mistaking a cached or inactive old version for live success, shipping blind with no destination signals, or exiting before delayed paths settle. *Overshoots:* running invasive live checks that disturb real users or pollute live state, or camping on dashboards indefinitely after steady-state health is confirmed.

Why: a green push or deploy only proves bits arrived; direct live signals prove the new version actually runs and survives where it counts.

**Desirable**

- **Activation proof:** confirms the exact new version or artefact is actually running, serving, installed or enabled in the real destination rather than a cached previous version or inactive path.
- **Golden signals:** judges live health from real destination signals — target CI on the merged head, clean install, error rates, latency, saturation, logs or downstream jobs — against the pre-ship baseline, not exit status alone.
- **Synthetic check:** a non-invasive end-to-end probe exercises the shipped artefact in its real destination without disturbing real users or mutating live state.
- **Soak period:** after exposure, enough real time, traffic or scheduled cycles settle proportional to risk to catch delayed failures across async jobs, caches, retries or leaks.

**Undesirable**

- **Deploy and pray:** pushing, merging or publishing and walking away without confirming the change landed and behaves as intended live.
- **Ghost deploy:** mistaking a green pipeline, cached response, unflipped flag or old-version health check for active execution of the shipped change.
- **Blind launch:** shipping with no logs, metrics, error tracking or live probe able to show whether the change is working or failing.
- **Invasive probe:** running live checks that mutate customer state, trigger unintended external effects, add harmful load or pollute production metrics.
- **Perpetual babysitting:** camping on dashboards indefinitely chasing perfection after steady-state health is confirmed.

#### Landing

The release reaches a clean terminal or honest async-interim state, with consumers and operators honestly informed in native format and long-horizon follow-ups tracked without blocking closure.

*Falls short:* leaving a rollout stranded mid-ramp, altering external behaviour or compatibility without warning consumers or operators, or leaving temporary release scaffolding abandoned in limbo. *Overshoots:* blocking closure on multi-day cleanups or tooling work, or broadcasting ceremonial release noise for trivial internal changes.

Why: shipping crosses out of the local workspace into third-party reliance; an unannounced breaking change or half-finished rollout shifts hidden cost onto consumers and operators.

**Desirable**

- **Terminal state:** the release closes at full intended exposure, safely aborted at baseline, or at an honest intermediate state for asynchronous boundaries such as a pull request awaiting review or checks — leaving no temporary release scaffold stranded and long-horizon follow-ups owned.
- **Honest versioning:** versions, tags and release channels accurately signal external compatibility and scope to both humans and automated consumers.
- **Release notes:** whoever consumes or operates the change knows what shipped, what changed externally and any required action, in the format the project uses.

**Undesirable**

- **Half-ship:** leaving a staged rollout stuck mid-ramp, an approved release unpromoted, an unverified async backfill or temporary release scaffolding abandoned in limbo.
- **Silent breaking change:** altering external behaviour, APIs, defaults, version semantics or operational expectations without warning consumers or operators.
- **Closure creep:** blocking release closure on long-horizon cleanups, flag retirement or unrelated follow-ups after live stability is confirmed.
- **Announcement theater:** broadcasting verbose release essays or noisy consumer notifications for trivial, internal or non-user-facing changes.
