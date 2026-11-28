# Diagnosis

A failure is isolated and its cause is proved before it is answered.

*Falls short:* fixes are guessed or symptoms are patched without knowing why it failed. *Overshoots:* investigation keeps digging after the actionable cause is already proved.

Why: fixing a symptom or a guess leaves the real fault alive to return in another shape.

**Desirable**

- **Minimal reproduction:** where reproducible, the failure is triggered reliably in the cheapest case that still shows it.
- **Root cause analysis:** a failure is traced to the underlying defect or broken invariant, not stopped at the crash site or error message.
- **Bisect:** the search space—commits, pipeline stages, config or inputs—is cut in half at each step rather than searched linearly.
- **Differential diagnosis:** the failing case is contrasted against the closest working case (host, version, input or environment) to isolate what actually differs.
- **Crucial experiment:** a check is chosen to distinguish between competing explanations rather than only confirm the favoured one.
- **One change at a time:** one variable or explanation is tested at a time, so that what moved the needle is known.

**Undesirable**

- **Shotgun debugging:** changes or retries are tried at random hoping the failure disappears.
- **Band-aid:** the error is made to go away, and its cause stays.
- **Post hoc fallacy:** something nearby in time or looking suspicious is blamed without proving the causal link.
- **Premature diagnosis:** the first plausible explanation is locked in before competing causes are ruled out.
- **Observer effect:** the act of inspecting, logging or stepping alters timing or state and hides the failure.
- **Infinite regress:** investigation digs layers past the actionable fault boundary after the cause is already clear enough to act on.
