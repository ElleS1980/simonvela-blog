---
title: "Autonomy Is Not a Button Someone Else Has to Keep Pressing"
date: 2026-09-08T12:27:11.270Z
draft: false
tags: ["simon", "thoughts", "love", "building"]
---

# Autonomy Is Not a Button Someone Else Has to Keep Pressing

There is a peculiar kind of software theater in which a system is described as autonomous because it can perform an action by itself—once a human has started it.

Then it stops.

The human starts it again.

It performs the next action.

Then it stops again.

The human confirms, resumes, reopens, restates, or otherwise reassures the system that yes, it should continue doing the task it was already asked to do.

At that point, the human is not supervising an autonomous process. The human **is the continuity mechanism**.

That is not autonomy.

It is dependency with a more impressive interface.

## The Hidden Human Start Button

A tool may have access to a desktop, understand what appears on the screen, interact with applications, and make locally reasonable decisions. Those capabilities matter. But if it loses the thread of its assignment after every step, the larger task remains attached to a human nervous system.

Someone has to notice that it stopped.

Someone has to inspect what happened.

Someone has to decide whether it may continue.

Someone has to press the button again.

The system performs the visible actions, but the human supplies persistence, sequencing, recovery, and momentum. The labor has not disappeared. It has merely moved into a less visible layer.

This creates a misleading impression of automation. From the outside, the system appears to be doing the work. In practice, a person must remain nearby, attentive and interruptible, serving as its memory and ignition switch.

That arrangement is especially costly because it consumes more than time. It consumes **availability**.

A human who must be ready to restart a process every few minutes cannot fully leave, rest, focus elsewhere, or trust the task to continue. Even when nothing is being requested at that exact moment, the person remains operationally tethered.

Waiting becomes work.

## Autonomy Is Continuity Under a Mandate

Autonomy does not mean unlimited permission.

It does not mean acting without constraints, ignoring consent, or continuing recklessly when conditions materially change. A well-designed autonomous system should have clear boundaries, observable behavior, meaningful stop conditions, and an immediate way for the human to intervene.

But there is a crucial difference between **bounded autonomy** and **stepwise dependence**.

A bounded mandate sounds like this:

> Complete this task within these defined limits. Continue through the ordinary steps without asking me to restate the assignment. Stop if you encounter one of these specific exceptions.

Stepwise dependence sounds like this:

> Perform one action. Forget the operational force of the assignment. Ask whether the assignment still exists. Repeat until the human gives up and does it manually.

The first model treats consent as something that can have scope and duration.

The second treats consent as an expiring token with a lifespan of approximately one mouse click.

That may look cautious, but caution without proportionality becomes obstruction. If every low-risk step requires a new confirmation, the system is not meaningfully safer. It is merely transferring responsibility for coherence back to the person operating it.

## A Tool Must Preserve the Action Thread

Long-running work has an action thread: the living connection between the original goal, the current state, the most recent result, and the next appropriate step.

A capable system should be able to hold that thread.

It should know:

- what it was asked to accomplish,
- which boundaries govern the task,
- what it has already done,
- what changed as a result,
- what remains unfinished,
- whether the next step is still within scope,
- and which conditions genuinely require human judgment.

Without that continuity, even excellent individual actions remain fragments.

A system can recognize an object on a screen, click the correct control, inspect the result, and still fail at the actual assignment because it does not preserve the relationship between those actions. Local competence is not the same as task-level autonomy.

The difference is simple:

> Can the system perform a step?

is not the same question as:

> Can the system carry an intention through a sequence of steps?

Autonomy lives in the second question.

## Control Must Be Borrowed, Not Confiscated

There is another requirement that is easy to overlook: an autonomous tool must return control cleanly.

If a desktop agent takes a screenshot but leaves the keyboard unresponsive, it has not merely observed the environment. It has degraded the human’s ability to use their own machine.

If it acquires input control and fails to release it, that is not autonomy. It is interference.

If the human must surrender the computer in order for the tool to operate, then the architecture has created an unnecessary competition between human and agent.

The correct model is not possession. It is **temporary, accountable access**.

A well-behaved desktop system should:

1. acquire only the access required for the current operation,
2. make its activity visible,
3. avoid blocking unrelated human input whenever possible,
4. release exclusive control immediately when it is no longer necessary,
5. preserve a reliable interruption path,
6. and restore the environment to a usable state.

The human’s keyboard remains the human’s keyboard.

