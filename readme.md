# How We Use AI at Work
## PyRVA Meeting — September 2025

**Presenter: Chris Way**

Topic: [Claude](https://docs.claude.com), specifically *Claude Code* and how it integrates with Python and software projects.

---

## Getting Started with Claude Code

- Install Claude Code:

```sh
  npm install -g @anthropic-ai/claude-code
````

* On first run, Claude will:

  * Ask for permissions (whether you trust the code you’ve written).
  * Run as a text-based command line interface.

* Setup steps:

  * You select a directory where Claude operates.
  * The first step is creating a `CLAUDE.md` file with instructions for Claude.
  * Running `/init` generates an initial `CLAUDE.md` based on the project.

---

## Working with `CLAUDE.md`

* Claude writes its findings in Markdown so you can review them.
* Chris emphasized:

  * **Keep `CLAUDE.md` small** → large files degrade quality.
  * Borrowed ideas from Kent Beck’s experiments with AI, including using a very long system prompt.
  * Differences between `CLAUDE.md` and `plan.md` can help separate context from planning information.

---

## Context Window

* Value of Claude often depends on the **size of the context window**.
* Command `/context` shows context usage.
* Problems:

  * When context is compacted, answers get worse.
  * Summarization reduces quality.

* Recommendation: **keep the context window as small as possible**.

---

## Modes and Commands

* **Modes**:

  * Shift+Tab opens *plan mode* and other modes.
  * Acceptance modes: *auto* vs. *one at a time*.

* **Useful commands**:

  * `/context` → show context window usage.
  * `/cost` → shows cost estimates. (Claude Pro has extra costs.)
  * Restarting: just type `go` and Claude reloads from `CLAUDE.md`.

* **Permissions**: stored in `.claude/` so they persist between sessions.

---

## Workflow and Refactoring

* Chris used Claude to perform a **massive refactor**:

  * Claude continuously ran tests.
  * It successfully merged a refactor with pending code changes.

* Output variability:

  * Test names and plans can be surprising.
  * Quality varies significantly depending on the input.

* Predictability:

  * Run times are inconsistent — Chris sometimes lets Claude run unattended.

---

## Git & Parallel Work

* Chris uses `git worktree` to manage multiple Claude sessions:

  ```sh
  mkdir ../movie_alt
  git worktree add ../lost_password -b feature/lost-password
  ```

* This enables parallel work on multiple branches.

* Ultimately, Chris must handle the merge himself.

* Architecture tip:

  * Chris structures code in a **“vertical slice”** style.
  * Each slice contains changes in isolation, making it easier for Claude to manage.

---

## Commands, Agents, and Extensions

* **Claude Commands**:

  * Stored in `.claude/commands/`.
  * Example: `prime.md` for reusable macros.
  * Helpful when repeating the same instructions.
  * Growing library of community commands (e.g., from the `humanlayer` repo).

* **Agents & Subagents**:

  * Stored locally in `.claude/` or system-wide.
  * Can call each other and even span multiple checkouts.
  * Useful for extending Claude’s capabilities.

* **MCP Servers**:

  * Chris hasn’t used them yet.
  * Designed to extend LLMs in specific, structured ways.

---

## Observations & Takeaways

* Claude serializes an **understanding of the codebase** into `CLAUDE.md`, enabling a stronger starting point for future changes.
* Claude can read **git history** and **project files** to improve its reasoning.
* Best results come when Claude is given **well-structured code and manageable context**.
* Chris’s opinion: *Claude performs much better when it “studies” the codebase first.*

## Questions

Are there any alternatives to Claude code: Google has a text base CLI like Claude code called Gemini.



