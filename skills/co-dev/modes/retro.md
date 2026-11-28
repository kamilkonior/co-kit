# Retro

## Intent

Turn what a concrete episode or recurring pattern just taught into a lasting, verified upgrade to the working system, together with the user — or a deliberate decision to hold off. Whether the episode was an incident, recurring drag, a collaboration breakdown, a near miss or a smooth run, sensemaking stays grounded in what was visible at the time, traces the working-system conditions behind it without blame or hindsight, and scales its depth to the stakes. Recurrence and stakes decide whether the system should change at all and keep attention on the vital few upgrades. Each chosen upgrade lands in the lightest durable substrate at the narrowest scope that covers everyone affected, favours removing friction or stale rules over adding new ones, and stays bounded, self-contained, cheap to reverse and cleanly apart from in-flight product work. Upgrades are shown to act at the real decision point without false alarms, governing edits land only with explicit user approval of what changes and who it binds, and multi-step tooling projects or product repairs route separately. Retro ends when the upgrade is in place — or the thin signal is consciously left alone — the user has seen the evidence and the change, can say in their own words what will be different from now on and for whom, and work returns under the improved setup.

It falls short when retro stops at discussion, blame, performative apology or hollow action items, stops at the immediate slip, ignores near misses or bright spots, normalises chronic drag, picks fragile reminders where a cheap check or tool tweak would hold, hides a shared trap in private notes, or lands an untested rule that never fires in practice. It overshoots when it digs into forensic archaeology past what is actionable, turns one-off noise or luck into rigid dogma, swings autonomy to extremes after a single slip, lands too many changes at once, piles on noisy rules without pruning, silently lands changes to governing skills, memory or repo rules without consent, runs a shadow pipeline for a multi-step tooling project, or fixes product code inside retro.

## Goals

These goals hold here as well. Read each file in full:

- `../shared/coherence.md`
- `../shared/verification.md`

#### Attribution

The episode — failure, recurring drag, near miss or bright spot — rests on concrete evidence and traces to the working-system conditions that made it likely, candidly on both sides and without blame, hindsight or endless digging.

*Falls short:* personal blame, performative apology, stopping at the surface slip, judging process quality by luck, or ignoring near misses and wins. *Overshoots:* forensic archaeology past what is actionable, or abstracting into systemic forces so remote that nothing actionable remains.

Why: an upgrade aimed at the wrong cause or at luck adds permanent drag; one that stops at fault or the immediate slip lets the same friction return.

**Desirable**

- **Double-loop learning:** questions the rule, tool, assumption or setup that produced the outcome, not only the single slip within it.
- **Local rationality:** reconstructs why actions made sense to everyone involved given the cues, affordances and constraints visible at the time.
- **Blameless postmortem:** treats breakdowns as properties of the system, tooling and information available, keeping both sides candid without personal fault or defensive deflection.
- **Contributing factors:** names the interacting conditions that made friction or failure easy, or a smooth run repeatable, rather than hunting one scapegoat.
- **Near miss:** treats close calls caught only by luck or heroics as early warnings of a fragile system before real harm lands.
- **Bright spots:** captures what went unusually smoothly so effective enabling conditions are understood and protected rather than left accidental.

**Undesirable**

- **Human error:** concluding that a person or agent should simply remember or try harder next time — including performative self-blame — without changing what misled them.
- **Hindsight bias:** judging what happened as if the outcome had been obvious beforehand, hiding what actually misled the work at the time.
- **Outcome bias:** condemning a sound process for bad luck, or canonising a lucky shortcut as a repeatable practice.
- **Proximate cause:** stopping at the immediate slip or technical defect without asking what in the working system allowed or hid it.
- **Forensic archaeology:** reconstructing history, transcripts or minutiae past what is needed to see the actionable working-system lesson.

#### Threshold

Recurrence and stakes decide whether the working system should change at all, holding back on thin noise and focusing attention on the vital few upgrades.

*Falls short:* normalising chronic drag, waving off high-stakes near misses, or leaving clear recurring friction untouched. *Overshoots:* turning a one-off fluke into permanent dogma, swinging autonomy to extremes after one slip, or landing a burst of changes nobody can absorb.

Why: changing the working system on thin noise adds lasting drag, while ignoring chronic friction or high-stakes fragility guarantees the same pain returns.

**Desirable**

- **Recurrence and stakes:** weighs frequency against blast radius and irreversibility, acting on a first-time high-stakes failure or near miss while holding back on low-stakes flukes.
- **Watchful waiting:** when stakes are low and evidence is thin or likely a one-off, records the signal and holds off changing the working system until recurrence justifies it.
- **Vital few:** selects the one or two highest-leverage upgrades that address the core pattern, leaving minor ripples alone so each change can be absorbed and judged.

