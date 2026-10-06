# Loopwright project settings

The only contract between this project and the `loopwright` plugin. The `loopwright:developer` and `loopwright:code-reviewer` agents read it, and so can a skill. Keep the section labels as they are.

## Tasks dir

<!-- Folder holding bugs/, features/, unrefined/, done/ and the generated INDEX.md. -->

`tasks/`

## Project rules file

<!-- Project-specific rules the developer follows and the reviewer checks. They add to the generic rules. -->

`docs/agent-rules.md`

## Test command

<!-- The command that runs the full test suite. Write "none" if the project has no tests yet. -->

`uv run pytest -q`

## Test files command

<!-- Optional. Runs only some test files, for the reviewer's base-revision check: the test command with a {files} placeholder and the runner's verbose flag, e.g. python -m pytest -v {files}. {files} must be an argument of its own, and paths in the command use forward slashes (it is split with POSIX shell rules). Write "none" to use the test command plus the file paths. -->

`uv run pytest -v {files}`

## Check commands

<!-- One bullet per check (linter, type checker, ...) the agents must run: a label, the command, and what counts as a pass. -->

- ruff: `uv run ruff check .`. Every file you touched must have zero hits.

## Trailer for commit messages

<!-- Line appended to commit messages. Write "none" for no trailer. -->

`Co-Authored-By: Claude Opus 5.5 <noreply@anthropic.com>`

## Notes

<!-- Anything else the agents need, e.g. commands only the orchestrating session can run. -->

User-facing commands are skills, which subagents can't invoke, so the orchestrating session runs and checks them. For changes to skills or agents, that check runs in a session started with `--plugin-dir <path to the clone>`, per the README's "Developing loopwright".
