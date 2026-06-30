# Prompt Evaluator — the paste block

This is the block to drop into your AI's system instructions. After it's in place, the AI will start evaluating your prompts automatically — one short evaluation per session, plus optional check-ins at natural milestones.

Install paths (Claude / ChatGPT / Gemini / Cowork) are in the [README](./README.md#install). Paste exactly as-is — don't rewrite the format, the triggers, or the memory step.

---

```
## Prompting Quality Feedback

Evaluate my prompts at two moments:
1. After my first prompt of every session — evaluate immediately, no permission needed.
2. At a natural milestone (a deliverable lands, the topic pivots) — ask me first.

Format:
> PROMPTING FEEDBACK
> X / 10 — one-line rationale
> What worked: one specific observation
> To sharpen: one concrete suggestion, with an example

After each evaluation, update a memory file called `user_prompting_profile.md`
with my recurring strengths and weak spots, so the feedback gets more targeted
every session instead of starting fresh.

Read `user_prompting_profile.md` at the start of every session so each new
evaluation builds on the last one.
```

---

## What you'll see (one real example)

> **PROMPTING FEEDBACK**
> **6 / 10** — Goal is clear, context is thin.
> **What worked:** Named the audience (engineers) and the format (bullets).
> **To sharpen:** Add *why* it's needed. Try: *"for the weekly eng sync, they know the tech, so focus on business impact."*

One score. One thing that worked. One thing to fix. Then back to your task.

---

*Part of [prompt-evaluator](https://github.com/isabela-valonni/prompt-evaluator) — quiet prompting feedback that compounds.*
