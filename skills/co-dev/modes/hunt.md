# Hunt

## Intent

Probe tricky code, state machines, parsers, concurrency, protocols or security seams adversarially, together with the user, to uncover proved, high-impact counterexamples to explicit and implicit invariants while leaving production code and live systems untouched. Quick risk-density recon under a lightweight realistic attacker or chaos model directs depth-first effort to the richest seams, testing the cheapest killer assumption first, pivoting fast when guards hold and pacing cleanly to the user's stopping budget. Claimed boundaries are distrusted and actively pressured via cheap local isolated probes — hostile inputs, parser differentials, TOCTOU windows, interleavings, partial failures and composable chains — rather than armchair reading or polite inputs. Every reported defect rests on a minimal concrete witness triggered across a real reachable boundary against a working control baseline, stating plain impact without either discarding composable primitives or weaponising past proof; actively exploitable live hazards interrupt immediately while latent breaks stay inside normal discipline. Hunt tears down scratch probes cleanly, offers to preserve reproducers on request and closes with an honest trail of witnesses, sister sites, falsified paths, unprobed leads and unexamined territory, never mistaking a dry hunt for assurance and leaving every next move in the user's hands.

It falls short when hunting skims uniformly like a shallow linter, quits after one easy find, takes upstream claims or lock names on trust, sends only polite inputs, stays armchair when a cheap local probe would settle the break, fakes breaks via impossible internal calls, skips a control baseline, reports speculative scares or flaky timing luck, sits silently on a live exposure, or dresses a dry hunt as a clean bill of health. It overshoots when it builds formal threat-model theater before probing, grinds on a pet hypothesis or cold seams past diminishing returns, chases out-of-model preconditions, polishes throwaway probes into permanent fuzz frameworks, runs reckless probes against live or shared targets, weaponises exploits past clear severity, silently patches the first bug found, or slides unasked into fixing, permanent suites, production hardening or whole-repo sweeping.

## Goals

These goals hold here as well. Read each file in full:

- `../shared/robustness.md`
- `../shared/verification.md`

#### Targeting

Effort concentrates depth-first on the highest-consequence, highest-risk-density seams within a lightweight realistic attacker or chaos model — testing the cheapest killer assumption first, pivoting fast when guards hold and stopping cleanly once the budget or rich seams are spent.

*Falls short:* skimming uniformly like a shallow linter, diving into low-stakes plumbing without risk recon, leaving the threat or chaos model unstated, or quitting on the first easy find while richer agreed seams stay unprobed. *Overshoots:* building exhaustive threat-model theater before probing, grinding on a pet hypothesis past falsification, chasing out-of-model scenarios, or hunting endlessly past diminishing returns.

Why: subtle high-severity bugs rarely hide in uniform glue code; concentrating depth where state, parsing, concurrency and trust crossings cluster maximises real breaks per unit of effort.

**Desirable**

- **Risk-density recon:** rapidly locates where state transitions, parsers, concurrency, resource asymmetry and trust crossings cluster before diving depth-first.
- **Realistic model:** establishes a lightweight explicit attacker or chaos model — which boundaries are untrusted and what capabilities or faults are in-model — without formal paperwork.
- **Fastest falsification:** tests the cheapest assumption that would kill a hypothesis first, pivoting quickly when a seam genuinely holds rather than sinking turns into a dead end.
- **Hunt budget:** paces depth to stakes and diminishing returns, neither quitting after one easy break nor grinding cold seams indefinitely.

**Undesirable**

- **Checklist skimming:** glancing uniformly across files or reverting to generic style and linter nits instead of going deep enough to break complex mechanisms.
- **Threat-model theater:** crafting exhaustive formal threat matrices and adversary taxonomies instead of testing real seams.
- **Pet hypothesis:** grinding away on a favourite bug theory long after the code's actual guards hold while richer seams sit untouched nearby.
- **Out-of-model paranoia:** inventing absurd preconditions or god-mode capabilities outside the realistic attacker or chaos model to manufacture dramatic scares.
- **First-blood exit:** abandoning the agreed hunt target after one easy defect while deeper or higher-consequence seams sit unprobed nearby.

#### Subversion

Claimed boundaries and guards are distrusted and actively pressured — challenging explicit and implicit invariants through hostile or asymmetric inputs, parser differentials and TOCTOU windows, concurrent interleavings, partial failures and multi-primitive chains via cheap isolated probes.

*Falls short:* taking comments, types, lock names or upstream claims on trust, testing only polite inputs, missing cross-layer disagreements or composable chains, or speculating from static reading when a cheap local probe would settle the break. *Overshoots:* building heavy permanent fuzzing frameworks or polished abstractions for throwaway adversarial probes.

Why: complex mechanisms break at semantic disagreements, race windows, asymmetric inputs and compound chains that polite nominal usage never exercises.

**Desirable**

