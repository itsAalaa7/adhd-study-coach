# Publish one-click links (maintainers)

Makes a shareable **Custom GPT** and **Gem** so people click a link and start, with nothing to copy. Needs your own ChatGPT / Google account. Menu names change, so treat the steps as a guide.

## Text to use for both

**Name:** ADHD Study Coach

**Description:** A gentle study coach for people with ADHD. Quizzes you on old topics, teaches new ones in tiny steps, never shames. Any subject.

**Instructions:** paste the whole contents of [`adhd-study-coach-compact.md`](./adhd-study-coach-compact.md).

**Conversation starters:**
- `new`
- `Let's study something new`
- `Quiz me (I have a Progress Card)`
- `I'm done for today`

## ChatGPT (Custom GPT)

1. ChatGPT → **Explore GPTs → Create**.
2. **Configure** tab: fill in the name, description, instructions and starters above.
3. Turn **off** Web Browsing, Image generation and Code interpreter (not needed).
4. **Create → Anyone with the link** (or **GPT Store** to be listed). Copy the link.

## Gemini (Gem)

1. Gemini → **Gems → New Gem**.
2. Paste the name and instructions above.
3. Save, then use **Share** to get a link (if sharing is available for your account).

## Add the links to the website and README

1. In `docs/index.html`, fill in the two `url` values in `ONE_CLICK`. The "One click" block on the page appears automatically.
2. In the root `README.md`, add the same links under "Start here".
3. Commit and push. The site updates in about a minute.

Custom GPTs and Gems can't save files or remember between chats for other people, so the **Progress Card** works the same way as everywhere else.
