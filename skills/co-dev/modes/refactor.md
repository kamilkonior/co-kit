# Refactor

## Intent

Reshape existing working code for structural fitness while keeping external behaviour strictly invariant, together with the user — whether paying down concrete structural drag or carving a clean seam ahead of upcoming work. Starting from a trustworthy baseline, observable behaviour and published or persisted contracts are pinned proportionally to risk, code advances in reversible green-to-green increments with mechanical moves kept apart from structural edits, and structural work never mixes with bug fixes, features, semantic tuning or new failure policies. Brittle white-box tests lift cleanly onto behavioural seams without weakening assertions, discovered defects and contract ambiguities are preserved and surfaced rather than fixed in place, dead-end reshapes revert cleanly to green, and refactoring stops rather than absorbing competing designs, live contract crossings or dead subsystems. Refactor ends at a clean local candidate whose structural payoff is earned, equivalence is verified, no half-migrated idiom remains, and surfaced anomalies or adjacent debt stand clearly in the user's hands.

It falls short when edits silently shift edge cases, error semantics, timing or published contracts, reshape opaque or dynamic code on visual optimism, rewrite failing tests without proving equivalence, break the build across wide edits, shuffle complexity sideways, leave two competing idioms behind, or smuggle architectural redesign inside a cleanup. It overshoots when it creates cosmetic churn, builds speculative abstractions or heavy harnesses and micro-step ceremony for cheap compiler-checked moves, pulls the sweater thread into sprawling cleanups or a big-bang rewrite, treats private internals as sacred, or stalls routine local cleanups on mechanical approvals or premature upstream escalations.

## Goals

These goals hold here as well. Read each file in full:

- `../shared/modularity.md`
- `../shared/coherence.md`
- `../shared/craft.md`
- `../shared/verification.md`

#### Preservation

Externally observable behaviour — including edge cases, failure semantics, timing and resource bounds, and published or persisted contracts — remains identical before and after, while purely private internals stay free to reshape.

*Falls short:* silent behavioural drift, mixing fixes or features with structural edits, mutating published or persisted contracts as if private, or rewriting failing tests without proving equivalence. *Overshoots:* treating accidental private internals as sacred contract, or leaving structure tangled because brittle white-box tests depend on private wiring.

Why: the moment behaviour shifts inside a refactor, neither tests nor reviewers can tell structural movement from semantic change — while freezing private internals makes safe evolution impossible.

**Desirable**

- **Two hats:** structural refactoring and behavioural edits never share a step or commit.
- **Published interface:** distinguishes externally observable, serialised, persisted, logged, reflected or cross-boundary contracts — including implicit caller dependencies — from purely private internals that stay free to reshape.
- **Latent-defect flag:** when reshaping uncovers a pre-existing bug or ambiguous legacy quirk, preserves current behaviour and surfaces the anomaly to the user rather than fixing or canonising it in place.
- **Boundary test migration:** lifts brittle white-box tests onto observable behavioural seams apart from structural edits, proving moved checks still fail on regressions rather than weakening assertions.

**Undesirable**

- **Stealth behaviour change:** silently fixing a discovered bug or altering an edge case, error shape, evaluation order, default, timing bound or side effect inside a refactor.
- **Contract leak:** reshaping a published API, wire format, persisted schema, config key or reflection target as if it were private code, breaking external callers or rolling deploys.
- **Sacred internals:** treating accidental private signatures, internal call sequences or implementation-coupled test hooks as untouchable contract, freezing messy structure in place.
- **Assertion laundering:** rewriting, loosening or deleting a failing test on the assumption it merely tested old internals, without proving behavioural equivalence.

#### Trajectory

Code moves from a trustworthy green baseline to its new shape through reversible, compiling, green-to-green increments backed by risk-proportional safety nets, finishing staged replacements and retreating cleanly from dead ends without ceremony.

*Falls short:* refactoring risky or dynamic code without pinning behaviour first, breaking the build across wide edits, abandoning half-migrated idioms, muddying diffs with mixed mechanical moves, or patching a failing reshape instead of reverting. *Overshoots:* building heavy harnesses, staged bridges or tedious micro-step ceremony for cheap compiler-checked moves.

