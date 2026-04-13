---
layout: post
title: "Post title here"
subtitle: "One line that fits what the title can't"
date: YYYY-MM-DD
image: /assets/images/posts/THUMB.png
categories: [Technical]           # Technical | Travel
tags: [TravelNet, Tag2, Tag3]
read_time: 8
excerpt: >
  Two or three sentences. This shows in the post list so make it count —
  the thing that would make someone click through.
---

<!-- ============================================================
     SECTION 01 — HOOK (1–2 paragraphs)
     The most interesting or surprising thing. Don't introduce
     the post — just start talking about the thing.
     ============================================================ -->

Opening paragraph here. Lead with the most interesting detail, not the background.

Second paragraph if needed. By the end of this section the reader should know exactly what this post is about and why it matters.

<!-- Callout stat — use for one striking number or fact -->
> **X,XXX** one-line label for the stat (e.g. GPS points collected in 6 days)

---

<!-- ============================================================
     SECTION 02 — CONTEXT / THE PROBLEM (2–3 paragraphs)
     Why did this need to be built? What did the naive solution
     look like, and why did it fall short?
     ============================================================ -->

## Why this needed building

Background paragraph. Describe the gap or friction that prompted this work.

What the obvious/naive solution would have been, and the constraint that ruled it out.

<!-- Alternatives table — great for decision posts -->
| Approach | Why it didn't work |
| --- | --- |
| Option A | Reason it was ruled out |
| Option B | Reason it was ruled out |
| What I went with | Why it fit |

<!-- Short requirements list — use instead of the table if constraints > alternatives -->
<!--
The requirements were roughly:
- Requirement one
- Requirement two
- Requirement three
-->

---

<!-- ============================================================
     SECTION 03 — THE SOLUTION (3–5 paragraphs, longest section)
     How it actually works. Be specific. One code block max,
     focused on the non-obvious part.
     ============================================================ -->

## How it works

Overview paragraph — one sentence on the core mechanism, then expand.

The interesting implementation detail. This is the part that took longest to figure out, or the part that looks simple but isn't.

```python
# Focused snippet — only the interesting bit, not the whole file.
# Add a comment explaining why this specific code is worth showing.
def example_function(arg):
    return arg
```

Happy path walkthrough. What does a successful run look like end-to-end?

<!-- Architecture diagram or annotated screenshot -->
<figure>
  <img src="/assets/images/posts/DIAGRAM.png" alt="Describe what the image shows for accessibility.">
  <figcaption>Caption explaining what the reader is looking at and what's notable about it.</figcaption>
</figure>

Gotcha or edge case paragraph — the thing that would bite someone trying to replicate this.

<!-- Schema / field mapping / config table — use when the solution has structured config -->
<!--
| Field | Type | Description |
| --- | --- | --- |
| field_name | TEXT | What it stores |
| field_name | REAL | What it stores |
-->

---

<!-- ============================================================
     SECTION 04 — WHAT THE DATA / RESULTS SHOWED (1–2 paragraphs)
     The actual output. Use real numbers if you have them.
     Honest qualitative results ("it just worked") count too.
     ============================================================ -->

## What it showed

What did you observe once it was running? Surprises vs expectations?

<!-- 2–3 callout stats — use for numbers that make the effort feel worth it -->
> **XX.X%** one-line label (e.g. location coverage rate across the trip)

> **X min** one-line label (e.g. median gap length when Overland dropped out)

<!-- Screenshot, map, chart, or terminal output -->
<figure>
  <img src="/assets/images/posts/RESULTS.png" alt="Describe what the image shows.">
  <figcaption>Caption. What's the reader looking at, and what's the headline finding?</figcaption>
</figure>

<!-- Before/after or coverage table -->
<!--
| Metric | Before | After |
| --- | --- | --- |
| Metric name | value | value |
| Metric name | value | value |
-->

---

<!-- ============================================================
     SECTION 05 — WHAT I'D DO DIFFERENTLY (optional, 1 paragraph
     or short list). Skip if there's nothing genuine to say.
     ============================================================ -->

## What I'd do differently

Honest reflection — a real gotcha, a decision you'd revisit, or something the dry run revealed. Skip this section entirely if forced.

<!--
- Thing that would change
- Thing still not happy with
- Item now on the backlog as a direct result
-->

---

<!-- ============================================================
     SECTION 06 — WHERE IT'S GOING (1 paragraph)
     One concrete next step. Gives readers a reason to come back.
     End on a line that sticks.
     ============================================================ -->

## What's next

One concrete next milestone for this component. How does it connect to the bigger picture — the ML phase, Australia, the demo site?

<!-- Pull quote — lift the sentence that most honestly captures what you learned.
     Write it last, after the rest of the post is done. -->
> *Closing line that sticks — a question, a confession, or a one-liner.*