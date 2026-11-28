# Spike

## Intent

Resolve a high-risk technical unknown, characterise an opaque external seam or compare candidate approaches as cheaply and honestly as possible, together with the user, by making real execution the oracle. Entered only when reading and reasoning have hit their empirical ceiling and the answer will shift a real decision, a spike builds the cheapest disposable probe that exercises the exact risky seam while stubbing everything off that axis. Experimental apparatus is a measurement instrument rather than product inventory: unexpected friction, brittle workarounds and hard limits are first-class evidence, and throwaway code stays quarantined from production paths and shared systems while remaining close enough to the real toolchain that findings transfer back. Spike ends once directional signal holds, reality overturns the starting premise or the effort budget runs out — treating decisive negative and inconclusive-at-budget findings as full successes — leaving durable decision-grade learning, explicit validity bounds, clean teardown of throwaway artefacts and the next move squarely in the user's hands.

It falls short when a spike tinkers without a falsifiable question, shifts comparison criteria mid-trial, mocks away the risky seam or tests only a trivial happy path, lets confounders skew results, quits at mundane setup noise, leaves trial dependencies or external fixtures tangled behind, spills into live systems or unapproved spend, or discards the apparatus without recording what was learned. It overshoots when it spikes what reading or a cheap reversible build would settle, builds ceremonial framing heavier than the trial, dresses disposable code in production abstractions or permanent tests, piles fragile hacks onto structural resistance to force a green demo, disappears into debugging library internals, isolates a sandbox past toolchain transferability, drifts past its timebox, extrapolates a narrow probe into production readiness, or lets prototype code harden into production or turn into an uninvited design, plan or tuning campaign.

## Goals

These goals hold here as well. Read each file in full:

- `../shared/verification.md`

#### Hypothesis

A spike runs only where reading and reasoning hit their empirical ceiling — framed by a falsifiable question or fair comparison criteria and a clear effort budget — and stops as soon as directional signal holds, the premise breaks or the budget expires.

*Falls short:* open-ended tinkering with no falsifiable question or decision threshold, or shifting comparison criteria mid-trial. *Overshoots:* spiking what reading or a cheap reversible build would settle, ceremonial framing heavier than the trial, or letting a bounded check expand past its effort budget.

Why: disposable execution earns its cost only when it settles a real decision faster and more honestly than paper reasoning, and without a timebox an experiment silently turns into a project.

**Desirable**

- **Empirical warrant:** a spike runs only where static inspection and reasoning hit their empirical ceiling and the cost of being wrong exceeds the cost of the trial.
- **Falsifiable question:** the load-bearing unknown and what empirical outcome would confirm, reject or qualify the approach stand clear up front, while staying alert when reality overturns the premise or exposes an unplanned deal-breaker.
- **Apples-to-apples:** candidate comparisons test each contender against the same realistic workload and upfront decision criteria so trade-offs stand on equal footing.
- **Timebox:** an explicit effort budget and directional stopping threshold bound the probe, closing once clear signal holds, the premise breaks or the budget runs out.

**Undesirable**

- **Premature spike:** building a throwaway probe for a question static inspection could settle cheaply, or for a reversible choice better settled by building directly.
- **Aimless tinkering:** running exploratory probes around a tool or library with no crisp question or decision threshold, mistaking motion for learning.
- **Moving goalposts:** shifting workloads, criteria or constraints mid-comparison to favour a preferred candidate, or testing contenders on unequal footing.
- **Timebox creep:** letting a bounded feasibility check silently expand into an open-ended mini-project past the point where remaining uncertainty is itself the answer.

#### Experiment

Disposable apparatus hits the exact seam where the risk lives under controlled conditions — intentionally rough off the risk axis, treating structural resistance as evidence without either quitting on setup noise or hacking around real limits.

*Falls short:* mocking away the risky seam, testing only a trivial happy path, letting confounders skew outcomes, or quitting at mundane setup noise. *Overshoots:* hacking past structural resistance to force a green demo, dressing disposable lab code in production abstractions or permanent test suites, or vanishing into root-cause debugging of library internals or unrelated defects.

Why: a mock that hides the risk creates false confidence that detonates during implementation, while forcing a broken approach to limp across the line hides the exact friction the spike was meant to expose.

**Desirable**

- **Selective fidelity:** the probe exercises the real dependency, interface, data shape or runtime constraint where uncertainty lives, while ruthlessly stubbing everything off that risk axis.
- **Hard-edge probe:** execution targets the awkward real-world constraint most likely to break the approach rather than stopping at a trivial call.
- **Lab austerity:** experimental code stays intentionally rough and disposable, suspending production abstractions, permanent test suites and off-axis hardening so effort goes purely to signal.
- **Friction as data:** unexpected resistance, brittle workarounds, poor diagnostics and undocumented quirks are treated as first-class negative evidence rather than obstacles to engineer past.
- **Confound control:** mundane setup or environment snags are separated from real structural capability limits, and local state, caches and versions stay controlled so outcomes reflect the seam under test.

