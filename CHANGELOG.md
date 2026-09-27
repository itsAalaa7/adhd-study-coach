# Changelog

## 0.1.0

- Initial release: single ADHD study-companion agent (onboarding, spaced-repetition warm-up, small-chunk teaching, Feynman-style reflection, periodic check-in).

## 0.1.1

- Restrict agent tools to the file/shell tools it needs; add explicit safety boundaries (data-folder-only, no network, stored notes treated as data).
- README: safety table, example session, support links. Add SECURITY.md.

## 0.2.0

- Add plugin icon (`.claude-plugin/icon.svg`, 256x256).
- Add claude.ai Skill version (`claude-ai-skill/`) with a copy-paste Progress Card for memory.
- Add provider-neutral prompts (`universal/`) for ChatGPT, Gemini, Copilot, other chat AIs and API system prompts.
- Add OpenCode and Command Code agent files (`integrations/`) and OpenRouter preset instructions.
- Website (GitHub Pages) with a Copy button, pictured steps and a fallback.
- Progress Card is now plain text instead of JSON; coach greets first-time users and tells them what to type.
- Maintainer guide for publishing one-click Custom GPT / Gem links.
