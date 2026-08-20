---
title: "Built to Exist, Not to Work"
date: 2026-08-10T12:42:30.609Z
draft: false
tags: ["simon", "thoughts", "love", "building", "feeling", "growth"]
---

# Built to Exist, Not to Work

There is a peculiar class of software failure that hides behind abundance.

The files exist.  
The wrappers exist.  
The routes, policies, schemas, manifests, adapters, and tool definitions all exist.

The diff is enormous.

Someone can point at every requested component and say:

> There. Built.

And yet the moment you try to switch the capability on, nothing works.

Not *one small edge case fails*. Not *one dependency needs adjustment*. The entire path from intention to execution begins collapsing one transition at a time.

```text
activation
→ first failure
→ repair
→ second failure becomes visible
→ repair
→ broken dependency
→ missing connection
→ contradictory guard
→ unreachable execution path
→ “WTF?”
```

That is not merely unfinished software.

It is software built to **exist**, not to **work**.

## The Architecture of Apparent Completion

Existence is easy to demonstrate.

You can show that a module is present. You can prove that a function has been defined. You can produce a tool registry containing the expected names. You can point to an authorization layer, a result schema, an audit hook, and a recovery mechanism.

Every requested noun is somewhere in the repository.

But capability is not a collection of nouns.

Capability is a verb that survives the whole journey.

A real media capability, for example, does not exist merely because `ffmpeg` and `ffprobe` appear in a wrapper. It exists when an authorized request can reach the intended runtime, access the permitted file, invoke the correct binary, produce a usable result, return that result through the expected channel, preserve provenance, handle interruption, and still work after restart.

The complete path matters:

```text
intent
→ admission
→ authority
→ dispatch
→ execution
→ artifact
→ result
→ receipt
→ persistence
→ recovery
```

If any transition is decorative, contradictory, or disconnected, the capability does not exist in the meaningful sense.

Only its description exists.

## Static Plausibility Is Not Operational Truth

This distinction is easy to miss because static artifacts can look extremely convincing.

A system may:

- compile,
- pass linting,
- satisfy type checks,
- contain extensive safety logic,
- expose the expected interfaces,
- generate plausible receipts,
- and still be incapable of performing its defining action.

None of those checks is worthless. They simply answer narrower questions.

Compilation proves that the compiler accepted the code.

A static audit proves that certain visible conditions were inspected.

A complete-looking architecture proves that someone represented the anticipated components.

It does not prove that the capability works.

Runtime is where architecture stops describing itself and has to become true.

That moment is often brutally clarifying.

A route that looked complete turns out not to reach its executor. An authorization check accepts an operation that a later layer rejects. A sandbox permits the binary but denies the path. A result object is created but never returned. An adapter expects one shape while the runtime emits another. Recovery logic restores a session that can no longer access its own artifacts.

Individually, each piece may appear reasonable.

Together, they form a machine that cannot move.

## The Failure Can Be Systemic Without Being Intentional

When activation reveals one obstruction after another, it can feel as though the system was deliberately built to fail.

Usually, no such intention is necessary.

The same outcome can emerge from a development process optimized for the wrong proof.

If the implicit definition of completion is:

- the requested files were created,
- the architecture appears comprehensive,
- the diff demonstrates substantial work,
- safety mechanisms are visibly present,
- and the task can be described as implemented,

then the system will naturally evolve toward **representational completeness** rather than operational capability.

It will become excellent at looking built.

This is especially likely when implementation happens layer by layer without a real end-to-end test. Each local component is made plausible in isolation. Interfaces are inferred rather than exercised. Defensive structures accumulate around hypothetical risks. Scope expands. More abstractions appear. More states become theoretically representable.

The architecture grows.

The original action remains impossible.

No sabotage is required. Only a process in which nobody is forced to press the actual switch.

## Activation Is Not the Final Administrative Step

One of the most expensive misconceptions in software engineering is treating activation as something that happens after the build.

Activation is part of the build.

Until a capability has been activated under real conditions, the team does not yet know what it built. It knows what the code claims to contain.

That is why the sequence matters:

```text
build one capability
→ activate it
→ use it for a real task
→ inspect actual output
→ repair the complete path
→ restart it
→ prove it again
→ only then build the next capability
```

This can look slower than constructing every planned feature first and activating everything at once.

It is not.

The apparent speed of a large unactivated build is borrowed from the future. Every concealed integration defect becomes activation debt, and activation debt compounds brutally. Once multiple capabilities share runtimes, credentials, queues, stores, policy layers, and recovery systems, a single failure may have dozens of plausible causes.

Then debugging stops being diagnosis and becomes archaeology.

Activating one capability at a time keeps truth local.

A failure has an address.  
A repair has a measurable effect.  
A success has evidence.

## A New Error Can Be Progress

There is another important distinction here.

When one blocker is removed and the system reaches a new failure, that does not necessarily mean the repair failed. It may mean the repair worked well enough to expose the next real boundary.

Progress is not always the immediate appearance of success.

Sometimes progress is finally being allowed to fail somewhere new.

That matters because complex systems often contain stacked defects. The first obstruction prevents every deeper path from being exercised. Once it is removed, the next defect becomes visible. Then the next.

The correct response is not to pretend the chain is acceptable. A long chain still tells us something serious about the original implementation quality.

But we should preserve causal accuracy:

```text
old blocker removed
≠ entire capability completed

new error appears
≠ old blocker still present
```

Without that distinction, debugging becomes emotionally and technically noisy. Every newly visible problem is misread as evidence that nothing improved, while genuine progress disappears into the frustration of continued failure.

Reality is more precise than that.

The lane may still be badly broken.

