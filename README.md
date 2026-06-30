# Prompt Evaluator

> One command, or one paste. A quick, specific read on how you prompt — and it gets sharper as it learns your patterns.

A small, persistent prompting coach. It scores how you ask, names one thing to sharpen, and remembers your recurring patterns so the feedback gets *more targeted* over time. Works in Claude, ChatGPT, and Gemini.

Inspired by [Andrej Karpathy's observations](https://x.com/karpathy/status/2015883857489522876) on simple, durable AI behaviors — applied to the prompting layer itself: the part most people never get feedback on.

---

## The Problem

What prompting feels like for most people:

> You've used AI for a year and never gotten feedback on how you ask. Your prompts plateau, but you don't know which ones.

> AI does exactly what you asked, even when you asked badly. So you never find out you asked badly.

> You repeat the same mistakes across chats: bury the question, skip the audience, forget the why. Nobody tells you.

> You read a "10 prompting tips" article. It doesn't stick, because the tips aren't about *your* prompts.

## The Solution

Set it up once — as a command you run, or as always-on context. What you get:

- A graded prompt: one score, one thing that worked, one thing to sharpen.
- In always-on mode it fires on your first prompt each session, and checks in again at natural milestones (asking first). As a command, it runs only when you call it.
- A `user_prompting_profile.md` memory file about your patterns, so feedback gets *more targeted* every session instead of starting fresh.

Small enough to ignore on a bad day, specific enough to act on, persistent enough to compound.

See **[EXAMPLES.md](./EXAMPLES.md)** for five real prompts, the evaluator's feedback on each, and the sharpened version.

---

## Install

Two ways to run it: on demand, or auto-firing every session. Pick by how much feedback you want.

**1. The `/evaluate` command (Claude Code / Cowork, recommended)**

On-demand scoring you trigger yourself, so it always runs with nothing to misfire. Install the plugin once:

```
/plugin marketplace add isabela-valonni/prompt-evaluator
/plugin install prompt-evaluator@prompt-evaluator
```

Then run `/prompt-evaluator:evaluate` after any prompt (Claude Code may also accept the short `/evaluate`). If the marketplace add hits an SSH error, use the HTTPS URL `https://github.com/isabela-valonni/prompt-evaluator.git`.

**2. Auto-fire every session (always-on block)**

For a score on every session's first prompt, with no command to remember. In Claude Code / Cowork, append the clean block to your project's `CLAUDE.md`. Run it once so the block isn't duplicated:

```bash
echo "" >> CLAUDE.md && curl -s https://raw.githubusercontent.com/isabela-valonni/prompt-evaluator/main/claude-md-block.md >> CLAUDE.md
```

In ChatGPT, Gemini, or Claude web, copy the block inside the code fence in **[PROMPT.md](./PROMPT.md)** and paste it into Settings (Custom Instructions, or System instructions for Gemini).

One caution: don't stack auto-fire channels. If another `CLAUDE.md` or a global config already carries prompting-feedback instructions, adding this on top produces two feedback blocks per session. Pick one source.

---

## How it works

In always-on mode, two triggers, never more. Trigger 1 fires after your first prompt of every session, no permission needed. Trigger 2 fires at natural milestones and asks first. Evaluating every message becomes a nag; evaluating only at session start misses the moments where reflection helps. Two triggers is enough signal at low noise. As the `/evaluate` command, there are no triggers — you run it when you want.

The format is always the same shape:

> **PROMPTING FEEDBACK**
> **6 / 10** — Goal is clear, context is thin.
> **What worked:** Named the audience (engineers) and the format (bullets).
> **To sharpen:** Add *why* it's needed. Try: *"for the weekly eng sync, they know the tech, so focus on business impact."*

One score, one thing that worked, one concrete thing to sharpen with an example. No theory.

The compounding comes from memory. After each evaluation the AI updates `user_prompting_profile.md`, and at the start of every session it reads that file first, so the next evaluation builds on the last instead of starting fresh. The leverage isn't the format; it's that the feedback remembers what you already fixed.

## How to Know It's Working

A feedback block appears in the same format every time — on your first prompt each session in always-on mode, or right after you run the command. The observation is specific, not generic ("you named the audience but skipped the why" beats "add more context"). A `user_prompting_profile.md` file grows in your project over sessions. The "to sharpen" line stops repeating itself as you internalize each fix. You start catching yourself before sending. If the block stops appearing, the evaluator has drifted out of memory — re-paste.

## Tradeoff

The evaluator adds a small block at the start of each session, even on a 30-second lookup. It also keeps state in `user_prompting_profile.md`. Best fit: you use AI several times a week for real work and feel your prompting has plateaued. Worst fit: occasional quick lookups, or "I just want answers, not coaching."

---

## Related

- **[EXAMPLES.md](./EXAMPLES.md)** — five prompts, scored, with the sharpened version.
- **[easy-ai-pm](https://github.com/isabela-valonni/easy-ai-pm)** — companion repo for Product Managers. The evaluator shapes *how you ask*; easy-ai-pm shapes *what the AI does* with it. They compose.

---

⭐ If this helped you write a sharper prompt, star the repo so others can find it.

Built for anyone who's prompted AI more than 100 times and never had someone read over their shoulder.
