# What to learn next: agent instructions, not prompt engineering

*Written 2026-10-21, after a review of how I work with Claude Code.*

## Verdict

I don't need a general prompt-engineering course. I already do most of what one teaches. What I should learn instead is narrower: **how to write and test instructions for agents** (skills, rules and memory). That should take about 2 hours.

## Why not a general course

My everyday prompts are short, and that works because the context carries them: the rules, the memory and the project docs load before I type anything. The gaps I found are not about phrasing a prompt. They are about the instructions around it:

- **I don't say the output format up front.** One comparison table took 3 turns to get right: list, then filter, then add a column.
- **Some of my rules contradict how I actually work.** A standing rule told the agent to open pull requests automatically, while I kept typing "draft it, don't open it yet".
- **Too much context loads every session.** More than 10 global rules, 2 style modes and about 70 memory lines load every time. Some of them overlap or conflict, and every line competes for the agent's attention.
- **Requests I repeat are not skills yet.** For example "is this PR safe to approve?" and "compare sprint tickets with git".

## The plan (about 2 hours)

1. **Skill and rule authoring (about 45 minutes).** Learn how a good skill is structured: when it triggers, what output it must produce, and where it stops applying. Then rewrite one skill I use often.
2. **Testing instructions (about 45 minutes).** Learn to check whether a rule actually changes what the agent does, for example with `claude plugin eval`, instead of assuming it works because it is written down.
3. **Anthropic's prompting best practices (about 20 minutes).** Skim only "be clear and direct" and "specify the output format". Skip role-play prompting and chain-of-thought tricks; current models don't need them.

## First step

Find the one standing rule I override most often and edit it to match what I actually want. For me that is the rule that opens pull requests automatically. It should default to a draft that waits for my go.

## What I already do well (so I don't relearn it)

1. **I turn mistakes into standing instructions.** I catch an error and save it once. The saved note records what happened, why it matters, and where it stops applying.
2. **I make the agent show a draft before anything goes out.**
3. **I narrow the scope**: what's in and what's out.
4. **I ask the agent to show its reasoning** before I trust a claim.
