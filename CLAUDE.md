# claude-read-aloud — rules for the session

What the plugin does and how to install and use it — README.md.

- Two pieces: the Claude Code plugin (`.claude-plugin/`, `hooks/`, `skills/`, `scripts/`) and the VS Code extension
  (`vscode-extension/`).
- Do not run tests in the session: the pull request runs them; only when the human asks.
- A test file is no longer than 1500 lines: a suite, a scene and the shared code in `tests/` — helpers and the runner. A
  long file runs as one process and is not split between the blocks of a run. A file past the limit is split into suite
  files by topic (`tests/<topic>.test.mjs`), the shared code goes to its own file next to them (`tests/helpers.mjs`).
  Checks move word for word and in the same order; a suite sets up by itself the environment the checks before the cut
  left. The runner runs the suites at once, in lines of blocks. A new check goes to the suite of its topic, not to the
  biggest one. In repositories with test-audit (from 0.4.0) a long file is an auditor error.
- No AI in commits or pull requests: no co-author trailers, no «Generated with». Changes go through pull requests;
  merges, tags and pushes only when the owner asks.
