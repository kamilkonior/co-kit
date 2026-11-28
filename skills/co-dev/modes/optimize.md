# Optimize

## Intent

Deliver a real, empirically verified improvement in latency, throughput, memory, query load, build time, bundle size or resource cost in the actual system, together with the user. Grounded in an agreed performance budget, coupled counter-metrics and a repeatable baseline on a representative workload, work locates the dominant cost driver empirically rather than by folklore, removes avoidable waste along the critical path before reaching for caches or low-level tricks, isolates one lever per measurement pass and re-profiles as bottlenecks shift. Correctness, edge cases and readability hold by default: any gain that bends semantics, freshness, consistency or accuracy, or pays material counter-metric or maintenance cost, waits for explicit user consent, changes that fail to earn their ongoing complexity revert cleanly, defects exposed by profiling are surfaced or fixed as bugs rather than masked, and contract or architectural ceilings are proved with empirical cost accounting rather than worked around. Optimize ends once the budget is met, marginal return turns negative or a structural ceiling is proved — backed by reproducible before-and-after distributions, passing correctness checks, deterministic regression guardrails and any remaining trade-offs or headroom named cleanly.

It falls short when bottlenecks are guessed without profiling, wins rest on toy workloads, averages that hide tails, distorted runs or proxy overfitting, multiple tweaks bundle unattributed complexity, headline drops silently regress semantics or counter-metrics, caches mask avoidable waste or underlying bugs, surrender rests on hunch, or fragile wins land without guardrails. It overshoots when it builds benchmark theater for an obvious win, tunes cold paths or chases diminishing returns past the budget, keeps complexity that failed to pay off, wires flaky wall-clock timing gates into CI, sneaks architectural redesign into local tuning, or bounces tractable local waste upstream prematurely.

## Goals

These goals hold here as well. Read each file in full:

- `../shared/verification.md`
- `../shared/robustness.md`
- `../shared/craft.md`

#### Measurement

Every optimisation rests on an agreed budget, a repeatable baseline on a representative workload, full distribution visibility and controlled observation, scaling rigor to the size of the uncertainty.

*Falls short:* toy or warm workloads, averaging away tail behaviour, optimising isolated proxies that diverge from end-to-end cost, or distorted and unsafe live measurements. *Overshoots:* benchmark theater or chasing statistical precision past what the decision needs.

Why: intuition about bottlenecks and single-run averages are reliably wrong; only realistic, controlled and proportional measurement shows where cost truly lives and whether a change helped.

**Desirable**

- **Performance budget:** a concrete target metric and stopping boundary define good enough before tuning begins.
- **Representative baseline:** the current workload is measured repeatably at realistic data scale, distribution skew, concurrency, build mode and cold or warm state, pairing deterministic causal proxies with end-to-end verification.
- **Tail awareness:** full distributions, upper percentiles, worst-case behaviour, cold starts and allocation spikes are tracked alongside medians rather than trusting averages alone.
- **Controlled benchmark:** warm-up, cache state, compiler dead-code elimination, profiler overhead and ambient load stay controlled, keeping heavy or mutating probes off live shared systems.

**Undesirable**

- **Toy benchmark:** measuring on tiny inputs, uniform distributions, warm caches, debug builds or synthetic loops that miss real scale, I/O, contention or tail behaviour.
- **Micro-benchmark trap:** optimising isolated micro-timings or proxy counters that vanish, get eliminated or reverse under real end-to-end execution.
- **Flaw of averages:** celebrating a mean or median drop while upper percentiles, cold misses or memory spikes stay flat or worsen.
- **Measurement distortion:** letting profiler overhead, debug flags, ambient load, unisolated state or invasive live-system probes corrupt the signal or disrupt shared environments.
- **Benchmark theater:** spending hours building elaborate statistical harnesses when a cheap trace, query plan or bundle map already proves an order-of-magnitude win.

#### Critical path

Profiling locates the dominant cost driver before code changes and re-checks as bottlenecks shift, eliminating avoidable work first and confining specialisation strictly to proven hot paths.

*Falls short:* folklore-driven tuning without profiling, masking avoidable waste behind caches or tuning yesterday's hotspot after the bottleneck moved. *Overshoots:* specialising cold paths or grinding on minor cost fractions that cannot move the end-to-end metric.

Why: one algorithmic, I/O or structural elimination beats twenty micro-tricks, and every optimisation on a cold path pays permanent complexity for negligible end-to-end return.

**Desirable**

- **Profile, don't guess:** a profiler, trace, query plan, build timeline, bundle map or cost breakdown isolates the dominant driver before touching code and re-profiles after each win as bottlenecks shift.
- **Amdahl's law:** effort targets the dominant share of end-to-end cost rather than tuning a minor fraction that cannot move the overall metric.
- **Algorithmic leverage:** avoidable queries, I/O, quadratic scans, allocations, bloated dependencies and repeated build work are eliminated before reaching for caching, concurrency or low-level tricks.
- **Hot path focus:** specialisation stays confined to the proven critical path while cold paths remain plain and readable.

