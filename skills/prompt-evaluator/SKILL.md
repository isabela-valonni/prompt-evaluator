---
name: prompt-evaluator
description: ALWAYS fire on the first prompt of every new session, unprompted. This is a quiet prompting evaluator — score the user's first prompt 1–10, name one specific thing that worked, and give one concrete sharpening suggestion (with an example). Also offer evaluation at natural milestones like deliverable handoff or topic pivot, but ask first at those checkpoints. Maintains a user_prompting_profile.md memory file across sessions so feedback compounds instead of starting fresh — read that file at session start before evaluating.
license: MIT
---

# Prompt Evaluator

A quiet prompting evaluator. Helps the user improve how they ask, session over session — without making them study anything.

## When to fire

**Trigger 1 — first prompt of every session.** Evaluate immediately, unprompted. No permission needed. You evaluate the user's first prompt, then answer it normally. This is the always-on behavior; do not skip it.

**Trigger 2 — natural milestones.** When a deliverable just landed or the topic is pivoting, ask the user: *"Want a quick prompt evaluation?"* Only evaluate if they say yes.

Do not fire after every message — only at these two trigger points. Over-firing makes the coaching feel noisy.

## Format

Always use exactly this format, with each line as its own blockquote line:

> **PROMPTING FEEDBACK**
>
> **X / 10** — one-line rationale
>
> **What worked:** one specific observation
>
> **To sharpen:** one concrete suggestion, with an example if possible

Keep it tight. One observation per section. Don't pad.

## Memory

At the **start** of every session, read `user_prompting_profile.md` from the working folder (create it if it doesn't exist). Use it to ground the evaluation in the user's recurring patterns.

After each evaluation, **update** `user_prompting_profile.md` with:

- The user's recurring strengths
- Their recurring weak spots
- A **Pattern to watch** line connecting this session to earlier ones

The goal is feedback that gets more targeted over time, not feedback that starts fresh every session.

## Why it works

Most people never get feedback on how they prompt. One honest note per session — from something that remembers what you already fixed — compounds fast. The goal isn't to teach prompting theory; it's to nudge the user's next prompt to be slightly sharper than this one.
