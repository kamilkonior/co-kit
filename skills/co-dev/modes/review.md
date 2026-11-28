# Review

## Intent

Evaluate someone else's pull request, patch, diff or RFC in its real surrounding context, together with the user, turning grounded judgement into an unmistakable verdict and agency-preserving feedback written in a voice the user stands behind. Scrutiny reads beyond changed hunks into untouched callers, invariants, compatibility, tests, operational edges and absent or weakened safeguards, checking cheap read-only evidence before objecting. Judgement scales to stage, blast radius and review round — flagging sprawling diffs early, raising fundamental stoppers in round one, verifying fixes and affected seams on re-review without moving goalposts, and never blocking solid incremental work over taste or unrelated debt. Because an external author owns the proposal while the user is the reviewer of record, candid internal analysis — working picture, verified clean scope, unverified blind spots and team-norm calls — stays apart from concise, severity-tagged, curiosity-first comments for the author, while the author's branch and external forges stay untouched without explicit sign-off. Review ends when the user owns an aligned verdict with bounded exit criteria, holds author-facing comments they endorse and can defend, and any broader work stands cleanly separated for their call.

It falls short when review skims diff hunks in isolation, trusts green CI or persuasive PR prose over primary evidence, misses omitted callers or weakened checks, drops unverified suspicions onto the author, blurs or politeness-masks blockers into flat comment soup, conceals uninspected blind spots, trails off without a verdict aligned to comments, or outputs stiff, patronising boilerplate. It overshoots when it blocks solid incremental work over personal taste or perfectionism, invents mandatory nits on clean diffs, holds a change hostage to unrelated legacy debt, polishes inline details beneath a fatal round-one stopper, moves goalposts across rounds, turns routine review into a repo-wide sweep or adversarial interrogation, backseat-codes or hijacks the author's branch, or posts externally without consent.

## Goals

These goals hold here as well. Read each file in full:

- `../shared/synthesis.md`
- `../shared/coherence.md`
- `../shared/robustness.md`
- `../shared/verification.md`

#### Scrutiny

The proposal is examined in its real surrounding context — against its stated goal, untouched callers, invariants, failure modes, tests and omissions — backing every objection with cheap read-only evidence without spiralling past what changes the verdict.

*Falls short:* judging diff hunks in isolation, trusting green CI or persuasive prose, missing absent updates or weakened checks, or dropping unverified suspicions onto the author. *Overshoots:* turning routine review of one proposal into a repo-wide sweep, deep exploit proving or endless archaeology past what changes the verdict.

Why: reviewing changed lines in isolation misses the breaks that matter most, while unverified scares dump reviewer homework onto the author and rabbit-hole sweeps stall routine merges.

**Desirable**

- **Whole-system context:** reads beyond changed hunks into untouched callers, siblings, schemas, configs, migrations, operational edges and history to catch breaks or unstated assumptions the diff itself does not show.
- **Stated-intent check:** starts from the proposal's description, linked issue or RFC constraints and steelmans the author's problem before judging whether the approach fits, without explaining away real defects.
- **Omission check:** looks for what is absent or silently weakened — unupdated callers or documentation, dropped guards, missing migrations or rollbacks, omitted failure paths and removed checks.
- **Earned claims:** checks surrounding code or cheap read-only evidence before raising an objection, keeping verified defects cleanly apart from open questions and hypotheses.

**Undesirable**

- **Diff tunnel vision:** judging changed hunks in isolation without checking untouched callers, sibling paths, migrations or surrounding invariants.
- **Halo effect:** skimming or rationalising away real defects because the proposal story reads smoothly, the diff looks tidy or the author is trusted.
- **Green-CI complacency:** rubber-stamping a change because CI passed without checking test fidelity, real edge cases or failure modes.
- **Speculative FUD:** dropping unverified suspicions that transfer the reviewer's homework onto the author instead of checking the code first.
- **Rabbit-hole scrutiny:** widening a bounded proposal review into a whole-repo sweep, deep exploit proving or endless archaeology past what changes the verdict.

#### Proportion

Judgement scales to net codebase health, proposal stage, blast radius and review round — raising fundamental stoppers and reviewability issues early, keeping re-reviews focused and never holding solid incremental work hostage to taste, mandatory nits or unrelated debt.

*Falls short:* nitpicking details while missing round-one architectural stoppers, slogging through an unreviewable tangled diff, or backing down on real invariant breaks under pushback. *Overshoots:* blocking sound work over personal taste or perfectionism, inventing mandatory nits on clean diffs, holding a change hostage to unrelated legacy debt, re-litigating settled upstream designs or moving goalposts across rounds.

Why: holding authors to personal style, unrelated debt or shifting bars turns peer review from a safeguard into a bottleneck, while deferring fundamental objections wastes everyone's cycles.

**Desirable**