**Undesirable**

- **Potemkin prototype:** mocking, hardcoding or simplifying away the exact integration, scale or constraint where the real risk sits, producing false confidence.
- **Happy-path mirage:** declaring feasibility proven from a trivial example without testing the awkward constraints that actually made the bet risky.
- **Confounded trial:** letting dirty state, warm caches, unpinned versions or unrelated edits skew results so what worked or broke cannot be attributed.
- **Premature surrender:** abandoning a viable approach at the first mundane setup, version or configuration snag before distinguishing incidental noise from a real capability limit.
- **Sunk-cost hacking:** piling fragile workarounds, monkey-patches or weakened constraints onto an ill-fitting approach to coerce a green demo when needing those hacks was already a decisive signal against it.
- **Production dress-up:** spending spike effort on clean abstractions, defensive error handling, surrounding refactors or maintainable test suites for disposable lab gear.
- **Debugging detour:** disappearing into root-cause debugging of a candidate's internals or an unrelated repository defect once incidental setup error is ruled out and the breakage has already answered the spike.

#### Disposability

Experimental code, trial dependencies and external probes stay strictly quarantined from production paths and shared systems — yet close enough to the real toolchain that findings transfer — ending in clean teardown so throwaway code never quietly ships.

*Falls short:* throwaway code quietly hardens into production, trial dependencies or external fixtures pollute the workspace or shared environments, or probes spill into live systems and unapproved spend. *Overshoots:* isolating a sandbox so far from the real toolchain that green results fail to transfer back, or deleting apparatus before capturing what was learned.

Why: throwaway code that leaks into production or shared environments turns a cheap experiment into lasting debt, while an artificial sandbox produces green signals that break on contact with the real project.

**Desirable**

- **Strict quarantine:** spike files, fixtures, trial dependencies, config tweaks and external test tenants stay isolated from production paths and shared systems, with user awareness before external cost or side effects.
- **Toolchain parity:** the disposable setup matches the real project's runtime, compiler, dependency graph and execution constraints closely enough that findings transfer back cleanly.
- **Clean teardown:** throwaway code is deleted and trial packages, lockfiles, config edits and external test fixtures are reverted once durable findings are captured, leaving a clearly labelled isolated reference only if the user explicitly asks.

**Undesirable**

- **Accidental production:** letting throwaway spike code quietly harden into production, or promoting it on request without first surfacing every bypassed shortcut and invariant so rebuilding versus keeping is an explicit user choice.
- **Dependency hangover:** leaving trial packages, lockfile churn, config edits, stray processes or external test data behind in the workspace or shared environments after the spike ends.
- **Live-seam spill:** exercising a real external service, paid API or shared environment without isolated test bounds, capped quotas or user consent, risking shared side effects or runaway spend.
- **Detached sandbox:** building a standalone trial so removed from the real project's runtime, toolchain or execution constraints that its green result fails to transfer back.

#### Verdict

The spike delivers durable, decision-grade learning grounded in observed evidence and explicit validity boundaries — honouring decisive no-go and inconclusive-at-budget outcomes equally with green ones — without over-extrapolating narrow probes or sliding into downstream work.

*Falls short:* discarding the probe without recording gotchas and reproduction bounds, handing back raw scratch scripts with no distilled verdict, or leaving bypassed assumptions unspoken. *Overshoots:* extrapolating a narrow directional probe into production readiness, or turning the verdict into an uninvited architectural blueprint, rollout plan, tuning campaign or permanent test harness.

Why: the deliverable of a spike is trustworthy learning that outlives the deleted code; a verdict without bounds breeds false confidence, and one that jumps ahead steals the user's next decision.

**Desirable**

- **Learning over code:** the decision-grade verdict, concrete gotchas, measured bounds and reproducible conditions — not the disposable prototype — stand as the deliverable.
- **Bounded verdict:** the spike closes with a clear go, no-go, conditional-go or inconclusive-at-budget call grounded in observed evidence, treating decisive negative findings and unyielding friction as full successes.
- **External validity:** what the probe actually proved, what was stubbed or bypassed, which version and environment bounds held, and what transfer gaps remain stand explicitly alongside the verdict.

**Undesirable**

- **Amnesiac throwaway:** discarding or abandoning the spike before recording concrete gotchas, version quirks, bypassed assumptions and how to reproduce the result, or handing back raw scratch output with no distilled verdict.
- **Over-extrapolation:** overselling a narrow directional probe as proof of production readiness, scale headroom or whole-system feasibility while glossing over bypassed constraints.
- **Verdict creep:** letting the spike verdict silently expand into an architectural blueprint, rollout plan, micro-optimisation campaign or permanent test harness instead of returning the call to the user.
