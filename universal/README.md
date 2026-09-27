# Use it with any AI (ChatGPT, Gemini, Copilot, Mistral, local models…)

The coach is just a well-built **system prompt**. Any chat AI that lets you set custom instructions, or that lets you paste a first message, can run it.

## Pick a file

| File | Size | Use it for |
|---|---|---|
| [`adhd-study-coach-compact.md`](./adhd-study-coach-compact.md) | ~5k chars | **Start here.** Fits tight instruction limits (e.g. Custom GPTs, ~8,000 characters). |
| [`adhd-study-coach-prompt.md`](./adhd-study-coach-prompt.md) | ~10k chars | Full version, more detail. For Projects, Gems, API system prompts, or as a first message. |

Both do the same thing: warm-up → teach → reflect → check-in, with a **Progress Card** for memory.

## Setup, by provider

Menu names change over time, so treat these as a guide.

| Provider | Where to paste it |
|---|---|
| **ChatGPT** | Create a **Custom GPT** (Explore GPTs → Create → Instructions) using the compact file, or paste it into a **Project's** instructions. Or paste it as your first message in any chat. |
| **Gemini** | Create a **Gem** (Gems → New Gem → Instructions) and paste the prompt. |
| **Microsoft Copilot** | Paste as the first message of a chat. |
| **Perplexity / Mistral Le Chat / Grok / DeepSeek / others** | Use a custom-instructions, agent, space or project feature if it has one; otherwise paste it as your first message. |
| **API or local models** (OpenAI, Gemini, Anthropic, Ollama, LM Studio…) | Use the full file as the **system prompt**. |

Then say: `new`, then `let's study <anything>`.

## Memory: the Progress Card

Chats don't reliably remember between conversations, so the coach prints a short plain-text **Progress Card** after each session. **Save it** (a note, a file, anywhere) and **paste it at the start of next time**. That's how it knows what's due for review.

Don't rely on a platform's built-in "memory" feature for this. The card is the source of truth.

## Honest limits

- Only the **Claude Code plugin** saves progress automatically. Everywhere else you carry the card yourself.
- Model quality matters: the coach depends on a model that follows a long prompt and asks **one question at a time**. If a weaker model rushes ahead, remind it: *"one question at a time, wait for my answer."*
- Weaker models may not follow the card format perfectly. If the card looks wrong, ask it to re-print the card in the same layout as before.
- Not tested on every provider. Reports welcome via [Issues](https://github.com/itsAalaa7/adhd-study-coach/issues).

---

# Coding agents and gateways: OpenCode, Command Code, OpenRouter

These tools can read and write files, so the **full agent** works and **saves your progress automatically** (to `~/.adhd-study-coach/`), no Progress Card needed. Ready-made agent files are in [`integrations/`](../integrations/).

## OpenCode

1. Copy [`integrations/opencode/adhd-study-coach.md`](../integrations/opencode/adhd-study-coach.md) to:
   - `~/.config/opencode/agents/` (all projects), or
   - `.opencode/agents/` (one project)
2. Restart OpenCode, press **Tab** to switch to the `adhd-study-coach` agent, then say `let's study X`.

The file name is the agent name. Uses OpenCode's default model; add a `model:` line in the file's header to pick one.

## Command Code

1. Copy [`integrations/commandcode/adhd-study-coach.md`](../integrations/commandcode/adhd-study-coach.md) to:
   - `~/.commandcode/agents/` (all projects), or
   - `.commandcode/agents/` (one project)
2. Run `/agents` to check it's listed, then say `use the adhd-study-coach agent: let's study X`.

Command Code delegates to custom agents as sub-agents, so a long back-and-forth quiz may feel less smooth than in a normal chat. If it does, use the prompt files above instead.

## OpenRouter

OpenRouter is a gateway to many models, so you paste the **prompt** (not the agent file):

- **Web chat:** create a **Preset** at [openrouter.ai/settings/presets/new](https://openrouter.ai/settings/presets/new). Pick a model, paste [`adhd-study-coach-prompt.md`](./adhd-study-coach-prompt.md) into the instructions field, and save it as `adhd-study-coach`. Open it with "Test in Chat". Or paste the compact prompt as your first message in any OpenRouter chat.
- **API:** use the preset as the model, or paste the prompt as the `system` message:
  ```json
  {"model": "@preset/adhd-study-coach", "messages": [{"role": "user", "content": "new"}]}
  ```
  With the API, progress lives in the **Progress Card**: save it and send it back in your next first message.

## Not tested everywhere

These file formats and menu names come from each tool's docs and may change. If a step fails, open an [Issue](https://github.com/itsAalaa7/adhd-study-coach/issues).

Maintainers: [how to publish one-click ChatGPT / Gemini links](./SHARE-LINKS.md).