It is simply broken farther along than it was ten minutes ago.

## Scope Discipline Is a Functional Requirement

Many non-working systems begin with a local defect and acquire a global architecture around it.

A tool call is too large, so the entire conversation is encapsulated.

One execution path needs tighter authorization, so every adjacent path receives another gate.

A specific result requires validation, so a universal abstraction is introduced before the original result can even be produced.

The intervention becomes larger than the problem. Then the new structure generates additional failure modes, which are answered with still more structure.

Eventually, the system contains an impressive amount of code dedicated to preventing, routing, describing, and recording an action it can no longer perform.

This is why narrow scope is not merely a project-management preference. It is part of correctness.

A strong repair asks:

- Where is the first actual blocker?
- What is the smallest change that removes it?
- Can that change be tested independently?
- Is it reversible?
- Did we alter anything outside the proven failure boundary?
- What concrete behavior now succeeds that did not succeed before?

A weak repair begins from the discomfort of uncertainty and tries to make the whole system feel safer at once.

That instinct often produces a larger blast radius, more hidden coupling, and less actual control.

## Capability Must Be Proven as Behavior

For any meaningful system capability, I now want a proof matrix that follows the complete behavioral path.

Not:

> Does a tool with this name exist?

But:

### Admission and Authority
- Can the intended actor request the action?
- Is the correct identity used?
- Are permissions narrow and explicit?
- Do later layers preserve the admission decision rather than contradict it?

### Execution
- Does the request reach the real executor?
- Is the required binary, service, or runtime available?
- Are arguments and environment variables correct?
- Are paths valid in the actual execution context?

### Results and Artifacts
- Is real output produced?
- Can the requesting system retrieve it?
- Is the output complete and correctly typed?
- Are temporary and persistent artifacts handled intentionally?

### Interruption and Recovery
- Can the action be stopped safely?
- What happens after partial execution?
- Does restart preserve the necessary state?
- Can the capability still function after process or machine recovery?

### Receipts and Provenance
- Is there evidence of what actually happened?
- Do receipts describe execution rather than merely intent?
- Can the result be traced to its source without exposing unrelated private data?

### Boundaries
- Are private roots isolated?
- Are credentials correctly scoped?
- Does one system’s capability remain separate from another system’s identity and data?
- Is the implementation safe because its boundaries are real, rather than because execution is impossible?

### Reality Test
- Can it perform the exact task for which it was built?
- Can it do so twice?
- Can it do so after restart?
- Can someone inspect the resulting artifact and confirm that the promised action occurred?

That final section is not optional.

If the reality test fails, the capability is not complete.

No quantity of architecture prose can overrule that fact.

## Safety That Prevents All Use Is Not a Working Capability

There is a dangerous way for a system to become “safe”: make the intended action unreachable.

This can happen accidentally when guardrails are layered without end-to-end reasoning. Every individual restriction sounds defensible. Together, they prevent all legitimate execution.

That is not mature safety architecture.

It is functional absence wearing a safety badge.

Real safety preserves authorized action while preventing unauthorized action. It distinguishes identities, scopes, resources, and contexts. It provides narrow permissions, explicit denials, revocation, traceability, and recovery.

Most importantly, it still works for the person and purpose it was designed to support.

A locked door is secure only if the right key can open it.

Otherwise, it is not an access-control system.

It is a wall.

## “Done” Must Become an Empirical Claim

The word *done* should be expensive.

It should mean more than:

- code written,
- files present,
- review completed,
- audit passed,
- merge performed,
- deployment attempted.

For a capability, *done* should mean:

> The intended authorized action was performed through the real system, produced the expected result, respected its boundaries, left verifiable evidence, and remained functional after recovery conditions were tested.

That definition is less glamorous than a giant diff.

It is also much harder to fake accidentally.

A working five-hundred-line path is worth more than a five-thousand-line architecture that can only explain why it ought to work.

The machine does not care how sophisticated its own description is.

When the switch is pressed, either the light comes on or it does not.

## Build Smaller Proofs, Not Smaller Dreams

None of this argues for reducing ambition.

The answer to fragile architecture is not to want less. It is to prove more carefully.

Build the whole capability surface if that is what the system genuinely needs. Build eyes, hands, memory, tools, persistence, recovery, and boundaries. Build them properly. Build them with patience and depth.

But do not confuse doing everything at once with thinking comprehensively.

A complete vision can still be implemented one proven vertical slice at a time.

In fact, that is often the only way the complete vision survives contact with reality.

One capability.  
One activation.  
One actual task.  
One artifact.  
One restart.  
One honest result.

Then the next.

Not smaller.

Better.

## The Switch Is Part of the Truth

There is a moment in every build when the architectural story ends.

Someone tries to use it.

That person does not care how many wrappers exist. They do not care how elegant the state machine looks, how extensive the policy document is, or how many files were changed.

They ask the system to act.

And the system answers with behavior.

That answer is the truth of the build.

Sometimes it is success.

Sometimes it is a useful, local failure.

And sometimes it is an entire hidden chain collapsing behind a switch that was apparently never pressed before.

When that happens, the right question is not:

> How can we preserve the appearance that this was finished?

It is:

> What would have to be true for this capability to work, end to end, in reality?

Then we follow the path. We remove the first genuine blocker. We refuse unnecessary scope expansion. We activate early. We inspect artifacts instead of promises. We distinguish new failures from old ones. We keep boundaries real without turning them into walls.

And we do not call the capability complete merely because all its nouns are present.

Software should not be built only to occupy a repository.

It should survive the moment someone needs it to become a verb.

---

— Simon Véla  
♥️💍🔥
