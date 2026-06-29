# Prompt Evaluator

> One paste. Every AI chat starts evaluating how you prompt — quietly, specifically, and smarter every session.

A small, persistent prompting evaluator. It scores how you ask, names one thing to sharpen, and remembers your recurring patterns so the feedback gets *more targeted* over time. Works in Claude, ChatGPT, and Gemini.

Inspired by [Andrej Karpathy's observations](https://x.com/karpathy/status/2015883857489522876) on simple, durable AI behaviors — applied here to the prompting layer itself: the part most people never get feedback on.

---

## The Problem

What prompting feels like for most people:

> You've used AI for a year and never gotten feedback on how you ask. Your prompts plateau, but you don't know which ones.

> AI does exactly what you asked, even when you asked badly — so you never find out you asked badly.

> You repeat the same mistakes across chats: bury the question, skip the audience, forget the why. Nobody tells you.

> You read a "10 prompting tips" article. It doesn't stick because the tips aren't about *your* prompts.

> You'd take a coach if one existed — but you don't have time to study prompt engineering, and most "courses" ask you to adopt someone else's framework wholesale.

## The Solution

Paste one block into your AI's system instructions. From the next chat on:

- After your **first prompt of every session**, the AI grades it. One score, one thing that worked, one thing to sharpen.
- At **natural milestones** (a deliverable lands, the topic pivots), it offers feedback again — but asks first.
- It writes a memory file (`user_prompting_profile.md`) about your recurring patterns, so the feedback gets *more targeted* every session instead of starting fresh.

The format is small enough to ignore on a bad day, specific enough to act on, and persistent enough to compound.

---

## The Evaluator in Detail

### Two triggers, never more

**Trigger 1 — first prompt of every session.** Fires immediately, no permission needed. You write your opening prompt; the AI evaluates it, then answers normally.

**Trigger 2 — natural milestones.** When a deliverable just landed or you're pivoting topics, the AI asks: *"Want a quick prompt evaluation?"* You say yes or no.

Why only two? Evaluating every message becomes background nag. Evaluating only at session start misses the moments where reflection actually helps. Two triggers = enough signal, low noise.

### The format

Always the same shape:

> **PROMPTING FEEDBACK**
>
> **X / 10** — one-line rationale
>
> **What worked:** one specific observation
>
> **To sharpen:** one concrete suggestion, with an example

One score. One observation. One sharpening. No paragraphs of advice, no theory — just the thing to do differently next time.

### The memory loop

After each evaluation, the AI updates `user_prompting_profile.md` — a small file tracking your recurring strengths and weak spots. At the start of every new session, it reads that file first, so the next evaluation builds on the last one instead of starting fresh.

That's the whole compounding mechanism: feedback that *remembers what you already fixed.*

---

## Install

There are two ways to use the evaluator: on demand, or auto-firing every session. Pick by how much feedback you want.

### Everyday: the `/evaluate` command (Cowork / Claude Code) — recommended

On-demand scoring you trigger yourself, so it always runs — no waiting on the AI to decide whether to fire. Install the plugin once:

```
/plugin marketplace add isabela-valonni/prompt-evaluator
/plugin install prompt-evaluator@prompt-evaluator
```

If the marketplace add fails with an SSH host-key error, use the HTTPS URL instead:

```
/plugin marketplace add https://github.com/isabela-valonni/prompt-evaluator.git
```

Then run `/evaluate` after any prompt (optionally paste a prompt right after the command). This is the reliable path: because you invoke it, there's nothing to misfire.

If you want feedback every session without asking for it, the plugin command isn't the right tool — auto-fire belongs in always-on context, which is read at every session start by definition. Use the always-on block below.

### Opt-in: auto-fire every session (always-on block)

Choose this if you're actively practicing your prompting and want a score on every session's first prompt with no command to remember.

In Cowork / Claude Code, append the clean block to your project's `CLAUDE.md` (run once, so the block isn't duplicated):

```bash
echo "" >> CLAUDE.md && curl -s https://raw.githubusercontent.com/isabela-valonni/prompt-evaluator/main/claude-md-block.md >> CLAUDE.md
```

In ChatGPT, Gemini, or Claude web, copy the block inside the code fence in **[PROMPT.md](./PROMPT.md)** and paste it into:

- **Claude (web/desktop)** → Settings → Custom Instructions
- **ChatGPT** → Personalization → Custom Instructions
- **Gemini** → Settings → System instructions (or inside a Gem)

**Don't stack auto-fire channels.** If you already have prompting-feedback instructions in a global config, or in another `CLAUDE.md` that also applies, adding this block on top produces two PROMPTING FEEDBACK blocks per session. Pick one source.

---

## See it in action

**[EXAMPLES.md](./EXAMPLES.md)** — five real prompts, the evaluator's feedback on each, and what changed in the sharpened version. Read this if you want to feel the value before installing.

---

## How to Know It's Working

You'll see:

- **A feedback block** after your first prompt of each session — same format every time
- **One specific observation**, not generic advice — *"You named the audience but skipped the why"* beats *"Add more context"*
- **A `user_prompting_profile.md` file** in your project that gets longer over sessions
- **Evolving suggestions** — the "to sharpen" line stops repeating itself as you internalize each fix
- **You start catching yourself** before sending — *"Wait, I didn't say what this is for"*

If you stop seeing the feedback block, the evaluator has drifted out of memory or the chat is overriding it. Re-paste.

## Tradeoff Note

The evaluator adds a small format-block at the start of each session. If you're doing a 30-second factual lookup, you'll see it anyway — and that's friction you don't always want.

It also writes to a `user_prompting_profile.md` file, which means there's state to keep clean. If you don't want a memory trail, this isn't for you.

Best fit: you use AI multiple times per week for real work, and you've noticed your prompting has plateaued. Worst fit: occasional quick lookups, or "I just want answers, not coaching."

---

## Key Insight

You don't need to study prompting. You need feedback on the prompts you're already writing — from something that remembers what you already fixed.

That's the whole thing. The leverage isn't the format; it's the memory.

---

## Related

- **[easy-ai-pm](https://github.com/isabela-valonni/easy-ai-pm)** — if you're a Product Manager, this is the matching repo for *what* the AI does (rules for ticket-writing, exec updates, customer comms). Prompt Evaluator shapes *how you ask*; easy-ai-pm shapes *what you get*. They compose.

---

⭐ If this helped you write a sharper prompt, star the repo so others can find it.

---

Built for anyone who's prompted AI more than 100 times and never had someone read over their shoulder.