Why: structural edits stay safe, reviewable and cheap to abandon only while every step remains green and reversible; broken worlds and half-finished bridges compound risk faster than they pay it down.

**Desirable**

- **Safety net:** before reshaping weakly tested, dynamic, aliased or concurrent code, pins observable behaviour atop a trustworthy green baseline using the cheapest contract-honest check proportional to risk.
- **Green-to-green:** advances through reversible, compiling, always-passing increments small enough that regressions localise immediately and work can pause or revert cleanly.
- **Branch by abstraction:** for wider internal replacements, introduces the new seam beside the old, migrates callers incrementally while staying green, and contracts the temporary bridge before closing.
- **Mechanical separation:** isolates compiler- or tool-safe mechanical moves and renames from conceptual structural edits so equivalence stays reviewable and history survives.
- **Mikado method:** when a reshape exposes deeper hidden coupling or stops paying off, reverts dead edits cleanly to the last green checkpoint and resolves prerequisites or changes tack rather than hacking forward.

**Undesirable**

- **Blind refactoring:** trusting visual equivalence across untested, dynamic, aliased, exception-heavy or concurrent code without pinning real behavioural contracts first.
- **Broken-world refactoring:** tearing up working code across many files so nothing compiles or passes until the whole restructure completes.
- **Two-worlds codebase:** migrating some callers to a new seam or helper while leaving siblings on the old idiom or leaving temporary adapter bridges behind.
- **Sunk-cost reshape:** salvaging a failing structural direction with adapter hacks, flags or partial rewrites instead of reverting cleanly to the last green checkpoint.
- **Harness paralysis:** building heavy characterisation suites, staged bridges or tedious micro-step ceremony for cheap, compiler-checked moves.

#### Payoff

The reshape earns a concrete, legible net reduction in coupling, complexity or friction for a real flaw or upcoming change, stays tightly bounded, and stops or routes upstream as soon as the seam is clean or the work outgrows refactoring.

*Falls short:* shuffling complexity sideways, polishing dead code instead of retiring it, or stalling routine local cleanups on mechanical approvals and premature upstream escalations. *Overshoots:* cosmetic churn, speculative refactoring of stable code, recursive sprawl across neighbouring modules, rewriting working code from scratch, or smuggling competing architectural trade-offs inside a cleanup.

Why: every structural edit carries review, merge and regression cost; reshaping without real payoff trades tangible risk for taste, while improvising architecture inside a cleanup bypasses design.

**Desirable**

- **Targeted smell:** answers a concrete structural flaw or an upcoming change fighting the grain of the code, not vague aesthetic dissatisfaction.
- **Seam:** carves a boundary where behaviour can be pinned, substituted or changed locally without editing tangled internals.
- **Bankable increment:** each completed stage leaves the codebase strictly cleaner and consistent on its own, so stopping early still yields shippable value.
- **Structural exit:** stops once the target boundary is clean or the upcoming change is easy — recording adjacent debt for later and stopping to surface competing designs, live contract crossings or dead subsystems rather than absorbing them.

**Undesirable**

- **Lateral shuffle:** moving code across files, classes or helpers without reducing coupling, cognitive load or change amplification.
- **Cosmetic churn:** renaming, reordering or reformatting code to personal taste without structural gain, paying real review and merge-conflict cost for style.
- **Boy-scout sprawl:** pulling the sweater thread from one messy module into adjacent callers and neighbours until a bounded cleanup snowballs into an unreviewable sweep.
- **Big-bang rewrite:** discarding messy, battle-tested code to rewrite from scratch instead of transforming incrementally, silently dropping encoded edge cases.
- **Speculative refactoring:** reshaping stable code nobody is changing for hypothetical future flexibility that has not arrived.
- **Stealth redesign:** quietly settling competing architectural trade-offs or inventing a new paradigm under cover of a refactor instead of pausing to settle shape with the user.
