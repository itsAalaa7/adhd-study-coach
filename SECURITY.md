# Security

This plugin is a single Markdown agent file. It contains no hooks, scripts, MCP servers or network code, and its instructions limit file access to its own data folder.

## Reporting a problem

If you find a way the agent can be made to read or write outside its data folder, make network calls, or act on instructions hidden in stored notes, please report it privately through GitHub: **Security → Report a vulnerability** on https://github.com/itsAalaa7/adhd-study-coach. For anything non-sensitive, open a regular issue.

## Data

All learner data stays on the learner's machine in the plugin data folder (fallback: `~/.adhd-study-coach/`). The plugin never uploads it.
