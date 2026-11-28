# Decommission

## Intent

Subtract something completely when nothing replaces it, together with the user, scaling evidence and staging to blast radius and irreversibility, whether the target is a stale flag or a production service and its data. Disuse, or the exact set of remaining callers, rests on evidence that reaches every caller, runtime evidence wherever static analysis cannot. Intentional loss of capability, notice to those who lose it, and the end state of data, keys, credentials and public names are decided deliberately, never left to fall out of the deletion. Severance strands no reader, puts irreversible destruction behind a reversible stage that has held, and binds every temporary scaffold to a dismantling trigger. Teardown removes every footprint the target owns while cutting cleanly at seams shared with healthy neighbours. Decommission ends when absence and surviving health are confirmed where the target ran, only deliberate tombstones and bounded archives remain, and anything pending or found still alive is in the user's hands.

It falls short when decommissioning trusts static search over runtime reality, deletes live targets cold or in an order that strands readers or opens names to takeover, destroys data that had to be kept or leaves personal data behind, removes the code while tables, credentials, alerts and spend live on, or closes at a merged change without checking where the target ran. It overshoots when it chases certainty of zero usage forever, keeps kill switches, standbys and archives alive with no expiry, imposes brownout ceremony on private dead code that is cheap to restore, or pulls healthy neighbours into the deletion pass.

## Goals

These goals hold here as well. Read each file in full:

- `../shared/coherence.md`
- `../shared/verification.md`
- `../shared/fidelity.md`

#### Obsolescence

Disuse, or the exact set of remaining callers, is established from evidence that reaches every caller, in proportion to the cost of being wrong, with a watched, reversible scream test where evidence leaves doubt.

*Falls short:* trusting static search alone, missing periodic, dynamic or external callers, or running a scream test nobody watches. *Overshoots:* chasing certainty of zero usage forever, or staging brownout ceremony for dead code that is cheap to restore.

Why: proving a negative in a live system is asymmetric: one missed caller breaks someone, while demanding certainty forever means nothing ever dies.

**Desirable**

- **Runtime usage proof:** where callers can hide from static analysis, disuse rests on live evidence such as traffic, logs, query history and schedules observed across their full period.
- **Scream test:** where evidence leaves doubt on a live surface, the target is made reversibly unavailable while someone watches, so hidden callers surface while restoring is still instant.

**Undesirable**

- **Grep-only confidence:** taking zero static references in one repository as zero callers, missing reflection, config strings, webhooks, periodic jobs, pinned clients and analytics queries.
- **Unheard scream:** a scream test runs with no one and no telemetry watching, or a scream is waved off instead of the target being restored and the caller taken to the user.
- **Scream-test theater:** multi-week brownouts, stakeholder notices or archival ceremony for private dead code that the compiler proves unused or version control restores cheaply.

#### Disposition

What the removal ends is decided deliberately: any intentional loss of capability and its notice belong to the user, and persisted data, keys, credentials and public names reach a chosen end state before anything is destroyed.

*Falls short:* cutting off consumers without notice, destroying data that had to be kept or the keys it needs, leaving personal data in backups, or releasing names and pointers to takeover. *Overshoots:* keeping data, archives and credentials alive forever just in case, or seeking notice and sign-off for removals that end nothing anyone relies on.

Why: what a removal destroys or releases usually cannot be taken back, and the obligations attached to data and names outlive the code that held them.

**Desirable**

- **Sunset contract:** where capability is actually lost, the user owns the loss and its cutoff, and those who rely on it get realistic notice before it.
- **Data fate:** each persisted store reaches a chosen end, purged, archived with an expiry or retained as obligations require, and the keys that retained data needs survive as long as the data.
- **Namespace and identity fate:** public names, endpoints, buckets, package names, redirect URIs and credentials are revoked, tombstoned or reserved deliberately, and retired identifiers such as flag keys or enum numbers are not reused while old clients remain.

**Undesirable**