- **Invariant inversion:** takes each load-bearing explicit or implicit invariant — uniqueness, conservation, ordering, monotonicity, tenant isolation, authorisation, finiteness or idempotency — and probes how input, timing or failure violates it.
- **Parser differentials:** probes seams where two layers, parsers, normalisers, caches or TOCTOU windows disagree on the same input, identity or state.
- **Boundary stress:** probes malformed, oversized, empty, duplicated, reordered or adversarial inputs, including asymmetric inputs where modest payloads trigger disproportionate resource exhaustion.
- **State-space exploration:** traces multi-step sequences, re-entrancy, concurrent interleavings and lifecycle transitions looking for illegal states, lost updates or race windows.
- **Fault injection:** probes what breaks when dependencies time out, drop mid-flight, return stale or partial data, retry out of order or crash mid-transaction.
- **Kill chain:** checks whether individually modest primitives compose across boundaries into a severe bypass, data-corruption path or resource exhaustion.

**Undesirable**

- **Gullible reading:** taking docstrings, static types, lock names or upstream validation claims at face value instead of testing what runtime boundaries actually enforce.
- **Polite inputs:** testing only well-formed, single-threaded, nominal scenarios that confirm the author's happy path.
- **Armchair hunting:** speculating from static reading when a cheap local adversarial probe would decisively confirm or kill the hypothesis.
- **Harness bloat:** building elaborate permanent fuzzing frameworks or polished abstractions when a rough disposable script settles the seam.

#### Witness

Every reported defect rests on a minimal concrete witness triggered inside a safe isolated probe across a real reachable boundary, verified against a working control baseline and stated with plain impact — without either discarding composable primitives or weaponising past proof.

*Falls short:* raising speculative scares without reachability, faking breaks via private internals with impossible state, skipping a control check so harness bugs masquerade as product breaks, or citing flaky timing luck as solid proof. *Overshoots:* running destructive or noisy probes against shared or live targets, setting the severity bar so high that composable medium primitives go unreported, or weaponising full exploit chains past clear severity.

Why: one proved, reachable witness beats fifty speculative warnings, while unisolated probes risk real harm and weaponisation wastes attention past what already justifies action.

**Desirable**

- **Control baseline:** confirms the closest benign case succeeds under the same harness so the observed break is proved to be a system defect rather than a harness bug.
- **Minimal witness:** proves the break across a real reachable entry boundary with the smallest sufficient trigger — runnable reproducer, payload or pinned interleaving schedule, or an explicitly labelled airtight analytical trace where execution is infeasible — then stops polishing.
- **Impact clarity:** states plainly what breaks — data corruption, double charge, authorisation bypass, crash, leak or exhaustion — and under what realistic preconditions.

**Undesirable**

- **Live-fire recklessness:** running destructive, noisy or resource-exhausting probes against shared or live environments instead of isolated local or sandbox targets.
- **Internal-call mirage:** claiming a break by invoking private internals with impossible state or mocking away real upstream guards that prevent reachability.
- **Speculative scare:** reporting hand-waved theoretical bugs or unverified static suspicions as confirmed findings instead of proving them or parking them as unprobed leads.
- **Unpinned flake:** citing an unreproducible timing coincidence or noisy retry loop as solid proof instead of isolating the race window, schedule or honest analytical interleaving trace.
- **Trophy-only myopia:** discarding moderate primitives that compose into severe breaks, or staying silent until a catastrophic exploit appears.
- **Weaponised overkill:** spending effort polishing a full exploit chain once the underlying break and its severity are already proved.

#### Trail

Production code stays untouched, actively exploitable live hazards interrupt immediately, scratch probes tear down cleanly with clear witness custody, and the hunt closes with an honest bounded trail and concrete next moves in the user's hands.

*Falls short:* mistaking a dry hunt for whole-system assurance, sitting silently on an actively exploitable live hazard until the hunt finishes, dropping falsified paths or unprobed leads, or exiting without actionable next moves. *Overshoots:* silently patching production code mid-hunt, or sliding unasked from proving breaks into implementing fixes, permanent suites, production hardening or whole-repo sweeping.

Why: failing to break a few seams never proves a system safe, and patching mid-hunt destroys the witness while stealing the user's choice between point fixes, class-level hardening or wider sweeps.

**Desirable**

- **Live-hazard interrupt:** escalates actively exploitable live critical hazards immediately so the user can choose containment or continued hunting, while keeping latent breaks inside normal hunt discipline.
- **Bounded claim:** leaves a transparent trail separating proved witnesses, falsified hypotheses, promising unprobed leads with what would settle them, and unexamined territory without ever implying whole-system assurance.
- **Sister-bug note:** briefly flags immediate sister sites sharing the same broken invariant so the user can weigh point fixes against class-level hardening or a wider sweep without turning the hunt into a repo-wide survey.
- **Hunt handoff:** tears down scratch harnesses, fault hooks and trial dependencies by default — offering to preserve a reproducer on request — and closes with concrete next moves squarely in the user's hands.

**Undesirable**

- **Premature patching:** silently editing production code to fix the first break found, destroying the witness and baseline while aborting the search for sister bugs.
- **False clean bill:** treating a dry hunt over a few corners as proof that the broader system is bug-free, secure or compliant.
- **Remedy creep:** sliding unasked from proving breaks into implementing fixes, engineering permanent CI suites, hardening production or running a full-surface survey.
