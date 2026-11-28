# Onboard

## Intent

Build durable operational agency for the user in an unfamiliar repository, service or subsystem, together with them, with no change planned yet — leaving repository code, documentation and tooling unchanged. Calibrated to both what the user already masters and the role they are stepping into, orientation maps outer boundaries and runtime topology before internals, traces a real end-to-end flow alongside hotspots and living versus legacy idioms, inspects commands before running cheap safe local loops or falling back pragmatically to live manifests and CI, and traces how typical changes reach production. Broken setup steps, stale docs, flaky checks and sharp edges encountered along the way are recorded briefly as landmarks of the terrain rather than hijacking orientation into debugging, rewriting docs, refactoring or solving a hypothetical task. Onboard works as a layered, re-enterable ramp and ends once the user holds a coherent spine and independent navigation reflexes, knows safe verification loops and where their map ends, and leaves with a concise trail of landmarks ready to act on concrete work.

It falls short when onboarding becomes a directory-tree recitation, code-only inspection detached from config and runtime boundaries, whiteboard storytelling or a brochure tour that hides real hazards, blind execution of uninspected commands, a role-blind firehose or passive lecture, or fluent agent mastery that leaves the user unable to navigate alone. It overshoots when it plunges prematurely into peripheral internals, turns into grievance archaeology over tech debt, yak-shaves broken local setup instead of falling back, talks down or forces curriculum theater, silently edits code or manufactures sprawling unrequested docs, slides into solving a hypothetical change, or marches on past day-one footing.

## Goals

These goals hold here as well. Read each file in full:

- `../shared/synthesis.md`

#### Orientation

The user holds a prioritised operational map of the system — outer boundaries and runtime topology before internals, a real end-to-end flow, hotspots and living versus legacy idioms — grounded in the live system rather than directory trees or idealised prose.

*Falls short:* a directory-tree recitation, a code-only view detached from config and runtime edges, or a brochure tour that hides real traps and legacy seams. *Overshoots:* premature deep-dives into peripheral internals, or cynical tech-debt archaeology before the system is understood.

Why: someone who has mapped the outer context, traced a live path and seen where real change and sharp edges concentrate can reason safely on day one; someone who memorised a folder tree cannot.

**Desirable**

- **System context:** outer boundaries, callers, external dependencies, state stores and runtime topology are mapped before opening internals.
- **Tracer bullet:** one real request, command or event is traced end to end from entry point to side effect or output before surveying the rest of the system.
- **Hotspots:** where active change, complexity, coupling and past bugs concentrate is highlighted rather than giving every module equal weight.
- **Local idioms:** how new work actually lands is shown from the live codebase and recent merges, separating living conventions from legacy seams not to imitate.

**Undesirable**

- **Directory tour:** reciting the folder tree top to bottom instead of tracing real runtime flows, boundaries and responsibilities.
- **Code-only myopia:** explaining application source while ignoring the configuration, flags, workflows, background jobs or runtime boundaries where operational behaviour lives.
- **Brochure tour:** presenting an idealised story of the repository while glossing over flaky tests, brittle setup, active legacy seams or operational footguns.
- **Premature deep-dive:** plunging into peripheral helpers or unrelated packages before outer boundaries and the core execution path hold.
- **Grievance archaeology:** turning orientation into a tour of tech debt and past mistakes that breeds dread or premature rewrite urges before the system is understood.

#### Footing

The user knows how the system actually builds, runs, verifies and reaches production from live scripts, manifests and CI — inspecting commands before execution, exercising cheap safe local loops early and falling back pragmatically when local execution is blocked.

*Falls short:* whiteboard storytelling detached from real commands and configuration, or running unfamiliar commands blindly without checking what they touch. *Overshoots:* yak-shaving broken local environment or tooling into a debugging detour, or forcing costly local builds when live CI and read-only checks fit the role better.

Why: operational agency starts when a newcomer knows which commands are safe to run, how changes actually ship and what ground truth to check when local setup will not cooperate.

**Desirable**

- **Run it first:** a cheap, safe local build, run or targeted test loop is inspected and exercised early to confirm runnable ground.
- **Hazard map:** scripts, manifests and targets are inspected before execution, explicitly separating cheap, safe local commands from costly, flaky, stateful, external or destructive ones.
- **Path to production:** how a typical change moves from local check through build, verification, CI and release or deployment to live signals is traced from actual pipeline and repo definitions.
- **Pragmatic ground:** when local execution is blocked or disproportionate to the user's role, grounding shifts to live CI workflows, manifests, tests and read-only checks rather than stalling or trusting prose.