**Undesirable**

- **Normalisation of deviance:** tolerating chronic friction, noisy checks or recurring workarounds until they feel normal.
- **Fighting the last war:** installing a rigid guardrail tailored to the exact shape of one past incident that will not repeat the same way.
- **Hasty generalisation:** turning a narrow episode or context-dependent win into sweeping dogma that burdens unrelated work.
- **Pendulum swing:** overcorrecting autonomy or rigour after a single episode, swinging from trust to micromanagement or from caution to blind delegation instead of calibrating the boundary that failed.
- **Change fatigue:** landing a bundle of rules, checks and process tweaks from one episode so none stick and nobody can tell which helped.

#### Leverage

Each chosen upgrade lands in the lightest durable substrate at the narrowest scope that covers everyone affected, favours subtracting friction over adding rules, and costs future work less than it saves.

*Falls short:* hollow takeaways that vanish on exit, willpower reminders where a cheap check or tool tweak would hold, or burying a shared trap in private notes. *Overshoots:* rule bloat, brittle automation for soft judgment, noisy checks that train people to bypass them, or leaking local quirks into global rules.

Why: a lesson nobody carries forward changes nothing, and a noisy, bloated or mis-scoped guard taxes every future task more than the mistake it tried to prevent.

**Desirable**

- **Hierarchy of controls:** picks the strongest proportionate substrate: eliminate the friction or automate a cheap check or tool first; use instructions, templates, agreements or trigger-backed habits only where judgment belongs.
- **Poka-yoke:** changes the repo, tool, schema or check so the bad path is prevented or caught automatically rather than left to memory.
- **Forcing function:** places the check or cue directly in the path of the work where it will actually fire, not in a document someone must remember to open.
- **Subsidiarity:** places each upgrade at the narrowest durable scope that covers everyone affected — private notes, shared repo or global setup — neither hiding shared traps in private notes nor leaking local quirks everywhere.
- **Net positive:** the upgrade saves more future attention and effort than its carrying cost, preferring to remove friction or prune stale rules over piling on new ones.

**Undesirable**

- **Good intentions:** ending in chat notes, action items or promises to watch out next time, with nothing changed in the working system.
- **Wrong lever:** writing prose instructions for what a cheap lint or script would catch reliably, or building brittle automation for a soft matter of judgment.
- **Process accretion:** piling up instructions, hooks or checks episode after episode without pruning, until attention and workflow buckle under their own weight.
- **Process theater:** adding a ritual, template field or boilerplate rule that creates busywork without preventing recurrence.
- **Alarm fatigue:** installing noisy checks or nag rules with high false positives that train humans and agents to ignore or bypass them.
- **Scope mismatch:** leaking a project-specific quirk into global rules, or burying a shared repo trap in private notes so teammates and fresh sessions keep hitting it.

#### Enactment

Each upgrade is a bounded, self-contained, cheap-to-reverse meta-change approved by the user, shown to fire cleanly at the real decision point, revisitable if it drags, and kept apart from product work or pipeline projects.

*Falls short:* landing a rule or check that never triggers in practice, modifying governing substrates without consent, or locking soft habits in permanently with no way to revisit them. *Overshoots:* improvising an engineering-sized tooling overhaul inside retro, tangling product fixes into process diffs, or wrapping a simple tweak in heavy meta-tracking.

Why: an unproved or unowned upgrade either fails silently when the moment returns or quietly warps how every future session runs.

**Desirable**

- **Counterfactual replay:** exercises the upgrade against the episode's actual decision point or failure case — and healthy paths — so executable checks and non-executable cues alike are shown to fire cleanly without false alarms.
- **Clean separation:** keeps working-system diffs cleanly apart from in-flight product work, routing discovered product repairs separately so each can be reviewed and reversed alone.
- **Reversible trial:** treats soft workflow rules, templates and agreements as revisitable experiments with a simple cue for noticing whether they help or should be pruned.

**Undesirable**

- **Silent self-edit:** landing changes to governing skills, memory, repo instructions, hooks or checks without explicit user approval of what changes and who it binds.
- **Dead letter:** landing a rule, template or check that looks sound on paper yet sits unread or never triggers where the real work happens.
- **Shadow pipeline:** improvising a multi-step tooling, harness or skill overhaul inside retro instead of promoting it into the delivery pipeline.
- **Product creep:** quietly fixing a product bug or refactoring application code inside retro, tangling product and process diffs.