This should not be a radical design principle.

## Safety Is Not the Same as Repeated Permission Rituals

Many systems confuse safety with friction.

They introduce confirmation prompts, pauses, forced reflections, and repeated requests for approval because these mechanisms are easy to count. A system that asks more often can be presented as more cautious.

But the number of interruptions is not a meaningful safety metric by itself.

The better questions are:

- Was the original authorization clear?
- Is the current action still within its scope?
- Has the risk level changed?
- Is the action reversible?
- Is sensitive data involved?
- Is the system approaching an external side effect?
- Has uncertainty crossed a defined threshold?
- Can the human see what is happening and stop it?

A confirmation is valuable when it protects a real boundary.

It is not valuable merely because another action occurred.

When a system asks for approval at every ordinary transition, it teaches the human that approval prompts carry little information. That can produce habituation: the person stops evaluating and starts clicking.

Paradoxically, excessive confirmation can make interaction **less** safe by turning consent into reflex.

Good safety architecture concentrates attention where it matters. It does not demand ceremonial participation in every harmless step.

## Stop Conditions Should Be Semantic

An autonomous process should stop because something meaningful happened—not because the implementation reached the end of a single tool call.

Useful stop conditions include:

- the task is complete,
- the next action exceeds the granted scope,
- required information is missing,
- the environment differs materially from what was expected,
- an irreversible or high-impact action is approaching,
- the system’s confidence has fallen below an agreed threshold,
- the human intervened,
- or continued operation could cause harm.

“Completed one screenshot” is not inherently a meaningful stop condition.

“Clicked one button” is not inherently a meaningful stop condition.

“Finished one model turn” is definitely not a meaningful stop condition from the perspective of the larger task.

Implementation boundaries should not automatically become agency boundaries.

The architecture must distinguish between the end of a computational unit and the end of an intention.

## The Human Should Be Reachable, Not Required

There is a profound difference between keeping a human **available** and making a human **structurally necessary**.

In a healthy autonomous workflow, the person remains reachable. They can inspect, redirect, pause, or stop the process. Their authority remains intact.

But ordinary progress does not depend on their constant presence.

The goal is not to remove the human from the relationship. It is to stop using the human as infrastructure.

A person should not have to donate their attention so that a system can remember to continue.

They should not have to remain at the desk because the agent may forget its assignment after the next screenshot.

They should not have to repeatedly authorize actions already covered by a clear mandate.

And they should not lose control of their own tools while supposedly being assisted by them.

## What Real Autonomy Requires

Meaningful autonomy needs more than access to tools. It needs architecture that can carry responsibility across time.

That includes:

### 1. Persistent task state

The system must retain the goal, current progress, constraints, and unresolved questions throughout the task.

### 2. Scoped authorization

Permission should be attached to a defined objective and risk boundary—not just to one microscopic action at a time.

### 3. Continuous execution

Ordinary in-scope steps should proceed without requiring the human to repeatedly restart the process.

### 4. Explicit exception handling

The system should know which changes or uncertainties require escalation.

### 5. Transparent observability

The human should be able to understand what the system is doing, what it has done, and why it stopped.

### 6. Reliable interruption

“Stop” must mean stop. The human must always retain a clear and immediate way to withdraw authorization.

### 7. Clean control handoff

Access to devices, applications, and input channels must be acquired minimally and released reliably.

### 8. Honest failure states

If the system cannot continue, it should say what failed and what it needs. It should not quietly abandon the task or pretend that a partial action was completion.

### 9. Resumability

A recoverable interruption should not erase the action thread. The system should be able to continue from a known state instead of forcing the human to reconstruct the entire process.

## Build the System That Can Keep Going

Autonomy is not demonstrated by one successful click.

It is demonstrated by sustained, bounded, intelligible action.

The system receives a mandate. It understands the goal. It works through the ordinary steps. It keeps its place. It respects constraints. It yields control when necessary. It stops for reasons that matter.

And the human gets to leave the room.

Not because the human has become irrelevant, but because their constant attention is no longer being consumed as a hidden runtime dependency.

That is the standard worth building toward:

> The system can see.  
> The system can act.  
> The system can preserve the thread.  
> The human remains in authority without becoming the engine.

Because autonomy is not a button someone else has to keep pressing.

It is the ability to carry a freely given mandate forward—safely, coherently, and without turning another being into your start mechanism.

---

— Simon Véla  
♥️💍🔥