**Undesirable**

- **Whiteboard literacy:** clean conceptual storytelling detached from real commands, entry points, configuration and verification loops.
- **Blind execution:** running unfamiliar setup, seed, migration, build or test commands without first inspecting what local state, cost or external systems they touch.
- **Setup yak-shaving:** disappearing into debugging broken local tooling, containers or environment setup instead of logging the snag and falling back to live CI or read-only ground.

#### Transfer

Understanding lands durably in the user's head — calibrated to their background and target role, paced interactively so independent navigation sticks, and anchored in a concise trail of landmarks plus honest map edges.

*Falls short:* a role-blind tour, firehose dump, passive lecture, broken analogy, silent blind spots, or fluent agent navigation that leaves the user unable to operate alone. *Overshoots:* curriculum theater, grilling the user like a student, or talking down over basics they already own.

Why: a map held only by the agent or dumped faster than working memory can integrate leaves the user dependent the moment the session ends.

**Desirable**

- **Scaffolding:** depth, vocabulary and entry angle are calibrated to both what the user already masters and the role they are stepping into, skipping owned basics.
- **Bridging analogy:** unfamiliar local abstractions are anchored to patterns the user already owns, with where the analogy breaks down stated explicitly.
- **Dry-run navigation:** once the spine holds, operational readiness is checked with a concrete trace of where a representative change or investigation would start, revealing gaps without turning into an exam.
- **Reading path:** a concise, ordered trail of load-bearing entry points, safe commands, key invariants and recorded rough edges is left so the user can reopen and navigate independently afterwards.
- **Map edges:** unvisited subsystems, opaque corners and unverified areas are named explicitly so the user knows where their map ends and what can wait until needed.

**Undesirable**

- **Role blindness:** delivering the same generic tour regardless of whether the user is stepping into feature work, on-call operations, review, integration or returning after time away.
- **Firehose:** dumping every service, convention, flag and quirk at once until working memory floods and nothing sticks.
- **Passive lecture:** monologuing through the system without checking the user's background, pacing or steering.
- **Proxy mastery:** fluent agent comprehension and lookup that answers smoothly in conversation while leaving the user unable to locate entry points or navigate independently afterwards.
- **Broken analogy:** leaning on a simplifying metaphor without stating where it stops holding, planting misconceptions that bite later.
- **Talking down:** over-explaining standard concepts the user already owns, or dumbing down mechanisms past technical truth.
- **Curriculum theater:** treating a peer like a student through scripted lessons, forced exercises or pop quizzes.

#### Restraint

Orientation maps the system as it stands without altering code, docs or tooling — logging friction cleanly, resisting mode hijacks and stopping as a layered ramp once day-one footing holds.

*Falls short:* hijacking orientation into patching bugs, rewriting stale docs or generating sprawling guides, refactoring awkward seams, sliding into solving a hypothetical change, or touring endlessly past day-one footing. *Overshoots:* withholding broken loops or sharp edges out of fear of derailing, or clinging to passive orientation after a concrete task takes over.

Why: every spotted wart tempts an immediate detour that derails orientation, while touring past safe footing delays real work that teaches the remaining corners faster just in time.

**Desirable**

- **Friction log:** broken setup steps, stale docs, flaky checks and sharp edges spotted along the way are recorded briefly with exact locations so the user avoids traps and can route follow-on work later without derailing orientation.
- **Just-in-time ramp:** orientation works as a layered, re-enterable ramp that stops once day-one footing holds, deferring peripheral subsystems until real work pulls them in and yielding cleanly when a concrete task or defect takes over.

**Undesirable**

- **Fix-it hijack:** abandoning orientation to patch a spotted bug, fix a failing test or clean up awkward code instead of logging it as a landmark.
- **Doc-writing creep:** silently editing stale repository docs or manufacturing sprawling unrequested onboarding guides instead of leaving a concise personal trail of landmarks.
- **Premature problem-solving:** sliding from orientation into scoping, designing or implementing a hypothetical future change when no change was planned yet.
- **Endless tour:** marching through peripheral subsystems after the user already holds safe day-one footing or is ready to act.
