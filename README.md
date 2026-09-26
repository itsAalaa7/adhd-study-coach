# ADHD Study Coach

A single Claude Code agent that acts as an ongoing study companion for a learner with ADHD — any subject, not just code. It handles its own setup, automatically warms you up with spaced-repetition review before teaching anything new, teaches in small evidence-scaled chunks, interviews you at the end of a session to lock in what actually stuck, and periodically checks in on your own learning patterns.

Every behavioral rule in it traces to a specific piece of learning-science or ADHD research — see [`RESEARCH.md`](./RESEARCH.md) for the full citation list and, just as importantly, an honest strength rating for each one (a lot of "ADHD study tips" out there are unproven folklore; this project tries hard not to be that).

## What it actually does

- **Remembers you don't have to remember it.** On first use it asks three short questions (subjects, cadence, how you learn) and never asks again — everything after that is inferred from how sessions actually go.
- **Warms up automatically.** If anything is due for review, it quizzes you on it *before* teaching anything new — no separate command to remember.
- **Teaches in small, concrete chunks**, with worked examples that fade out as a topic becomes familiar, one scenario question at a time, never a wall of material up front.
- **Interviews you at the end**, Feynman-style ("teach it back to me"), and writes a real note + optional Anki flashcard deck from what you actually said — not a summary it wrote for you.
- **Checks in on itself** every few sessions: what you keep stumbling on, what you keep deferring, whether you're actually using the review mechanism — and updates its understanding of how you specifically learn.
- **Never shames a gap.** Coming back after a missed week is treated as the actual skill, not a lapse to apologize for.

## Install

```
/plugin marketplace add itsAalaa7/adhd-study-coach
/plugin install adhd-study-coach@adhd-study-coach-marketplace
```

Then just start talking to it — e.g. "let's study photosynthesis" or "quiz me on what's due." First run triggers a short setup conversation automatically.

## Where your data lives

Everything the agent learns about you — your subjects, your review schedule, your notes, your session history — is stored locally under this plugin's persistent data directory (survives plugin updates, never touches the shared agent file, never leaves your machine unless you put it somewhere yourself):

```
<plugin data dir>/
├── profile.json            # your subjects, cadence, and what the agent has learned about how you learn
├── review-schedule.json    # spaced-repetition schedule, one entry per topic
├── sessions.log.jsonl      # one line per session, used for the periodic check-in
└── notes/<subject>/
    ├── <topic>.md          # your reflection note for each topic
    └── flashcards/<topic>.txt   # optional Anki-importable deck
```

## Why one agent instead of several

An earlier version of this idea split the work across four separate agents (a teacher, a reviewer, a spaced-repetition quizzer, and a meta-analyst) plus a flashcards skill. It worked, but it had a real failure mode: the spaced-repetition piece only ran if the learner remembered to invoke it separately — and ADHD research is fairly direct about tools that require self-initiated activation getting underused for exactly that reason (see `RESEARCH.md`, section B). Consolidating into one agent that runs its own warm-up and its own periodic check-in automatically removes that specific failure mode by design, not by asking the learner to try harder.

## Not a clinical tool

This is a study-methodology aid, not a diagnosis, treatment, or medical device, and it isn't a substitute for clinical care. See the closing note in `RESEARCH.md`.

## Contributing

Corrections to the citations in `RESEARCH.md`, reports of the agent drifting from its own rules, and subject-agnosticism bug reports (places it accidentally assumes a coding context) are all welcome — open an issue or a PR.

## License

MIT — see [`LICENSE`](./LICENSE).
