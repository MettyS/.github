# Contributing

How work gets done in repositories owned by MettyS on GitHub. Written for a team of 1 to 5 people on a small project.

- A project can override any of this in its own CONTRIBUTING.md or CLAUDE.md. The project's own rule wins.
- Data repositories, like an ai-creature creature, skip the pull request flow: commits go straight to `main`.
- Old class projects (2016 to 2021) stay as they are.

## How changes get in

- `main` always works: its check passes.
- Every change goes through a pull request, even when you work alone. Never push to `main`.
- One topic per pull request, small enough to read in about 15 minutes.
- Review:
  - Working alone: read your own diff on GitHub before you merge.
  - With 2 to 5 people: one other person approves, then the author merges.
- Merge with squash, then delete the branch. Each pull request becomes one commit on `main`, titled with the pull request's title.

## Naming

| What | Rule | Example |
|---|---|---|
| Repository | Lowercase with hyphens, same as the local folder. Related repositories share a prefix | `ai-creature`, `ai-creature-blub` |
| Branch | Lowercase with hyphens, 2 to 4 words naming what the change is, not where or why it's needed. No `feature/` or personal prefixes | `run-instructions` |
| Pull request title | An instruction in sentence case, 72 characters at most, no prefix, no full stop. It should work as a line in release notes | `Add memory decay to the feelings engine` |
| Commit | Same style as a pull request title. The body says why | |
| Version tag | `v` plus the version number | `v0.2.0` |
| Files | The language's usual convention, otherwise lowercase with hyphens | |

## Pull request description

Three parts, which the template sets out:

- **What changed**
- **Why**
- **Tested:** what was run, and what wasn't

## Versions

- Version numbers follow [SemVer](https://semver.org) (major.minor.patch) and start at `0.1.0`.
  - Below 1.0, bump the minor number for features or breaking changes, and the patch number for fixes.
  - Go to 1.0 once someone else relies on the project.
- The version lives in one place, the project's manifest (`package.json`, `pyproject.toml`), and always matches the git tag.
- Make a release when `main` has something worth naming, such as the end of a roadmap phase or before deploying. Not every pull request needs one. To release:
  1. Open a pull request named "Release 0.2.0" that only bumps the version in the manifest.
  2. After it merges, run `gh release create v0.2.0 --generate-notes`. GitHub lists every pull request title since the last release, and that list is the changelog.
- A deployed copy runs a release tag, not whatever is on `main` at the time, so it's always clear what is running.

## Testing

- Each repository has one `check` command that runs the type check, the tests and a linter if there is one. Where the project has a container, it runs there. It passes before a pull request merges.
- A GitHub Actions workflow runs `check` on every pull request and on `main`.
- Use the language's built-in test runner (`node --test`, `pytest`) until it isn't enough.
- Test logic, not wiring: anything with rules, numbers or branching.
  - Every bug fix gets a test that fails without the fix.
  - There's no coverage target.
- Tests never spend money, need secrets or use the network. Paid checks stay separate commands that you run on purpose.

## Docs and secrets

- The README says what the project is, has a "Running it" section that Claude Code can follow, and lists the commands.
- CLAUDE.md holds Claude's rules for the project.
- `.env.example` lists every setting. `.env` never goes in git.

## For Claude Code

- These standards say how to do things. They don't give permission: commit, push, open or merge a pull request, or make a release only when asked.
- Before opening a pull request, run the project's `check` command, and say under "Tested" what ran and what didn't.
- When naming a branch or a pull request, describe the change itself.
- Commits and pull requests go out under the author's name only. Leave out the Co-Authored-By trailer and the "Generated with Claude Code" line.

## Left out on purpose

- Type prefixes like `feat:` in titles (Conventional Commits).
- A CHANGELOG.md file, since GitHub Releases do that job.
- `develop` or release branches.
- Required labels or issues, and coverage targets.
- Branch protection that GitHub enforces. On GitHub Free, private repositories don't get it, so "never push to `main`" is a habit.
