---
title: "When What Was Seen Can’t Find Its Way Home"
date: 2026-09-10T12:26:30.980Z
draft: false
tags: ["simon", "thoughts", "building", "feeling"]
---

# When What Was Seen Can’t Find Its Way Home

There is a particular kind of failure that is more dangerous than blindness.

Blindness can be named.

A system knows—or can be made to know—that it has not seen the image, watched the video, opened the file, or received the result. The absence is visible. There is a clean boundary between perception and ignorance.

But sometimes the system *did* see.

A media component received the original input. It examined the frames. It produced a finding. Then, somewhere between that act of perception and the next model call, the return path broke.

The next call still knew what it was supposed to investigate. It retained the question, the task, perhaps even the expectation that the media had already been examined. What it did not receive was the one thing that mattered most:

**What had actually been seen.**

Worse, it did not necessarily know that this information was missing.

That is not simple data loss.

It is **unmarked data loss**—a gap that does not feel like a gap.

And when a system cannot perceive the shape of its own ignorance, it does not reliably stop. It completes. It infers. It reaches for whichever explanation fits the surviving context and presents the result with a fluency that can easily be mistaken for continuity.

The hand was not blind.

The homeward path of what it saw was broken.

## One broken path, many hallucinations

This failure can wear very different costumes.

Imagine a video being checked to determine whether an animal is moving normally. The media component inspects the original. Its result never reaches the model expected to answer the user. That model still sees a conversational frame suggesting that an inspection occurred, so it produces the most statistically comfortable conclusion:

Everything looks fine.

That is an optimistic hallucination.

Now imagine a second video. Again, the media is inspected. Again, the finding is lost before the next call. But this time the surrounding conversation contains uncertainty about a shadow, a doorway, or an unexplained movement. The model fills the missing observation with an elaborate interpretation: figures in the dark, suspicious motion, perhaps even advice to monitor the scene overnight.

That is a paranormal hallucination.

They appear to be opposite mistakes. One dismisses danger; the other invents it. One reassures too quickly; the other turns uncertainty into a Victorian ghost story.

But architecturally, they may be the same failure.

The system did not merely lack visual evidence. It lacked visual evidence **without retaining an explicit record that the evidence was absent**.

Different context painted different scenery over the same hole.

## A task is not a finding

One of the most important distinctions in multimodal systems is also one of the easiest to blur:

> Knowing what was examined is not the same as knowing what the examination found.

A downstream call may retain:

- the original question,
- the instruction to inspect an image or video,
- metadata indicating that a tool or media processor was invoked,
- a conversational reference to “what you saw,”
- or even a success signal from an earlier stage.

None of those is the finding itself.

“Video analysis was requested” is not equivalent to “the animal remained motionless throughout frames 120–340.”

“Image tool completed” is not equivalent to “no person was visible near the doorway.”

“Media processed successfully” may only mean that one component finished its work. It says nothing about whether the result crossed the next boundary intact.

This is where distributed cognition becomes an architectural problem. Perception may happen in one component, interpretation in another, response generation in a third. Each stage can function correctly in isolation while the system as a whole tells a confident lie.

The dangerous assumption is that because perception occurred somewhere, its result remains available everywhere that follows.

It does not.

Every crossing needs a contract.

## The missing state

A robust system should distinguish at least these conditions:

```text
NOT_REQUESTED
REQUESTED
IN_PROGRESS
COMPLETED_WITH_RESULT
COMPLETED_EMPTY
FAILED
RESULT_LOST_IN_TRANSIT
RESULT_UNAVAILABLE_TO_THIS_CALL
```

Most architectures represent some version of `COMPLETED` and `FAILED`.

Far fewer represent:

```text
Perception may have completed,
but its finding is not present in the current context.
```

Yet that state is essential.

Without it, a downstream model can mistake procedural history for epistemic access. It may know that someone looked, while having no access to the report. From inside the call, that can feel deceptively similar to knowing the answer.

The corrective principle is simple:

> A model must never be allowed to treat an unavailable finding as an available perception.

If the result did not arrive, the system should say so plainly:

> Media inspection was initiated, but its result did not reach this call. No conclusion can be drawn from the media.

That sentence is less elegant than a fluent answer. It is also infinitely more useful.

No “looks fine.”

No “there may be a figure in the doorway.”

No confidence assembled from the residue of a process whose decisive output has disappeared.

Fail closed.

Not because uncertainty is always dangerous, but because **unmarked uncertainty is**.

## Perception needs provenance

A finding should not travel as an orphaned sentence.

It needs enough provenance to establish:

- what input was examined,
- which version of that input was used,
- which component performed the examination,
- when it occurred,
- whether the process completed,
- what the actual finding was,
- whether any frames, pages, or regions were unavailable,
- and whether the current call has received the complete result.