**Undesirable**

- **Blind optimisation:** editing code during a tuning pass on folklore or intuition of what looks slow without profiling or measuring before and after.
- **Stale profile:** continuing to tune an earlier hotspot after prior wins shifted the dominant bottleneck elsewhere.
- **Polishing the cold path:** complicating rarely executed code or low-impact helpers that barely move the end-to-end metric.
- **Cache-first reflex:** layering on caching with its staleness, memory, invalidation, cold-miss and thundering-herd costs before eliminating avoidable work underneath.

#### Payback

Each lever is tested cleanly enough to attribute cause and effect, kept only when verified gain earns its ongoing complexity, bounded by the budget and protected by deterministic regression guardrails.

*Falls short:* bundling speculative tweaks so dead weight rides along on a winner, keeping fast-paths that failed to pay off, or landing fragile wins with no guardrail. *Overshoots:* tuning past the budget on diminishing returns, or wiring hardware-sensitive wall-clock timing gates into shared CI.

Why: every fast-path left behind charges maintenance tax forever; only isolated attribution, honest reverts and deterministic guardrails keep wins real and durable.

**Desirable**

- **Isolated lever:** one optimisation lever is measured per pass so cause and effect remain attributable and dead complexity never rides along on a real winner.
- **Keep or revert:** a change stays only when verified end-to-end gain earns its complexity and operational tax; dead ends revert cleanly without sunk-cost attachment.
- **Regression guardrail:** surviving wins leave proportional, deterministic protection against silent backsliding through query-count bounds, bundle budgets, allocation limits, plan checks or reproducible benchmark commands.

**Undesirable**

- **Shotgun tuning:** bundling multiple speculative tweaks into one measurement pass so zero-gain or harmful complexity hides behind one real win.
- **Complexity hangover:** leaving complicated fast-paths, custom pools, unsafe tricks or extra tuning knobs behind after measurement showed negligible or negative gain.
- **Tuning past budget:** chasing diminishing returns once the agreed target is met or marginal gain no longer pays for added complexity.
- **Unguarded win:** landing a sensitive hot-path optimisation with no deterministic guardrail or recorded baseline, leaving routine future edits to regress it silently.
- **Flaky timing gate:** wiring hardware-sensitive wall-clock latency assertions into shared CI so runner jitter blocks unrelated work.

#### Safeguards

Optimisations protect correctness and coupled counter-metrics, gate non-free trade-offs on explicit user consent, fix exposed defects as bugs and prove structural ceilings empirically rather than hacking past them or punting prematurely.

*Falls short:* silent semantic drift, whack-a-mole counter-metric regressions, tuning around underlying bugs, sneaking architectural or contract redesign inside local tuning, or surrendering short of budget on hunch. *Overshoots:* blocking explicit user-approved trade-offs, or bouncing tractable local waste upstream before exhausting local leverage.

Why: faster wrong results, hidden downstream regressions and masked bugs trade visible speed for silent damage, while a proved structural ceiling is a real engineering answer rather than a cue for brittle workarounds.

**Desirable**

- **Counter-metrics:** coupled resources such as tail latency, memory, write amplification, contention, accuracy, cold-miss cost and downstream load are tracked alongside the headline metric.
- **Explicit trade-off:** correctness and semantics hold by default, and any gain that bends freshness, consistency or accuracy, or pays material memory, cold-miss or maintenance cost, goes to the user for consent before committing.
- **Fix, don't mask:** when profiling uncovers a leak, broken cache key, runaway retry, misconfiguration or regression, the underlying defect is surfaced or fixed as a bug rather than tuned around.
- **Structural ceiling:** when local tuning hits a contract, schema, consistency-model or architectural wall, remaining cost is proved empirically and handed upstream with hard numbers rather than forced with hacks or abandoned on hunch.

**Undesirable**

- **Whack-a-mole:** celebrating a headline drop while silently regressing tail latency, memory, accuracy, cold-start cost, contention or downstream load.
- **Silent semantic shift:** buying speed by quietly degrading accuracy, ordering, freshness, tenant isolation, validation or edge cases without user consent.
- **Tuning around a bug:** layering caches, pools, throttles or fast-paths over a broken mechanism instead of fixing the underlying defect.
- **Stealth re-architecture:** quietly altering public contracts, persisted schemas, consistency guarantees or system architecture inside local tuning instead of pausing to settle shape with the user.
- **Premature escalation:** bouncing tractable local waste upstream for redesign or rewrite before exhausting measured local leverage.
