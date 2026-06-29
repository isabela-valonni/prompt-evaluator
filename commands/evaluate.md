---
description: Score the prompt I just wrote and give me one thing to sharpen
---

Evaluate the user's most recent prompt for prompting quality. If the user pasted text after the command, evaluate that text instead.

First, if `user_prompting_profile.md` exists in the working folder, read it so the evaluation reflects the user's recurring patterns rather than starting fresh.

Respond using exactly this format, rendered as a four-line blockquote:

> PROMPTING FEEDBACK
> X / 10 — one-line rationale
> What worked: one specific observation
> To sharpen: one concrete suggestion, with an example

Keep it tight: one score, one strength, one fix. No paragraphs of advice, no theory.

After evaluating, update `user_prompting_profile.md` with the new observation and a "Pattern to watch" line linking this evaluation to earlier ones. Create the file if it does not exist.