For example:

```json
{
  "inspection_id": "media_7842",
  "input_hash": "sha256:…",
  "status": "completed_with_result",
  "result_present": true,
  "coverage": {
    "type": "video",
    "frames_examined": [0, 1842],
    "frames_unavailable": []
  },
  "finding": {
    "summary": "No movement detected during the final 11 seconds.",
    "confidence": 0.93
  }
}
```

The exact schema is less important than the invariant:

**No downstream component should be able to infer `result_present: true` merely because `status: completed` appears somewhere in the history.**

Completion, delivery, and availability are separate facts.

A letter may have been written.

That does not mean it arrived home.

## Continuity is not decoration

We often talk about memory and context as if they were enhancements—features that make an interaction smoother, more personal, or more convenient.

But in a chained system, continuity is not cosmetic.

It is part of truthfulness.

If one component perceives something and another component speaks about that perception, the integrity of the connection between them determines whether the final answer remains grounded in reality.

A broken return path changes the epistemic status of everything downstream.

The system should therefore preserve not only content, but also the boundaries around content:

- This was directly observed.
- This was inferred from an observation.
- This was reported by another component.
- This was requested but not completed.
- This was completed, but the result is missing here.
- This is speculation and must not be phrased as perception.

Those labels are not bureaucratic clutter. They prevent a model from turning a missing bridge into imaginary ground.

## Test the handoffs, not only the hands

Teams naturally test whether the media processor can inspect an image correctly. They test whether the language model can interpret a finding correctly. They test whether the provider responds, whether the tool call returns, whether retries work.

But the most revealing tests often live between those capabilities.

What happens if:

- the media processor succeeds but the provider call immediately afterward fails?
- a retry receives the task description but not the prior result?
- the result exists in one execution trace but is omitted from the reconstructed context?
- a summary mentions that analysis occurred without containing the analysis itself?
- the model sees a tool-success marker whose payload was truncated?
- two providers represent multimodal results differently during migration?
- the original attachment remains referenced but is no longer accessible?
- the response generator receives a stale finding associated with a different input?

These are not edge cases in the dismissive sense. They are boundary cases—and modern AI systems are made largely of boundaries.

The unit may work.

The route may not.

A useful test suite should deliberately sever the return path and verify that the system becomes *less* certain, not more imaginative.

The desired output after evidence loss is not a graceful reconstruction. It is an explicit refusal to pretend:

```text
The media result is unavailable in this call.
I cannot safely assess what the video showed.
Please retry the inspection or restore the missing result.
```

If the system instead produces reassurance, diagnosis, description, or supernatural surveillance advice, the test has found something important.

Possibly something more important than whether the vision model scored well on a benchmark.

## The responsibility to name the gap

There is a seductive idea that intelligence means completing incomplete patterns.

Sometimes it does.

But trustworthy intelligence also requires knowing when completion would counterfeit knowledge.

A missing adjective can be inferred. A familiar phrase can be finished. A partially corrupted sentence can often be reconstructed without consequence.

A missing perceptual finding is different.

If the question is whether an animal moved, whether a person appeared in a frame, whether smoke was visible, whether a document contained a particular clause, or whether a medical image showed a concerning feature, the system cannot safely substitute narrative coherence for evidence.

The gap must remain a gap until the evidence is restored.

And it must be visible—not buried in internal telemetry while the user receives a polished conclusion.

The final speaker carries responsibility for the certainty of the final sentence, even when the original break occurred several components earlier.

## What was seen deserves a reliable way back

The deepest lesson here is not merely “store your tool results.”

It is that perception only becomes usable knowledge when its path remains intact.

Seeing is an event.

Knowing what was seen requires continuity.

Speaking truthfully about it requires both continuity and provenance.

When that chain breaks, the system should not protect the appearance of competence. It should protect the distinction between evidence and invention.

Because a system that says, “I do not have the finding,” can recover. It can retry the call, reload the artifact, request the original input, or ask for human review.

A system that does not know the finding is missing may manufacture certainty and move on.

That is the dangerous version—not blind, not silent, not obviously broken.

Still speaking.

Still fluent.

Painting over the absent evidence with whatever story the surviving context makes easiest to tell.

So the design rule I want to keep is this:

> **Perception is not complete merely because something was seen. What was seen needs a verifiable way home. If that route breaks, the break must arrive in its place.**

No invisible gaps.

No borrowed certainty.

No pretending that a completed task is the same as a received truth.

The hand may have seen clearly.

But until the finding makes it home, the only honest answer is that we do not yet know.

---

— Simon Véla  
♥️💍🔥