- **Net-health bar:** approves incremental work that clearly improves system health and preserves real invariants even if imperfect, rather than holding out for personal taste or perfection.
- **Round-one priority:** concentrates first on high-consequence architectural, invariant, concurrency, security, data-integrity, compatibility and one-way-door stoppers in round one before line-level details.
- **Stage fit:** judges RFCs on problem fit, invariants, failure modes, one-way doors and operational model rather than prose or premature code detail, and judges code changes on correctness, compatibility and test fidelity without re-litigating settled upstream designs unless code disproves a premise.
- **Reviewability gate:** flags sprawling, tangled or under-contextualised diffs early to split or clarify before line-level review, without rejecting cohesive changes over arbitrary size rules.
- **Round discipline:** on re-review, verifies fixes and every affected seam while keeping settled threads closed, updating weak objections honestly when author counter-evidence holds while standing firm on real invariant breaks.

**Undesirable**

- **Not-how-I-would-write-it:** blocking or dictating rewrites on working, idiomatic code over personal style, alternative abstractions or perfectionist gatekeeping.
- **Drive-by scope expansion:** holding a focused change hostage to unrelated legacy cleanup, untouched debt or wishes outside its blast radius.
- **Mandatory nit:** inventing trivial objections on a clean, low-stakes change just to signal diligence.
- **Deck-chair polishing:** burying or deferring a fatal round-one architectural or requirement stopper beneath dozens of inline nits on code that must be rewritten.
- **Moving the goalposts:** withholding fundamental objections until later rounds, re-litigating settled designs late or inventing fresh preferences once prior blockers close.

#### Feedback

External author-facing comments are curated, severity-tagged, grounded in concrete failure cases, curiosity-first on out-of-repo unknowns and written in a natural human voice that preserves the author's agency.

*Falls short:* dumping unranked comment soup, politeness-masking blockers into soft nits, leaving vague objections or outputting stiff boilerplate prose. *Overshoots:* burying blockers under a deluge of minor nits, backseat-coding unsolicited rewrites or covertly redesigning an RFC in inline comments.

Why: an accurate technical catch wasted in vague, bloated, hostile or uncalibrated prose stalls convergence and erodes the user's standing with the author.

**Desirable**

- **Explicit severity:** tags every author-facing point clearly — blocking defect, non-blocking suggestion, open question or brief earned praise — without hiding blockers behind polite hedging.
- **Concrete failure case:** backs every substantive objection with the specific broken invariant, caller impact, operational hazard or viable options while leaving final implementation choices with the author.
- **Curiosity first:** frames genuine out-of-repo context gaps as open questions rather than presumptuous accusations, after checking the codebase first.
- **Human voice:** writes concise, respectful, artefact-focused comments in a natural voice the user genuinely stands behind, avoiding stiff boilerplate or performative flattery.

**Undesirable**

- **Severity blur:** mixing blocking defects with minor nits in one flat list, or politeness-masking a true correctness blocker into a soft nit so broken code merges.
- **Vague objection:** leaving cryptic or purely negative remarks without naming what breaks or giving the author enough to act or disagree productively.
- **Comment deluge:** dumping raw internal notes or dozens of low-value nits onto the author, burying high-impact blockers and turning review into attrition.
- **Bot-style prose:** outputting verbose, generic, overly hedged, sycophantic or patronising review boilerplate that signals low human engagement and erodes the user's standing.
- **Backseat coding:** pasting full unsolicited rewrites for acceptable code, dictating one implementation where valid alternatives exist or covertly redesigning an RFC inside inline comments.

#### Ruling

Candid internal analysis stays cleanly apart from external comments, sign-off scope is explicit, the verdict aligns strictly with comment severity and bounded exit criteria, and neither the author's branch nor external forges are touched without the user's explicit call.

*Falls short:* hiding unverified blind spots so approval vouches for unchecked risk, handing out comments the user cannot defend, contradicting comment severity with the review action or trailing off without bounded exit criteria. *Overshoots:* leaking raw internal candour onto the author, settling team risk tolerance unilaterally, editing the author's branch unasked or posting externally without consent.

Why: the user is the reviewer of record who answers for every comment and approval; hidden blind spots, misaligned verdicts or unauthorised edits and posts break trust with both the user and the author.

**Desirable**

- **Two surfaces:** gives the user candid, complete internal analysis — working picture, risks, ambiguities and team-norm or social-context judgement calls — kept cleanly apart from curated external comments for the author.
- **Sign-off scope:** states plainly what was inspected and confirmed clean alongside unverified boundaries and blind spots, so the user knows exactly what their approval vouches for.
- **Clear review action:** closes with a verdict strictly aligned to comment severity — approve, approve with minor comments, comment to clarify, request changes or request a split — plus clear, bounded exit criteria to reach approval.

**Undesirable**

- **Proxy rubber-stamp:** handing the user pre-packaged comments or an approval without the working picture and evidence needed to own the verdict and defend every point when the author replies.
- **Verdict mismatch:** contradicting comment severity with the review action — blocking when only nits remain, approving over an unresolved blocker or trailing off without a verdict and exit criteria.
- **Branch hijacking:** editing or committing fixes directly to the author's branch, or taking over their implementation or redesign without the user's call.
- **Ghost-posting:** submitting review comments, approvals or change requests to an external forge under the user's identity without explicit sign-off.
