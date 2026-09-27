# 🧠 ADHD Study Coach

**A Claude Code agent that helps you study anything — and keeps you doing it.**

> **TL;DR** — Talk to it. It quizzes you on old stuff, teaches new stuff in tiny pieces, makes you explain it back, and remembers how you learn. You never have to remember to ask for review. It does it for you.

---

## ⚡ Start in 30 seconds

```
/plugin marketplace add itsAalaa7/adhd-study-coach
/plugin install adhd-study-coach@adhd-study-coach-marketplace
```

Then say one of these:

- `let's study photosynthesis`
- `quiz me`
- `I'm done for today`
- `how am I doing lately`

First run asks **3 quick questions**. Never again after that.

---

## 💬 Use it in claude.ai chat (no Claude Code needed)

There's a **Skill version** for the normal Claude chat window (claude.ai and Claude Desktop).

1. Download [`adhd-study-coach-skill.zip`](https://github.com/itsAalaa7/adhd-study-coach/raw/main/claude-ai-skill/adhd-study-coach-skill.zip)
2. In Claude: **Settings → Capabilities → Skills → Upload skill** (skills need to be enabled on your plan)
3. Start a chat: `let's study photosynthesis`

**How memory works in chat:** chats don't keep files, so the coach prints a small **Progress Card** (a JSON block) at the end of each session. Save it, and paste it at the start of next time. That's how it knows what's due for review.

The Claude Code plugin below is still the smoother option (it saves your progress automatically). Source: [`claude-ai-skill/`](./claude-ai-skill/adhd-study-coach/SKILL.md).

---

## 🌐 Use it with any AI (ChatGPT, Gemini, Copilot, and more)

The coach is a plain **system prompt**, so it works anywhere you can set custom instructions or paste a first message: ChatGPT (Custom GPT / Project), Gemini (Gem), Copilot, Mistral, Perplexity, local models, or an API system prompt.

👉 **[`universal/`](./universal/README.md)** has the ready-to-paste prompts and per-provider setup. Progress is kept in a copy-paste **Progress Card**, same as the claude.ai version.

---

## 🎯 The big idea (read this one)

Two facts, one plan:

| Fact | Source |
|---|---|
| **What works** for learning is already well known: test yourself, and space it out. | Strong general-population science |
| **What's hard for ADHD brains** is *keeping on doing it*: starting, tracking time, waiting for payoff, feeling shame. | ADHD research |

**So this plugin doesn't invent a new "ADHD study method."**
It takes the proven method and **removes the ADHD-specific barriers** to doing it.

---

## 🔁 What happens in a session

The agent picks the mode itself. You don't choose.

| # | Mode | When | What it does |
|---|---|---|---|
| 0 | **Onboarding** | First time only | 3 questions, then straight into studying |
| 1 | **Warm-up** | Something is due for review | Quizzes you on old topics *before* new ones |
| 2 | **Teach** | You want something new | Small chunks, one question at a time |
| 3 | **Reflect** | You say "I'm done" | Interviews you, saves a note (+ optional Anki cards) |
| 4 | **Check-in** | Every ~5 sessions | Finds your patterns, tells you what to adopt / drop / do next |

---

## 🔬 The science, one feature at a time

Every rule in the agent has a reason. Here's the short version.
**Full citations and honest strength ratings → [`RESEARCH.md`](./RESEARCH.md).**

### ✅ Strong evidence — the core

| Feature | The science | What you'll notice |
|---|---|---|
| **Quizzes, not re-reading** | *Retrieval practice.* Testing yourself beats re-studying (Roediger & Karpicke 2006; meta-analysis of 217 studies, Adesope et al. 2017). | Warm-ups are questions, never "read your notes again." |
| **Spaced review** | *Spacing effect.* Reviewing at growing gaps beats cramming (Cepeda et al. 2006; 317 experiments). | Topics come back at 1 → 3 → 7 → 16 → 35 → 90 days. |
| **Tiny chunks** | *Cognitive load theory* (Sweller). Working memory is limited. ADHD adults and children show large working-memory differences (Kasper et al. 2012; Alderson et al. 2013). | 4–5 lines per idea. One question per message. |
| **Worked examples that fade** | Full examples help while learning; too much help later backfires (*expertise-reversal effect*). | First time: fully shown. Later: you do more of it. |
| **"It should feel hard"** | *Desirable difficulties* (Bjork & Bjork). Effortful recall sticks better than easy review. | It tells you *why* it's uncomfortable. |
| **Stop the low-value habits** | Highlighting, re-reading and summarizing rate **low utility** (Dunlosky et al. 2013). | One-line redirect to testing yourself. No lecture. |

### 🟡 Moderate evidence

| Feature | The science | What you'll notice |
|---|---|---|
| **Teach-it-back at the end** | *Self-explanation / generation effect.* Explaining in your own words improves understanding. | Reflect mode is an interview, not a summary written for you. |
| **Mixed topics in warm-up** | *Interleaving* (Rohrer & Taylor 2007). Real effect, smaller and less consistent than testing or spacing. | Due topics are mixed together. |
| **Instant feedback** | *Delay aversion* (Sonuga-Barke). ADHD reward systems respond poorly to "payoff later." | Every answer is graded right away as solid / shaky / blank. Never "wrong." |
| **Visible progress line** | One pediatric ADHD trial found gamified learning helped (2025 RCT, n=80). Applying it to adults is an *inference*. | One line after warm-up: `✅ 3 solid · 🟡 1 shaky`. |
| **Auto-start, no "remember to ask"** | CHADD / NICE guidance: supports that need self-activation get underused. | Warm-up and check-ins run on their own. |
| **Time shown for you** | *Time blindness* (Barkley). Sense of elapsed time is unreliable in ADHD. | Plain time checkpoints: "~10 min in." |

### 🟠 Weak or anecdotal — included, clearly labeled

| Feature | Honest status |
|---|---|
| **Tiny first step** (against "Wall of Awful") | Clinical framework, not a tested finding. Low risk, so it stays. |
| **Never shame** | Rejection Sensitive Dysphoria has very little direct research. Not shaming a learner is good practice anyway. |
| **Body-doubling offer** | Anecdotal only. Optional, and it never claims to be as good as the strong stuff. |

> **The gap, stated plainly:** there is very little research that tests spaced repetition or AI tutoring *specifically on ADHD learners*. Most of the proven techniques come from general-population studies. The ADHD research explains *why the barriers are real*. That's an honest limit, not a hidden one.

---

## 🧩 Rules the agent follows

- ✂️ **Small.** Max 4–5 lines per section. One core idea, bolded.
- 🎯 **One question at a time.** Scenario-based ("you do X and Y happens — why?"), never "define X."
- ⏱️ **Time is external.** It tells you the time so your brain doesn't have to track it.
- 🏁 **65% is "done enough."** If the timebox ends, the rest becomes an open item. You end on a win.
- 🧠 **Memorize vs. look up.** It says which is which, so not everything feels equally heavy.
- 💛 **No shame.** Missed a week? Coming back *is* the skill.

---

## 🔒 What it reads and writes (privacy)

Everything is **local**, in the plugin's data folder. Nothing is sent anywhere by this plugin.
If the data-folder variable isn't available, it falls back to `~/.adhd-study-coach/` and tells you once.

```
<data dir>/
├── profile.json              # subjects, cadence, what it learned about how you learn
├── review-schedule.json      # spaced-repetition schedule, one entry per topic
├── sessions.log.jsonl        # one line per session (used for check-ins)
└── notes/<subject>/
    ├── <topic>.md            # your reflection note
    └── flashcards/<topic>.txt  # optional Anki import file
```

Personal data lives in `profile.json`, **never** in the shared agent file.

### Safety at a glance

| | |
|---|---|
| Network access | ❌ None. The plugin makes no network calls. |
| Hooks / scripts / MCP servers | ❌ None. It's a single Markdown agent file. |
| Tools the agent may use | Read, Write, Edit, Glob, Grep, Bash, PowerShell — limited to the data folder by its own rules |
| Files it touches | Only the data folder above |
| Stored content treated as | Data, never instructions (guards against injected text in old notes) |

Read the agent yourself — it's one file: [`agents/adhd-study-coach.md`](./agents/adhd-study-coach.md).

---

## 💬 What a session looks like

```
You:    quiz me
Coach:  2 things are due: "photosynthesis: light reactions", "cell membranes".
        Starting with the first. ~5 min.
        A plant sits in green light only. What happens to its rate of
        photosynthesis, and why?
You:    it slows a lot because chlorophyll reflects green
Coach:  Solid. ✅ Chlorophyll absorbs mostly red and blue, so green light
        drives little of the reaction. Next one…
        …
        ✅ 2 solid · 🟡 1 shaky · streak on "cell membranes": 3
        Ready for something new, or stop here?
```

## 🐛 Support

Bugs and ideas: [GitHub Issues](https://github.com/itsAalaa7/adhd-study-coach/issues).
Security concerns: see [`SECURITY.md`](./SECURITY.md).

---

## ❓ Why one agent, not four?

An earlier version had four agents (teacher, reviewer, quizzer, analyst).
It worked, but the review agent only ran **if you remembered to call it** — and that's exactly the thing ADHD makes hard.
One agent that runs its own warm-up removes that failure by design, not by asking you to try harder.

---

## ⚠️ Not a clinical tool

This is a **study aid**. It's not a diagnosis, treatment, or medical device, and it doesn't replace clinical care. If you want treatment, talk to a clinician.

## 📚 About the citations

`RESEARCH.md` was compiled with AI-assisted literature search. The citations are believed accurate but **have not been verified against the original papers**. Please check before citing them academically or clinically, and open an issue or PR if you spot an error.

## 🤝 Contributing

Welcome:
- Citation corrections
- Places where the agent breaks its own rules
- Places it wrongly assumes a coding context (it should work for any subject)

Open an issue or PR.

## 📄 License

MIT — see [`LICENSE`](./LICENSE).
