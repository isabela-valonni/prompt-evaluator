# Examples

Five real prompts. For each: what the evaluator says about it, the sharpened version, and what changed.

These aren't strawman prompts. They're the kind people actually type when they're in a hurry.

---

## 1. Drafting (vague brief)

### Original prompt

> *"Write a blog post about AI for project managers."*

### Evaluator feedback

> **PROMPTING FEEDBACK**
> **4 / 10** — Topic is clear, everything else (audience, length, angle, tone) is unspecified.
> **What worked:** Single noun-phrase topic — unambiguous.
> **To sharpen:** Name *one* of: audience, angle, OR length. Example: *"…for PMs new to AI tools, 800 words, focused on workflow not theory."*

### Sharpened prompt

> *"Write an 800-word blog post about AI for PMs new to AI tools. Focus on three workflow shifts (not theory), and assume the reader has tried ChatGPT once and bounced off it."*

### What changed

The angle is now concrete (workflow shifts, not theory), the audience has texture (new to AI tools, tried once and bounced), and the length is bounded. Three rounds of clarification removed.

---

## 2. Summarizing (no audience)

### Original prompt

> *"Summarize this thread."*

### Evaluator feedback

> **PROMPTING FEEDBACK**
> **5 / 10** — Action verb is clear, but for whom and at what depth is missing.
> **What worked:** Concise, no extraneous framing.
> **To sharpen:** Specify the audience and the goal. Example: *"Summarize this thread for the engineer joining Monday — what was decided, what's still open."*

### Sharpened prompt

> *"Summarize this thread for the engineer joining the project Monday. They need to know: what was decided, what's still being argued about, and who to ask about pricing."*

### What changed

Audience specificity (an onboarding engineer, joining Monday) implies the right tone and level. The three-bucket structure (decided / open / who to ask) is now explicit — no guessing.

---

## 3. Asking for advice (buries the question)

### Original prompt

> *"I've been thinking about whether to take this new role and there's a lot of factors at play — comp is better but the team is smaller and I'd be reporting to someone less senior than my current manager. The work seems interesting but it's also a startup so risk is higher. Also my partner just got a job in this city. What do you think?"*

### Evaluator feedback

> **PROMPTING FEEDBACK**
> **5 / 10** — Rich context, but the actual ask is buried at the end and too broad ("what do you think").
> **What worked:** You named the real tradeoffs (comp, team, manager, risk, partner) instead of generic ones.
> **To sharpen:** Lead with the question, not the context. Narrow "what do you think" to a specific frame. Example: *"Which of these 5 factors should weigh most heavily — and what would change your mind?"*

### Sharpened prompt

> *"I'm deciding between two jobs and want help weighing the tradeoffs. Current role: stable, senior manager I trust. New role: better comp, smaller team, less senior manager, startup risk. My partner's new job ties us to this city. Which factor should weigh most heavily in your view, and what would change your mind?"*

### What changed

The question is at the front, not buried. Factors are listed cleanly. The ask is specific (which one weighs most) instead of generic (what do you think). The "what would change your mind" line invites pushback instead of a hedge.

---

## 4. Editing (drive-by improvement risk)

### Original prompt

> *"Fix this paragraph: [paragraph]"*

### Evaluator feedback

> **PROMPTING FEEDBACK**
> **3 / 10** — "Fix" gives the AI license to rewrite everything. You probably wanted a specific change.
> **What worked:** You attached the paragraph itself.
> **To sharpen:** Name what's actually broken — grammar, length, tone, clarity. Otherwise the AI will restructure it. Example: *"Tighten this by half. Keep the voice."*

### Sharpened prompt

> *"Tighten this paragraph by 50%. Keep my voice (not corporate). Don't reorder the points."*

### What changed

Goal is specific (50% shorter). What to preserve is named (voice, point order). This eliminates the worst AI editing failure: drive-by restructuring of things you didn't ask to change.

---

## 5. Code question (no context)

### Original prompt

> *"Why isn't my code working?"*

### Evaluator feedback

> **PROMPTING FEEDBACK**
> **2 / 10** — The AI has no code, no error, no expected behavior, no context. This is almost a placeholder for a prompt.
> **What worked:** It's short.
> **To sharpen:** Three pieces, one prompt: the code, the actual error (or actual output), and what you expected. Example: *"This function returns None when I expected a list. Code: [...]. Call site: [...]. Expected: [...]. Got: [...]."*

### Sharpened prompt

> *"This Python function returns `None` when I expected a list of dicts.
>
> Function: `[code]`
> Call site: `[code]`
> Expected: `[{'id': 1, 'name': 'foo'}]`
> Got: `None` — no error raised.
>
> Why is it returning None?"*

### What changed

Three artifacts now exist (code, call site, expected-vs-actual). The "no error raised" detail is itself a diagnostic clue. AI can now reason about the gap instead of guess at the problem.

---

## The pattern

Look at what every sharpened prompt has that the original didn't:

| Original weakness | What the sharpening added |
|-------------------|---------------------------|
| Vague brief | One concrete constraint (audience, length, angle) |
| No audience | Named reader + their context |
| Buried question | Question moved to front; specific frame |
| "Fix" / "improve" | Named what to change *and* what to preserve |
| Missing artifacts | Code + actual output + expected output |

None of these are advanced prompting techniques. They're things you'd notice yourself if someone read your prompt back to you before you sent it.

That's the evaluator's job: reading the prompt back to you, fast, with one specific thing to do next time.

---

## Key insight

The evaluator doesn't teach you prompting theory. It just makes you *notice* the gap between what you typed and what you meant — once per session, in 30 seconds.

Over a year of sessions, that compounds into a sharper prompter than any course produces.

---

*Part of [prompt-evaluator](https://github.com/isabela-valonni/prompt-evaluator) — quiet prompting feedback that compounds.*