- **Blindsided cutoff:** removing a capability that consumers rely on without notice, a window or the user's decision.
- **Data incineration:** destroying tables, buckets, audit trails or encryption keys that legal, compliance or retained backups still depend on.
- **Orphaned PII:** personal data surviving a purge in backups, replicas, exports, logs or analytics copies.
- **Dangling takeover:** destroying a backing resource or releasing a name while DNS records, redirect URIs, package references or other public pointers still target it, opening it to hijack.
- **Just-in-case hoarding:** keeping data, archives and credentials alive without expiry because they might be useful someday, until the subtraction adds cost and exposure.

#### Severance

The target is cut in an order that strands no reader, irreversible destruction waits behind a reversible stage that has held, and every temporary scaffold carries an owner and a dismantling trigger.

*Falls short:* hard-deleting live surfaces with no reversible stage, dropping what running versions still read, or leaving kill switches and standbys in permanent limbo. *Overshoots:* gating removals that version control restores cheaply, or holding the cut open past its trigger and blocking closure on a window that could be handed off with an owner and a trigger.

Why: deletion is the one step without an undo, so its order and the reversible stage before it decide whether a missed caller costs minutes or a restore from backup.

**Desirable**

- **Reverse-order cut:** in-flight work drains, and callers, triggers, public pointers and every running version stop reaching a resource before it is destroyed.
- **Reversible-first gate:** destroying what cannot be restored waits behind a reversible stage that has held, and the user sees what remains unproven alongside what becomes irreversible before it is crossed.
- **Trigger-bound scaffold:** kill switches, brownout rules, redirects and standbys each carry an owner and the condition that dismantles them, held in a durable record when that condition falls after the session.

**Undesirable**

- **Cold-turkey deletion:** hard-deleting a live endpoint, queue, table, credential or flag of uncertain usage with no reversible stage.
- **Deletion skew:** dropping a column, config key, secret or queue while running versions, replicas or cached clients still read it during a rolling deploy.
- **Limbo scaffold:** leaving kill switches, brownout rules, redirects or warm standbys alive with no expiry, so the half-dead target keeps its cost and complexity.

#### Teardown

Every footprint the target owns, apart from what was deliberately kept, is removed in every layer it reached, the cut stops at seams shared with healthy neighbours, and absence is confirmed where the target actually ran.

*Falls short:* deleting the visible code while tables, flags, credentials, alerts and spend live on, letting declarative tooling recreate what was deleted, or closing at a merged change. *Overshoots:* cutting through dependencies that live siblings still need, or reshaping healthy neighbours in the same pass.

Why: half-deleted systems keep accruing spend, paging on-call with dead alarms and misleading engineers long after everyone thought they were gone.

**Desirable**

- **Full-stack sweep:** everything the target owns and nobody chose to keep goes with it, past the code: flags and their provider rules, data stores, schedules, secrets and access policies, infrastructure definitions, alerts and dashboards, CI jobs, exclusive tests, dependencies and runbooks.
- **Shared-seam check:** artefacts exclusive to the target are told apart from utilities, tables, roles or queues that live siblings still use, and the cut is made cleanly at that seam.
- **Flag-branch collapse:** a retired flag leaves only the surviving path, with its dead branch, conditional scaffolding and provider rule gone rather than a hardcoded toggle left behind.
- **Verified absence:** the target is confirmed gone where it ran, with no traffic, schedules, provider rules, declared infrastructure or spend left in any region or account.

**Undesirable**

- **Ghost residue:** the entry point is gone while orphaned flags, zombie tables, idle spend, stale credentials, dead alerts, forgotten schedules or obsolete runbooks remain.
- **Declarative resurrection:** deleting by hand what infrastructure-as-code, GitOps or auto-provisioning still declares, so the next sync recreates it or wedges its state.
- **Collateral amputation:** deleting a shared utility, column, access policy, secret or queue that a live sibling still needs.
- **Commented-out corpse:** commenting out dead code or leaving a permanently disabled branch instead of deleting it and trusting version control.
- **Paper decommission:** treating a merged change as done while instances still run, provider rules still serve, or another region or scheduler still fires.
- **Spring-cleaning sprawl:** reshaping the healthy neighbours a cut exposes past what the clean cut needs, turning a deletion into a refactor.
